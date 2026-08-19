# ProgressInfo

定义进度上报的数据。

**起始版本：** 23

<!--Device-unifiedDataChannel-interface ProgressInfo--><!--Device-unifiedDataChannel-interface ProgressInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## progress

```TypeScript
progress: int
```

系统上报拖拽任务进度百分比。取值范围为[-1-100]的整数，其中-1时代表本次获取数据失败，100时表示本次获取数据完成。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressInfo-progress: int--><!--Device-ProgressInfo-progress: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## status

```TypeScript
status: ListenerStatus
```

系统上报拖拽任务的状态码。

**类型：** [ListenerStatus](arkts-arkdata-unifieddatachannel-listenerstatus-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressInfo-status: ListenerStatus--><!--Device-ProgressInfo-status: ListenerStatus-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

