# VersionComponent (System API)

Represents a version component.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## componentId

```TypeScript
componentId: string
```

Component ID, which uniquely identifies a component in the upgrade package. The value is obtained from the **versionComponents** array in the version check result and is used for subsequent description query or component information display.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## componentType

```TypeScript
componentType: ComponentType
```

Component type.

**Type:** [ComponentType](arkts-basicservices-update-componenttype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## descriptionInfo

```TypeScript
descriptionInfo: DescriptionInfo
```

Information about the version description file.

**Type:** [DescriptionInfo](arkts-basicservices-update-descriptioninfo-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## displayVersion

```TypeScript
displayVersion: string
```

Display version number.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## effectiveMode

```TypeScript
effectiveMode: EffectiveMode
```

Effective mode. The value **COLD** indicates the cold upgrade, which takes effect after the device is restarted; **LIVE** indicates the hot upgrade, which does not require restarting the device to take effect; **LIVE_AND_COLD** indicates the integrated upgrade, which combines the characteristics of **COLD** and **LIVE**.

**Type:** [EffectiveMode](arkts-basicservices-update-effectivemode-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## innerVersion

```TypeScript
innerVersion: string
```

Internal version number.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## otaMode

```TypeScript
otaMode?: OtaMode
```

OTA mode. Pass this parameter to specify a specific upgrade mode, which is applicable to special scenarios such as the upgrade with limited storage space, fast upgrade, and A/B partition device upgrade. The value **REGULAR_OTA** indicates a regular upgrade, which is applicable to most common upgrade scenarios. **STREAM_OTA** indicates a streaming upgrade, which is applicable to scenarios where the storage space is limited or a fast upgrade is required. **AB_REGULAR_OTA** indicates the normal A/B upgrade and applies to the A/B partition device. **AB_STREAM_OTA** indicates the A/B streaming upgrade and applies to the A/B partition device. If this parameter is not specified, the default value **REGULAR_OTA** is used, indicating that the regular upgrade mode is used.

**Type:** [OtaMode](arkts-basicservices-update-otamode-e-sys.md)

**Since:** 20

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## size

```TypeScript
size: number
```

Size of the upgrade package, in bytes. The value range is [0, +∞]. An exception is thrown if the value is out of range.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## upgradeAction

```TypeScript
upgradeAction: UpgradeAction
```

Upgrade action. The value **UPGRADE** indicates that the upgrade package is a differential package, which applies to incremental upgrade. The value **RECOVERY** indicates that the upgrade package is a repair package, which applies to system failure repair.

**Type:** [UpgradeAction](arkts-basicservices-update-upgradeaction-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
