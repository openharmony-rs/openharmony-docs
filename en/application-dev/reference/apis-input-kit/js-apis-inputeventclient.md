# @ohos.multimodalInput.inputEventClient (Input Event Injection)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

The input event injection module provides the capability to simulate keyboard, mouse, and touch input events.

**Since:** 26.0.0

## Modules to Import

```js
import { inputEventClient } from '@kit.InputKit';
```

## inputEventClient.createKeyboardController

createKeyboardController(): Promise&lt;KeyboardController&gt;

Creates a keyboard controller for simulating key operations. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences**: This API is supported on PCs/2-in-1 devices. On other device types, it returns error code 801.

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;[KeyboardController](#keyboardcontroller)&gt; | Promise used to return the keyboard controller instance.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 801  | Capability not supported.  |
| 3800001  | Input service exception.  |

**Example:**

```js
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createKeyboardController()
            .then(keyboardController => {
              console.info('Succeeded in creating keyboard controller');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to create keyboard controller. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

## inputEventClient.createMouseController

createMouseController(): Promise&lt;MouseController&gt;

Creates a mouse controller for simulating mouse operations. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences**: This API is supported on PCs/2-in-1 devices. On other device types, it returns error code 801.

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;[MouseController](#mousecontroller)&gt; | Promise used to return the mouse controller instance.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 801  | Capability not supported.  |
| 3800001  | Input service exception.  |

**Example:**

```js
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createMouseController()
            .then(mouseController => {
              console.info('Succeeded in creating mouse controller');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to create mouse controller. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

## inputEventClient.createTouchController

createTouchController(): Promise&lt;TouchController&gt;

Creates a touch controller for simulating touch operations. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences**: This API is supported on PCs/2-in-1 devices. On other device types, it returns error code 801.

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;[TouchController](#touchcontroller)&gt; | Promise used to return the touch controller instance.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 801  | Capability not supported.  |
| 3800001  | Input service exception.  |

**Example:**

```js
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createTouchController()
            .then(touchController => {
              console.info('Succeeded in creating touch controller');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to create touch controller. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

## KeyboardController

Provides the capability of simulating key operations. The simulated key operation sequence must meet the following requirements:

1. A key can only be pressed when it is in the released state, or when it is the most recently pressed key and has not been released.
2. A key can only be released after it has been pressed.
3. A maximum of five keys can be pressed and held simultaneously.

### pressKey

pressKey(keyCode: KeyCode): Promise&lt;void&gt;

Presses a key. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| keyCode | [KeyCode](js-apis-keycode.md#keycode) | Yes  | Key code of the key to be pressed.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300001  | The key is already pressed and is not the most recently pressed key.  |

**Example:**

```js
import { inputEventClient, KeyCode } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createKeyboardController()
            .then((keyboardController: inputEventClient.KeyboardController) => {
              keyboardController.pressKey(KeyCode.KEYCODE_A);
              return keyboardController;
            })
            .then((keyboardController: inputEventClient.KeyboardController) => {
              keyboardController.releaseKey(KeyCode.KEYCODE_A);
            })
            .then(() => {
              console.info('Succeeded in releasing key');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to release key. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

### releaseKey

releaseKey(keyCode: KeyCode): Promise&lt;void&gt;

Releases a key. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| keyCode | [KeyCode](js-apis-keycode.md#keycode) | Yes  | Key code of the key to be released.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300001  | The key is not pressed.  |

**Example:**

For details, see [pressKey](#presskey).

## MouseController

Provides the capability of simulating mouse operations. The simulated mouse operation sequence must meet the following requirements:

1. A mouse button can be pressed only when it is in the released state.
2. A mouse button can only be released after it has been pressed.
3. A valid axis event sequence must begin with a **beginAxis** call, followed by zero or more **updateAxis** calls, and end with an **endAxis** call.
4. Only one axis event sequence can be in progress at a time.

### moveTo

moveTo(displayId: number, displayX: number, displayY: number): Promise&lt;void&gt;

Moves the mouse cursor to the specified display coordinates. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| displayId | number | Yes  | ID of the target display.|
| displayX | number | Yes  | X coordinate relative to the left edge of the display, in px. If the value exceeds the valid range of the display, the actual coordinate will be clamped to the valid range [0, display width - 1].|
| displayY | number | Yes  | Y coordinate relative to the top edge of the display, in px. If the value exceeds the valid range of the display, the actual coordinate will be clamped to the valid range [0, display height - 1].|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300002  | The display does not exist.  |

**Example:**

```js
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createMouseController()
            .then(mouseController => {
              return mouseController.moveTo(0, 100, 200);
            })
            .then(() => {
              console.info('Succeeded in moving mouse');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to move mouse. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

### pressButton

pressButton(button: Button): Promise&lt;void&gt;

Presses a mouse button. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| button | [Button](js-apis-mouseevent.md#button) | Yes  | Mouse button to be pressed.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300001  | The mouse button is already pressed.  |

**Example:**

```js
import { inputEventClient, Button } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createMouseController()
            .then((mouseController: inputEventClient.MouseController) => {
              mouseController.pressButton(Button.LEFT);
              return mouseController;
            })
            .then((mouseController: inputEventClient.MouseController) => {
              mouseController.releaseButton(Button.LEFT);
            })
            .then(() => {
              console.info('Succeeded in releasing mouse button');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to release mouse button. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

### releaseButton

releaseButton(button: Button): Promise&lt;void&gt;

Release a mouse button. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| button | [Button](js-apis-mouseevent.md#button) | Yes  | Mouse button to be released.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300001  | The mouse button is not pressed.  |

**Example:**

For details, see [pressButton](#pressbutton).

### beginAxis

beginAxis(axis: Axis, value: number): Promise&lt;void&gt;

Starts an axis event. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | Yes  | Axis type.|
| value | number | Yes  | Axis value.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300001  | The axis event is in progress.  |

**Example:**

```js
import { inputEventClient, Axis } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createMouseController()
            .then((mouseController: inputEventClient.MouseController) => {
              mouseController.beginAxis(Axis.SCROLL_VERTICAL, 10);
              return mouseController;
            })
            .then((mouseController: inputEventClient.MouseController) => {
              mouseController.updateAxis(Axis.SCROLL_VERTICAL, 20);
              return mouseController;
            })
            .then((mouseController: inputEventClient.MouseController) => {
              mouseController.endAxis(Axis.SCROLL_VERTICAL);
            })
            .then(() => {
              console.info('Succeeded in ending axis event');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to end axis event. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

### updateAxis

updateAxis(axis: Axis, value: number): Promise&lt;void&gt;

Updates an axis event. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | Yes  | Axis type.|
| value | number | Yes  | Axis value.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300001  | The axis event is not in progress.  |

**Example:**

For details, see [beginAxis](#beginaxis).

### endAxis

endAxis(axis: Axis): Promise&lt;void&gt;

Ends an axis event. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name     | Type                  | Mandatory | Description      |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | Yes  | Axis type.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 3800001  | Input service exception.  |
| 4300001  | The axis event is not in progress.  |

**Example:**

For details, see [beginAxis](#beginaxis).

## TouchPoint

Represents information about a single touch point on the display.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| id | number | No| No| Unique ID of a touch point. The value must be an integer in the range of [0, 9].|
| displayId | number | No| No| Unique ID of the display where the touch point is located. The value must be an integer.|
| displayX | number | No| No| X coordinate of the touch point relative to the left edge of the display, in pixels. The value must be an integer.|
| displayY | number | No| No| Y coordinate of the touch point relative to the top edge of the display, in pixels. The value must be an integer.|

## TouchController

Provides the capability of simulating touch operations. The simulated touch operation sequence must meet the following requirements:

1. All touch points must share the same **displayId**.
2. Each touch point must begin with a **touchDown()** call, followed by zero or more **touchMove()** calls, and end with an **touchUp()** call.

### touchDown

touchDown(touch: TouchPoint): Promise&lt;void&gt;

Presses down a touch point. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| touch | [TouchPoint](#touchpoint) | Yes| Information about the touch point that is in contact with the display.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 4300001 | Invalid input event sequence. Possible causes: 1. The touch point is touching the display; 2. The touch point ID is not within the valid range [0,9]. |
| 4300002 | The display does not exist. |
| 3800001 | Input service exception. |

**Example:**

```js
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createTouchController()
            .then((touchController: inputEventClient.TouchController) => {
              const touchPoint: inputEventClient.TouchPoint = {
                id: 0,
                displayId: 0,
                displayX: 600,
                displayY: 1200
              };
              touchController.touchDown(touchPoint);
              return touchController;
            })
            .then((touchController: inputEventClient.TouchController) => {
              touchController.touchMove({
                id: 0,
                displayId: 0,
                displayX: 720,
                displayY: 1200
              });
              return touchController;
            })
            .then((touchController: inputEventClient.TouchController) => {
              touchController.touchUp({
                id: 0,
                displayId: 0,
                displayX: 720,
                displayY: 1200
              });
            })
            .then(() => {
              console.info('Succeeded in touch up');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to simulate touch. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}
```

### touchMove

touchMove(touch: TouchPoint): Promise&lt;void&gt;

Moves a touch point. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| touch | [TouchPoint](#touchpoint) | Yes| Information about the touch point to be moved.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 4300001 | Invalid input event sequence. Possible causes: 1. The touch point is not touching the display; 2. The touch point ID is not within the valid range [0,9]. |
| 3800001 | Input service exception. |

**Example:**

For details, see [touchDown](#touchdown).

### touchUp

touchUp(touch: TouchPoint): Promise&lt;void&gt;

Releases a touch point. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MultimodalInput.Input.InputSimulator

**Required permissions**: ohos.permission.CONTROL_DEVICE

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other device types, it does not take effect.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| touch | [TouchPoint](#touchpoint) | Yes| Information about the touch point to be released.|

**Returns**

| Type                  | Description      |
| --------------------- | --------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Event Injection Error Codes](errorcode-inputeventclient.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 4300001 | Invalid input event sequence. Possible causes: 1. The touch point is not touching the display; 2. The touch point ID is not within the valid range [0,9]. |
| 3800001 | Input service exception. |

**Example:**

For details, see [touchDown](#touchdown).
