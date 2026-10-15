# Measurable

```TypeScript
declare interface Measurable
```

子组件测量信息。Measurable对象由ArkUI框架在onMeasureSize调用时创建并传入，用于测量阶段。与Layoutable（用于布局阶段）不同，Measurable主要用于测量子组件尺寸，开发者通过measure方法设置约束条件并获取测量结果。Measurable和Layoutable是同一子组件在不同布局阶段的两种表示形式。

**起始版本：** 10

<!--Device-unnamed-declare interface Measurable--><!--Device-unnamed-declare interface Measurable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth() : DirectionalEdgesT<number>
```

获取子组件的borderWidth信息，返回其边框宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Measurable-getBorderWidth() : DirectionalEdgesT<number>--><!--Device-Measurable-getBorderWidth() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的边框宽度对象，包含四个方向的边框宽度值。单位：vp。 |

## getMargin

```TypeScript
getMargin() : DirectionalEdgesT<number>
```

获取子组件的margin信息，返回其外边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Measurable-getMargin() : DirectionalEdgesT<number>--><!--Device-Measurable-getMargin() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的外边距对象，包含四个方向的边距值。单位：vp。 |

## getPadding

```TypeScript
getPadding() : DirectionalEdgesT<number>
```

获取子组件的padding信息，返回其内边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Measurable-getPadding() : DirectionalEdgesT<number>--><!--Device-Measurable-getPadding() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的内边距对象，包含四个方向的内边距值。单位：vp。 |

## measure

```TypeScript
measure(constraint: ConstraintSizeOptions) : MeasureResult
```

调用此方法限制子组件的尺寸范围，返回测量后的组件布局信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Measurable-measure(constraint: ConstraintSizeOptions) : MeasureResult--><!--Device-Measurable-measure(constraint: ConstraintSizeOptions) : MeasureResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 约束尺寸，包含minWidth、maxWidth、minHeight、maxHeight等约束条件，用于限制子组件的尺寸范围。取值原则：minWidth≤maxWidth，minHeight≤maxHeight；单位：vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MeasureResult](arkts-arkui-common-comp-measureresult-i.md) | 测量后的组件布局信息，包含测量后的宽度和高度。 |

## uniqueId

```TypeScript
uniqueId?: number
```

系统为子组件分配的唯一标识UniqueID。用于唯一标识子组件以进行后续操作（如通过getFrameNodeByUniqueId获取FrameNode）。取值范围[0, +∞)。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-Measurable-uniqueId?: number--><!--Device-Measurable-uniqueId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
