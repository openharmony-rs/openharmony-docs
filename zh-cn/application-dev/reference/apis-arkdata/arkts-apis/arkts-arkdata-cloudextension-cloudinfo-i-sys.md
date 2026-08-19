# CloudInfo（系统接口）

云信息。

**起始版本：** 23

<!--Device-cloudExtension-export interface CloudInfo--><!--Device-cloudExtension-export interface CloudInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## apps

```TypeScript
apps: Record<string, AppBriefInfo>
```

简要应用信息。

**类型：** Record&lt;string, [AppBriefInfo](arkts-arkdata-cloudextension-appbriefinfo-i-sys.md)&gt;

**起始版本：** 23

<!--Device-CloudInfo-apps: Record<string, AppBriefInfo>--><!--Device-CloudInfo-apps: Record<string, AppBriefInfo>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## cloudInfo

```TypeScript
cloudInfo: ServiceInfo
```

云服务信息。

**类型：** [ServiceInfo](arkts-arkdata-cloudextension-serviceinfo-i-sys.md)

**起始版本：** 23

<!--Device-CloudInfo-cloudInfo: ServiceInfo--><!--Device-CloudInfo-cloudInfo: ServiceInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

