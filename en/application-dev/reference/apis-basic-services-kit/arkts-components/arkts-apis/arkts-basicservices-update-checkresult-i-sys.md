# CheckResult (System API)

Indicates the version check result.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## isExistNewVersion

```TypeScript
isExistNewVersion: boolean
```

Whether a new version is available. The value **true** indicates that a new version is available, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## newVersionInfo

```TypeScript
newVersionInfo: NewVersionInfo
```

Information about the new version.

**Type:** [NewVersionInfo](arkts-basicservices-update-newversioninfo-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
