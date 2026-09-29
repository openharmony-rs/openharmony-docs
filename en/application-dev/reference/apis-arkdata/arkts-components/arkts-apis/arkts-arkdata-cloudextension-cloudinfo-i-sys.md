# CloudInfo (System API)

```TypeScript
export interface CloudInfo
```

Represents the cloud information.

**Since:** 11

<!--Device-cloudExtension-export interface CloudInfo--><!--Device-cloudExtension-export interface CloudInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## apps

```TypeScript
apps: Record<string, AppBriefInfo>
```

Brief application information.

**Type:** Record&lt;string, [AppBriefInfo](arkts-arkdata-cloudextension-appbriefinfo-i-sys.md)&gt;

**Since:** 11

<!--Device-CloudInfo-apps: Record<string, AppBriefInfo>--><!--Device-CloudInfo-apps: Record<string, AppBriefInfo>-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## cloudInfo

```TypeScript
cloudInfo: ServiceInfo
```

Cloud service information.

**Type:** [ServiceInfo](arkts-arkdata-cloudextension-serviceinfo-i-sys.md)

**Since:** 11

<!--Device-CloudInfo-cloudInfo: ServiceInfo--><!--Device-CloudInfo-cloudInfo: ServiceInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
