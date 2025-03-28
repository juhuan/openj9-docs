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

# -Dcom.ibm.tools.attach.log.name

Specify the path and prefix for the log files.

## Syntax

        -Dcom.ibm.tools.attach.log.name=<path/prefix>

| Setting                 | Value           |  Default                   |
|-------------------------|-----------------|----------------------------|
| `<path/prefix>`         | [string]        | VM process directory       |

By default, when `-Dcom.ibm.tools.attach.logging=true` is set, timestamped log files are written to the current directory for the running VM. Use the  `-Dcom.ibm.tools.attach.log.name` option to change the path and prefix for the logfiles.


## See also

- [Java&trade; Attach API](attachapi.md)
- [-Dcom.ibm.tools.attach.command_timeout](dcomibmtoolsattachcommand_timeout.md)
- [-Dcom.ibm.tools.attach.directory](dcomibmtoolsattachdirectory.md)
- [-Dcom.ibm.tools.attach.displayName](dcomibmtoolsattachdisplayname.md)
- [-Dcom.ibm.tools.attach.enable](dcomibmtoolsattachenable.md)
- [-Dcom.ibm.tools.attach.id](dcomibmtoolsattachid.md)
- [-Dcom.ibm.tools.attach.logging](dcomibmtoolsattachlogging.md)
- [-Dcom.ibm.tools.attach.shutdown_timeout](dcomibmtoolsattachshutdown_timeout.md)
- [-Dcom.ibm.tools.attach.timeout](dcomibmtoolsattachtimeout.md)


<!-- ==== END OF TOPIC ==== dcomibmtoolsattachlogname.md ==== -->
