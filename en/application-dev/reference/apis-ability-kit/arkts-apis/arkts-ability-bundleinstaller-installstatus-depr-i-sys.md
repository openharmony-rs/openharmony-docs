# InstallStatus (System API)

```TypeScript
export interface InstallStatus
```

Describes the bundle installation or uninstall status.

**Since:** 7

**Deprecated since:** 9

<!--Device-unnamed-export interface InstallStatus--><!--Device-unnamed-export interface InstallStatus-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## status

```TypeScript
status: bundle.InstallErrorCode
```

Installation or uninstall error code. The value must be defined in [InstallErrorCode](arkts-ability-bundle-installerrorcode-e.md).

**Type:** [bundle.InstallErrorCode](arkts-ability-bundle-installerrorcode-e.md)

**Default:** Indicates the install or uninstall error code

**Since:** 7

**Deprecated since:** 9

<!--Device-InstallStatus-status: bundle.InstallErrorCode--><!--Device-InstallStatus-status: bundle.InstallErrorCode-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## statusMessage

```TypeScript
statusMessage: string
```

String result information indicating installation or uninstallation. The value range includes:

"SUCCESS" : Installation succeeded.</br> "STATUS_INSTALL_FAILURE": Installation failure (the installation file does not exist).</br> "STATUS_INSTALL_FAILURE_ABORTED": Installation aborted. </br> "STATUS_INSTALL_FAILURE_INVALID": Invalid installation parameter. </br> "STATUS_INSTALL_FAILURE_CONFLICT": Installation conflict (commonly caused by inconsistent basic information between the upgrade and the existing application). </br> "STATUS_INSTALL_FAILURE_STORAGE": Failed to store the bundle information. </br> "STATUS_INSTALL_FAILURE_INCOMPATIBLE": Installation incompatible (commonly caused by a downgrade installation or incorrect signature information). </br > "STATUS_UNINSTALL_FAILURE": Uninstallation failure (the application to uninstall does not exist). </br> " STATUS_UNINSTALL_FAILURE_ABORTED": Uninstallation aborted (not used). </br> "STATUS_UNINSTALL_FAILURE_CONFLICT":Uninstallation conflict (failed to uninstall a system application or failed to terminate the application process). </br> "STATUS_INSTALL_FAILURE_DOWNLOAD_TIMEOUT": Installation failure (download timed out).</br> "STATUS_INSTALL_FAILURE_DOWNLOAD_FAILED": Installation failure (download failed). </br> "STATUS_RECOVER_FAILURE_INVALID": Failed to recover the preset application. </br> "STATUS_ABILITY_NOT_FOUND":Ability not found.</br> "STATUS_BMS_SERVICE_ERROR": BMS service error. </br> "STATUS_FAILED_NO_SPACE_LEFT": Insufficient device space.</br> "STATUS_GRANT_REQUEST_PERMISSIONS_FAILED": Failed to grant application permissions. </br> "STATUS_INSTALL_PERMISSION_DENIED": Installation permission missing. </br> "STATUS_UNINSTALL_PERMISSION_DENIED": Uninstallation permission missing.

**Type:** string

**Default:** Indicates the install or uninstall result string message

**Since:** 7

**Deprecated since:** 9

<!--Device-InstallStatus-statusMessage: string--><!--Device-InstallStatus-statusMessage: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.
