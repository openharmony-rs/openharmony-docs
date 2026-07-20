# DataDeleteOperation

删除数据操作。

**起始版本：** 12

<!--Device-unnamed-interface DataDeleteOperation--><!--Device-unnamed-interface DataDeleteOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

删除数据数量，默认为1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataDeleteOperation-count?: number--><!--Device-DataDeleteOperation-count?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

起始删除位置索引值。取值范围是[0, 数据源长度-1]。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataDeleteOperation-index: number--><!--Device-DataDeleteOperation-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.DELETE
```

数据删除类型。

**类型：** DataOperationType.DELETE

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataDeleteOperation-type: DataOperationType.DELETE--><!--Device-DataDeleteOperation-type: DataOperationType.DELETE-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

