# BaseSpan

```TypeScript
declare class BaseSpan<T> extends CommonMethod<T>
```

Defines the base class **BaseSpan**, including the universal attributes of the **Span** component.

**Inheritance/Implementation:** BaseSpan extends CommonMethod<T>

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## baselineOffset

```TypeScript
baselineOffset(value: LengthMetrics): T
```

Sets the offset of the baseline. This attribute coexists with the **baselineOffset** attribute of the parent component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Offset of the baseline. If the value specified is a percentage, the default value is used.<br>A positive value moves the content upwards, while a negative value moves it downwards.<br>Default value: **0**<br>In the **ImageSpan**, when this parameter is set to a non-zero value, the [verticalAlign](arkts-arkui-imagespan-comp-attribute.md#verticalalign) is fixed to **ImageSpanAlignment.BASELINE**; when this parameter is set to **0**, [verticalAlign](arkts-arkui-imagespan-comp-attribute.md#verticalalign) must be set to **ImageSpanAlignment.BASELINE** for the baseline alignment strategy to take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attributes of the span. |

## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle): T
```

Background style. This attribute prioritizes the value separately set for the component. If it is not set, the component can inherit the settings from its parent [ContainerSpan](arkts-arkui-containerspan-comp-attribute.md#containerspanattribute).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-span-comp-textbackgroundstyle-i.md) | Yes | Sets the background style.<br>Default value:<br>{<br> color: Color.Transparent,<br> radius: 0<br>} |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attributes of the span. |
