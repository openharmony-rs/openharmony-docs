# Indicator

Sets the distance between the navigation indicator and the **Swiper** component. Note that due to its default interaction area height of 32 vp, the navigation indicator cannot be placed flush against the bottom edge. To implement the function of completely attaching to the bottom, you can use the IndicatorComponent component to adjust the position more flexibly.

**Since:** 10

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the navigation indicator relative to the bottom edge of the **Swiper** component.<br>If neither **top** nor **bottom** is set, the navigation indicator is aligned at the bottom along the cross axis based on its own size and the size of the **Swiper** component, which is the same effect as setting **bottom=0**.<br>If the value specified is **0**, the navigation indicator is placed at the position 0. <br>Priority: lower than the **top** property<br>Value range: [0, Swiper height - Navigation indicator area height]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation indicator. |

## bottom

```TypeScript
bottom(bottom: LengthMetrics | Length, ignoreSize: boolean): T
```

Sets the position of the navigation indicator relative to the bottom edge of the **Swiper** component. You can also choose to ignore the size of the navigation indicator using the **ignoreSize** property.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bottom | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) &#124; [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the navigation indicator relative to the bottom edge of the **Swiper** component.<br>If neither **top** nor **bottom** is set, the navigation indicator is aligned at the bottom along the cross axis based on its own size and the size of the **Swiper** component, which is the same effect as setting **bottom=0**.<br>If the value specified is **0**, the navigation indicator is placed at the position 0.<br>Priority: lower than the **top** property<br>Value range: [0, Swiper height - Navigation indicator area height]. Values outside this range are adjusted to the nearest boundary. |
| ignoreSize | boolean | Yes | Whether to ignore the size of the navigation indicator.<br>Default value: **false**.<br>Setting **true** positions the indicator closer to the **Swiper** component's bottom. For the usage, see [Example 9: Using the space and bottom APIs on the Navigation Indicator](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-9-using-the-space-and-bottom-apis-on-the-navigation-indicator). <br> **NOTE:** <br>The **ignoreSize** property does not apply to the digit-style navigation indicator in the following scenarios:<br> ? [vertical](arkts-arkui-swiper-comp-attribute.md#vertical) is set to **false** and the value of **bottom** is greater than 0.<br> ? When [vertical](arkts-arkui-swiper-comp-attribute.md#vertical) is set to **true**:<br>1. The value of **bottom** is greater than 0.<br> 2. The value of **bottom** is **undefined**.<br> 3. **isSidebarMiddle** is set to **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation indicator. |

## digit

```TypeScript
static digit(): DigitIndicator
```

Returns a **DigitIndicator** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DigitIndicator](arkts-arkui-digitindicator-c.md) | Digit-style indicator. |

## dot

```TypeScript
static dot(): DotIndicator
```

Returns a **DotIndicator** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DotIndicator](arkts-arkui-dotindicator-c.md) | Dot-style indicator. |

## end

```TypeScript
end(value: LengthMetrics): T
```

Sets the distance between the navigation point indicator and the left edge (in right-to-left scripts) or the right edge (in left-to-right scripts) of the **Swiper** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | Yes | Right-to-left scripts: Distance between the navigation indicator and the left edge of the **Swiper** component.<br>Left-to-right scripts: Distance between the navigation indicator and the right edge of the **Swiper** component.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation indicator. |

## left

```TypeScript
left(value: Length): T
```

Sets the position of the navigation indicator relative to the left edge of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the navigation indicator relative to the left edge of the **Swiper** component.<br>If neither **left** nor **right** is set, the navigation indicator is centered along the main axis based on its own size and the size of the **Swiper** component.<br>If the value specified is **0**, the navigation indicator is placed at the position 0.<br>Priority: higher than the **right** property<br>Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation indicator. |

## right

```TypeScript
right(value: Length): T
```

Sets the position of the navigation indicator relative to the right edge of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the navigation indicator relative to the right edge of the **Swiper** component.<br>If neither **left** nor **right** is set, the navigation indicator is centered along the main axis based on its own size and the size of the **Swiper** component.<br>If the value specified is **0**, the navigation indicator is placed at the position 0.<br>Priority: lower than the **left** property.<br>Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation indicator. |

## start

```TypeScript
start(value: LengthMetrics): T
```

Sets the distance between the navigation indicator and the right edge (in [RTL](../arkts-apis/arkts-arkui-layoutdirection-e.md) scripts) or the left edge (in [LTR](../arkts-apis/arkts-arkui-layoutdirection-e.md) scripts) of the **Swiper** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | Yes | Right-to-left scripts: Distance between the navigation indicator and the right edge of the **Swiper** component.<br>Left-to-right scripts: Distance between the navigation indicator and the left edge of the **Swiper** component.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation indicator. |

## top

```TypeScript
top(value: Length): T
```

Sets the position of the navigation indicator relative to the top edge of the **Swiper** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Position of the navigation indicator relative to the top edge of the **Swiper** component.<br>If neither **top** nor **bottom** is set, the navigation indicator is aligned at the bottom along the cross axis based on its own size and the size of the **Swiper** component, which is the same effect as setting **bottom=0**.<br>If the value specified is **0**, the navigation indicator is placed at the position 0. <br>Priority: higher than the **bottom** property<br>Value range: [0, Swiper height - Navigation indicator area height]. Values outside this range are adjusted to the nearest boundary. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current navigation indicator. |
