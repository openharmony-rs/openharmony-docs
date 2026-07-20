# DataAddOperation

添加数据操作。

**起始版本：** 12

<!--Device-unnamed-interface DataAddOperation--><!--Device-unnamed-interface DataAddOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

插入数量，默认为1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataAddOperation-count?: number--><!--Device-DataAddOperation-count?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

插入数据索引值。取值范围是[0, 数据源长度]。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataAddOperation-index: number--><!--Device-DataAddOperation-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string | Array<string>
```

为插入的数据分配键值，默认使用原键值。

**类型：** string \| Array&lt;string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataAddOperation-key?: string | Array<string>--><!--Device-DataAddOperation-key?: string | Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.ADD
```

数据添加类型。

**类型：** DataOperationType.ADD

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataAddOperation-type: DataOperationType.ADD--><!--Device-DataAddOperation-type: DataOperationType.ADD-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

