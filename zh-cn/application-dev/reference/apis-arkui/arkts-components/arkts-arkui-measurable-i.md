# Measurable

子组件位置信息。

**起始版本：** 10

<!--Device-unnamed-declare interface Measurable--><!--Device-unnamed-declare interface Measurable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth() : DirectionalEdgesT<number>
```

调用此方法获取子组件的borderWidth信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Measurable-getBorderWidth() : DirectionalEdgesT<number>--><!--Device-Measurable-getBorderWidth() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的borderWidth信息。 |

## getMargin

```TypeScript
getMargin() : DirectionalEdgesT<number>
```

调用此方法获取子组件的margin信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Measurable-getMargin() : DirectionalEdgesT<number>--><!--Device-Measurable-getMargin() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的margin信息。 |

## getPadding

```TypeScript
getPadding() : DirectionalEdgesT<number>
```

调用此方法获取子组件的padding信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Measurable-getPadding() : DirectionalEdgesT<number>--><!--Device-Measurable-getPadding() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的padding信息。 |

## measure

```TypeScript
measure(constraint: ConstraintSizeOptions) : MeasureResult
```

调用此方法限制子组件的尺寸范围。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Measurable-measure(constraint: ConstraintSizeOptions) : MeasureResult--><!--Device-Measurable-measure(constraint: ConstraintSizeOptions) : MeasureResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 约束尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MeasureResult](arkts-arkui-measureresult-i.md) | Provides the measurement result of the component. |

## uniqueId

```TypeScript
uniqueId?: number
```

系统为子组件分配的唯一标识UniqueID。取值限定为整数。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Measurable-uniqueId?: number--><!--Device-Measurable-uniqueId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

