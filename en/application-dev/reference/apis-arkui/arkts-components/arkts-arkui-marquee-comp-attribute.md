# Marquee properties/events

```TypeScript
declare class MarqueeAttribute extends CommonMethod<MarqueeAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** MarqueeAttribute extends CommonMethod<MarqueeAttribute>

**Since:** 8

<!--Device-unnamed-declare class MarqueeAttribute extends CommonMethod<MarqueeAttribute>--><!--Device-unnamed-declare class MarqueeAttribute extends CommonMethod<MarqueeAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowScale

```TypeScript
allowScale(value: boolean)
```

Sets whether to allow text scaling. If this API is not called, text scaling is not allowed by default.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-allowScale(value: boolean): MarqueeAttribute--><!--Device-MarqueeAttribute-allowScale(value: boolean): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to allow text scaling. <br>true: text scaling is allowed; false: text scaling is not allowed. <br>**Note:** <br>This takes effect only when [fontSize](#fontsize) is in fp units. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color. If this API is not called, the default font color is '#e6182431', which indicates dark gray (with an opacity of about 90%). On Wearable devices, the default font color is '#c5ffffff', which indicates white (with an opacity of about 77%).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-fontColor(value: ResourceColor): MarqueeAttribute--><!--Device-MarqueeAttribute-fontColor(value: ResourceColor): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color. |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

Sets the font family.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-fontFamily(value: string | Resource): MarqueeAttribute--><!--Device-MarqueeAttribute-fontFamily(value: string | Resource): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font family. Default font: **'HarmonyOS Sans'** <br>Supported fonts include **'HarmonyOS Sans'** and custom fonts registered using [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync). <br>Only the 'HarmonyOS Sans' font is supported for widgets. |

## fontSize

```TypeScript
fontSize(value: Length)
```

Sets the text size.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-fontSize(value: Length): MarqueeAttribute--><!--Device-MarqueeAttribute-fontSize(value: Length): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Font size. When fontSize is of the number type, the fp unit is used. The default font size is 16fp. Percentage strings are not supported. <br>Default value on Wearable devices: 15fp <br>**Note:** <br>When used with the [allowScale](#allowscale) attribute, the value must be set in fp units. |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

Sets the font weight of the text. If the value is set too large, the text may be truncated under different fonts. If this API is not called, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-fontWeight(value: number | FontWeight | string): MarqueeAttribute--><!--Device-MarqueeAttribute-fontWeight(value: number | FontWeight | string): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string | Yes | Font weight of the text.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. The default value is 400. A larger value indicates a bolder font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. If the value is set too large, the font may be truncated in different fonts. <br>If a value beyond the value range is passed, the default value is used. If a value that does not meet the interval requirement is passed, the passed value is used when enableVariableFontWeight of fontWeightConfigs is set to true; otherwise, the default value is used. |

## marqueeUpdateStrategy

```TypeScript
marqueeUpdateStrategy(value: MarqueeUpdateStrategy)
```

Scrolling strategy of the **Marquee** component after its attributes are updated. (This attribute takes effect when the **Marquee** component is in the playing state and the text content width is greater than or equal to the component's width.) If this API is not called, MarqueeUpdateStrategy.DEFAULT is used by default.

Usage scenarios:

- MarqueeUpdateStrategy.DEFAULT: suitable for scenarios where you want to restart scrolling with the default  
strategy after the content is updated.  
- MarqueeUpdateStrategy.PRESERVE_POSITION: suitable for scenarios where you want to keep the current scrolling  
position and continue scrolling when the content is dynamically updated, such as real-time clocks, stock prices, and other dynamic content display.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MarqueeAttribute-marqueeUpdateStrategy(value: MarqueeUpdateStrategy): MarqueeAttribute--><!--Device-MarqueeAttribute-marqueeUpdateStrategy(value: MarqueeUpdateStrategy): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [MarqueeUpdateStrategy](../arkts-apis/arkts-arkui-marqueeupdatestrategy-e.md) | Yes | Scrolling strategy of the marquee after the marquee component properties are updated. |

## onBounce

```TypeScript
onBounce(event: () => void)
```

Triggered when a complete scrolling cycle is completed. If the loop count is not 1, this event is triggered multiple times.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-onBounce(event: () => void): MarqueeAttribute--><!--Device-MarqueeAttribute-onBounce(event: () => void): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when a complete scrolling is finished. |

## onFinish

```TypeScript
onFinish(event: () => void)
```

Triggered when the marquee has finished the number of scrolling times set by the **loop** attribute.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-onFinish(event: () => void): MarqueeAttribute--><!--Device-MarqueeAttribute-onFinish(event: () => void): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when the marquee has finished the number of scrolling times set by the **loop** attribute. |

## onStart

```TypeScript
onStart(event: () => void)
```

Triggered when the marquee text changes or starts scrolling.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeAttribute-onStart(event: () => void): MarqueeAttribute--><!--Device-MarqueeAttribute-onStart(event: () => void): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when the marquee text changes or starts scrolling. |

## onStop

```TypeScript
onStop(event: Callback<void> | undefined)
```

Triggered when the marquee finishes scrolling or stops.

When the marquee stops, it restarts the loop from the beginning. This does not include the pause scenario, and pausing does not trigger this callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-MarqueeAttribute-onStop(event: Callback<void> | undefined): MarqueeAttribute--><!--Device-MarqueeAttribute-onStop(event: Callback<void> | undefined): MarqueeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; &#124; undefined | Yes | Triggered when the marquee finishes scrolling or stops.<br>When set to undefined, the callback is not executed. |
