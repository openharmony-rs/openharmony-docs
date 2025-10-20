# Bundle Manager Subsystem Changelog

## cl.bundlemanager.1 Behavior Change in install for Preinstalled System Applications

**Access Level**

System API

**Reason for Change**

Previously, any version of a system application can be installed directly, allowing versions earlier than or equal to the preinstalled version to be successfully installed. After the change, when reinstalling a preinstalled system application that has been uninstalled, if a preinstalled version exists, it will be installed first, followed by the target version. If the target version number is earlier than or equal to the preinstalled version number, the target version installation will fail, preventing the installation of system applications with versions earlier than or equal to the preinstalled version. Additionally, the target version application can inherit the preinstalled attributes of the preinstalled version.

**Impact of the Change**

This change requires application adaptation.

Before the change, any version of a system application can be installed directly.

After the change, when installing a system application, if a preinstalled version exists and has been uninstalled, the preinstalled version is installed first, followed by the target version. If the target version number is later than the preinstalled version, the installation succeeds; otherwise, the preinstalled version is installed successfully, but the target version installation fails.

**Start API Level**

API 9

**Change Since**

OpenHarmony 5.1.0.52

**Key API/Component Changes**

APIs in **bundle.installer.d.ts**:

1. install(hapFilePaths: Array\<string\>, installParam: InstallParam, callback: AsyncCallback\<void\>)
2. install(hapFilePaths: Array\<string\>, callback: AsyncCallback\<void\>)
3. install(hapFilePaths: Array\<string\>, installParam?: InstallParam): Promise\<void\>

**Adaptation Guide**

When installing a preinstalled system application, if the installation fails but the preinstalled version is successfully installed, ensure that the target version number is later than the corresponding preinstalled version number, and then reinstall the specified application.
