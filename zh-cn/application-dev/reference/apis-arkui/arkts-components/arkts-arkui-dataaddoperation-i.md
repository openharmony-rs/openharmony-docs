# DataAddOperation

添加数据操作。

**起始版本：** 12

<!--Device-unnamed-interface DataAddOperation--><!--Device-unnamed-interface DataAddOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## count

```TypeScript
count?: number
```

添加数量，必须是正整数（大于0），默认为1。传入0或负数时可能导致渲染效果异常。

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

添加数据索引值。取值范围是[0, 数据源长度]。超出取值范围时渲染异常。

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

为添加的数据分配键值，默认使用原键值。键值支持string或Array&lt;string&gt;类型；当键值为数组且长度大于count时报参数无效错误。

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

**类型：** [DataOperationType.ADD](arkts-arkui-dataoperationtype-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataAddOperation-type: DataOperationType.ADD--><!--Device-DataAddOperation-type: DataOperationType.ADD-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

