# DataMoveOperation

移动数据操作。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface DataMoveOperation--><!--Device-unnamed-export interface DataMoveOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: MoveIndex
```

移动位置。取值范围是[0, 数据源长度-1]。

**类型：** [MoveIndex](arkts-na-lazyforeach-moveindex-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataMoveOperation-index: MoveIndex--><!--Device-DataMoveOperation-index: MoveIndex-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

为被移动的数据分配新的键值，默认使用原键值。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataMoveOperation-key?: string--><!--Device-DataMoveOperation-key?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType
```

数据移动类型。

**类型：** [DataOperationType](arkts-na-lazyforeach-dataoperationtype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataMoveOperation-type: DataOperationType--><!--Device-DataMoveOperation-type: DataOperationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

