# BusinessType (System API)

Represents an upgrade service type.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## subType

```TypeScript
subType: BusinessSubType
```

Upgrade type, which is used to specify the target object to be upgraded.

Use scenarios: The system selects the upgrade package and upgrade process based on the upgrade type.

The value can be **FIRMWARE**, indicating firmware upgrade,which is applicable to upgrade of the system firmware instead of the app.

You are advised to set **subType** to **FIRMWARE** for system firmware upgrade. Other values should be selected for app upgrade.

**Type:** [BusinessSubType](arkts-basicservices-update-businesssubtype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## vendor

```TypeScript
vendor: BusinessVendor
```

Vendor type, which is used to identify the vendor of the upgrade package.

Use scenarios: The system selects the upgrade package management server and verification policy based on the vendor type.

The value can be **PUBLIC**, indicating an open-source vendor, applicable to open-source version upgrade.

You are advised to select a vendor type based on the actual upgrade package source. Set **vendor** to **PUBLIC** for open-source version upgrade.

**Type:** [BusinessVendor](arkts-basicservices-update-businessvendor-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
