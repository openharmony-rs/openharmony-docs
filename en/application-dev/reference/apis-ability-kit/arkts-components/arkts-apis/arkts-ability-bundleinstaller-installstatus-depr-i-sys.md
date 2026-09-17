# InstallStatus (System API)

Describes the bundle installation or uninstall status.

**Since:** 7

**Deprecated since:** 9

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

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## statusMessage

```TypeScript
statusMessage: string
```

Installation or uninstall status message.

**SUCCESS**: Installation succeeded.

**STATUS_INSTALL_FAILURE**: Installation failed (no installation file exists).

**STATUS_INSTALL_FAILURE_ABORTED**: Installation aborted.

**STATUS_INSTALL_FAILURE_INVALID**: Invalid installation parameter.

**STATUS_INSTALL_FAILURE_CONFLICT**: Installation conflict. (The basic information of the application to update is inconsistent with that of the existing application.)

**STATUS_INSTALL_FAILURE_STORAGE**: Failed to store the bundle information.

**STATUS_INSTALL_FAILURE_INCOMPATIBLE**: Installation incompatibility. (A downgrade occurs or the signature information is incorrect.)

**STATUS_UNINSTALL_FAILURE**: Uninstallation failed. (The application to be uninstalled is not found.)

**STATUS_UNINSTALL_FAILURE_ABORTED**: Uninstallation aborted. (This error code is not in use.)

**STATUS_UNINSTALL_FAILURE_ABORTED**: Uninstallation conflict. (Failed to uninstall a system application or end the application process.)

**STATUS_INSTALL_FAILURE_DOWNLOAD_TIMEOUT**: Installation failed. (Download timed out.)

**STATUS_INSTALL_FAILURE_DOWNLOAD_FAILED**: Installation failed. (Download failed.)

**STATUS_RECOVER_FAILURE_INVALID**: Failed to restore the pre-installed application.

**STATUS_ABILITY_NOT_FOUND**: Ability not found.

**STATUS_BMS_SERVICE_ERROR**: BMS service error.

**STATUS_FAILED_NO_SPACE_LEFT**: Insufficient device space.

**STATUS_GRANT_REQUEST_PERMISSIONS_FAILED**: Application authorization failed.

**STATUS_INSTALL_PERMISSION_DENIED**: No installation permission.

**STATUS_UNINSTALL_PERMISSION_DENIED**: No uninstallation permission.

**Type:** string

**Default:** Indicates the install or uninstall result string message

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.
