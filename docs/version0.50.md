<!--
* Copyright (c) 2017, 2025 IBM Corp. and others
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

# What's new in version 0.50.0

The following new features and notable changes since version 0.49.0 are included in this release:

- [New binaries and changes to supported environments](#binaries-and-supported-environments)
- [New parameter `maxstringlength` added to the `-Xtrace` option](#new-parameter-maxstringlength-added-to-the-xtrace-option)
- ![Start of content that applies to Java 24 and later](cr/java24plus.png) [New JDK 24 features](#new-jdk-24-features) ![End of content that applies to Java 24 and later](cr/java_close.png)

## Features and changes

### Binaries and supported environments

Eclipse OpenJ9&trade; release 0.50.0 supports OpenJDK 24.

OpenJDK 24 with Eclipse OpenJ9 is *not* a long term support (LTS) release.

To learn more about support for OpenJ9 releases, including OpenJDK levels and platform support, see [Supported environments](openj9_support.md).

### New parameter `maxstringlength` added to the `-Xtrace` option

You can use the `maxstringlength` parameter of the `-Xtrace` option to specify the length of the string arguments and return values of a method that are now printed in a trace output in addition to the addresses.

For more information, see [`maxstringlength`](xtrace.md#maxstringlength).

### ![Start of content that applies to Java 24 and later](cr/java24plus.png) New JDK 24 features

The following features are supported by OpenJ9:

- [JEP 472](https://openjdk.java.net/jeps/472): Prepare to Restrict the Use of JNI
- [JEP 486](https://openjdk.java.net/jeps/486): Permanently Disable the Security Manager
- [JEP 491](https://openjdk.java.net/jeps/491): Synchronize Virtual Threads without Pinning

The following features are implemented in OpenJDK and available in any build of OpenJDK 24 with OpenJ9:

- [JEP 478](https://openjdk.java.net/jeps/478): Key Derivation Function API (Preview)
- [JEP 484](https://openjdk.java.net/jeps/484): Class-File API
- [JEP 485](https://openjdk.java.net/jeps/485): Stream Gatherers
- [JEP 487](https://openjdk.java.net/jeps/487): Scoped Values (Fourth Preview)
- [JEP 488](https://openjdk.java.net/jeps/488): Primitive Types in Patterns, instanceof, and switch (Second Preview)
- [JEP 489](https://openjdk.java.net/jeps/489): Vector API (Ninth Incubator)
- [JEP 492](https://openjdk.java.net/jeps/492): Flexible Constructor Bodies (Third Preview)
- [JEP 493](https://openjdk.java.net/jeps/493): Linking Run-Time Images without JMODs
- [JEP 494](https://openjdk.java.net/jeps/494): Module Import Declarations (Second Preview)
- [JEP 495](https://openjdk.java.net/jeps/495): Simple Source Files and Instance Main Methods (Fourth Preview)
- [JEP 496](https://openjdk.java.net/jeps/496): Quantum-Resistant Module-Lattice-Based Key Encapsulation Mechanism
- [JEP 497](https://openjdk.java.net/jeps/497): Quantum-Resistant Module-Lattice-Based Digital Signature Algorithm
- [JEP 498](https://openjdk.java.net/jeps/498): Warn upon Use of Memory-Access Methods in sun.misc.Unsafe
- [JEP 499](https://openjdk.java.net/jeps/499): Structured Concurrency (Fourth Preview)

You can find the full list of features for JDK 24 at the [OpenJDK project](https://openjdk.org/projects/jdk/24/).
Any remaining features that are listed either do not apply to OpenJ9 or are not implemented and hence not applicable to OpenJ9 in this release. ![End of content that applies to Java 24 and later](cr/java_close.png)

## Known problems and full release information

To see known problems and a complete list of changes between Eclipse OpenJ9 v0.49.0 and v0.50.0 releases, see the [Release notes](https://github.com/eclipse-openj9/openj9/blob/master/doc/release-notes/0.50/0.50.md).

<!-- ==== END OF TOPIC ==== version0.50.md ==== -->
