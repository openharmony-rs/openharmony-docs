# @ohos.multimodalInput.inputMonitor (Input Monitor) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:26:12.015Z pushedAt=2026-06-12T08:22:39.248Z -->

The **inputMonitor** module implements listening for events of input devices, including the touchscreen, mouse, and touchpad.

>**NOTE**
>
>- The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>- In this document, **global** indicates the entire touchscreen or touchpad. For example, listening for global touch events means to listen for touch events triggered when a user touches at any position on the touchpad.
>
>- The APIs provided by this module are system APIs.

## Modules to Import

```js
import { inputMonitor } from '@kit.InputKit';
```

## inputMonitor.on('touch')

on(type: 'touch', receiver: TouchEventReceiver): void

Listens for global touchscreen input events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                                      | Mandatory  | Description                 |
| -------- | ---------------------------------------- | ---- | ------------------- |
| type     | string                                   | Yes   | Event type. This field has a fixed value of **touch**.|
| receiver | [TouchEventReceiver](#toucheventreceiver) | Mandatory    | Callback used to return touchscreen input events. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Permission denied, non-system app called system api.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Touch Events
            inputMonitor.on('touch', (touchEvent: TouchEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor the touch screen event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('mouse')<sup>9+</sup>

on(type: 'mouse', receiver: Callback&lt;MouseEvent&gt;): void

Enables listening for global mouse events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **mouse**.|
| receiver | Callback&lt;[MouseEvent](js-apis-mouseevent.md#mouseevent)&gt; | Mandatory    | Callback used to return the mouse input event.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Permission denied, non-system app called system api.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Mouse Events
            inputMonitor.on('mouse', (mouseEvent: MouseEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('mouse')<sup>11+</sup>

on(type: 'mouse', rect: display.Rect[], receiver: Callback&lt;MouseEvent&gt;): void

Enables listening for mouse events. When the mouse pointer moves to the specified rectangular area, a callback is triggered. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **mouse**.|
| rect     | [display.Rect](../apis-arkui/js-apis-display.md#rect9)[]             | Yes   | Rectangular area where a callback is triggered. One or two rectangular areas can be specified.|
| receiver | Callback&lt;[MouseEvent](js-apis-mouseevent.md#mouseevent)&gt; | Mandatory    | Callback used to return the mouse input event.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';
import { display } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          /**
           * Callback triggered when the mouse pointer moves to the specified rectangular area.
           */
          let callback = (mouseEvent : MouseEvent) => {
            this.getUIContext().getPromptAction().showToast({
              message: `Monitor on success: ${JSON.stringify(mouseEvent)}`
            })
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            return false;
          };

          /**
           * Rectangular area where a callback is triggered.
           */
          let rect: display.Rect[] = [{
            left: 100,
            top: 100,
            width: 100,
            height: 100
          }, {
            left: 600,
            top: 100,
            width: 100,
            height: 100
          }];

          try {
            // Subscribe to Mouse Events
            inputMonitor.on('mouse', rect, callback);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('touch')

off(type: 'touch', receiver?: TouchEventReceiver): void

Cancels listening for global touchscreen input events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                                      | Mandatory  | Description                 |
| -------- | ---------------------------------------- | ---- | ------------------- |
| type     | string                                   | Yes   | Event type. This field has a fixed value of **touch**.|
| receiver | [TouchEventReceiver](#toucheventreceiver) | No   | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Permission denied, non-system app called system api.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (touchEvent: TouchEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Touch Events
            inputMonitor.on('touch', callback);
            // Unsubscribe from Touch Events
            inputMonitor.off('touch', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the touch screen event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (touchEvent: TouchEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(touchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Touch Events
            inputMonitor.on('touch', callback);
            // Unsubscribe from Touch Events
            inputMonitor.off('touch');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the touch screen event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('mouse')<sup>9+</sup>

off(type: 'mouse', receiver?: Callback&lt;MouseEvent&gt;): void

Disables listening for global mouse events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **mouse**.|
| receiver | Callback&lt;[MouseEvent](js-apis-mouseevent.md#mouseevent)&gt; | No   | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Permission denied, non-system app called system api.   |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (mouseEvent: MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Mouse Events
            inputMonitor.on('mouse', callback);
            // Unsubscribe from Mouse Events
            inputMonitor.off('mouse', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (mouseEvent: MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Mouse Events
            inputMonitor.on('mouse', callback);
            // Unsubscribe from Mouse Events
            inputMonitor.off('mouse');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## TouchEventReceiver

type TouchEventReceiver = (touchEvent: TouchEvent) => boolean

Callback used to return the touch event.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name        | Type                                      | Mandatory  | Description                                      |
| ---------- | ---------------------------------------- | ---- | ---------------------------------------- |
| touchEvent | [TouchEvent](js-apis-touchevent.md#touchevent) | Yes   | Touch event.|

**Return value**

| Type     | Description                                      |
| ------- | ---------------------------------------- |
| boolean | If **true** is returned, subsequent events generated by this touchscreen interaction will no longer be dispatched to the window. If **false** is returned, subsequent events generated by this touchscreen interaction will still be dispatched to the window. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Touch Events
            inputMonitor.on('touch', touchEvent => {
              if (touchEvent.touches.length === 3) { // Three fingers are pressed.
                return true;
              }
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor the touch screen event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('pinch')<sup>10+</sup>

on(type: 'pinch', receiver: Callback&lt;Pinch&gt;): void

Enables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **pinch**.|
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | Mandatory    | Callback used to return pinch input event.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Pinch Event
            inputMonitor.on('pinch', (pinchEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor the pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('pinch')<sup>10+</sup>

off(type: 'pinch', receiver?: Callback&lt;Pinch&gt;): void

Disables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **pinch**.|
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | No   | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Pinch Event
            inputMonitor.on('pinch', callback);
            // Unsubscribe from Pinch Event
            inputMonitor.off('pinch', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Pinch Event
            inputMonitor.on('pinch', callback);
            // Unsubscribe from Pinch Event
            inputMonitor.off('pinch');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('threeFingersSwipe')<sup>10+</sup>

on(type: 'threeFingersSwipe', receiver: Callback&lt;ThreeFingersSwipe&gt;): void

Enables listening for three-finger swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **threeFingersSwipe**.|
| receiver | Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt; | Mandatory    | Callback used to return the three-finger swipe input event.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Three-Finger Swipe Events
            inputMonitor.on('threeFingersSwipe', (threeFingersSwipe) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor three fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('threeFingersSwipe')<sup>10+</sup>

off(type: 'threeFingersSwipe', receiver?: Callback&lt;ThreeFingersSwipe&gt;): void

Disables listening for three-finger swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **threeFingersSwipe**.|
| receiver | Callback&lt;[ThreeFingersSwipe](js-apis-multimodalinput-gestureevent.md#threefingersswipe)&gt; | No   | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Three-Finger Swipe Event
            inputMonitor.on('threeFingersSwipe', callback);
            // Unsubscribe from Three-Finger Swipe Event
            inputMonitor.off("threeFingersSwipe", callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (threeFingersSwipe: ThreeFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Three-Finger Swipe Events
            inputMonitor.on("threeFingersSwipe", callback);
            // Unsubscribe from Three-Finger Swipe Events
            inputMonitor.off("threeFingersSwipe");
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('fourFingersSwipe')<sup>10+</sup>

on(type: 'fourFingersSwipe', receiver: Callback&lt;FourFingersSwipe&gt;): void

Enables listening for four-finger swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **fourFingersSwipe**.|
| receiver | Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt; | Mandatory    | Callback used to return the four-finger swipe input event.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Four-Finger Swipe Events
            inputMonitor.on('fourFingersSwipe', (fourFingersSwipe) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor four fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('fourFingersSwipe')<sup>10+</sup>

off(type: 'fourFingersSwipe', receiver?: Callback&lt;FourFingersSwipe&gt;): void

Disables listening for four-finger swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **fourFingersSwipe**.|
| receiver | Callback&lt;[FourFingersSwipe](js-apis-multimodalinput-gestureevent.md#fourfingersswipe)&gt; | No   | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Four-Finger Swipe Event
            inputMonitor.on('fourFingersSwipe', callback);
            // Unsubscribe from Four-Finger Swipe Event
            inputMonitor.off('fourFingersSwipe', callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitoring four fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { FourFingersSwipe } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (fourFingersSwipe: FourFingersSwipe) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fourFingersSwipe)}.`);
            return false;
          };
          try {
            // Subscribe to Four-Finger Swipe Event
            inputMonitor.on('fourFingersSwipe', callback);
            // Unsubscribe from Four-Finger Swipe Event
            inputMonitor.off('fourFingersSwipe');
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitoring four fingers swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('rotate')<sup>11+</sup>

on(type: 'rotate', fingers: number, receiver: Callback&lt;Rotate&gt;): void

Enables listening for rotation events of the touchpad. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **rotate**.|
| fingers     | number                     | Yes   | Number of fingers that trigger a rotation. The value must not be greater than **2**.|
| receiver | Callback&lt;[Rotate](js-apis-multimodalinput-gestureevent.md#rotate11)&gt; | Mandatory    | Callback used to return the rotation input event.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Number of Fingers for Rotation Gesture Monitoring: 2
            inputMonitor.on('rotate', 2, (rotateEvent: Rotate) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor rotate event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('rotate')<sup>11+</sup>

off(type: 'rotate', fingers: number, receiver?: Callback&lt;Rotate&gt;): void

Disables listening for rotation events of the touchpad. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **rotate**.|
| fingers     | number                     | Yes   | Number of fingers that trigger a rotation. The value must not be greater than **2**.|
| receiver | Callback&lt;[Rotate](js-apis-multimodalinput-gestureevent.md#rotate11)&gt; | No   | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (rotateEvent: Rotate) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
            return false;
          };
          try {
            // Rotation gesture listening finger count 2
            inputMonitor.on('rotate', 2, callback);
            // Unsubscribe from rotation events
            inputMonitor.off('rotate', 2, callback);
            console.info(`Succeeded in turning off monitor.`); 
          } catch (error) {
            console.error(`Failed to cancel monitor rotate event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (rotateEvent: Rotate) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
            return false;
          };
          try {
            // Number of fingers for rotation gesture monitoring: 2
            inputMonitor.on('rotate', 2, callback);
            // Unsubscribe from rotation events
            inputMonitor.off('rotate', 2);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor rotate event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('pinch')<sup>11+</sup>

on(type: 'pinch', fingers: number, receiver: Callback&lt;Pinch&gt;): void

Enables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **pinch**.|
| fingers     | number                     | Yes   | Number of fingers that trigger the pinch. The value must be greater than or equal to **2**.|
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | Mandatory    | Callback used to return the pinch input event.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Number of fingers for pinch gesture monitoring: 2
            inputMonitor.on('pinch', 2, (pinchEvent: Pinch) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('pinch')<sup>11+</sup>

off(type: 'pinch', fingers: number, receiver?: Callback&lt;Pinch&gt;): void

Disables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name      | Type                        | Mandatory  | Description                 |
| -------- | -------------------------- | ---- | ------------------- |
| type     | string                     | Yes   | Event type. This field has a fixed value of **pinch**.|
| fingers     | number                     | Yes   | Number of fingers that trigger the pinch. The value must be greater than or equal to **2**.|
| receiver | Callback&lt;[Pinch](js-apis-multimodalinput-gestureevent.md#pinch)&gt; | No   | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Pinch Event
            inputMonitor.on('pinch', 2, callback);
            // Unsubscribe from Pinch Event
            inputMonitor.off('pinch', 2, callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { Pinch } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (pinchEvent: Pinch) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(pinchEvent)}.`);
            return false;
          };
          try {
            // Number of fingers for pinch gesture monitoring: 2
            inputMonitor.on('pinch', 2, callback);
            // Unsubscribe from pinch events
            inputMonitor.off('pinch', 2);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor pinch event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('threeFingersTap')<sup>11+</sup>

on(type: 'threeFingersTap', receiver: Callback&lt;ThreeFingersTap&gt;): void

Enables listening for three-finger tap events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                     |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------- |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **threeFingersTap**.|
| receiver | Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt; | Mandatory   | Callback used to return the three-finger tap input event.      |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Three-Finger Tap Event
            inputMonitor.on('threeFingersTap', (threeFingersTap) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor three fingers tap, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('threeFingersTap')<sup>11+</sup>

off(type: 'threeFingersTap', receiver?: Callback&lt;ThreeFingersTap&gt;): void

Disables listening for three-finger tap events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **threeFingersTap**.                   |
| receiver | Callback&lt;[ThreeFingersTap](js-apis-multimodalinput-gestureevent.md#threefingerstap11)&gt; | No  | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
            return false;
          };
          try {
            // Subscribe to three-finger tap event
            inputMonitor.on('threeFingersTap', callback);
            // Unsubscribe from three-finger tap event
            inputMonitor.off("threeFingersTap", callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers tap, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { ThreeFingersTap } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (threeFingersTap: ThreeFingersTap) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
            return false;
          };
          try {
            // Subscribe to three-finger tap event
            inputMonitor.on('threeFingersTap', callback);
            // Unsubscribe from three-finger tap event
            inputMonitor.off("threeFingersTap");
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor three fingers tap, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('touchscreenSwipe')<sup>18+</sup>

on(type: 'touchscreenSwipe', fingers: number, receiver: Callback&lt;TouchGestureEvent&gt;): void

Enables listening for touchscreen swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **touchscreenSwipe**.                   |
| fingers  | number                                                       | Yes  | Number of fingers that trigger the swipe. The value range is [3, 5].|
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent18)&gt; | Mandatory | Callback used to return the touchscreen swipe event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Caller is not a system application.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Swipe Events
            inputMonitor.on('touchscreenSwipe', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor touch screen swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('touchscreenSwipe')<sup>18+</sup>

off(type: 'touchscreenSwipe', fingers: number, receiver?: Callback&lt;TouchGestureEvent&gt;): void

Disables listening for touchscreen swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **touchscreenSwipe**.                   |
| fingers  | number                                                       | Yes  | Number of fingers that trigger the swipe. The value range is [3, 5].|
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent18)&gt; | No  | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Caller is not a system application.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (event: TouchGestureEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
          };
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Swipe Events
            inputMonitor.on('touchscreenSwipe', fingers, callback);
            // Unsubscribe from Touchscreen Swipe Events
            inputMonitor.off('touchscreenSwipe', fingers, callback);
          } catch (error) {
            console.error(`Failed to cancel monitor touch screen swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Swipe Events
            inputMonitor.on('touchscreenSwipe', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // Unsubscribe from Touchscreen Swipe Events
            inputMonitor.off('touchscreenSwipe', fingers);
          } catch (error) {
            console.error(`Failed to monitor touch screen swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('touchscreenPinch')<sup>18+</sup>

on(type: 'touchscreenPinch', fingers: number, receiver: Callback&lt;TouchGestureEvent&gt;): void

Enables listening for touchscreen pinch events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **touchscreenPinch**.                   |
| fingers  | number                                                       | Yes  | Number of fingers that trigger the pinch. The value range is [4, 5].|
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent18)&gt; | Mandatory | Callback used to return the touchscreen pinch event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Caller is not a system application.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Pinch Event
            inputMonitor.on('touchscreenPinch', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor touch screen pinch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('touchscreenPinch')<sup>18+</sup>

off(type: 'touchscreenPinch', fingers: number, receiver?: Callback&lt;TouchGestureEvent&gt;): void

Disables listening for touchscreen pinch events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **touchscreenPinch**.                   |
| fingers  | number                                                       | Yes  | Number of fingers that trigger the pinch. The value range is [4, 5].|
| receiver | Callback&lt;[TouchGestureEvent](js-apis-multimodalinput-gestureevent-sys.md#touchgestureevent18)&gt; | No  | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | Caller is not a system application.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (event: TouchGestureEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
          };
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Pinch Event
            inputMonitor.on('touchscreenPinch', fingers, callback);
            // Unsubscribe from Touchscreen Pinch Event
            inputMonitor.off("touchscreenPinch", fingers, callback);
          } catch (error) {
            console.error(`Failed to cancel monitor touch screen pinch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let fingers: number = 4;
          try {
            // Subscribe to Touchscreen Pinch Event
            inputMonitor.on('touchscreenPinch', fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // Unsubscribe from Touchscreen Pinch Event
            inputMonitor.off("touchscreenPinch", fingers);
          } catch (error) {
            console.error(`Failed to cancel monitor touch screen pinch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.on('keyPressed')<sup>15+</sup>

on(type: 'keyPressed', keys: Array&lt;KeyCode&gt;, receiver: Callback&lt;KeyEvent&gt;): void

Listens for the press and release events of the specified key, which can be the **META_LEFT**, **META_RIGHT**, power, or volume key. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------ |
| type     | string                                                      | Yes  | Event type. This parameter has a fixed value of **keyPressed**.|
| keys     | Array<[KeyCode](js-apis-keycode.md#keycode)> | Yes  | Key value. The following key values are supported: KEYCODE_META_LEFT, KEYCODE_META_RIGHT, KEYCODE_POWER, KEYCODE_VOLUME_DOWN, and KEYCODE_VOLUME_UP.                     |
| receiver | Callback&lt;[KeyEvent](js-apis-keyevent.md#keyevent)&gt;    | Mandatory   | Callback used to return the key input event.         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Input Monitor Error Codes](./errorcode-inputmonitor.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 4100001  | Event listening not supported for the key.                   |

**Example**

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // Subscribe to Key Press Events
            inputMonitor.on('keyPressed', keys, (event: KeyEvent ) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('keyPressed')<sup>15+</sup>

off(type: 'keyPressed', receiver?: Callback&lt;KeyEvent&gt;): void

Cancels listening for the press and release events of the specified key, which can be the **META_LEFT**, **META_RIGHT**, power, or volume key. This API must be used together with **inputMonitor.on ('keyPressed')**. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                     | Mandatory| Description                                                        |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                    | Yes  | Event type. This parameter has a fixed value of **keyPressed**.                        |
| receiver | Callback&lt;[KeyEvent](js-apis-keyevent.md#keyevent)&gt; | No  | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          try {
            let callback = (event: KeyEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            };
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // Subscribe to Key Press Event
            inputMonitor.on('keyPressed', keys, callback);
            // Unsubscribe from Key Press Event
            inputMonitor.off("keyPressed", callback);
          } catch (error) {
            console.error(`Failed to cancel monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            // Subscribe to Key Press Events
            inputMonitor.on('keyPressed', keys, (event: KeyEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // Unsubscribe from Key Press Events
            inputMonitor.off("keyPressed");
          } catch (error) {
            console.error(`Failed to cancel monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.queryTouchEvents()<sup>20+</sup>

queryTouchEvents(count: number): Promise&lt;Array&lt;TouchEvent&gt;&gt;

Queries recent touchscreen input events. A maximum of 100 events can be queried. Since API version 26.0.0, a maximum of 60 events can be queried. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                     | Mandatory| Description                                                        |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| count     | number                                                    | Mandatory   | Number of touchscreen input events to query. The value range is an integer from 0 to 100. If the value is less than 0, the value **0** is used. If the value is greater than 100, the value **100** is used. Since API version 26.0.0, if the value is greater than 60, the value **60** is used. If there are only 30 actual touchscreen input events but this parameter is set to **50**, only 30 touchscreen input events can be queried. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;Array&lt;[TouchEvent](js-apis-touchevent-sys.md#touchevent)&gt;&gt; | Promise used to return the queried touchscreen input events. It contains the following valid information; all other information is invalid:<br/>- **actionTime**: Time when the touchscreen input event occurred, in microseconds (μs) since system startup.<br/>- [SourceType](js-apis-touchevent.md#sourcetype): Device type of the touch source.<br/>- [isInject](js-apis-touchevent-sys.md#touchevent): Whether the touchscreen input event is an injected event.<br/>- **pressure**: Pressure value, with a value range of [0.0, 1.0], where **0.0** indicates not supported.<br/>- **tiltX**: Angle relative to the YZ plane, with a value range of [-90, 90], where a positive value indicates tilting to the right.<br/>- **tiltY**: Angle relative to the XZ plane, with a value range of [-90, 90], where a positive value indicates tilting downward.<br/>Since API version 23, the following additional valid information can be obtained:<br/>- [Action](js-apis-touchevent.md#action): Touchscreen input event type.<br/>- **screenX**: X-axis coordinate relative to the upper left corner of the screen, in pixels, with a value range of [0, screen width], increasing to the right. It is available only for specified applications.<br/>- **screenY**: Y-axis coordinate relative to the upper left corner of the screen, in pixels, with a value range of [0, screen height], increasing downward. It is available only for specified applications.<br/>Since API version 26.0.0, a maximum of 60 events can be queried, and events of the MOVE and PULL_MOVE types will not be returned. **screenX** and **screenY** are no longer restricted to specified applications and can be obtained by all system applications. Additionally, the following valid information can be obtained:<br/>- **screenId**: Target screen ID. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Permission denied, non-system app called system api.         |

**Example**

```js
import { inputMonitor, TouchEvent } from '@kit.InputKit'
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Querying the Number of Touchscreen Events
  inputMonitor.queryTouchEvents(10).then((events: Array<TouchEvent>) => {
    events.forEach((event, index) => {
      console.info(`Succeeded in querying touch event ${index}, actionTime=${event.actionTime}, sourceType=${event.sourceType}.`);
    });
  }).catch((error: BusinessError) => {
    console.error(`Failed to query touch events promise, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
  });
} catch (error) {
  const code = (error as BusinessError).code;
  const message = (error as BusinessError).message;
  console.error(`Failed to query touch events, Code: ${code}, message: ${message}.`);
}
```

## inputMonitor.on('swipeInward')<sup>12+</sup>

on(type: 'swipeInward', receiver: Callback&lt;SwipeInward&gt;): void

Listens for inward swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------ |
| type     | string                                                      | Yes  | Input event type. The value is fixed at **SwipeInward**.|
| receiver | Callback&lt;[SwipeInward](js-apis-multimodalinput-gestureevent-sys.md#swipeinward)&gt;    | Mandatory   | Callback used to return the inward swipe event.         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | SystemAPI permit error.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Swipe Inward Event
            inputMonitor.on('swipeInward', (SwipeInward) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(SwipeInward)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor swipe inward, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('swipeInward')<sup>12+</sup>

off(type: 'swipeInward', receiver?: Callback&lt;SwipeInward&gt;): void

Cancels listening for inward swipe events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Input event type. The value is fixed at **SwipeInward**.                   |
| receiver | Callback&lt;[SwipeInward](js-apis-multimodalinput-gestureevent-sys.md#swipeinward)&gt; | No  | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor, SwipeInward } from '@kit.InputKit';

@Entry
@Component
struct Index {
build() {
  RelativeContainer() {
    Text()
      .onClick(() => {
        // Disable listening for a single callback.
        let callback = (swipeInward: SwipeInward) => {
          console.info(`Succeeded in monitoring on ${JSON.stringify(swipeInward)}.`);
          return false;
        };
        try {
          // Subscribe to Swipe Inward Event
          inputMonitor.on('swipeInward', callback);
          // Unsubscribe from Swipe Inward Event
          inputMonitor.off("swipeInward", callback);
          console.info(`Succeeded in turning off monitor.`);
        } catch (error) {
          console.error(`Failed to cancel monitor swipe inward, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
        }
      })
  }
}
}
```

```js
import { inputMonitor, SwipeInward } from '@kit.InputKit';

@Entry
@Component
struct Index {
build() {
  RelativeContainer() {
    Text()
      .onClick(() => {
        // Cancel listening for all callbacks.
        let callback = (swipeInward: SwipeInward) => {
          console.info(`Succeeded in monitoring on ${JSON.stringify(swipeInward)}.`);
          return false;
        };
        try {
          // Subscribe to Swipe Inward Event
          inputMonitor.on('swipeInward', callback);
          // Unsubscribe from Swipe Inward Event
          inputMonitor.off("swipeInward");
          console.info(`Succeeded in turning off monitor.`);
        } catch (error) {
          console.error(`Failed to cancel monitor swipe inward, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
        }
      })
  }
}
}
```

## inputMonitor.on('fingerprint')<sup>12+</sup>

on(type: 'fingerprint', receiver: Callback&lt;FingerprintEvent&gt;): void

Enables listening for fingerprint gesture input events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------ |
| type     | string                                                      | Yes  | Input event type. The value is unique and is **fingerprint**.|
| receiver | Callback&lt;[FingerprintEvent](js-apis-shortKey-sys.md#fingerprintevent12)&gt;    | Mandatory   | Callback used to return the fingerprint device gesture input event.         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | SystemAPI permit error.         |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Subscribe to Fingerprint Events
            inputMonitor.on('fingerprint', (FingerprintEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(FingerprintEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor finger print event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputMonitor.off('fingerprint')<sup>12+</sup>

off(type: 'fingerprint', receiver?: Callback&lt;FingerprintEvent&gt;): void

Disables listening for fingerprint gesture input events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INPUT_MONITORING

**System capability**: SystemCapability.MultimodalInput.Input.InputMonitor

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Input event type. The value is **fingerprint**.                   |
| receiver | Callback&lt;[FingerprintEvent](js-apis-shortKey-sys.md#fingerprintevent12)&gt; | No  | Callback for which listening is disabled. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied.   |
| 202  | SystemAPI permit error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputMonitor } from '@kit.InputKit';
import { FingerprintEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Disable listening for a single callback.
          let callback = (fingerprintEvent: FingerprintEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fingerprintEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Fingerprint Events
            inputMonitor.on('fingerprint', callback);
            // Unsubscribe from Fingerprint Events
            inputMonitor.off("fingerprint", callback);
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor finger print event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputMonitor } from '@kit.InputKit';
import { FingerprintEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Cancel listening for all callbacks.
          let callback = (fingerprintEvent: FingerprintEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(fingerprintEvent)}.`);
            return false;
          };
          try {
            // Subscribe to Fingerprint Events
            inputMonitor.on('fingerprint', callback);
            // Unsubscribe from Fingerprint Events
            inputMonitor.off("fingerprint");
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to cancel monitor finger print event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```