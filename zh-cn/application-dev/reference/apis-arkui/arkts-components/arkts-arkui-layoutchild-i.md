# LayoutChild

布局和测量发生时，框架传递给子组件的信息。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layout

```TypeScript
layout(childLayoutInfo: LayoutInfo)
```

在 onLayout 回调中调用此布局方法，将布局信息分配给子组件。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| childLayoutInfo | LayoutInfo | 是 |  |

## measure

```TypeScript
measure(childConstraint: ConstraintSizeOptions)
```

在 onMeasure 回调中调用此 measure 方法以提供子组件的尺寸。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| childConstraint | ConstraintSizeOptions | 是 |  |

## borderInfo

```TypeScript
borderInfo: LayoutBorderInfo
```

子组件边框信息

**类型：** LayoutBorderInfo

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constraint

```TypeScript
constraint: ConstraintSizeOptions
```

子组件约束

**类型：** ConstraintSizeOptions

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string
```

子组件id

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

子组件名字

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position: Position
```

子组件位置信息

**类型：** Position

**起始版本：** 9

**废弃版本：** 10

**替代接口：** Measurable/Layoutable

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

