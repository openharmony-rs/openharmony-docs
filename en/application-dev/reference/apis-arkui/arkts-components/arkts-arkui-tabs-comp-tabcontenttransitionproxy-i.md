# TabContentTransitionProxy

```TypeScript
declare interface TabContentTransitionProxy
```

Implements the proxy object returned during the execution of the custom switching animation of the **Tabs** component. You can use this object to obtain the information about the start and target pages of the custom animation. You can also call the **finishTransition** API of this object to notify the **Tabs** component that the custom animation has finished playing.

**Since:** 11

<!--Device-unnamed-declare interface TabContentTransitionProxy--><!--Device-unnamed-declare interface TabContentTransitionProxy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## finishTransition

```TypeScript
finishTransition(): void
```

Notifies the **Tabs** component that the custom animation of this page has ended.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TabContentTransitionProxy-finishTransition(): void--><!--Device-TabContentTransitionProxy-finishTransition(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: number
```

Index of the start page of the custom animation. The index starts from 0.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TabContentTransitionProxy-from: number--><!--Device-TabContentTransitionProxy-from: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: number
```

Index of the target page of the custom animation. The index starts from 0.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TabContentTransitionProxy-to: number--><!--Device-TabContentTransitionProxy-to: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
