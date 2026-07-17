# DataLoadHandler

```TypeScript
type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null
```

用于延迟加载数据的处理函数。支持数据发送方根据接收方传入的信息，动态生成数据，实现更灵活、精准的数据交互策略。

该处理函数为同步函数，适用于处理简单业务逻辑，若函数业务逻辑较复杂、执行时间较长（3s以上），推荐使用异步处理函数[DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null--><!--Device-unifiedDataChannel-type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| acceptableInfo | DataLoadInfo | 否 | 表示数据接收方可以接收的数据类型和数量，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UnifiedData \| null | 当延迟处理函数触发时，返回根据接收方信息生成的UnifiedData对象，用于数据传输。若无法生成数据或生成失败则返回null。 |

