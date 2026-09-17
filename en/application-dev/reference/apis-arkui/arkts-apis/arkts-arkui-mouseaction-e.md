# MouseAction

Sets the action type of a mouse operation.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Press

```TypeScript
Press
```

The mouse button is pressed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Release

```TypeScript
Release
```

The mouse button is released.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Move

```TypeScript
Move
```

The mouse cursor moves.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Hover

```TypeScript
Hover
```

The mouse pointer is hovered on an element.

Note: This value has no effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENTER_WINDOW

```TypeScript
ENTER_WINDOW = 4
```

The mouse pointer moves into the window.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LEAVE_WINDOW

```TypeScript
LEAVE_WINDOW = 5
```

The mouse pointer moves out of the window.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CANCEL

```TypeScript
CANCEL = 13
```

The mouse button action is canceled. It is triggered in the following scenarios:

1. Component focus loss: This action is triggered when a currently focused component loses focus due to a system
event (such as pop-up interruption or app switching).
2. Event interruption: During a mouse operation, if a higher-priority event occurs (such as a system-level gesture
or forced event stream recycling), causing the current mouse operation to be forcibly terminated.
3. Abnormal state exit: In scenarios such as component destruction or abnormal rendering environment, unfinished
mouse events are marked as canceled.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
