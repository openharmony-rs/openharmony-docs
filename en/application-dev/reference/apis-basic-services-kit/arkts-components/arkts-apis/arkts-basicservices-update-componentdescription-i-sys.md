# ComponentDescription (System API)

Represents a component description file.

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

Component ID, which uniquely identifies a component in the upgrade package.

Use scenarios: Pass this parameter to obtain the description of the corresponding component when calling **getNewVersionDescription**. Use this parameter to distinguish different components when displaying version details.

How to obtain: Obtain the value of **componentId** of the corresponding component from the **versionComponents** array in the version check result.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## descriptionInfo

```TypeScript
descriptionInfo: DescriptionInfo
```

Information about the description file.

**Type:** [DescriptionInfo](arkts-basicservices-update-descriptioninfo-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
