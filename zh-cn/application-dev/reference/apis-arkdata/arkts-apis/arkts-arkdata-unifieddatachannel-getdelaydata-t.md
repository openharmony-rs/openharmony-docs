# GetDelayData

```TypeScript
type GetDelayData = (type: string) => UnifiedData
```

对UnifiedData的延迟封装，支持延迟获取数据。当数据接收方请求特定类型数据时，系统会触发此回调函数，数据发送方可在回调中动态生成数据，而非提前准备所有数据。当前只支持同设备剪贴板场景。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-type GetDelayData = (type: string) => UnifiedData--><!--Device-unifiedDataChannel-type GetDelayData = (type: string) => UnifiedData-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 作为延迟数据类型的标识，用于区分不同类型的数据。取值见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)，如'general.plain-text'表示纯文本类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UnifiedData | 当延迟回调触发时，返回包含相应类型数据的UnifiedData对象，可用于跨应用数据共享和传输。 |

