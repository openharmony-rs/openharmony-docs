# SyncInfo（系统接口）

端云同步信息，包含最近一次端云同步的时间、结果和状态。

**起始版本：** 12

<!--Device-cloudData-interface SyncInfo--><!--Device-cloudData-interface SyncInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## code

```TypeScript
code: relationalStore.ProgressCode
```

最近一次端云同步的结果。

**类型：** relationalStore.ProgressCode

**起始版本：** 12

<!--Device-SyncInfo-code: relationalStore.ProgressCode--><!--Device-SyncInfo-code: relationalStore.ProgressCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## finishTime

```TypeScript
finishTime: Date
```

最近一次端云同步的结束时间。

**类型：** Date

**起始版本：** 12

<!--Device-SyncInfo-finishTime: Date--><!--Device-SyncInfo-finishTime: Date-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## startTime

```TypeScript
startTime: Date
```

最近一次端云同步的开始时间。

**类型：** Date

**起始版本：** 12

<!--Device-SyncInfo-startTime: Date--><!--Device-SyncInfo-startTime: Date-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## syncStatus

```TypeScript
syncStatus?: SyncStatus
```

最近一次端云同步的状态，默认值为cloudData.SyncStatus.RUNNING。

**类型：** SyncStatus

**起始版本：** 18

<!--Device-SyncInfo-syncStatus?: SyncStatus--><!--Device-SyncInfo-syncStatus?: SyncStatus-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

