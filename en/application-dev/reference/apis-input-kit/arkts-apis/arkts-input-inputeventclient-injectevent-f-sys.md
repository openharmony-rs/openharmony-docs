# injectEvent (System API)

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## injectEvent

```TypeScript
function injectEvent({ KeyEvent: KeyEvent }): void
```

Injects keys (including single keys and combination keys). Since API version 26.0.1, the caller can specify the display ID for injecting a key event. If the specified display ID does not exist, the operation will not take effect. If displayId is not specified, the operation will take effect on the display group of the same user as the caller.

**Since:** 8

**Required permissions:** 
- API version 12 and later: ohos.permission.INJECT_INPUT_EVENT
- API versions 8 to 11: N/A

<!--Device-inputEventClient-function injectEvent({ KeyEvent: KeyEvent }): void--><!--Device-inputEventClient-function injectEvent({ KeyEvent: KeyEvent }): void-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| KeyEvent | [KeyEvent](arkts-input-multimodalinput-keyevent-keyevent-i.md) | Yes | Key event to inject. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 12 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

<!--Del-->
**Examples**

```TypeScript
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
            };
            // Inject Event
            inputEventClient.injectEvent({ KeyEvent: backKeyDown });

            let backKeyUp: inputEventClient.KeyEvent = {
              isPressed: false,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            };
            // Inject Event
            inputEventClient.injectEvent({ KeyEvent: backKeyUp });
          } catch (error) {
            console.error(`Failed to inject KeyEvent, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

<!--DelEnd-->
