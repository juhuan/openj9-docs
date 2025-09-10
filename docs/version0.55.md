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

# What's new in version 0.55.0

The following new features and notable changes since version 0.54.0 are included in this release:

- [New binaries and changes to supported environments](#binaries-and-supported-environments)
- [New system property added to support a list of java.security property files](#new-system-property-added-to-support-a-list-of-javasecurity-property-files)
- ![Start of content that applies to Java 24 and later](cr/java25plus.png) [New JDK 25 features](#new-jdk-25-features) ![End of content that applies to Java 25 and later](cr/java_close.png)

## Features and changes

### Binaries and supported environments

Eclipse OpenJ9&trade; release 0.55.0 supports OpenJDK 25.

OpenJDK 25 with Eclipse OpenJ9 is a long term support (LTS) release and supersedes OpenJDK 24 with Eclipse OpenJ9.

To learn more about support for OpenJ9 releases, including OpenJDK levels and platform support, see [Supported environments](openj9_support.md).

### New system property added to support a list of java.security property files

A new system property, `-Djava.security.propertiesList` is added to configure a superset of profile files in different java.security property files. Instead of putting those different profiles into a single java.security file, you can now specify a list of java.security property files that have the profiles that you want to use.

For more information, see [`-Djava.security.propertiesList`](djavasecuritypropertieslist.md).

### ![Start of content that applies to Java 25 and later](cr/java25plus.png) New JDK 25 features

The following features are supported by OpenJ9:

- [JEP 508](https://openjdk.java.net/jeps/508): Vector API (Tenth Incubator)

The following features are implemented in OpenJDK and available in any build of OpenJDK 24 with OpenJ9:

- [JEP 470](https://openjdk.java.net/jeps/470): PEM Encodings of Cryptographic Objects (Preview)
- [JEP 502](https://openjdk.java.net/jeps/502): Stable Values (Preview)
- [JEP 505](https://openjdk.java.net/jeps/505): Structured Concurrency (Fifth Preview)
- [JEP 506](https://openjdk.java.net/jeps/506): Scoped Values
- [JEP 507](https://openjdk.java.net/jeps/507): Primitive Types in Patterns, instanceof, and switch (Third Preview)
- [JEP 510](https://openjdk.java.net/jeps/510): Key Derivation Function API
- [JEP 511](https://openjdk.java.net/jeps/511): Module Import Declarations
- [JEP 512](https://openjdk.java.net/jeps/512): Compact Source Files and Instance Main Methods
- [JEP 513](https://openjdk.java.net/jeps/513): Flexible Constructor Bodies

You can find the full list of features for JDK 25 at the [OpenJDK project](https://openjdk.org/projects/jdk/25/).
Any remaining features that are listed either do not apply to OpenJ9 or are not implemented and hence not applicable to OpenJ9 in this release. ![End of content that applies to Java 25 and later](cr/java_close.png)

## Known problems and full release information

To see known problems and a complete list of changes between Eclipse OpenJ9 v0.54.0 and v0.55.0 releases, see the [Release notes](https://github.com/eclipse-openj9/openj9/blob/master/doc/release-notes/0.55/0.55.md).

<!-- ==== END OF TOPIC ==== version0.55.md ==== -->
