# Measurable

Sub component info passed from framework when measure happens.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface Measurable--><!--Device-unnamed-export declare interface Measurable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth(): DirectionalEdgesT<double> | undefined
```

Obtains the border width of the child component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Measurable-getBorderWidth(): DirectionalEdgesT<double> | undefined--><!--Device-Measurable-getBorderWidth(): DirectionalEdgesT<double> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../../apis-arkui/arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;double&gt; | Border width of the child component, unit is vp. If some errors occur in the internal runtime environment, returns undefined. |

## getMargin

```TypeScript
getMargin(): DirectionalEdgesT<double> | undefined
```

Obtains the margin of the child component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Measurable-getMargin(): DirectionalEdgesT<double> | undefined--><!--Device-Measurable-getMargin(): DirectionalEdgesT<double> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../../apis-arkui/arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;double&gt; | Margin of the child component, unit is vp. If some errors occur in the internal runtime environment, returns undefined. |

## getPadding

```TypeScript
getPadding(): DirectionalEdgesT<double> | undefined
```

Obtains the padding of the child component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Measurable-getPadding(): DirectionalEdgesT<double> | undefined--><!--Device-Measurable-getPadding(): DirectionalEdgesT<double> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../../apis-arkui/arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;double&gt; | the padding of sub component, unit is vp. If some errors occur in the internal runtime environment, returns undefined. |

## measure

```TypeScript
measure(constraint: ConstraintSizeOptions | undefined): MeasureResult | undefined
```

Applies the size constraint to the child component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Measurable-measure(constraint: ConstraintSizeOptions | undefined): MeasureResult | undefined--><!--Device-Measurable-measure(constraint: ConstraintSizeOptions | undefined): MeasureResult | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [ConstraintSizeOptions](../../apis-arkui/arkts-apis/arkts-arkui-constraintsizeoptions-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MeasureResult](arkts-na-common-measureresult-i.md) | Provides the measurement result of the component. If some errors occur in the internal runtime environment, returns undefined. |

## uniqueId

```TypeScript
uniqueId?: int
```

Unique ID that the system assigns to the child component.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Measurable-uniqueId?: int--><!--Device-Measurable-uniqueId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

