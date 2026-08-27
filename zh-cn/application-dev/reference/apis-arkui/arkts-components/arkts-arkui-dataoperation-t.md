# DataOperation

```TypeScript
declare type DataOperation =
  DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation
```

数据操作类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| [DataAddOperation](arkts-arkui-dataaddoperation-i.md) | 添加数据操作。 |
| [DataDeleteOperation](arkts-arkui-datadeleteoperation-i.md) | 删除数据操作。 |
| [DataChangeOperation](arkts-arkui-datachangeoperation-i.md) | 改变数据操作。 |
| [DataMoveOperation](arkts-arkui-datamoveoperation-i.md) | 移动数据操作。 |
| [DataExchangeOperation](arkts-arkui-dataexchangeoperation-i.md) | 交换数据操作。 |
| [DataReloadOperation](arkts-arkui-datareloadoperation-i.md) | 重载所有数据操作。 |
