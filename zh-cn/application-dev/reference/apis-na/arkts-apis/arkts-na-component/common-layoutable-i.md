# Layoutable

Provides the child component layout information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface Layoutable--><!--Device-unnamed-export declare interface Layoutable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth(): DirectionalEdgesT<double> | undefined
```

Obtains the border width of the child component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Layoutable-getBorderWidth(): DirectionalEdgesT<double> | undefined--><!--Device-Layoutable-getBorderWidth(): DirectionalEdgesT<double> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | the borderWidth of sub component, unit is vp. If some errors |

## getMargin

```TypeScript
getMargin(): DirectionalEdgesT<double> | undefined
```

Obtains the margin of the child component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Layoutable-getMargin(): DirectionalEdgesT<double> | undefined--><!--Device-Layoutable-getMargin(): DirectionalEdgesT<double> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | the margin of sub component, unit is vp. If some errors |

## getPadding

```TypeScript
getPadding(): DirectionalEdgesT<double> | undefined
```

Call this method to get the padding of sub component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Layoutable-getPadding(): DirectionalEdgesT<double> | undefined--><!--Device-Layoutable-getPadding(): DirectionalEdgesT<double> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | Padding of the child component, unit is vp. If some errors |

## layout

```TypeScript
layout(position: Position | undefined): void
```

Applies the specified position information to the child component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Layoutable-layout(position: Position | undefined): void--><!--Device-Layoutable-layout(position: Position | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

## measureResult

```TypeScript
measureResult: MeasureResult
```

Measurement result of the child component.

**类型：** MeasureResult

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Layoutable-measureResult: MeasureResult--><!--Device-Layoutable-measureResult: MeasureResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId?: int
```

Unique ID of the child component.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Layoutable-uniqueId?: int--><!--Device-Layoutable-uniqueId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

