# DotIndicator

A constructor used to create a **DotIndicator** object. It inherits from [Indicator](arkts-arkui-indicator-c.md).

**Inheritance/Implementation:** DotIndicator extends Indicator<DotIndicator>

**Since:** 10

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the dot-style navigation indicator.<br>Default value: **'#1A182431'** (light gray) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

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

## indicatorIcon

```TypeScript
indicatorIcon(iconList: Array<IndicatorIconInfo>): DotIndicator
```

Set indicator icon.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iconList | Array&lt;[IndicatorIconInfo](arkts-arkui-indicatoriconinfo-i.md)&gt; | Yes | Indicator items whose icons need to be set. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | return the DotIndicator. |

## itemHeight

```TypeScript
itemHeight(value: Length): DotIndicator
```

Sets the height of a dot-style navigation indicator of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height of the dot-style indicator. This parameter cannot be set in percentage.<br>Default value: **6**<br>Unit: vp<br>Value range: (0, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

## itemWidth

```TypeScript
itemWidth(value: Length): DotIndicator
```

Sets the width of a dot-style navigation indicator of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the dot-style indicator. This parameter cannot be set in percentage.<br>Default value: **6**<br>Unit: vp<br>Value range: (0, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

## mask

```TypeScript
mask(value: boolean): DotIndicator
```

Sets whether to enable the mask for the dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the mask for the dot-style navigation indicator. The value **true** means to enable the mask for the dot-style navigation indicator, and **false** means the opposite.<br>Default value: **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

## maxDisplayCount

```TypeScript
maxDisplayCount(maxDisplayCount: number): DotIndicator
```

Sets the maximum number of navigation dots in the dot-style navigation indicator.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxDisplayCount | number | Yes | Maximum number of navigation dots in the dot-style navigation point indicator. If the actual number of navigation dots exceeds this limit, the overflow effect is activated, as shown in [Example 5](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-5-configuring-overflow-for-the-dot-style-indicator). <br>This parameter has no default value. If an invalid value is set, no overflow effect is applied.<br>Value range: [6, 9].<br>**NOTE:** <br>In scenarios involving overflow display:<br>1. Interactive features, such as gestures and mouse operations, are not supported.<br>2. The position of the selected navigation dot corresponding to the middle page is not strictly fixed; it depends on the sequence of previous page-turning operations.<br>3. Currently, only scenarios with **displayCount** set to **1** are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor): DotIndicator
```

Sets the color of the selected dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the selected dot-style navigation indicator.<br>Default value: **'#007DFF'** (blue) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

## selectedItemHeight

```TypeScript
selectedItemHeight(value: Length): DotIndicator
```

Sets the height of the selected dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height of the selected dot-style indicator. This parameter cannot be set in percentage.<br>Default value: **6**<br>Unit: vp<br>Value range: (0, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

## selectedItemWidth

```TypeScript
selectedItemWidth(value: Length): DotIndicator
```

Sets the width of the selected dot-style navigation indicator.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the selected dot-style navigation indicator. This parameter cannot be set in percentage.<br>Default value: **6**<br>Unit: vp<br>Value range: (0, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |

## space

```TypeScript
space(space: LengthMetrics): DotIndicator
```

Sets the spacing between dot-style navigation indicators of the **Swiper** component.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| space | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | Yes | Spacing between the dots in the dot-style navigation indicator. Percentage values are not supported.<br>Default value: **10** for PCs and 2-in-1 devices and **8** for other devices<br>Unit: vp<br>Value range: [0, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Current dot-style navigation indicator. |
