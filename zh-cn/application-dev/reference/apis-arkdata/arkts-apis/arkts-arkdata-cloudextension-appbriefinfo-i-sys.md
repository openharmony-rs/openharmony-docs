# AppBriefInfo（系统接口）

简要应用信息。

**起始版本：** 11

<!--Device-cloudExtension-export interface AppBriefInfo--><!--Device-cloudExtension-export interface AppBriefInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## appId

```TypeScript
appId: string
```

应用程序ID。

**类型：** string

**起始版本：** 11

<!--Device-AppBriefInfo-appId: string--><!--Device-AppBriefInfo-appId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 11

<!--Device-AppBriefInfo-bundleName: string--><!--Device-AppBriefInfo-bundleName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## cloudSwitch

```TypeScript
cloudSwitch: boolean
```

应用程序的云开关。true表示启用云，false表示不启用云。

**类型：** boolean

**起始版本：** 11

<!--Device-AppBriefInfo-cloudSwitch: boolean--><!--Device-AppBriefInfo-cloudSwitch: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## instanceId

```TypeScript
instanceId: number
```

应用分身ID，0表示应用本身，分身ID依次递增。

**类型：** number

**起始版本：** 11

<!--Device-AppBriefInfo-instanceId: int--><!--Device-AppBriefInfo-instanceId: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

