# TabContentAnimatedTransition

Provides the information about the custom tab switching animation.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

Timeout for the custom tab switching animation. The timer starts when the switching begins. If this timeframe passes without you calling the **finishTransition** API in [TabContentTransitionProxy](arkts-arkui-tabcontenttransitionproxy-i.md), the component will assume that the custom animation has ended and will proceed directly with subsequent operations.

Default value: **1000**

Unit: ms

Value range: [0, +∞)

**Type:** number

**Default:** 1000 ms

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<TabContentTransitionProxy>
```

Content of the custom tab switching animation.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[TabContentTransitionProxy](arkts-arkui-tabcontenttransitionproxy-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
