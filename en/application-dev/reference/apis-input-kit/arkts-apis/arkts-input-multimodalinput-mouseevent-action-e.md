# Action

```TypeScript
export declare enum Action
```

Enumerates mouse event types.

**Since:** 9

<!--Device-unnamed-export declare enum Action--><!--Device-unnamed-export declare enum Action-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## CANCEL

```TypeScript
CANCEL = 0
```

Canceled. The down event of the mouse is interrupted unexpectedly and does not close normally. For example, the **CANCEL** event is triggered when the mouse button is pressed but not released, the window transitions to the background, or an abnormal destruction occurs.

**Since:** 9

<!--Device-Action-CANCEL = 0--><!--Device-Action-CANCEL = 0-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## MOVE

```TypeScript
MOVE = 1
```

Moving of the mouse pointer.

**Since:** 9

<!--Device-Action-MOVE = 1--><!--Device-Action-MOVE = 1-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## BUTTON_DOWN

```TypeScript
BUTTON_DOWN = 2
```

Mouse button press.

**Since:** 9

<!--Device-Action-BUTTON_DOWN = 2--><!--Device-Action-BUTTON_DOWN = 2-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## BUTTON_UP

```TypeScript
BUTTON_UP = 3
```

Mouse button release.

**Since:** 9

<!--Device-Action-BUTTON_UP = 3--><!--Device-Action-BUTTON_UP = 3-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## AXIS_BEGIN

```TypeScript
AXIS_BEGIN = 4
```

Beginning of the mouse axis event.

**Since:** 9

<!--Device-Action-AXIS_BEGIN = 4--><!--Device-Action-AXIS_BEGIN = 4-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## AXIS_UPDATE

```TypeScript
AXIS_UPDATE = 5
```

Updating of the mouse axis event.

**Since:** 9

<!--Device-Action-AXIS_UPDATE = 5--><!--Device-Action-AXIS_UPDATE = 5-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## AXIS_END

```TypeScript
AXIS_END = 6
```

Mouse axis event ended.

**Since:** 9

<!--Device-Action-AXIS_END = 6--><!--Device-Action-AXIS_END = 6-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## ACTION_DOWN

```TypeScript
ACTION_DOWN = 7
```

Touchpad press.

**Since:** 11

<!--Device-Action-ACTION_DOWN = 7--><!--Device-Action-ACTION_DOWN = 7-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## ACTION_UP

```TypeScript
ACTION_UP = 8
```

Touchpad release.

**Since:** 11

<!--Device-Action-ACTION_UP = 8--><!--Device-Action-ACTION_UP = 8-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core
