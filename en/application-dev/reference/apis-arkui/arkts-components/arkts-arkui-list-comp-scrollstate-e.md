# ScrollState

```TypeScript
declare enum ScrollState
```

Enumerates the scrolling states.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Idle

```TypeScript
Idle
```

Idle state. Triggered when the scroll state returns to idle, and when the controller's non-animated methods are used to control the scroll.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Scroll

```TypeScript
Scroll
```

Scrolling state. Triggered when the list is dragged with the finger, when the scrollbar is dragged, or when the mouse scroll wheel is used.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Fling

```TypeScript
Fling
```

Inertial scrolling state. Triggered by all animated scroll actions. This includes: Inertial scrolling that occurs after a fling;

Bounce-back scrolling when the swipe reaches the edge; Inertial scrolling after quickly dragging the built-in scrollbar and releasing;

Scrolling controlled by the animated methods provided by the scroller.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
