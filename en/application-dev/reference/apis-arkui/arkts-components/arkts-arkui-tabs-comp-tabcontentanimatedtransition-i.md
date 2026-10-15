# TabContentAnimatedTransition

```TypeScript
declare interface TabContentAnimatedTransition
```

Defines the information about the custom switching animation of **Tabs**.

**Since:** 11

<!--Device-unnamed-declare interface TabContentAnimatedTransition--><!--Device-unnamed-declare interface TabContentAnimatedTransition-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

Timeout duration of the custom switching animation. If the developer has not called the **finishTransition** API of [TabContentTransitionProxy](arkts-arkui-tabs-comp-tabcontenttransitionproxy-i.md) to notify the **Tabs** component that the custom animation has ended after this duration elapses, the component considers the custom animation ended and directly performs subsequent operations.

Default value: **1000**

Unit: ms

Value range: [0, +∞). If a value less than 0 is set, the default value is used.

**Type:** number

**Default:** 1000 ms

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TabContentAnimatedTransition-timeout?: number--><!--Device-TabContentAnimatedTransition-timeout?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<TabContentTransitionProxy>
```

Specific content of the custom switching animation.

**Type:** Callback&lt;[TabContentTransitionProxy](arkts-arkui-tabs-comp-tabcontenttransitionproxy-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TabContentAnimatedTransition-transition: Callback<TabContentTransitionProxy>--><!--Device-TabContentAnimatedTransition-transition: Callback<TabContentTransitionProxy>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
