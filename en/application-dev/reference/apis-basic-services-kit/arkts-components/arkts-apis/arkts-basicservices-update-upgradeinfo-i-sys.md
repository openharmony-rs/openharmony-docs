# UpgradeInfo (System API)

Represents update information.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## businessType

```TypeScript
businessType: BusinessType
```

Upgrade service type.

**Type:** [BusinessType](arkts-basicservices-update-businesstype-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## upgradeApp

```TypeScript
upgradeApp: string
```

Caller package name, which is used to identify the app that calls the upgrade API. The value is in the format of **com.***xxx.xxx.xxx* and consists of multiple segments separated by dots (.). The value is a string of 1 to 255 characters, and each segment ranges from 1 to 64 characters. Only letters, digits, and dots (.) are supported. Each segment must start with a letter and cannot contain consecutive dots (.) or end with a dot (.). An exception is thrown when the value is out of range or the format is incorrect.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
