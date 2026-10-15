# TabsAnimationEvent

```TypeScript
declare interface TabsAnimationEvent
```

Defines a collection of animation-related information of the **Tabs** component.

**Since:** 11

<!--Device-unnamed-declare interface TabsAnimationEvent--><!--Device-unnamed-declare interface TabsAnimationEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentOffset

```TypeScript
currentOffset: number
```

Offset of the currently displayed element of **Tabs** relative to the start position of **Tabs** along the main axis. Unit: vp. Default value: **0**. A positive value indicates an offset to the right (horizontal) or downward (vertical), and a negative value indicates an offset to the left (horizontal) or upward (vertical).

**Type:** number

**Default:** 0.0 vp

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAnimationEvent-currentOffset: number--><!--Device-TabsAnimationEvent-currentOffset: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## targetOffset

```TypeScript
targetOffset: number
```

Offset of the animation target element of **Tabs** relative to the start position of **Tabs** along the main axis. Unit: vp. Default value: **0**. A positive value indicates an offset to the right (horizontal) or downward (vertical), and a negative value indicates an offset to the left (horizontal) or upward (vertical).

**Type:** number

**Default:** 0.0 vp

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAnimationEvent-targetOffset: number--><!--Device-TabsAnimationEvent-targetOffset: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: number
```

Release velocity of **Tabs** when the release animation starts. Unit: vp/s. Default value: **0**. A positive value indicates sliding to the right (horizontal) or downward (vertical), and a negative value indicates sliding to the left (horizontal) or upward (vertical). A larger velocity value indicates faster sliding. This parameter can be used to implement the inertial scrolling effect.

**Type:** number

**Default:** 0.0 vp/s

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAnimationEvent-velocity: number--><!--Device-TabsAnimationEvent-velocity: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
