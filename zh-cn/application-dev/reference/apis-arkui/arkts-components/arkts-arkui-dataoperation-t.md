# DataOperation

```TypeScript
declare type DataOperation =
  DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation
```

定义数据操作类型。

> **说明**

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type DataOperation =
  DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation--><!--Device-unnamed-declare type DataOperation =
  DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| DataAddOperation | Represents Represents Represents Represents Represents Represents Represents 添加单个数据。 |
| DataDeleteOperation | Represents Represents Represents Represents Represents Represents Represents 删除单个数据。 |
| DataChangeOperation | Represents Represents Represents Represents Represents Represents Represents 执行单个数据的插入、更新或删除。 |
| DataMoveOperation | Represents Represents Represents Represents Represents Represents Represents 移动单个数据。 |
| DataExchangeOperation | Represents Represents Represents Represents Represents Represents Represents 交换单个数据。 |
| DataReloadOperation | Represents Represents Represents Represents Represents Represents Represents 重载所有数据。 |

