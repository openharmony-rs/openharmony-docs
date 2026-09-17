# injectTouchEvent (System API)

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## injectTouchEvent

```TypeScript
function injectTouchEvent(touchEvent: TouchEventData): void
```

Injects a touch event.

**Since:** 11

**Required permissions:** 
- API version 12 and later: ohos.permission.INJECT_INPUT_EVENT
- API version 11: N/A

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| touchEvent | [TouchEventData](arkts-input-inputeventclient-toucheventdata-i-sys.md) | Yes | Touch event data. [Action](arkts-input-multimodalinput-touchevent-action-e.md) in this parameter cannot be set to **CANCEL**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { inputEventClient, Touch, TouchEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
            };

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
            };
            ;
            let touchEventUp: inputEventClient.TouchEventData = {
              touchEvent: touchEventUpData
            };
            // Inject touch event
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
            };
            ;
            let touchEventDown: inputEventClient.TouchEventData = {
              touchEvent: touchEventDownData
            }
            // Inject touch event
            inputEventClient.injectTouchEvent(touchEventDown);
          } catch (error) {
            console.error(`Failed to inject touchEvent, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
