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

**Inheritance/Implementation:** DigitIndicator extends Indicator<DigitIndicator>

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **DotIndicator** object.

> **NOTE:** 
> 
> - When pressed, the navigation indicator is zoomed in to 1.33 times. To account for this, there is a certain distance between the navigation indicator's visible boundary and its actual boundary in the non-pressed state.The distance increases with the value of **itemWidth**, **itemHeight**, **selectedItemWidth**, and
> **selectedItemHeight**.
> 
> - If there are too many pages and dot-style indicators exceed the page, you are advised to use the
> **maxDisplayCount** parameter to set the number of dots to be displayed.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## digitFont

```TypeScript
digitFont(value: Font): DigitIndicator
```

Sets the font style of the digit-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Font style of the digit-style navigation indicator.<br>Only the **size** and **weight** parameters in **Font** are adjustable. Setting **family** and **style** has no effect.<br>Default value:<br>{size:?14,?weight:?FontWeight.Normal?} |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Current digit-style navigation indicator. |

## fontColor

```TypeScript
fontColor(value: ResourceColor): DigitIndicator
```

Sets the font color of the digit-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the digit-style navigation indicator.<br>Default value: **'#ff182431'** |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Current digit-style navigation indicator. |

## selectedDigitFont

```TypeScript
selectedDigitFont(value: Font): DigitIndicator
```

Sets the font style of the selected digit-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Font style of the selected digit-style navigation indicator.<br>Default value:<br>{?size:?14,?weight:?FontWeight.Normal?} |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Current digit-style navigation indicator. |

## selectedFontColor

```TypeScript
selectedFontColor(value: ResourceColor): DigitIndicator
```

Sets the font color of the selected digit-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the selected digit-style navigation indicator.<br>Default value: **'#ff182431'** |

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Current digit-style navigation indicator. |
