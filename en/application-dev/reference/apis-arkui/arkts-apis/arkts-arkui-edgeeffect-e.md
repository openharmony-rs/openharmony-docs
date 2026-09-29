# EdgeEffect

```TypeScript
declare enum EdgeEffect
```

Defines the sliding effect of the scrollable container.

**Since:** 7

<!--Device-unnamed-declare enum EdgeEffect--><!--Device-unnamed-declare enum EdgeEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Spring

```TypeScript
Spring
```

Spring effect. When at one of the edges, the component can move beyond the bounds based on initial velocity or through touches, and produces a bounce effect when the user releases their finger.

In API version 22 and earlier versions, the spring effect of the scrollable component does not take effect when the scrollbar is dragged.

In API version 23 and later versions, the spring effect of the scrollable component takes effect when the scrollbar is dragged by fingers, but does not take effect when the scrollbar is dragged by a mouse.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-EdgeEffect-Spring--><!--Device-EdgeEffect-Spring-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Fade

```TypeScript
Fade
```

Fade effect. When at one of the edges, the component produces a fade effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-EdgeEffect-Fade--><!--Device-EdgeEffect-Fade-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None
```

No effect when the component is at one of the edges.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-EdgeEffect-None--><!--Device-EdgeEffect-None-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
