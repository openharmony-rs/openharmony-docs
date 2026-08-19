# DataOperation

```TypeScript
declare type DataOperation =
  DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation
```

数据操作类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type DataOperation =  DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation--><!--Device-unnamed-declare type DataOperation =  DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| DataAddOperation | 添加数据操作。 |
| DataDeleteOperation | 删除数据操作。 |
| DataChangeOperation | 改变数据操作。 |
| DataMoveOperation | 移动数据操作。 |
| DataExchangeOperation | 交换数据操作。 |
| DataReloadOperation | 重载所有数据操作。 |

