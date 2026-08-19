# DataDeleteOperation

删除单个数据。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface DataDeleteOperation--><!--Device-unnamed-export interface DataDeleteOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: int
```

删除数据数量，默认为1。

**类型：** int

**默认值：** 1

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataDeleteOperation-count?: int--><!--Device-DataDeleteOperation-count?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: int
```

起始删除位置索引值。取值范围是[0, 数据源长度-1]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataDeleteOperation-index: int--><!--Device-DataDeleteOperation-index: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType
```

数据删除类型。

**类型：** [DataOperationType](arkts-na-lazyforeach-dataoperationtype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataDeleteOperation-type: DataOperationType--><!--Device-DataDeleteOperation-type: DataOperationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

