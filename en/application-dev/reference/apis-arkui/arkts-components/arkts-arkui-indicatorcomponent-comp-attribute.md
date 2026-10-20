# IndicatorComponent properties/events

```TypeScript
declare class IndicatorComponentAttribute extends CommonMethod<IndicatorComponentAttribute>
```

Defines the IndicatorComponent attribute functions.

**Inheritance/Implementation:** IndicatorComponentAttribute extends CommonMethod&lt;IndicatorComponentAttribute&gt;

**Since:** 15

<!--Device-unnamed-declare class IndicatorComponentAttribute extends CommonMethod<IndicatorComponentAttribute>--><!--Device-unnamed-declare class IndicatorComponentAttribute extends CommonMethod<IndicatorComponentAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count(totalCount: number)
```

Sets the total number of indicators. When not bound to a **Swiper** component, you can use this API to customize the number of indicators.

When the **Indicator** component is bound to a **Swiper** component, the count is subject to the number of pages in the **Swiper** component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentAttribute-count(totalCount: number): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-count(totalCount: number): IndicatorComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| totalCount | number | Yes | Total number of navigation dots. The value range is [2, +∞). <br>Default value: 2.<br>If 0, 1, or a negative number is passed in, the default value 2 is used. |

## initialIndex

```TypeScript
initialIndex(index: number)
```

Sets the index value of the current indicator when it first appears. If the value is less than 0 or greater than or equal to the total number of indicators, the default value **0** is used.

This attribute does not take effect when the **Indicator** component is bound to a **Swiper** component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentAttribute-initialIndex(index: number): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-initialIndex(index: number): IndicatorComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Initial index of the navigation indicator when it first appears.<br>Default value: **0** |

## loop

```TypeScript
loop(isLoop: boolean)
```

Sets whether to enable looping for the indicators.

This attribute does not take effect when the **Indicator** component is bound to a **Swiper** component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentAttribute-loop(isLoop: boolean): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-loop(isLoop: boolean): IndicatorComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLoop | boolean | Yes | Whether to enable looping. The value **true** means to enable looping, and **false** means the opposite.<br>Default value: **true** |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Triggered when the currently selected navigation index changes. The callback provides the new index.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentAttribute-onChange(event: Callback<number>): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-onChange(event: Callback<number>): IndicatorComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Callback invoked when the index of the currently displayed selected indicator changes. The callback parameter is the index value of the currently selected indicator. |

## style

```TypeScript
style(indicatorStyle: DotIndicator | DigitIndicator)
```

Sets the indicator style.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentAttribute-style(indicatorStyle: DotIndicator | DigitIndicator): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-style(indicatorStyle: DotIndicator | DigitIndicator): IndicatorComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indicatorStyle | [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) &#124; [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Yes | the style value |

## vertical

```TypeScript
vertical(isVertical: boolean)
```

Sets whether the indicators are arranged vertically.

This attribute does not take effect when the **Indicator** component is bound to a **Swiper** component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentAttribute-vertical(isVertical: boolean): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-vertical(isVertical: boolean): IndicatorComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isVertical | boolean | Yes | Whether the indicator is arranged vertically. The value true means vertical arrangement, and false means horizontal arrangement.<br>Default value: false. |
