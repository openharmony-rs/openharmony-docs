# off

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## off('hotkeyChange')

```TypeScript
function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback<HotkeyOptions>): void
```

Unsubscribes from application shortcut key change events. This API uses an asynchronous callback to return the result.

**Since:** 14

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hotkeyChange' | Yes | Event type. This parameter has a fixed value of **hotkeyChange**. |
| hotkeyOptions | [HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md) | Yes | Shortcut key options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md)&gt; | No | Callback to unregister. If this parameter is left unspecified, listening will be disabled for all callbacks registered for the specified shortcut key options. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
          };
          let hotkeyOption: inputConsumer.HotkeyOptions = { preKeys: [leftCtrlKey], finalKey: zKey, isRepeat: true };
          try {
            // Subscribe to hotkey change events.
            inputConsumer.on('hotkeyChange', hotkeyOption, hotkeyCallback);
            // Unsubscribe from hotkey change events.
            inputConsumer.off('hotkeyChange', hotkeyOption, hotkeyCallback);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
          };
          let hotkeyOption: inputConsumer.HotkeyOptions = { preKeys: [leftCtrlKey], finalKey: zKey, isRepeat: true };
          try {
            // Subscribe to hotkey change events.
            inputConsumer.on('hotkeyChange', hotkeyOption, hotkeyCallback);
            // Unsubscribe from hotkey change events.
            inputConsumer.off('hotkeyChange', hotkeyOption);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## off('keyPressed')

```TypeScript
function off(type: 'keyPressed', callback?: Callback<KeyEvent>): void
```

Unsubscribes from key press events. This API uses an asynchronous callback to return the result. If the API call is successful, the system's default response to the key event will be resumed; that is, system-level actions, such as volume adjustment, will be triggered normally.

**Since:** 16

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyPressed' | Yes | Event type. This parameter has a fixed value of **keyPressed**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[KeyEvent](arkts-input-multimodalinput-keyevent-keyevent-i.md)&gt; | No | Callback to unregister. If this parameter is not specified, listening will be disabled for all registered callbacks. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { inputConsumer, KeyEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
            };
            // Subscribe to key press events.
            inputConsumer.on('keyPressed', options, callback);
            // Unsubscribe from key press events.
            inputConsumer.off('keyPressed', callback);
            // Disable listening for all callbacks.
            inputConsumer.off('keyPressed');
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
