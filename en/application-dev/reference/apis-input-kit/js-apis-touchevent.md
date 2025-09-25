# @ohos.multimodalInput.touchEvent (Touch Event)

The **touchEvent** module provides screen touch events reported by a device. It is inherited from [InputEvent](./js-apis-inputevent.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { Action,ToolType,SourceType,Touch,TouchEvent } from '@kit.InputKit';
```

## Action

Touch event type.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name    | Value  | Description  |
| ------ | ------ | ---- |
| CANCEL | 0 | Touch cancellation.|
| DOWN   | 1 | Touch press.|
| MOVE   | 2 | Touch moving.|
| UP     | 3 | Touch release.|

## ToolType

Enumerates touch tool types.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name      | Value  | Description  |
| -------- | ------ | ---- |
| FINGER   | 0 | Finger. |
| PEN      | 1 | Stylus.   |
| RUBBER   | 2 | Eraser. |
| BRUSH    | 3 | Brush.  |
| PENCIL   | 4 | Pencil.  |
| AIRBRUSH | 5 | Air brush.  |
| MOUSE    | 6 | Mouse.  |
| LENS     | 7 | Lens.  |

## SourceType 

Enumerates touch sources. Currently, only the touchscreen and touchpad are supported.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name          | Value | Description  |
| ------------ | ------ | ---- |
| TOUCH_SCREEN | 0 | Touchscreen. |
| PEN          | 1 | Stylus. |
| TOUCH_PAD    | 2 | Touchpad. |

## Touch

Defines the touch point information.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name         | Type  | Read-Only  | Optional  | Description                                 |
| ----------- | ------ | ---- | ---- | ----------------------------------- |
| id          | number | No   | No   | Touch event ID.                               |
| pressedTime | number | No   | No   | Press timestamp, in μs.                          |
| screenX     | number | No   | No   | X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin. The value can only be set to an integer.   |
| screenY     | number | No   | No   | Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin. The value can only be set to an integer.   |
| windowX     | number | No   | No   | X coordinate in the relative coordinate system with the upper-left corner of the window where the touch is located as the origin. The value can only be set to an integer.|
| windowY     | number | No   | No   | Y coordinate in the relative coordinate system with the upper-left corner of the window where the touch is located as the origin. The value can only be set to an integer.|
| pressure    | number | No   | No   | Pressure value. The value range is [0.0, 1.0]. The value **0.0** indicates that the pressure is not supported.      |
| width       | number | No   | No   | Width of the touch area. The value can only be set to an integer.        |
| height      | number | No   | No   | Height of the touch area. The value can only be set to an integer.        |
| tiltX       | number | No   | No   | Angle relative to the YZ plane. The value range is [-90, 90]. A positive value indicates a rightward tilt.|
| tiltY       | number | No   | No   | Angle relative to the XZ plane. The value range is [-90, 90]. A positive value indicates a downward tilt.|
| toolX       | number | No   | No   | X coordinate of the tool area center in the relative coordinate system with the upper-left corner of the specified screen as the origin. The value can only be set to an integer. |
| toolY       | number | No   | No   | Y coordinate of the tool area center in the relative coordinate system with the upper-left corner of the specified screen as the origin. The value can only be set to an integer. |
| toolWidth   | number | No   | No   | Width of the tool area. The value can only be set to an integer. |
| toolHeight  | number | No   | No   | Height of the tool area. The value can only be set to an integer. |
| rawX        | number | No   | No   | X coordinate of the input device. The value can only be set to an integer.|
| rawY        | number | No   | No   | Y coordinate of the input device. The value can only be set to an integer.|
| toolType    | [ToolType](#tooltype) | No   | No   | Tool type.                               |

## TouchEvent

Defines a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name        | Type      | Read-Only  | Optional  | Description       |
| ---------- | ---------- | ---- | ---- | --------- |
| action     | [Action](#action)     | No   | No   | Touch event type.    |
| touch      | [Touch](#touch)      | No   | No   | Current touch point.  |
| touches    | [Touch](#touch)[]    | No   | No   | All touch points.    |
| sourceType | [SourceType](#sourcetype) | No   | No   | Device type of the touch source.|
