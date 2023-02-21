<!--
* Copyright (c) 2017, 2023 IBM Corp. and others
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
* SPDX-License-Identifier: EPL-2.0 OR Apache-2.0 OR GPL-2.0 WITH
* Classpath-exception-2.0 OR LicenseRef-GPL-2.0 WITH Assembly-exception
-->

# What's new in version 0.37.0

The following new features and notable changes since version 0.36.x are included in this release:

- [New binaries and changes to supported environments](#binaries-and-supported-environments)
- [AIX is now built on AIX 7.2 TL5](#aix-is-now-built-on-aix-72-tl5)

## Features and changes

### Binaries and supported environments

Eclipse OpenJ9&trade; release 0.37.0 supports OpenJDK 19.

RHEL 8.2 is out of support. RHEL 8.4 is the new minimum operating system level.

Support for running OpenJDK 8 and OpenJDK 11 on CentOS 6.10 is deprecated and might be removed in a future release. OpenJ9 will not be tested with OpenJDK 11 on CentOS 6.10 for the 0.37.0 release.

To learn more about support for OpenJ9 releases, including OpenJDK levels and platform support, see [Supported environments](openj9_support.md).

### AIX is now built on AIX 7.2 TL5

All AIX compiles are now moved from AIX 7.1 TL5 to AIX 7.2 TL5.

For more information, see [Supported environments](openj9_support.md).

## Known problems and full release information

To see known problems and a complete list of changes between Eclipse OpenJ9 v0.36.x and v0.37.0 releases, see the [Release notes](https://github.com/eclipse-openj9/openj9/blob/master/doc/release-notes/0.37/0.37.md).

<!-- ==== END OF TOPIC ==== version0.37.md ==== -->