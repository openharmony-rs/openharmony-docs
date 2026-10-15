# DigitIndicator

```TypeScript
declare class DigitIndicator extends Indicator<DigitIndicator>
```

A constructor used to create a **DigitIndicator** object. It inherits from [Indicator](arkts-arkui-swiper-comp-indicator-c.md).

> **NOTE:** 
> 
> When pages are turned by group, the child nodes displayed in the digit-style navigation indicator do not count
> placeholder nodes.
> 
> The maximum value of [maxFontScale](arkts-arkui-text-comp-attribute.md#maxfontscale) for the digit-style navigation indicator is
> **2**.
> 
> The mirror display of the page number depends on the RTL status of the system.

**Inheritance/Implementation:** DigitIndicator extends Indicator&lt;DigitIndicator&gt;

**Since:** 10

<!--Device-unnamed-declare class DigitIndicator extends Indicator<DigitIndicator>--><!--Device-unnamed-declare class DigitIndicator extends Indicator<DigitIndicator>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **DigitIndicator** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DigitIndicator-constructor()--><!--Device-DigitIndicator-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## digitFont

```TypeScript
digitFont(value: Font): DigitIndicator
```

Sets the font style of the numeric navigation indicator of the **Swiper** component. When pages are turned by group, the number of child nodes displayed by the numeric navigation indicator does not include placeholder nodes.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DigitIndicator-digitFont(value: Font): DigitIndicator--><!--Device-DigitIndicator-digitFont(value: Font): DigitIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Font style of the digit-style navigation indicator.<br>Only the **size** and **weight** parameters in **Font** are adjustable. Setting **family** and **style** has no effect. <br>Default value: <br>{ size: 14, weight: FontWeight.Normal } |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Returns the current numeric indicator, which supports chained calls to configure other numeric style attributes. |

## fontColor

```TypeScript
fontColor(value: ResourceColor): DigitIndicator
```

Sets the font color of the digit-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DigitIndicator-fontColor(value: ResourceColor): DigitIndicator--><!--Device-DigitIndicator-fontColor(value: ResourceColor): DigitIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the digit-style navigation indicator.<br>Default value: **'#ff182431'** |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Returns the current numeric indicator, which supports chained calls to configure other numeric style attributes. |

## selectedDigitFont

```TypeScript
selectedDigitFont(value: Font): DigitIndicator
```

Sets the font style of the selected digit-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DigitIndicator-selectedDigitFont(value: Font): DigitIndicator--><!--Device-DigitIndicator-selectedDigitFont(value: Font): DigitIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Font style of the selected digit-style navigation indicator.<br>Default value: <br>{ size: 14, weight: FontWeight.Normal } |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Returns the current numeric indicator, which supports chained calls to configure other numeric style attributes. |

## selectedFontColor

```TypeScript
selectedFontColor(value: ResourceColor): DigitIndicator
```

Sets the font color of the selected digit-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DigitIndicator-selectedFontColor(value: ResourceColor): DigitIndicator--><!--Device-DigitIndicator-selectedFontColor(value: ResourceColor): DigitIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the selected digit-style navigation indicator.<br>Default value: **'#ff182431'** |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Returns the current numeric indicator, which supports chained calls to configure other numeric style attributes. |
