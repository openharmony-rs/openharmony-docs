# TouchPoint

Represents information about a single touch point on the display.

**Since:** 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## displayId

```TypeScript
displayId: number
```

Unique ID of the display where the touch point is located. The value must be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## displayX

```TypeScript
displayX: number
```

X coordinate of the touch point relative to the left edge of the display, in pixels. The value must be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## displayY

```TypeScript
displayY: number
```

Y coordinate of the touch point relative to the top edge of the display, in pixels. The value must be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## id

```TypeScript
id: number
```

Unique ID of a touch point. The value must be an integer in the range of [0, 9].

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator
