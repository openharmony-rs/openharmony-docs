# NewVersionInfo (System API)

```TypeScript
export interface NewVersionInfo
```

Represents information about the new version.

**Since:** 9

<!--Device-update-export interface NewVersionInfo--><!--Device-update-export interface NewVersionInfo-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## versionComponents

```TypeScript
versionComponents: Array<VersionComponent>
```

Version components.

**Type:** Array&lt;[VersionComponent](arkts-basicservices-update-versioncomponent-i-sys.md)&gt;

**Since:** 9

<!--Device-NewVersionInfo-versionComponents: Array<VersionComponent>--><!--Device-NewVersionInfo-versionComponents: Array<VersionComponent>-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## versionDigestInfo

```TypeScript
versionDigestInfo: VersionDigestInfo
```

Version digest information.

**Type:** [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md)

**Since:** 9

<!--Device-NewVersionInfo-versionDigestInfo: VersionDigestInfo--><!--Device-NewVersionInfo-versionDigestInfo: VersionDigestInfo-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
