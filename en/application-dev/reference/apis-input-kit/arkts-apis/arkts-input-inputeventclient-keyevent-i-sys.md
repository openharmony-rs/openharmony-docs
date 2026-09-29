# KeyEvent (System API)

```TypeScript
interface KeyEvent
```

Defines the key event to inject.

**Since:** 8

<!--Device-inputEventClient-interface KeyEvent--><!--Device-inputEventClient-interface KeyEvent-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## displayId

```TypeScript
displayId? : number
```

Target display ID. The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-KeyEvent-displayId? : int--><!--Device-KeyEvent-displayId? : int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## isIntercepted

```TypeScript
isIntercepted: boolean
```

Whether the key event can be intercepted.

The value **true** indicates that the key event can be intercepted, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 8

<!--Device-KeyEvent-isIntercepted: boolean--><!--Device-KeyEvent-isIntercepted: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## isPressed

```TypeScript
isPressed: boolean
```

Whether the key is pressed.

The value **true** indicates that the key is pressed, and the value **false** indicates that the key is released.

**Type:** boolean

**Since:** 8

<!--Device-KeyEvent-isPressed: boolean--><!--Device-KeyEvent-isPressed: boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## keyCode

```TypeScript
keyCode: number
```

Key code. Currently, only the **KEYCODE_BACK** key is supported.

**Type:** number

**Since:** 8

<!--Device-KeyEvent-keyCode: int--><!--Device-KeyEvent-keyCode: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## keyDownDuration

```TypeScript
keyDownDuration: number
```

Duration of key press, in microseconds (μs).

**Type:** number

**Since:** 8

<!--Device-KeyEvent-keyDownDuration: int--><!--Device-KeyEvent-keyDownDuration: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.
