# @ohos.multimodalInput.inputEventClient (Input Event Injection) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

The **inputEventClient** module provides the capability of injecting key, mouse/touchpad, and touchscreen events.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.

## Modules to Import

```js
import { inputEventClient } from '@kit.InputKit';
```

## inputEventClient.injectEvent

injectEvent({KeyEvent: KeyEvent}): void

Injects keys (including single keys and combination keys).

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.INJECT_INPUT_EVENT

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| KeyEvent | [KeyEvent](#keyevent) | Yes   | Key event to inject.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 202  | Permission denied, non-system app called system api.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let backKeyDown: inputEventClient.KeyEvent = {
              isPressed: true,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            }
            inputEventClient.injectEvent({ KeyEvent: backKeyDown });

            let backKeyUp: inputEventClient.KeyEvent = {
              isPressed: false,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            };
            inputEventClient.injectEvent({ KeyEvent: backKeyUp });
          } catch (error) {
            console.error(`Failed to inject KeyEvent, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputEventClient.injectKeyEvent<sup>11+</sup>

injectKeyEvent(keyEvent: KeyEventData): void

Injects key events (for both single keys and combination keys).

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.INJECT_INPUT_EVENT

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| keyEvent | [KeyEventData](#keyeventdata11) | Yes   | Key event to inject.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let backKeyDown: inputEventClient.KeyEvent = {
              isPressed: true,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            }

            class EventDown {
              keyEvent: inputEventClient.KeyEvent | null = null
            }

            let eventDown: EventDown = { keyEvent: backKeyDown }
            inputEventClient.injectKeyEvent(eventDown);

            let backKeyUp: inputEventClient.KeyEvent = {
              isPressed: false,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            };

            class EventUp {
              keyEvent: inputEventClient.KeyEvent | null = null
            }

            let eventUp: EventUp = { keyEvent: backKeyUp }
            inputEventClient.injectKeyEvent(eventUp);
          } catch (error) {
            console.error(`Failed to inject KeyEvent, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```
## inputEventClient.injectMouseEvent<sup>11+</sup>

injectMouseEvent(mouseEvent: MouseEventData): void

Injects a mouse/touchpad event.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.INJECT_INPUT_EVENT

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| mouseEvent | [MouseEventData](#mouseeventdata11) | Yes   | Mouse/touchpad event to inject. [Action](js-apis-mouseevent.md#action) in this parameter cannot be set to **CANCEL**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputEventClient } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let mouseButtonUpData: MouseEvent = {
              id: 0,
              deviceId: 1,
              actionTime: 2,
              screenId: 1,
              windowId: 0,
              action: 3,
              screenX: 100,
              screenY: 200,
              windowX: 100,
              windowY: 200,
              rawDeltaX: 200,
              rawDeltaY: 200,
              button: 2,
              pressedButtons: [2],
              axes: [],
              pressedKeys: [0],
              ctrlKey: false,
              altKey: false,
              shiftKey: false,
              logoKey: false,
              fnKey: false,
              capsLock: false,
              numLock: false,
              scrollLock: false,
              toolType: 1,
            }
            let mouseButtonUp: inputEventClient.MouseEventData = {
              mouseEvent: mouseButtonUpData
            }
            inputEventClient.injectMouseEvent(mouseButtonUp);

            let mouseButtonDownData: MouseEvent = {
              id: 0,
              deviceId: 1,
              actionTime: 2,
              screenId: 1,
              windowId: 0,
              action: 2,
              screenX: 100,
              screenY: 200,
              windowX: 100,
              windowY: 200,
              rawDeltaX: 200,
              rawDeltaY: 200,
              button: 2,
              pressedButtons: [2],
              axes: [],
              pressedKeys: [0],
              ctrlKey: false,
              altKey: false,
              shiftKey: false,
              logoKey: false,
              fnKey: false,
              capsLock: false,
              numLock: false,
              scrollLock: false,
              toolType: 1,
            }
            let mouseButtonDown: inputEventClient.MouseEventData = {
              mouseEvent: mouseButtonDownData
            };
            inputEventClient.injectMouseEvent(mouseButtonDown);
          }

          catch (error) {
            console.error(`Failed to inject MouseEvent, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputEventClient.injectTouchEvent<sup>11+</sup>

injectTouchEvent(touchEvent: TouchEventData): void

Injects a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.INJECT_INPUT_EVENT

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| touchEvent | [TouchEventData](#toucheventdata11) | Yes   | Touch event data. [Action](js-apis-touchevent.md#action) in this parameter cannot be set to **CANCEL**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputEventClient } from '@kit.InputKit';
import { Touch, TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let touchEvent: Touch = {
              id: 1,
              pressedTime: 1,
              screenX: 0,
              screenY: 0,
              windowX: 0,
              windowY: 0,
              pressure: 0,
              width: 0,
              height: 0,
              tiltX: 0,
              tiltY: 0,
              toolX: 0,
              toolY: 0,
              toolWidth: 0,
              toolHeight: 0,
              rawX: 0,
              rawY: 0,
              toolType: 0,
            }

            let touchEventUpData: TouchEvent = {
              action: 3,
              sourceType: 0,
              touch: touchEvent,
              touches: [],
              id: 0,
              deviceId: 0,
              actionTime: 0,
              screenId: 0,
              windowId: 0
            }
            ;
            let touchEventUp: inputEventClient.TouchEventData = {
              touchEvent: touchEventUpData
            }
            inputEventClient.injectTouchEvent(touchEventUp);

            let touchEventDownData: TouchEvent = {
              action: 1,
              sourceType: 0,
              touch: touchEvent,
              touches: [],
              id: 0,
              deviceId: 0,
              actionTime: 0,
              screenId: 0,
              windowId: 0
            }
            ;
            let touchEventDown: inputEventClient.TouchEventData = {
              touchEvent: touchEventDownData
            }
            inputEventClient.injectTouchEvent(touchEventDown);
          } catch (error) {
            console.error(`Failed to inject touchEvent, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputEventClient.permitInjection<sup>12+</sup>

permitInjection(result: boolean): void

Specifies whether to authorize event injection.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.INJECT_INPUT_EVENT

**Parameters**

| Name   | Type   | Mandatory  | Description       |
| -------- | ------  | ----   | --------- |
| result   | boolean | Yes    | Authorization result. The value **true** indicates that event injection is allowed, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |


```ts
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let result = true;
            inputEventClient.permitInjection(result);
          }catch(error){
            console.error("failed:" + JSON.stringify(error));
          }
        })
    }
  }
}
```

## inputEventClient.createKeyboardController<sup>26+</sup>

createKeyboardController(): Promise&lt;KeyboardController&gt;

Creates a keyboard controller for simulating key operations. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;[KeyboardController](#keyboardcontroller26)&gt; | Promise used to return the keyboard controller instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 801  | Capability not supported.  |
| 3800001  | Input service exception.  |

**Example**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let keyboardController = await inputEventClient.createKeyboardController();
            console.log('Keyboard controller created successfully');
          } catch (error) {
            console.error(`Failed to create keyboard controller, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputEventClient.createMouseController<sup>26+</sup>

createMouseController(): Promise&lt;MouseController&gt;

Creates a mouse controller for simulating mouse operations. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;[MouseController](#mousecontroller26)&gt; | Promise used to return the mouse controller instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 801  | Capability not supported.  |
| 3800001  | Input service exception.  |

**Example**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            console.log('Mouse controller created successfully');
          } catch (error) {
            console.error(`Failed to create mouse controller, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## KeyboardController<sup>26+</sup>

Provides functions for simulating key operations. Simulated key operation sequences must meet the following requirements:

1. A key can only be pressed if it is released, or if it is the last pressed key and has not been released.
2. A key can only be released after being pressed.
3. A maximum of five keys may be pressed and held at the same time.

### pressKey<sup>26+</sup>

pressKey(keyCode: KeyCode): Promise&lt;void&gt;

Presses a key. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| keyCode | [KeyCode](js-apis-keycode.md#keycode) | Yes   | Key code of the key to press.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300001  | The key is already pressed and is not the most recently pressed key.  |

**Example**

```js
import { inputEventClient, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let keyboardController = await inputEventClient.createKeyboardController();
            await keyboardController.pressKey(KeyCode.KEYCODE_A);
            console.log('Key pressed successfully');
          } catch (error) {
            console.error(`Failed to press key, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### releaseKey<sup>26+</sup>

releaseKey(keyCode: KeyCode): Promise&lt;void&gt;

Releases a key. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| keyCode | [KeyCode](js-apis-keycode.md#keycode) | Yes   | Key code of the key to release.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300001  | The key is not pressed.  |

**Example**

```js
import { inputEventClient, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let keyboardController = await inputEventClient.createKeyboardController();
            await keyboardController.pressKey(KeyCode.KEYCODE_A);
            await keyboardController.releaseKey(KeyCode.KEYCODE_A);
            console.log('Key released successfully');
          } catch (error) {
            console.error(`Failed to release key, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## MouseController<sup>26+</sup>

Provides functions for simulating mouse operations. Simulated mouse operation sequences must meet the following requirements:

1. A mouse button can only be pressed when it is released.
2. A mouse button can only be released when it is pressed.
3. A valid axis event sequence must begin, include zero or more updates, then end.
4. There can be only one outstanding axis event sequence at the same time.

### moveTo<sup>26+</sup>

moveTo(displayId: number, displayX: number, displayY: number): Promise&lt;void&gt;

Moves the mouse cursor to the specified display coordinates. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| displayId | number | Yes   | Target display ID.|
| displayX | number | Yes   | X coordinate of the target position relative to the left edge of the display, in px.|
| displayY | number | Yes   | Y coordinate of the target position relative to the top edge of the display, in px.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300002  | The display does not exist.  |

**Example**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.moveTo(0, 100, 200);
            console.log('Mouse moved successfully');
          } catch (error) {
            console.error(`Failed to move mouse, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### pressButton<sup>26+</sup>

pressButton(button: Button): Promise&lt;void&gt;

Presses a mouse button. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| button | [Button](js-apis-mouseevent.md#button) | Yes   | Mouse button to press.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300001  | The mouse button is already pressed.  |

**Example**

```js
import { inputEventClient, Button } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.pressButton(Button.LEFT);
            console.log('Mouse button pressed successfully');
          } catch (error) {
            console.error(`Failed to press mouse button, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### releaseButton<sup>26+</sup>

releaseButton(button: Button): Promise&lt;void&gt;

Releases a mouse button. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| button | [Button](js-apis-mouseevent.md#button) | Yes   | Mouse button to release.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300001  | The mouse button is not pressed.  |

**Example**

```js
import { inputEventClient, Button } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.pressButton(Button.LEFT);
            await mouseController.releaseButton(Button.LEFT);
            console.log('Mouse button released successfully');
          } catch (error) {
            console.error(`Failed to release mouse button, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### beginAxis<sup>26+</sup>

beginAxis(axis: Axis, value: number): Promise&lt;void&gt;

Begins an axis event. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | Yes   | Axis type.|
| value | number | Yes   | Axis value.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300001  | The axis event is in progress.  |

**Example**

```js
import { inputEventClient, Axis } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            console.log('Axis event begun successfully');
          } catch (error) {
            console.error(`Failed to begin axis event, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### updateAxis<sup>26+</sup>

updateAxis(axis: Axis, value: number): Promise&lt;void&gt;

Updates an axis event. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | Yes   | Axis type.|
| value | number | Yes   | Axis value.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300001  | The axis event is not in progress.  |

**Example**

```js
import { inputEventClient, Axis } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 20);
            console.log('Axis event updated successfully');
          } catch (error) {
            console.error(`Failed to update axis event, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### endAxis<sup>26+</sup>

endAxis(axis: Axis): Promise&lt;void&gt;

Ends an axis event. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

Permission required: ohos.permission.CONTROL_DEVICE

**Parameters**

| Name      | Type                   | Mandatory  | Description       |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | Yes   | Axis type.|

**Return value**

| Type                   | Description       |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.  |
| 3800001  | Input service exception.  |
| 4300001  | The axis event is not in progress.  |

**Example**

```js
import { inputEventClient, Axis } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 20);
            await mouseController.endAxis(Axis.VERTICAL_SCROLL);
            console.log('Axis event ended successfully');
          } catch (error) {
            console.error(`Failed to end axis event, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## KeyEvent

Defines the key event to inject.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| isPressed       | boolean | No   |  No| Whether the key is pressed.<br>The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.  |
| keyCode         | number  | No   |  No| Key code. Currently, only the **KEYCODE_BACK** key is supported.|
| keyDownDuration | number  | No   |  No| Duration for pressing a key, in μs.          |
| isIntercepted   | boolean | No   |  No| Whether the key event can be intercepted.<br>The value **true** indicates that the key event can be intercepted, and the value **false** indicates the opposite.|

## KeyEventData<sup>11+</sup>

Defines the key event to inject.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| keyEvent       | [KeyEvent](#keyevent) | No   |  No| Key event to inject.  |

## MouseEventData<sup>11+</sup>

Defines the mouse event data.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| mouseEvent | [MouseEvent](js-apis-mouseevent.md#mouseevent) | No   |  No| Mouse event.  |
| useGlobalCoordinate<sup>20+</sup> | boolean | No   |  Yes| Whether to use global coordinates to calculate the injected mouse event. The default value is **false**. If this parameter is set to **false**, the coordinates of the relative coordinate system with the upper left corner of the specified screen as the origin are used to calculate the injected mouse event. If this parameter is set to **true**, the coordinates of the global coordinate system with the upper left corner of the primary screen as the origin are used to calculate the injected mouse event. |

## TouchEventData<sup>11+</sup>

Defines the touch event data.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| touchEvent | [TouchEvent](js-apis-touchevent.md#touchevent) | No   |  No| Touch event.  |
| useGlobalCoordinate<sup>20+</sup> | boolean | No   |  Yes| Whether to use global coordinates to calculate the injected touch event. The default value is **false**. If this parameter is set to **false**, the coordinates of the relative coordinate system with the upper left corner of the specified screen as the origin are used to calculate the injected touch event. If this parameter is set to **true**, the coordinates of the global coordinate system with the upper left corner of the primary screen as the origin are used to calculate the injected touch event.  |

