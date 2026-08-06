# DataAddOperation

添加单个数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface DataAddOperation--><!--Device-unnamed-export interface DataAddOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: int
```

插入数量，默认为1。

**类型：** int

**默认值：** 1

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataAddOperation-count?: int--><!--Device-DataAddOperation-count?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: int
```

插入数据索引值。取值范围是[0, 数据源长度-1]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataAddOperation-index: int--><!--Device-DataAddOperation-index: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string | Array<string>
```

为插入的数据分配键值。

**类型：** string \| Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataAddOperation-key?: string | Array<string>--><!--Device-DataAddOperation-key?: string | Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType
```

数据添加类型。

**类型：** DataOperationType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataAddOperation-type: DataOperationType--><!--Device-DataAddOperation-type: DataOperationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

