# createKeyboardController

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## createKeyboardController

```TypeScript
function createKeyboardController(): Promise<KeyboardController>
```

Creates a keyboard controller for simulating key operations. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KeyboardController](arkts-input-inputeventclient-keyboardcontroller-i.md)&gt; | Promise used to return the keyboard controller instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

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
