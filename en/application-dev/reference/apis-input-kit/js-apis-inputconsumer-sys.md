# @ohos.multimodalInput.inputConsumer (Global Shortcut Keys) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1a59b01eb09cbde916aad8893b634e85d3707880 translatedAt=2026-11-04T04:36:50.470Z pushedAt=2026-11-04T08:04:44.686Z nl=1 -->

The **inputConsumer** module provides APIs for subscribing to and unsubscribing from global hotkeys.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.
>
> - The APIs provided by this module apply only to system shortcut keys, which are global shortcut keys defined by the system.


## Modules to Import

```js
import { inputConsumer } from '@kit.InputKit';
```

## inputConsumer.on('key')

on(type: 'key', keyOptions: KeyOptions, callback: Callback&lt;KeyOptions&gt;): void

Subscribes to the system shortcut key. This API uses an asynchronous callback to return the result.
> **NOTE**
>
> - Supports subscribing to only the key down event, or to both the key down event and the key up event.
> - If only the key up event needs to be subscribed, there is a risk that the down event is consumed by the focused window and the up event cannot be closed in a loop. In this case, check whether the design and implementation are reasonable.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Parameters** 

| Name        | Type                        | Mandatory  | Description                                      |
| ---------- | -------------------------- | ---- | ---------------------------------------- |
| type       | string                     | Yes   | Event type. Currently, only **key** is supported.                      |
| keyOptions | [KeyOptions](#keyoptions)  | Yes    | Key combination options. Since API version 26.0.0, a new parameter [KeyCommandTriggerType](#keycommandtriggertype) is added to keyOptions, and this API does not need to consider this parameter.|
| callback   | Callback&lt;[KeyOptions](#keyoptions)&gt; | Yes    | Callback invoked to return the key combination data. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
          let leftAltKey = 2045;
          let tabKey = 2049;
          let keyOptions: inputConsumer.KeyOptions = {
            preKeys: [ leftAltKey ],
            finalKey: tabKey,
            isFinalKeyDown: true,
            finalKeyDownDuration: 0
          };
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.info(`Succeeded in consuming key, keyOptions: ${JSON.stringify(keyOptions)}.`);
          };
          try {
            // Subscribe to the key event.
            inputConsumer.on('key', keyOptions, callback);
          } catch (error) {
            console.error(`Failed to subscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## inputConsumer.off('key')

off(type: 'key', keyOptions: KeyOptions, callback?: Callback&lt;KeyOptions&gt;): void

Disables listening for system hotkey change events. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Parameters** 

| Name        | Type                        | Mandatory  | Description                             |
| ---------- | -------------------------- | ---- | ------------------------------- |
| type       | string                     | Yes   | Event type. Currently, only **key** is supported.             |
| keyOptions | [KeyOptions](#keyoptions) | Yes | Key combination options. Since API version 26.0.0, a new parameter [KeyCommandTriggerType](#keycommandtriggertype) is added to keyOptions, and this API does not need to consider this parameter. |
| callback   | Callback&lt;[KeyOptions](#keyoptions)&gt; | No   | Callback to unregister. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
          let leftAltKey = 2045;
          let tabKey = 2049;
          // Disable listening for a single callback.
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.info(`Succeeded in consuming key, keyOptions: ${JSON.stringify(keyOptions)}.`);
          };
          let keyOption: inputConsumer.KeyOptions = {preKeys: [leftAltKey], finalKey: tabKey, isFinalKeyDown: true, finalKeyDownDuration: 0};
          try {
            // Subscribe to key events.
            inputConsumer.on('key', keyOption, callback);
            // Unsubscribe from key events.
            inputConsumer.off('key', keyOption, callback);
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
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftAltKey = 2045;
          let tabKey = 2049;
          // Disable listening for all callbacks.
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.info(`Succeeded in consuming key, keyOptions: ${JSON.stringify(keyOptions)}.`);
          };
          let keyOption: inputConsumer.KeyOptions = {preKeys: [leftAltKey], finalKey: tabKey, isFinalKeyDown: true, finalKeyDownDuration: 0};
          try {
            // Subscribe to key events.
            inputConsumer.on('key', keyOption, callback);
            // Unsubscribe from key events.
            inputConsumer.off('key', keyOption);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputConsumer.onKey

onKey(keyOptions: KeyOptions, callback: KeyCommandCallback): void

Subscribes to key combinations (key command mode), and supports specifying different trigger modes through triggerType. When a key combination input event that meets the conditions occurs, an asynchronous callback is used to return the result.

Differences from the existing API [inputConsumer.on('key')](#inputconsumeronkey):
- The keyOptions of this API supports the triggerType parameter, which can select modes such as triggering on key press, triggering on repeated press, or triggering on both repeated press and release.
- The callback parameter of this API is of the KeyCommandCallback type, which receives both the KeyOptions and KeyEvent objects.
- This API adopts the event consumption mechanism, which can prevent key events from being passed backward through event consumption.

**Since**: 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOptions | [KeyOptions](#keyoptions) | Yes | Key combination options, which support the triggerType parameter. |
| callback | [KeyCommandCallback](#keycommandcallback) | Yes | Callback function used to return the key combination options and key event data. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftCtrlKey = 2072;
let cKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`keyOptions: ${keyOptions} keyEvents: ${keyEvents}`);
};
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

```js
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [],
  finalKey: 2049,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.REPEAT_PRESSED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`Repeat key event`);
}
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

```js
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftAltKey = 2045;
let tabKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftAltKey],
  finalKey: tabKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.ALL_RELEASED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`All released event`);
}
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

## inputConsumer.offKey

offKey(keyOptions: KeyOptions, callback?: KeyCommandCallback): void

Disables listening for system hotkey change events. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOptions | [KeyOptions](#keyoptions) | Yes | Key combination options, which must be the same as the keyOptions passed in during subscription. |
| callback | [KeyCommandCallback](#keycommandcallback) | No | Callback to unregister. If this parameter is not specified, listening will be disabled for all callbacks registered by the current application. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftCtrlKey = 2072;
let cKey = 2049;
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`KeyEvent received`);
}
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
try {
  inputConsumer.onKey(keyOptions, callback);
  inputConsumer.offKey(keyOptions, callback);
  console.info(`Unsubscribe success`);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to execute operation. Code: ${err.code}, message: ${err.message}`);
}
```

```js
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftCtrlKey = 2072;
let cKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
try {
  inputConsumer.offKey(keyOptions);
  console.info(`Unsubscribe all success`);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to execute operation. Code: ${err.code}, message: ${err.message}`);
}
```

## KeyCommandCallback

type KeyCommandCallback = (keyOptions: KeyOptions, keyEvent: KeyEvent) => void

Defines the key command callback function type, which is triggered when the shortcut key registration condition is met.

**Since**: 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOptions | [KeyOptions](#keyoptions) | Yes | Combination key options when the callback is triggered. |
| keyEvent | [KeyEvent](js-apis-keyevent.md#keyevent) | Yes | Key event object, which contains the detailed key information. |

## inputConsumer.setShieldStatus<sup>11+</sup>

setShieldStatus(shieldMode: ShieldMode, isShield: boolean): void

Sets the system hotkey shield status.

**Required permissions:** ohos.permission.INPUT_CONTROL_DISPATCHING

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Parameters** 

| Name        | Type                        | Mandatory  | Description                                      |
| ---------- | -------------------------- | ---- | ---------------------------------------- |
| shieldMode       | [ShieldMode](#shieldmode11)                     | Yes   | System hotkey shield mode. Currently, only **FACTORY_MODE** is supported, which means to shield all system hotkeys.                      |
| isShield | boolean  | Yes   | Whether to enable shortcut key shielding. The value **true** means to enable shortcut key shielding, and the value **false** indicates the opposite.             |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
          let FACTORY_MODE = 0;
          try {
            // Set the blocking state.
            inputConsumer.setShieldStatus(FACTORY_MODE, true);
            console.info(`Succeeded in setting shield status.`);
          } catch (error) {
            console.error(`Failed to set shield status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputConsumer.getShieldStatus<sup>11+</sup>

getShieldStatus(shieldMode: ShieldMode): boolean

Obtains the system hotkey shield status.

**Required permissions:** ohos.permission.INPUT_CONTROL_DISPATCHING

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Parameters** 

| Name        | Type                        | Mandatory  | Description                                      |
| ---------- | -------------------------- | ---- | ---------------------------------------- |
| shieldMode       | [ShieldMode](#shieldmode11)                    | Yes   | System hotkey shield mode. Currently, only **FACTORY_MODE** is supported, which means to shield all system hotkeys.                      |

**Return value** 

| Type        |  Description                                      |
| ---------- |  ---------------------------------------- |
| boolean                    | Whether to enable shortcut key shielding. The value **true** means to enable shortcut key shielding, and the value **false** indicates the opposite.                      |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
          try {
            let FACTORY_MODE = 0;
            let shieldStatusResult: boolean = inputConsumer.getShieldStatus(FACTORY_MODE);
            console.info(`Succeeded in getting shield status, result: ${JSON.stringify(shieldStatusResult)}.`);
          } catch (error) {
            console.error(`Failed to get shield status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## KeyOptions

Represents combination key options.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| preKeys    | Array\<number>   | No    | No | Set of pre-keys, with the number ranging from 0 to 4. The pre-keys have no order requirement.<br>For example, in the key combination Ctrl+Alt+A, Ctrl+Alt are called pre-keys. |
| finalKey             | number  | No   |  No| Final key. This parameter is mandatory. A callback is triggered by the final key.<br>For example, in the combination keys **Ctrl+Alt+A**, **A** is called the final key.|
| isFinalKeyDown       | boolean | No   |  No| Whether the final key is pressed.<br>The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.|
| finalKeyDownDuration | number  | No    |  No | Duration for which the final key remains pressed, in microseconds (μs).<br>When finalKeyDownDuration is 0, the callback function is triggered immediately.<br>When finalKeyDownDuration is greater than 0, if isFinalKeyDown is true, the callback function is triggered after the final key has been pressed for longer than the set duration; if isFinalKeyDown is false, the callback function is triggered when the time from pressing to releasing the final key is less than the set duration.   |
| isRepeat<sup>18+</sup> | boolean  | No     | Yes     | Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite. The default value is **true**.|
| triggerType | [KeyCommandTriggerType](#keycommandtriggertype) | No | Yes | Trigger mode. The value is PRESSED (1), REPEAT_PRESSED (2), or ALL_RELEASED (3). Enables the command trigger mode. Once this value is set, isFinalKeyDown and isRepeat are ignored. For the [inputConsumer.on('key')](#inputconsumeronkey) API, this parameter is optional; for the [inputConsumer.onKey](#inputconsumeronkey-1) API, this parameter is mandatory.<br>**Since:** 26.0.0<br/>**Model constraint:** This API can be used only in the stage model.|

## ShieldMode<sup>11+</sup>

Enumerates system hotkey shield modes.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

| Name                       | Value| Description          |
| ------------------------------ | ----------- | ---------------- |
| FACTORY_MODE | 0 | Factory mode, which means to shield all system hotkeys.|

## KeyCommandTriggerType

Enumerates the key command trigger types, used to specify the trigger timing of a key combination.

**Since**: 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

| Name | Value | Description |
| --- | --- | --- |
| PRESSED | 1 | Triggered on the first press. The callback is triggered when the final key is pressed for the first time, and is not triggered on automatic repeated presses. |
| REPEAT_PRESSED | 2 | Triggered on repeated presses. The callback is triggered each time the final key is pressed, including automatic repeated presses. |
| ALL_RELEASED | 3 | The callback is triggered when a key is pressed or released, including keys that are automatically repeated. |
