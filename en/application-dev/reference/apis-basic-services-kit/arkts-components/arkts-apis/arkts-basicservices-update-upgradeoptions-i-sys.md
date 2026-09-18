# UpgradeOptions (System API)

Defines the upgrade options, which are used to specify the upgrade operation type.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## order

```TypeScript
order: Order
```

Upgrade command, which specifies the execution mode of the upgrade operation. The options are as follows: **DOWNLOAD**: download the upgrade package, which needs to be manually installed later; **INSTALL**: install the upgrade package that has been downloaded; **DOWNLOAD_AND_INSTALL**: download and install the upgrade package, which is the complete upgrade process; **APPLY**: apply the upgrade package that has been installed by restarting device; **INSTALL_AND_APPLY**: install the upgrade package and apply it immediately by restarting the device. Select a proper value based on the current upgrade status and service requirements.

**Type:** [Order](arkts-basicservices-update-order-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
