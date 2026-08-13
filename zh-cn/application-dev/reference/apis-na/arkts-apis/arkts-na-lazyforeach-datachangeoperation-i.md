# DataChangeOperation

执行单个数据的插入、更新或删除。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface DataChangeOperation--><!--Device-unnamed-export interface DataChangeOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: int
```

改变的数据的索引值。取值范围是[0, 数据源长度-1]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeOperation-index: int--><!--Device-DataChangeOperation-index: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

为改变的数据分配新的键值，默认使用原键值。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeOperation-key?: string--><!--Device-DataChangeOperation-key?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType
```

数据改变类型。

**类型：** [DataOperationType](arkts-na-lazyforeach-dataoperationtype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataChangeOperation-type: DataOperationType--><!--Device-DataChangeOperation-type: DataOperationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

