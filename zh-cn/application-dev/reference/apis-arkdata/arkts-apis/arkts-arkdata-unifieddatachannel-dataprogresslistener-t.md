# DataProgressListener

```TypeScript
type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void
```

定义获取进度信息和数据的监听回调函数。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void--><!--Device-unifiedDataChannel-type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progressInfo | ProgressInfo | 是 | 定义进度上报的进度信息，用于接收拖拽任务的进度状态和进度百分比。包含progress（进度百分比，取值范围[-1-100]）和status（任务状态码）两个字段，其中progress为-1表示获取数据失败，100表示获取数据完成。 |
| data | UnifiedData \| null | 是 | 进度达到100时获取的数据，进度未到100时返回null。 |

