# @ohos.multimodalInput.inputConsumer (Global Shortcut Keys)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

The **inputConsumer** module implements listening for combination key events as well as listening and interception for volume key events.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Global shortcut keys are combination keys defined by the system or application. System shortcut keys are defined by the system, and application shortcut keys are defined by applications.


## Modules to Import


```js
import { inputConsumer, KeyEvent } from '@kit.InputKit';
```

## HotkeyOptions

Defines shortcut key options.

**System capability**: SystemCapability.MultimodalInput.Input.InputConsumer

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ------- | ------- | ------- |
| preKeys   | Array&lt;number&gt; | No     | No     | Modifier key set (including Ctrl, Shift, and Alt). One to four modifier keys are supported. There is no requirement on the sequence of modifier keys.<br>For example, in **Ctrl+Shift+Esc**, **Ctrl** and **Shift** are modifier keys.|
| finalKey  | number  | No     | No     | Modified key, which can be any key except the modifier keys and Meta key. For details about the keys, see [@ohos.multimodalInput.keyCode (Keycode)](js-apis-keycode.md).<br>For example, in **Ctrl+Shift+Esc**, **Esc** is the modifier key.|
| isRepeat  | boolean  | No     | Yes     | Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite. The default value is **true**.|

## KeyPressedConfig<sup>16+</sup>

Sets the key event consumption configuration.

**System capability**: SystemCapability.MultimodalInput.Input.InputConsumer

**Device behavior differences**: In versions earlier than API version 23, this API can be properly called on phones and tablets. If it is called on other device types, error code 801 is returned. Since API version 23, this API can be properly called on phones, tablets, PCs/2-in-1 devices, and TVs. On other device types, error code 801 is returned.

<!--Table: 10%; 10%; 10%; 10%; 60%-->
| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ------- | ------- | ------- |
| key       | number  | No     | No     | Key value.<br>**Note:** Since API version 26.0.0, the [KEYCODE_FINGERPRINT_SLIDE_UP](js-apis-keycode.md#keycode) and [KEYCODE_FINGERPRINT_SLIDE_DOWN](js-apis-keycode.md#keycode) keys are supported. The keys are not universal device keys. Before using them, check whether the current device supports the reporting of related key events. For details, see [Preferential Response of System Function Keys](../../device/input/keypressed-guidelines.md).<br>Since API version 21, the [KEYCODE_MEDIA_PLAY_PAUSE](js-apis-keycode.md#keycode), [KEYCODE_MEDIA_NEXT](js-apis-keycode.md#keycode), and [KEYCODE_MEDIA_PREVIOUS](js-apis-keycode.md#keycode) keys are supported.<br>In API version 20 or earlier versions, only the [KEYCODE_VOLUME_UP](js-apis-keycode.md#keycode) and [KEYCODE_VOLUME_DOWN](js-apis-keycode.md#keycode) keys are supported.|
| action    | number  | No     | No     | Subscription type.<br>**Note**: Since API version 21, the value of this parameter can be **1** or **2**. The value **1** indicates subscription to only key press events, and the value **2** indicates subscription to both key press and release events.<br>In API version 20 or earlier versions, the value of this parameter can only be set to **1**, indicating subscription to only key press events.|
| isRepeat  | boolean  | No     | No     | Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite. The default value is **true**.|

## inputConsumer.getAllSystemHotkeys

getAllSystemHotkeys(): Promise&lt;Array&lt;HotkeyOptions&gt;&gt;

Obtains all system shortcut keys. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputConsumer

**Device behavior differences**: This API can be properly called on devices other than wearables. If it is called on wearables, error code 801 is returned.

**Return value**

| Type        |  Description                                      |
| ---------- |  ---------------------------------------- |
| Promise&lt;Array&lt;[HotkeyOptions](#hotkeyoptions)&gt;&gt;                    | Promise used to return the list of all system shortcut keys.|

**Error codes**:

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                 |
| -------- | ------------------------- |
| 801      | Capability not supported. |

**Example**

```js
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Obtains all system shortcut keys.
          inputConsumer.getAllSystemHotkeys().then((data: Array<inputConsumer.HotkeyOptions>) => {
            console.info(`Succeeded in getting list of system hotkeys: ${JSON.stringify(data)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get all system hotkeys, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          })
        })
    }
  }
}
```

## inputConsumer.on('hotkeyChange')

on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback&lt;HotkeyOptions&gt;): void

Subscribes to application shortcut key change events. This API obtains combination key input events that meet the specified conditions, and uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputConsumer

**Device behavior differences**: This API can be properly called on devices other than wearables. If it is called on wearables, error code 801 is returned.

**Parameters**

| Name        | Type                        | Mandatory  | Description                                      |
| ---------- | -------------------------- | ---- | ---------- |
| type       | string                     | Yes   | Event type. This parameter has a fixed value of **hotkeyChange**.                  |
| hotkeyOptions | [HotkeyOptions](#hotkeyoptions) | Yes   | Shortcut key options.                |
| callback   | Callback&lt;[HotkeyOptions](#hotkeyoptions)&gt; | Yes   | Callback used to return the combination key input events that meet the conditions.|

**Error codes**:

For details about the error codes, see [Global Shortcut Key Error Codes](errorcode-inputconsumer.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |
| 4200002  | The hotkey has been used by the system. |
| 4200003  | The hotkey has been subscribed to by another. |

**Example**

```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftCtrlKey = 2072;
          let zKey = 2042;
          let hotkeyOptions: inputConsumer.HotkeyOptions = {
            preKeys: [leftCtrlKey],
            finalKey: zKey,
            isRepeat: true
          };
          let hotkeyCallback = (hotkeyOptions: inputConsumer.HotkeyOptions) => {
            console.info(`Succeeded in consuming hotkey, hotkeyOptions: ${JSON.stringify(hotkeyOptions)}.`);
          }
          try {
            // Subscribe to shortcut key change events.
            inputConsumer.on("hotkeyChange", hotkeyOptions, hotkeyCallback);
          } catch (error) {
            console.error(`Failed to Subscribe hot key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputConsumer.off('hotkeyChange')

off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback&lt;HotkeyOptions&gt;): void

Unsubscribes from application shortcut key change events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputConsumer

**Parameters**

| Name        | Type                        | Mandatory  | Description                             |
| ---------- | -------------------------- | ---- | ---------- |
| type       | string                     | Yes   | Event type. This parameter has a fixed value of **hotkeyChange**.       |
| hotkeyOptions | [HotkeyOptions](#hotkeyoptions) | Yes   | Shortcut key options.            |
| callback   | Callback&lt;[HotkeyOptions](#hotkeyoptions)&gt; | No   | Callback to unregister. If this parameter is left unspecified, listening will be disabled for all callbacks registered for the specified shortcut key options.|

**Error codes**:

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |

**Example**

```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftCtrlKey = 2072;
          let zKey = 2042;
          // Disable listening for a single callback.
          let hotkeyCallback = (hotkeyOptions: inputConsumer.HotkeyOptions) => {
            console.info(`Succeeded in consuming hotkey, hotkeyOptions: ${JSON.stringify(hotkeyOptions)}.`);
          }
          let hotkeyOption: inputConsumer.HotkeyOptions = { preKeys: [leftCtrlKey], finalKey: zKey, isRepeat: true };
          try {
            // Subscribe to shortcut key change events.
            inputConsumer.on("hotkeyChange", hotkeyOption, hotkeyCallback);
            // Unsubscribe from shortcut key change events.
            inputConsumer.off("hotkeyChange", hotkeyOption, hotkeyCallback);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftCtrlKey = 2072;
          let zKey = 2042;
          // Disable listening for all callbacks.
          let hotkeyCallback = (hotkeyOptions: inputConsumer.HotkeyOptions) => {
            console.info(`Succeeded in consuming hotkey, hotkeyOptions: ${JSON.stringify(hotkeyOptions)}.`);
          }
          let hotkeyOption: inputConsumer.HotkeyOptions = { preKeys: [leftCtrlKey], finalKey: zKey, isRepeat: true };
          try {
            // Subscribe to shortcut key change events.
            inputConsumer.on("hotkeyChange", hotkeyOption, hotkeyCallback);
            // Unsubscribe from shortcut key change events.
            inputConsumer.off("hotkeyChange", hotkeyOption);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputConsumer.on('keyPressed')<sup>16+</sup>

on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback&lt;KeyEvent&gt;): void

Subscribes to key press events. If the current application is in the foreground focus window, a callback is triggered when the specified key is pressed. This API uses an asynchronous callback to return the result.

If the API call is successful, the system's default response to the key event will be intercepted; that is, system-level actions, such as volume adjustment, will no longer be triggered. To restore the system response, call [off](#inputconsumeroffkeypressed16) to disable listening for the key event.

**System capability**: SystemCapability.MultimodalInput.Input.InputConsumer

**Device behavior differences**: In versions earlier than API version 23, this API can be properly called on phones and tablets. If it is called on other device types, error code 801 is returned. Since API version 23, this API can be properly called on phones, tablets, PCs/2-in-1 devices, and TVs. On other device types, error code 801 is returned.

**Parameters**

| Name        | Type                               | Mandatory | Description                             |
| ---------- | --------------------------             | ----  | ---------- |
| type       | string                                 | Yes    | Event type. This parameter has a fixed value of **keyPressed**.       |
| options    | [KeyPressedConfig](#keypressedconfig16)| Yes    | Sets the key event consumption configuration.          |
| callback   | Callback&lt;[KeyEvent](./js-apis-keyevent.md#keyevent)&gt; | Yes   | Callback used to return key press events. Ensure that different callbacks are used for different key events. Otherwise, the subscription does not take effect.|

**Error codes**:

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |

**Example**

```js
import { inputConsumer, KeyEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let options: inputConsumer.KeyPressedConfig = {
              key: 16,
              action: 1,
              isRepeat: false,
            }
            // Subscribe to key press events.
            inputConsumer.on('keyPressed', options, (event: KeyEvent) => {
              console.info(`Succeeded in subscribing ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to subscribe , Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputConsumer.off('keyPressed')<sup>16+</sup>

off(type: 'keyPressed', callback?: Callback&lt;KeyEvent&gt;): void

Unsubscribes from key press events. This API uses an asynchronous callback to return the result. If the API call is successful, the system's default response to the key event will be resumed; that is, system-level actions, such as volume adjustment, will be triggered normally.

**System capability**: SystemCapability.MultimodalInput.Input.InputConsumer

**Device behavior differences**: In versions earlier than API version 23, this API can be properly called on phones and tablets. If it is called on other device types, error code 801 is returned. Since API version 23, this API can be properly called on phones, tablets, PCs/2-in-1 devices, and TVs. On other device types, error code 801 is returned.

**Parameters**

| Name        | Type                        | Mandatory  | Description                             |
| ---------- | -------------------------- | ---- | ---------- |
| type       | string                     | Yes   | Event type. This parameter has a fixed value of **keyPressed**.       |
| callback   | Callback&lt;[KeyEvent](./js-apis-keyevent.md#keyevent)&gt; | No   | Callback to unregister. If this parameter is not specified, listening will be disabled for all registered callbacks.|

**Error codes**:

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message            |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |

**Example**

```js
import { inputConsumer, KeyEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Disable listening for a single callback.
            let options: inputConsumer.KeyPressedConfig = {
              key: 16,
              action: 1,
              isRepeat: false,
            }
            let callback = (event: KeyEvent) => {
              console.info(`Succeeded in unsubscribing ${JSON.stringify(event)}.`);
            }
            // Subscribe to key press events.
            inputConsumer.on('keyPressed', options, callback);
            // Unsubscribe from key press events.
            inputConsumer.off('keyPressed', callback);
            // Disable listening for all callbacks.
            inputConsumer.off("keyPressed");
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
