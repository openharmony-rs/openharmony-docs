# Indicator

```TypeScript
declare class Indicator<T>
```

Sets the distance between the indicator and the **Swiper** component. Because the indicator has a default interaction area with a height of 32 vp, the displayed part cannot be completely stuck to the bottom. To achieve a completely bottom-aligned effect, use the [IndicatorComponent](arkts-arkui-indicatorcomponent-comp.md#indicatorcomponentinterface) component to adjust the position more flexibly.

**Since:** 10

<!--Device-unnamed-declare class Indicator<T>--><!--Device-unnamed-declare class Indicator<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom(value: Length): T
```

Sets the position of the navigation indicator relative to the bottom edge of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-Indicator-bottom(value: Length): T--><!--Device-Indicator-bottom(value: Length): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the bottom of the navigation dot relative to the **Swiper**.<br>When **top** and **bottom** are not set, adaptive layout is performed. Based on the size of the indicator itself and the size of the **Swiper**, the indicator is placed at the bottom in the cross-axis direction, with the same effect as setting **bottom** to **0**.<br>When set to **0**: the layout is calculated based on position 0.<br> Priority: lower than the **top** attribute.<br>Value range: [0, Swiper height - navigation dot area height]. If the value exceeds this range, the nearest boundary value is used.<br>For details about the unit, see [Length](../arkts-apis/arkts-arkui-length-t.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation dot indicator, which supports chained calls to configure other indicator attributes. |

## bottom

```TypeScript
bottom(bottom: LengthMetrics | Length, ignoreSize: boolean): T
```

Sets the position of the navigation indicator relative to the bottom edge of the **Swiper** component. You can also choose to ignore the size of the navigation indicator using the **ignoreSize** property.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

<!--Device-Indicator-bottom(bottom: LengthMetrics | Length, ignoreSize: boolean): T--><!--Device-Indicator-bottom(bottom: LengthMetrics | Length, ignoreSize: boolean): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bottom | LengthMetrics &#124; [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Sets the position of the bottom of the navigation dot relative to Swiper.<br>When top and bottom are not set, adaptive size layout is performed. Based on the size of the indicator itself and the size of Swiper, the indicator is placed at the bottom in the cross-axis direction, with the same effect as setting bottom to 0.<br>When set to 0: the layout is calculated based on position 0.<br>Priority: lower than the top attribute.<br>Value range: [0, Swiper height - navigation dot area height]. If the value exceeds this range, the nearest boundary value is used.<br>For the unit, see the description of the [Length](../arkts-apis/arkts-arkui-length-t.md) type. |
| ignoreSize | boolean | Yes | Sets whether to ignore the size of the navigation dot itself. The default value is **false**.<br>When set to **true**, the size of the navigation dot is ignored, so that the navigation dot can be placed closer to the bottom of Swiper. When set to **false**, the size of the navigation dot is not ignored, and the navigation dot is laid out at its default size. For usage, see [Example 9](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-9-using-the-space-and-bottom-apis-on-the-navigation-indicator). <br> Note: When the navigation dot is of the [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) type, the scenarios where it does not take effect are as follows:<br> • When [vertical](arkts-arkui-swiper-comp-attribute.md#vertical) is set to **false** and **bottom**   > 0.<br> • When [vertical](arkts-arkui-swiper-comp-attribute.md#vertical) is set to **true**:<br>         1. When **bottom**   > 0.<br> 2. When bottom is set to undefined. <br> 3. When **isSidebarMiddle** is set to **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation dot indicator, which supports chained calls to configure other navigation dot attributes. |

## digit

```TypeScript
static digit(): DigitIndicator
```

Returns a **DigitIndicator** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-Indicator-static digit(): DigitIndicator--><!--Device-Indicator-static digit(): DigitIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) | Numeric indicator object, used to set the numeric navigation style of the Swiper component. |

## dot

```TypeScript
static dot(): DotIndicator
```

Returns a **DotIndicator** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-Indicator-static dot(): DotIndicator--><!--Device-Indicator-static dot(): DotIndicator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) | Dot indicator object used to set the dot navigation style of the Swiper component. |

## end

```TypeScript
end(value: LengthMetrics): T
```

Sets the distance between the navigation point indicator and the left edge (in right-to-left scripts) or the right edge (in left-to-right scripts) of the **Swiper** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-Indicator-end(value: LengthMetrics): T--><!--Device-Indicator-end(value: LengthMetrics): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Right-to-left scripts: Distance between the navigation indicator and the left edge of the **Swiper** component. <br>Left-to-right scripts: Distance between the navigation indicator and the right edge of the **Swiper** component. <br>Default value: **0** <br>Unit: vp <br>Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation dot indicator, used to support chained calls for configuring other navigation dot attributes. |

## left

```TypeScript
left(value: Length): T
```

Sets the position of the navigation indicator relative to the left edge of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-Indicator-left(value: Length): T--><!--Device-Indicator-left(value: Length): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the left side of the navigation dot relative to **Swiper**.<br>When **left** and **right** are not set, adaptive layout is performed, and the indicator is centered on the main axis based on its own size and the size of **Swiper**.<br>When set to **0**, the layout is calculated based on position 0.<br>Priority: higher than the **right** attribute.<br>Value range: [0, Swiper width - navigation dot area width]. When the value is out of this range, the nearest boundary value is used.<br>For details about the unit, see [Length](../arkts-apis/arkts-arkui-length-t.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation dot indicator, which supports chained calls to configure other navigation dot attributes. |

## right

```TypeScript
right(value: Length): T
```

Sets the position of the navigation indicator relative to the right edge of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-Indicator-right(value: Length): T--><!--Device-Indicator-right(value: Length): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the right side of the indicator relative to the **Swiper**.<br>If **left** and **right** are not set, adaptive layout is performed, and the indicator is centered on the main axis based on its own size and the **Swiper** size.<br>When set to **0**, the layout is calculated based on position **0**.<br>Priority: lower than the **left** attribute.<br>Value range: [0, Swiper width - indicator area width]. If the value is out of this range, the nearest boundary value is used.<br>For details about the unit, see [Length](../arkts-apis/arkts-arkui-length-t.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation dot indicator, used to support chained calls for configuring other navigation dot attributes. |

## start

```TypeScript
start(value: LengthMetrics): T
```

Sets the distance between the navigation indicator and the right edge (in [RTL](../arkts-apis/arkts-arkui-layoutdirection-e.md) scripts) or the left edge (in [LTR](../arkts-apis/arkts-arkui-layoutdirection-e.md) scripts) of the **Swiper** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-Indicator-start(value: LengthMetrics): T--><!--Device-Indicator-start(value: LengthMetrics): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Right-to-left scripts: Distance between the navigation indicator and the right edge of the **Swiper** component. <br>Left-to-right scripts: Distance between the navigation indicator and the left edge of the **Swiper** component. <br>Default value: **0** <br>Unit: vp <br>Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation dot indicator, used to support chained calls for configuring other navigation dot attributes. |

## top

```TypeScript
top(value: Length): T
```

Sets the position of the navigation indicator relative to the top edge of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-Indicator-top(value: Length): T--><!--Device-Indicator-top(value: Length): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the top of the navigation dot relative to the **Swiper**.<br>If **top** and **bottom** are not set, adaptive layout is performed. Based on the size of the indicator and the **Swiper**, the indicator is placed at the bottom in the cross-axis direction, which is the same as setting bottom to **0**.<br>When set to **0**, the layout is calculated based on position 0.<br>Priority: higher than the **bottom** attribute.<br>Value range: [0, Swiper height - navigation dot area height]. If the value is out of this range, the nearest boundary value is used.<br>For details about the unit, see [Length](../arkts-apis/arkts-arkui-length-t.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation dot indicator, used to support chained calls to configure other navigation dot attributes. |
