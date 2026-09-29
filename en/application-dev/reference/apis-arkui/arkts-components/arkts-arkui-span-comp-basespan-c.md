# BaseSpan

```TypeScript
declare class BaseSpan<T> extends CommonMethod<T>
```

Defines the base class **BaseSpan**, including the universal attributes of the **Span** component.

**Inheritance/Implementation:** BaseSpan extends CommonMethod<T>

**Since:** 11

<!--Device-unnamed-declare class BaseSpan<T> extends CommonMethod<T>--><!--Device-unnamed-declare class BaseSpan<T> extends CommonMethod<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## baselineOffset

```TypeScript
baselineOffset(value: LengthMetrics): T
```

Sets the baseline offset of the Span. This is applicable to scenarios such as superscript and subscript layout and fine-tuning alignment of mixed-font-size text. This attribute coexists with the baselineOffset of the parent component. If this API is not used, the default offset is 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseSpan-baselineOffset(value: LengthMetrics): T--><!--Device-BaseSpan-baselineOffset(value: LengthMetrics): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Sets the baseline offset of the Span. If this value is set to a percentage, the default value is used. <br>A positive value shifts the content upward, and a negative value shifts it downward. <br>In ImageSpan, when this value is set to a non-zero value, [verticalAlign](arkts-arkui-imagespan-comp-attribute.md#verticalalign) is fixed to ImageSpanAlignment.BASELINE. When this value is set to 0, to make the baseline alignment policy take effect, you must also set [verticalAlign](arkts-arkui-imagespan-comp-attribute.md#verticalalign) to ImageSpanAlignment.BASELINE. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute object of the current Span, used for chained calls. |

## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle): T
```

Sets the text background style. When used as a child component of [ContainerSpan](arkts-arkui-containerspan-comp-attribute.md#containerspanattribute), this attribute value can be inherited, and the component's own setting takes precedence. If this API is not used, the default background color is Color.Transparent and the corner radius is 0.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseSpan-textBackgroundStyle(style: TextBackgroundStyle): T--><!--Device-BaseSpan-textBackgroundStyle(style: TextBackgroundStyle): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-span-comp-textbackgroundstyle-i.md) | Yes | Text background style. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute object of the current Span. |
