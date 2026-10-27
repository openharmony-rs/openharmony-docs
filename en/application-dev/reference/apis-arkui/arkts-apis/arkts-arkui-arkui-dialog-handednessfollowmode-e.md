# HandednessFollowMode

```TypeScript
export enum HandednessFollowMode
```

Indicates how a dialog follows the handedness.

**Since:** 26.1.0

<!--Device-unnamed-export enum HandednessFollowMode--><!--Device-unnamed-export enum HandednessFollowMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_ANCHOR

```TypeScript
FOLLOW_ANCHOR = 1
```

The dialog follows the position of the component that triggers it (the last interacted component).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-HandednessFollowMode-FOLLOW_ANCHOR = 1--><!--Device-HandednessFollowMode-FOLLOW_ANCHOR = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_GRIP_HAND

```TypeScript
FOLLOW_GRIP_HAND = 2
```

The dialog follows the grip hand (the hand holding the device, distinguished from the operating hand interacting with the screen).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-HandednessFollowMode-FOLLOW_GRIP_HAND = 2--><!--Device-HandednessFollowMode-FOLLOW_GRIP_HAND = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

No adaptation. The dialog keeps the current layout. Default value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-HandednessFollowMode-NONE = 0--><!--Device-HandednessFollowMode-NONE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
