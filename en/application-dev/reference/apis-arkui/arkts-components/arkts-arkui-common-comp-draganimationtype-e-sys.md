# DragAnimationType (System API)

```TypeScript
declare enum DragAnimationType
```

Enumerates drag animation types.

**Since:** 26.0.0

<!--Device-unnamed-declare enum DragAnimationType--><!--Device-unnamed-declare enum DragAnimationType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## DEFAULT

```TypeScript
DEFAULT = 0
```

Uses the default drag animation, which applies to common drag scenarios that do not require a custom drop animation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DragAnimationType-DEFAULT = 0--><!--Device-DragAnimationType-DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## FOLLOW_HAND_MORPH

```TypeScript
FOLLOW_HAND_MORPH = 1
```

Uses the follow-hand morph drag animation, which applies to scenarios where the dragged element morphs with the gesture and a custom drop animation is executed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DragAnimationType-FOLLOW_HAND_MORPH = 1--><!--Device-DragAnimationType-FOLLOW_HAND_MORPH = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
