# Order (System API)

```TypeScript
export enum Order
```

Enumerates update commands.

**Since:** 9

<!--Device-update-export enum Order--><!--Device-update-export enum Order-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## DOWNLOAD

```TypeScript
DOWNLOAD = 1
```

Download. This command is applicable to the scenario where only the upgrade package is downloaded.

**Since:** 9

<!--Device-Order-DOWNLOAD = 1--><!--Device-Order-DOWNLOAD = 1-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## INSTALL

```TypeScript
INSTALL = 2
```

Install. This command is applicable to the scenario where the downloaded upgrade package is directly installed.

**Since:** 9

<!--Device-Order-INSTALL = 2--><!--Device-Order-INSTALL = 2-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## DOWNLOAD_AND_INSTALL

```TypeScript
DOWNLOAD_AND_INSTALL = 3
```

Download and install. This command is applicable to the scenario where the upgrade package is downloaded and installed.

**Since:** 9

<!--Device-Order-DOWNLOAD_AND_INSTALL = 3--><!--Device-Order-DOWNLOAD_AND_INSTALL = 3-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## APPLY

```TypeScript
APPLY = 4
```

Apply. This command is applicable only to the scenario where the installed upgrade package takes effect. The device will restart to apply the new version. This command is applicable to the scenario where the installation is complete and the device needs to be restarted for the installation to take effect.

**Since:** 9

<!--Device-Order-APPLY = 4--><!--Device-Order-APPLY = 4-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## INSTALL_AND_APPLY

```TypeScript
INSTALL_AND_APPLY = 6
```

Install and apply. After the installation, the device restarts to apply the new version. This command is applicable to the scenario where the system upgrade needs to be completed quickly and take effect immediately.

**Since:** 9

<!--Device-Order-INSTALL_AND_APPLY = 6--><!--Device-Order-INSTALL_AND_APPLY = 6-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
