# MouseEvent

Defines the mouse event.

**Inheritance/Implementation:** MouseEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action as MouseAction, Axis, AxisValue, Button, MouseEvent, ToolType as MouseToolType } from '@kit.InputKit';
```

## action

```TypeScript
action: Action
```

Enumerates mouse event types.

**Type:** [Action](arkts-input-multimodalinput-mouseevent-action-e.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## altKey

```TypeScript
altKey: boolean
```

Whether altKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## axes

```TypeScript
axes: AxisValue[]
```

Defines the mouse axis type and axis value.

**Type:** [AxisValue](arkts-input-multimodalinput-mouseevent-axisvalue-i.md)[]

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## button

```TypeScript
button: Button
```

Enumerates mouse buttons.

**Type:** [Button](arkts-input-multimodalinput-mouseevent-button-e.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## capsLock

```TypeScript
capsLock: boolean
```

Whether capsLock is enabled.

The value **true** indicates that capsLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## ctrlKey

```TypeScript
ctrlKey: boolean
```

Whether ctrlKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## fnKey

```TypeScript
fnKey: boolean
```

Whether fnKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## globalX

```TypeScript
globalX?: number
```

X coordinate of the mouse event in the global coordinate system with the upper left corner of the primary screen as the origin, in px. When this parameter is used as an input parameter, it is mandatory and supports only integers if [MouseEventData.useGlobalCoordinate](arkts-input-inputeventclient-mouseeventdata-i-sys.md) is set to **true**. If **MouseEventData.useGlobalCoordinate** is set to **false**, this parameter is optional, and the X coordinate in the relative coordinate system with the upper left corner of the specified screen as the origin is used to calculate the injected event. When this parameter is used as an output parameter, it is reported by the system.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalInput.Input.Core

## globalY

```TypeScript
globalY?: number
```

Y coordinate of the mouse event in the global coordinate system with the upper left corner of the primary screen as the origin, in px. When this parameter is used as an input parameter, it is mandatory and supports only integers if [MouseEventData.useGlobalCoordinate](arkts-input-inputeventclient-mouseeventdata-i-sys.md) is set to **true**. If **MouseEventData.useGlobalCoordinate** is set to **false**, this parameter is optional, and the Y coordinate in the relative coordinate system with the upper left corner of the specified screen as the origin is used to calculate the injected event. When this parameter is used as an output parameter, it is reported by the system.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalInput.Input.Core

## logoKey

```TypeScript
logoKey: boolean
```

Whether logoKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## numLock

```TypeScript
numLock: boolean
```

Whether numLock is enabled.

The value **true** indicates that numLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## pressedButtons

```TypeScript
pressedButtons: Button[]
```

Button being pressed.

**Type:** [Button](arkts-input-multimodalinput-mouseevent-button-e.md)[]

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## pressedKeys

```TypeScript
pressedKeys: KeyCode[]
```

List of pressed keys.

**Type:** [KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md)[]

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## rawDeltaX

```TypeScript
rawDeltaX: number
```

X coordinate offset of the current mouse event relative to the previous event, in px. Currently, the value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## rawDeltaY

```TypeScript
rawDeltaY: number
```

Y coordinate offset of the current mouse event relative to the previous event, in px. Currently, the value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## screenX

```TypeScript
screenX: number
```

X coordinate of the mouse event in the relative coordinate system with the upper left corner of the specified screen as the origin, in px. Currently, the value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## screenY

```TypeScript
screenY: number
```

Y coordinate of the mouse event in the relative coordinate system with the upper left corner of the specified screen as the origin, in px. Currently, the value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## scrollLock

```TypeScript
scrollLock: boolean
```

Whether scrollLock is enabled.

The value **true** indicates that scrollLock is enabled, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## shiftKey

```TypeScript
shiftKey: boolean
```

Whether shiftKey is being pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## toolType

```TypeScript
toolType: ToolType
```

Tool type.

**Type:** [ToolType](arkts-input-multimodalinput-mouseevent-tooltype-e.md)

**Since:** 11

**System capability:** SystemCapability.MultimodalInput.Input.Core

## windowX

```TypeScript
windowX: number
```

X coordinate in the relative coordinate system with the upper left corner of the window where the mouse is located as the origin, in px. Currently, the value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## windowY

```TypeScript
windowY: number
```

Y coordinate in the relative coordinate system with the upper left corner of the window where the mouse is located as the origin, in px. Currently, the value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core
