# CurrentVersionInfo (System API)

```TypeScript
export interface CurrentVersionInfo
```

Represents information about the current version.

**Since:** 9

<!--Device-update-export interface CurrentVersionInfo--><!--Device-update-export interface CurrentVersionInfo-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## deviceName

```TypeScript
deviceName: string
```

Device name.

**Type:** string

**Since:** 9

<!--Device-CurrentVersionInfo-deviceName: string--><!--Device-CurrentVersionInfo-deviceName: string-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## osVersion

```TypeScript
osVersion: string
```

System version number.

**Type:** string

**Since:** 9

<!--Device-CurrentVersionInfo-osVersion: string--><!--Device-CurrentVersionInfo-osVersion: string-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## versionComponents

```TypeScript
versionComponents: Array<VersionComponent>
```

Version components.

**Type:** Array&lt;[VersionComponent](arkts-basicservices-update-versioncomponent-i-sys.md)&gt;

**Since:** 9

<!--Device-CurrentVersionInfo-versionComponents: Array<VersionComponent>--><!--Device-CurrentVersionInfo-versionComponents: Array<VersionComponent>-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
