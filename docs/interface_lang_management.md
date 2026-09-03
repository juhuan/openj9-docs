<!--
* Copyright (c) 2017, 2026 IBM Corp. and others
*
* This program and the accompanying materials are made
* available under the terms of the Eclipse Public License 2.0
* which accompanies this distribution and is available at
* https://www.eclipse.org/legal/epl-2.0/ or the Apache
* License, Version 2.0 which accompanies this distribution and
* is available at https://www.apache.org/licenses/LICENSE-2.0.
*
* This Source Code may also be made available under the
* following Secondary Licenses when the conditions for such
* availability set forth in the Eclipse Public License, v. 2.0
* are satisfied: GNU General Public License, version 2 with
* the GNU Classpath Exception [1] and GNU General Public
* License, version 2 with the OpenJDK Assembly Exception [2].
*
* [1] https://www.gnu.org/software/classpath/license.html
* [2] https://openjdk.org/legal/assembly-exception.html
*
* SPDX-License-Identifier: EPL-2.0 OR Apache-2.0 OR GPL-2.0-only WITH Classpath-exception-2.0 OR GPL-2.0-only WITH OpenJDK-assembly-exception-1.0
-->

# Language management interface

Eclipse OpenJ9&trade; provides MXBean extensions to the standard `java.lang.management` API, which can be used to monitor and manage the Java&trade; virtual machine.
These extensions provide access to information about the state of the OpenJ9 VM and the environment in which it is running. The following tables list the MXBeans by package and describe the monitoring or management capabilities.


**Package: `com.ibm.lang.management`**

|  MXBean  | Description                                                                                                  |
|---------------------------|--------------------------------------------------------------------------------------------------------------|
| `GarbageCollectorMXBean`    | Discovers Garbage Collection (GC) operations (collection times, compactions, heap memory usage, and freed memory). |
| `JvmCpuMonitorMXBean`       | Discovers CPU consumption by category (GC, JIT, or other threads).                                             |
| `MemoryMXBean`              | Discovers memory usage (minimum and maximum heap sizes, and shared classes cache sizes).             |
| `MemoryPoolMXBean`          | Discovers memory pool usage for specific GC policies.                                                         |
| `OperatingSystemMXBean`     | Discovers information about the operating system (memory, CPU capacity/utilization).                         |
| `RuntimeMXBean`             | Discovers information about the runtime environment (CPU load, Java process ID, and VM state)                |
| `ThreadMXBean`              | Discovers information about native thread IDs.                                                                |
| `UnixOperatingSystemMXBean` | Discovers information for Unix operating systems (memory, file descriptors, processors, processor usage, and hardware)|


**Package: `com.ibm.virtualization.management`**


| MXBean | Description                                                                                                  |
|---------------------------|--------------------------------------------------------------------------------------------------------------|
| `GuestOSMXBean`             | Discovers CPU and memory statistics of a virtual machine or logical partition as seen by the Hypervisor.       |
| `HypervisorMXBean`          | Discovers whether the operating system is running on a hypervisor and provides information about the hypervisor.|


**Package: `openj9.lang.management`**

| MXBean | Description                                                                                                  |
|---------------------------|--------------------------------------------------------------------------------------------------------------|
| `OpenJ9DiagnosticsMXBean`   | Configures and dynamically triggers dump agents.                                                              |


For more information about using these MXBeans, read the API documentation. For Java 8, see the [OpenJ9 Language Management API documentation](api-langmgmt.md). <!-- Link to API -->

## ThreadMXBean and locked synchronizers

:fontawesome-solid-pencil:{: .note aria-hidden="true"} **Note:** From the 0.60.0 release onwards, querying locked synchronizer information triggers a global garbage collection (GC) with compaction. Review this section before using `lockedSynchronizers=true` in any regularly scheduled monitoring loop.

The VM tracks object-monitor locks (traditional `synchronized` blocks) natively for deadlock detection. But for deadlock detection that involves `java.util.concurrent` locks, such as `ReentrantLock`, the VM's built-in deadlock detector,`findDeadlockedThreads()`, needs to know which thread *owns* a `ReentrantLock` and which threads are *waiting* for it. This information is available in the locked-sychronizer list. Without the locked-synchronizer list, it can detect deadlocks only in `synchronized` blocks. The detector would silently miss any deadlock that is built on `AbstractOwnableSynchronizer` subclasses.

`java.lang.management.ThreadMXBean` provides runtime thread information, such as state, stack trace, CPU time, and lock contention. Two of its methods accept a `lockedSynchronizers` boolean parameter.

- `ThreadInfo[] getThreadInfo(long[] ids, boolean lockedMonitors, boolean lockedSynchronizers)`
- `ThreadInfo[] dumpAllThreads(boolean lockedMonitors, boolean lockedSynchronizers)`

Either of these methods can be used to retrieve the set of [`java.util.concurrent.locks.AbstractOwnableSynchronizer`](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/locks/AbstractOwnableSynchronizer.html) objects locked by each thread. These methods are useful for deadlock analysis and diagnostic thread dumps.

### Behavior change in the 0.60.0 release

Before the 0.60.0 release, OpenJ9 maintained a locked-sychronizer list continuously during GC cycles. Calling these methods with `lockedSynchronizers=true` was inexpensive because the list was always current.

Starting with the 0.60.0 release, the continuously maintained list is no longer kept. This change improves correctness. With the previous approach, it was difficult to keep the list consistent across all GC policies and concurrent GC phases. Now the list is rebuilt on demand each time the locked-synchronizer information is requested for.

Rebuilding the list requires a walkable heap, a heap in which every live object on the Java heap is reachable and iterable in a single sequential pass. If the heap is not already in a walkable state when `lockedSynchronizers=true` is requested, OpenJ9 triggers a global stop-the-world (STW) GC with compaction, where compaction is the physical movement of all live objects together into one contiguous block of memory, eliminating the gaps left behind by objects that were collected. Every call to `getThreadInfo(ids, lockedMonitors, true)` or `dumpAllThreads(lockedMonitors, true)` might therefore trigger a compacting STW GC pause.

### API usage and GC impact

You can choose the appropriate `ThreadMXBean` variant based on what information you need:

|      Information needed                |     API to use                                                                                |  GC impact |
|----------------------------------------|-----------------------------------------------------------------------------------------------|------------|
| Thread IDs only                        |   `ThreadMXBean.getAllThreadIds()`                                                            |   None     |
| Thread state, no stack                 |   `ThreadMXBean.getThreadInfo(long id)`                                                       |   None     |
| Thread state and bounded stack         |   `ThreadMXBean.getThreadInfo(long[] ids, int maxDepth)`                                      |   None     |
| Thread state, stack and locked monitors (no synchronizers) |   `ThreadMXBean.getThreadInfo(long[] ids, true, false)`                   |   None     |
| Locked synchronizers for diagnostic use  | `ThreadMXBean.getThreadInfo(long[] ids, boolean, true)` or `dumpAllThreads(boolean, true)`  | Global GC with compaction |

:fontawesome-solid-pencil:{: .note aria-hidden="true"} **Note:** `ThreadMXBean.findDeadlockedThreads()` detects deadlocks that involve `java.util.concurrent` locks and does **not** trigger a GC. Use this method for routine deadlock detection instead of querying locked synchronizers.

### Guidance for monitoring and APM tools

If your monitoring tool (for example, IBM HealthCenter, OMEGAMON, or a custom APM agent) calls `getThreadInfo` or `dumpAllThreads`, apply the following guidance:

- Audit every call to `getThreadInfo` and `dumpAllThreads` and check whether `lockedSynchronizers` is `true`. If the call does not explicitly need ownable-synchronizer data, pass `false` instead.
- Avoid using `lockedSynchronizers=true` in high-frequency polling loops. Treat it as a diagnostic operation with a cost comparable to heap dump generation.
- Use `findDeadlockedThreads()` for deadlock detection instead.
- Expect a GC pause whenever `lockedSynchronizers=true` is used. On IBM z/OS, elevated zIIP CPU utilization is also expected during compaction.

### Diagnostic confirmation

To confirm whether a GC pause was caused by a `getLockedSynchronizers` call, enable verbose GC logging (`-verbose:gc`) and look for `reason="rasdump"` in the output. For more information about verbose GC log output, see [Verbose GC log examples](vgclog_examples.md).

<!-- ==================================================================================================== -->


<!-- ==== END OF TOPIC ==== interface_lang_management.md ==== -->
