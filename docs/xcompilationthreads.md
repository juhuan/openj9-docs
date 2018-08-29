<!--
* Copyright (c) 2017, 2018 IBM Corp. and others
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
* [2] http://openjdk.java.net/legal/assembly-exception.html
*
* SPDX-License-Identifier: EPL-2.0 OR Apache-2.0 OR GPL-2.0 WITH
* Classpath-exception-2.0 OR LicenseRef-GPL-2.0 WITH Assembly-exception
-->

# -XcompilationThreads 


Use this option to specify the number of compilation threads that are used by the JIT compiler.

## Syntax

        -XcompilationThreads<n>

: where `<n>` is the number of threads, in the range 1-4 inclusive. A number greater than 4 prevents the Java&trade; VM from starting successfully. 

: Setting the compilation threads to zero does not prevent the JIT from working. Instead, if you do not want the JIT to work, use the [`-Xint`](xint.md) option.

## Explanation

When multiple compilation threads are used, the JIT might generate several diagnostic log files. A log file is generated for each compilation thread. The naming convention for the log file generated by the first compilation thread uses the following pattern:

    :::java
    <specified_filename>.<date>.<time>.<pid>

The first compilation thread has ID 0. Log files generated by the second and subsequent compilation threads append the ID of the corresponding compilation thread as a suffix to the log file name. The pattern for these log file names is as follows:

    :::java
    <specified_filename>.<date>.<time>.<pid>.<compilation_thread_ID>

For example, the second compilation thread has ID 1. The result is that the corresponding log file name has the form:

    :::java
    <specified_filename>.<date>.<time>.<pid>.1



<!-- ==== END OF TOPIC ==== xcompilationthreads.md ==== -->
