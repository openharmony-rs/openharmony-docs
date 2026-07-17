# DelayedDataLoadHandler

```TypeScript
type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>
```

用于延迟加载数据的处理函数。支持数据发送方根据接收方传入的信息，动态生成数据，实现更灵活、精准的数据交互策略。

该处理函数为异步函数，返回Promise对象，不阻塞主线程，可处理复杂业务逻辑、执行长耗时任务。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>--><!--Device-unifiedDataChannel-type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| acceptableInfo | DataLoadInfo | 否 | 表示数据接收方可以接收的数据类型和数量，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UnifiedData \| null&gt; | Promise对象。resolve返回根据接收方信息生成的UnifiedData对象或null，reject返回错误信息。 |

