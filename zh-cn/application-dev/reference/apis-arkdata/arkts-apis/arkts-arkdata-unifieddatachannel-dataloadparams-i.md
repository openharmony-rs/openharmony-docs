# DataLoadParams

用于在延迟加载场景下描述发送方的数据加载策略。

当同时传入loadHandler和delayedDataLoadHandler时，优先使用delayedDataLoadHandler，loadHandler不生效。

**起始版本：** 20

<!--Device-unifiedDataChannel-interface DataLoadParams--><!--Device-unifiedDataChannel-interface DataLoadParams-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## dataLoadInfo

```TypeScript
dataLoadInfo: DataLoadInfo
```

用于描述当前发送方可生成的数据类型及数量信息。

**类型：** DataLoadInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataLoadParams-dataLoadInfo: DataLoadInfo--><!--Device-DataLoadParams-dataLoadInfo: DataLoadInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## delayedDataLoadHandler

```TypeScript
delayedDataLoadHandler?: DelayedDataLoadHandler
```

表示用于延迟加载数据的异步处理函数。默认值为undefined，不填写时仅使用loadHandler。

**类型：** DelayedDataLoadHandler

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-DataLoadParams-delayedDataLoadHandler?: DelayedDataLoadHandler--><!--Device-DataLoadParams-delayedDataLoadHandler?: DelayedDataLoadHandler-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## loadHandler

```TypeScript
loadHandler: DataLoadHandler
```

表示用于延迟加载数据的处理函数。该处理函数为同步函数，适用于处理简单业务逻辑，若函数业务逻辑较复杂、执行时间较长（3s以上），推荐使用[DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md)。

**类型：** DataLoadHandler

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataLoadParams-loadHandler: DataLoadHandler--><!--Device-DataLoadParams-loadHandler: DataLoadHandler-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

