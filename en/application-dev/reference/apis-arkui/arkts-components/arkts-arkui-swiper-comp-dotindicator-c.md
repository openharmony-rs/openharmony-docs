# DotIndicator

```TypeScript
declare class DotIndicator extends Indicator<DotIndicator>
```

A constructor used to create a **DotIndicator** object. It inherits from [Indicator](arkts-arkui-swiper-comp-indicator-c.md).

**Inheritance/Implementation:** DotIndicator extends Indicator&lt;DotIndicator&gt;

**Since:** 10

<!--Device-unnamed-declare class DotIndicator extends Indicator<DotIndicator>--><!--Device-unnamed-declare class DotIndicator extends Indicator<DotIndicator>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor): DotIndicator
```

Sets the color of the dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DotIndicator-color(value: ResourceColor): DotIndicator--><!--Device-DotIndicator-color(value: ResourceColor): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the dot-style navigation indicator.<br>Default value: **'#1A182431'** (light gray) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which is used to support chained calls for configuring other dot style attributes. |

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

<!--Device-DotIndicator-constructor()--><!--Device-DotIndicator-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicatorIcon

```TypeScript
indicatorIcon(iconList: Array<IndicatorIconInfo>): DotIndicator
```

Sets the icon of the **Swiper** dot navigation indicator.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-DotIndicator-indicatorIcon(iconList: Array<IndicatorIconInfo>): DotIndicator--><!--Device-DotIndicator-indicatorIcon(iconList: Array<IndicatorIconInfo>): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iconList | Array&lt;[IndicatorIconInfo](arkts-arkui-swiper-comp-indicatoriconinfo-i.md)&gt; | Yes | Icons of the dot navigation indicator. Each element in the array contains two attributes: **index** (indicator index) and **icon** (icon content). |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## itemHeight

```TypeScript
itemHeight(value: Length): DotIndicator
```

Sets the height of a dot-style navigation indicator of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DotIndicator-itemHeight(value: Length): DotIndicator--><!--Device-DotIndicator-itemHeight(value: Length): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height of the dot indicator of the **Swiper** component. Percentages are not supported.<br>Default value: **6**<br>Unit: vp<br>Value range: (0, +∞). If the value is out of range, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## itemWidth

```TypeScript
itemWidth(value: Length): DotIndicator
```

Sets the width of a dot-style navigation indicator of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DotIndicator-itemWidth(value: Length): DotIndicator--><!--Device-DotIndicator-itemWidth(value: Length): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the dot indicator of the **Swiper** component. Percentage is not supported.<br> Default value: **6**<br>Unit: vp<br>Value range: (0, +∞). If the value is out of range, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## mask

```TypeScript
mask(value: boolean): DotIndicator
```

Sets whether to enable the mask for the dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DotIndicator-mask(value: boolean): DotIndicator--><!--Device-DotIndicator-mask(value: boolean): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the mask style of the dot navigation indicator of the Swiper component. The value **true** means to display the mask style of the dot navigation indicator of the Swiper component, and **false** means the opposite.<br>Default value: **false** |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## maxDisplayCount

```TypeScript
maxDisplayCount(maxDisplayCount: number): DotIndicator
```

Sets the maximum number of navigation dots in the dot-style navigation indicator.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DotIndicator-maxDisplayCount(maxDisplayCount: number): DotIndicator--><!--Device-DotIndicator-maxDisplayCount(maxDisplayCount: number): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxDisplayCount | number | Yes | Maximum number of navigation dots displayed in the dot indicator style. When the actual number of navigation dots is greater than the maximum number, the overlong display style takes effect, as shown in [Example 5](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-5-configuring-overflow-for-the-dot-style-indicator). <br>Value range: [6, 9]. When the value is out of range, it is equivalent to no overlong display effect.<br> **NOTE:** <br>1. In the overlong display scenario, interaction (including finger tap and drag and mouse operation) is not supported before API version 26.0.0. Since API version 26.0.0, finger tap and drag interaction is supported, but mouse operation interaction is not supported.<br>2. In the overlong display scenario, the position of the selected navigation dot corresponding to the middle page is not completely fixed, and depends on the previous page turn operation sequence.<br>3. Currently, only the scenario where **displayCount** is 1 is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor): DotIndicator
```

Sets the color of the selected dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DotIndicator-selectedColor(value: ResourceColor): DotIndicator--><!--Device-DotIndicator-selectedColor(value: ResourceColor): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the selected dot-style navigation indicator.<br>Default value: **'#007DFF'** (blue) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## selectedItemHeight

```TypeScript
selectedItemHeight(value: Length): DotIndicator
```

Sets the height of the selected dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DotIndicator-selectedItemHeight(value: Length): DotIndicator--><!--Device-DotIndicator-selectedItemHeight(value: Length): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height of the selected dot indicator of the **Swiper** component. Percentages are not supported.<br>Default value: **6**<br>Unit: vp<br>Value range: (0, +∞). If the value is out of range, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## selectedItemWidth

```TypeScript
selectedItemWidth(value: Length): DotIndicator
```

Sets the width of the selected dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-DotIndicator-selectedItemWidth(value: Length): DotIndicator--><!--Device-DotIndicator-selectedItemWidth(value: Length): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the dot indicator of the selected **Swiper** component. Percentages are not supported.<br>Default value: **6**<br>Unit: vp<br>Value range: (0, +∞). If the value is out of range, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |

## space

```TypeScript
space(space: LengthMetrics): DotIndicator
```

Sets the spacing between dot-style navigation indicators of the **Swiper** component.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

<!--Device-DotIndicator-space(space: LengthMetrics): DotIndicator--><!--Device-DotIndicator-space(space: LengthMetrics): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| space | LengthMetrics | Yes | Spacing between dot indicators. Percentages are not supported.<br>Default value: **10** on PC/2-in-1 devices and **8** on other devices.<br>Unit: vp<br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Returns the current dot indicator, which supports chained calls to configure other dot style attributes. |
