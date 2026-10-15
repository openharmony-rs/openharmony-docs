# on (System API)

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## on('key')

```TypeScript
function on(type: 'key', keyOptions: KeyOptions, callback: Callback<KeyOptions>): void
```

Subscribes to system hotkeys. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - Only the key down event, or both the key down and key up events, can be subscribed to.
> 
> - If only the key up event needs to be subscribed to, there is a risk that the down event is consumed by the focused window, leaving the up event unpaired. The design and implementation should be reviewed to determine whether this is reasonable.

**Since:** 8

<!--Device-inputConsumer-function on(type: 'key', keyOptions: KeyOptions, callback: Callback<KeyOptions>): void--><!--Device-inputConsumer-function on(type: 'key', keyOptions: KeyOptions, callback: Callback<KeyOptions>): void-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'key' | Yes | Event type. Currently, only **key** is supported. |
| keyOptions | [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | Yes | Key combination options. Since API version 26.0.0, the parameter [KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md) is added to keyOptions. However, this API can ignore it. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md)&gt; | Yes | Callback invoked to return the key combination data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

<!--Del-->
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

<!--DelEnd-->
