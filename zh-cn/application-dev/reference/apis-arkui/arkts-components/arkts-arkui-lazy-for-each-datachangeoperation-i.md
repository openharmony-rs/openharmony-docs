# DataChangeOperation

改变数据操作。

**起始版本：** 12

<!--Device-unnamed-interface DataChangeOperation--><!--Device-unnamed-interface DataChangeOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

改变的数据的索引值。取值范围是[0, 数据源长度-1]。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeOperation-index: number--><!--Device-DataChangeOperation-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

为改变的数据分配新的键值，默认使用原键值。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeOperation-key?: string--><!--Device-DataChangeOperation-key?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.CHANGE
```

数据改变类型。

**类型：** DataOperationType.CHANGE

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataChangeOperation-type: DataOperationType.CHANGE--><!--Device-DataChangeOperation-type: DataOperationType.CHANGE-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

