# Touch

Defines the touch point information.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action as KeyAction, SourceType, ToolType, Touch, TouchEvent, FixedMode } from '@kit.InputKit';
```

## globalX

```TypeScript
globalX?: number
```

X coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin, in px. <!--Del--> When being used as an input parameter, this parameter is mandatory if the value of [TouchEventData.useGlobalCoordinate](arkts-input-inputeventclient-toucheventdata-i-sys.md) is **true**, and its value can only be an integer. Otherwise, you do not need to set this parameter. In this case, the X coordinate of the relative coordinate system with the upper left corner of the specified screen as the origin is used to calculate the injected event. <!--DelEnd-->When being used as an output parameter, its value is reported by the system.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalInput.Input.Core

## globalY

```TypeScript
globalY?: number
```

Y coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin, in px. <!--Del--> When being used as an input parameter, this parameter is mandatory if the value of [TouchEventData.useGlobalCoordinate](arkts-input-inputeventclient-toucheventdata-i-sys.md) is **true**, and its value can only be an integer. Otherwise, you do not need to set this parameter. In this case, the Y coordinate of the relative coordinate system with the upper left corner of the specified screen as the origin is used to calculate the injected event. <!--DelEnd-->When being used as an output parameter, its value is reported by the system.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalInput.Input.Core

## height

```TypeScript
height: number
```

Height of the touch area, in pixels. The value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## id

```TypeScript
id: number
```

Touch event ID.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## pressedTime

```TypeScript
pressedTime: number
```

Press timestamp, in microseconds (μs) since the system starts.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## pressure

```TypeScript
pressure: number
```

Pressure value. The value range is [0.0, 1.0]. The value **0.0** indicates that the pressure is not supported.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## rawX

```TypeScript
rawX: number
```

X coordinate of the input device. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## rawY

```TypeScript
rawY: number
```

Y coordinate of the input device. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## screenX

```TypeScript
screenX: number
```

X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## screenY

```TypeScript
screenY: number
```

Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## tiltX

```TypeScript
tiltX: number
```

Angle relative to the YZ plane, in degrees. The value range is [-90, 90]. A positive value indicates a rightward tilt.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## tiltY

```TypeScript
tiltY: number
```

Angle relative to the XZ plane, in degrees. The value range is [-90, 90]. A positive value indicates a downward tilt.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## toolHeight

```TypeScript
toolHeight: number
```

Height of the tool area, in pixels. The value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## toolType

```TypeScript
toolType: ToolType
```

Tool type.

**Type:** [ToolType](arkts-input-multimodalinput-touchevent-tooltype-e.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## toolWidth

```TypeScript
toolWidth: number
```

Width of the tool area, in pixels. The value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## toolX

```TypeScript
toolX: number
```

X coordinate of the tool area center in the relative coordinate system with the upper-left corner of the specified screen as the origin. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## toolY

```TypeScript
toolY: number
```

Y coordinate of the tool area center in the relative coordinate system with the upper-left corner of the specified screen as the origin. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## width

```TypeScript
width: number
```

Width of the touch area, in pixels. The value can only be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## windowX

```TypeScript
windowX: number
```

X coordinate in the relative coordinate system with the upper-left corner of the window where the touch is located as the origin. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## windowY

```TypeScript
windowY: number
```

Y coordinate in the relative coordinate system with the upper-left corner of the window where the touch is located as the origin. Currently, only integers are supported. The unit is pixels.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core
