# DataDeleteOperation

删除数据操作。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-interface DataDeleteOperation--><!--Device-unnamed-interface DataDeleteOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

删除数据数量，必须是正整数（大于0），且index与count之和不超过数据源长度，默认为1。传入负数时该操作会被忽略；传入0时会异常地将index处的数据项标记删除。index与count之和超过数据源长度时可能导致渲染异常。

**类型：** number

**默认值：** 1

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataDeleteOperation-count?: number--><!--Device-DataDeleteOperation-count?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

起始删除位置索引值。取值范围是[0, 数据源长度-1]。超出取值范围时渲染异常。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataDeleteOperation-index: number--><!--Device-DataDeleteOperation-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.DELETE
```

数据删除类型。

**类型：** [DataOperationType.DELETE](arkts-arkui-dataoperationtype-e.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataDeleteOperation-type: DataOperationType.DELETE--><!--Device-DataDeleteOperation-type: DataOperationType.DELETE-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

