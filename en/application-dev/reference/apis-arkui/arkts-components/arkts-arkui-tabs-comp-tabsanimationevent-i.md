# TabsAnimationEvent

```TypeScript
declare interface TabsAnimationEvent
```

Describes the animation information of the **Tabs** component.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentOffset

```TypeScript
currentOffset: number
```

Offset of the currently displayed element relative to the start position of the **Tabs** component along the main axis.

Unit: vp.

Default value: **0**.

**Type:** number

**Default:** 0.0 vp

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## targetOffset

```TypeScript
targetOffset: number
```

Offset of the target element relative to the start position of the **Tabs** component along the main axis.

Unit: vp.

Default value: **0**.

**Type:** number

**Default:** 0.0 vp

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: number
```

Hands-off velocity at the beginning of the animation. Unit: vp/s.

Default value: **0**.

**Type:** number

**Default:** 0.0 vp/s

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
