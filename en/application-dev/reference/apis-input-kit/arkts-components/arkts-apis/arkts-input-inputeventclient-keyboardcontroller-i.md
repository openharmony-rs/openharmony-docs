# KeyboardController

Provides the capability of simulating key operations. The simulated key operation sequence must meet the following requirements:

1. A key can only be pressed when it is in the released state, or when it is the most recently pressed key and
has not been released.
2. A key can only be released after it has been pressed.
3. A maximum of five keys can be pressed and held simultaneously.

**Since:** 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## pressKey

```TypeScript
pressKey(keyCode: KeyCode): Promise<void>
```

Presses a key. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyCode | [KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md) | Yes | Key code of the key to be pressed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [4300001](../errorcode-inputeventclient.md#4300001-status-error) | The key is already pressed and is not the most recently pressed key. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

**Examples**

```TypeScript
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

## releaseKey

```TypeScript
releaseKey(keyCode: KeyCode): Promise<void>
```

Releases a key. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyCode | [KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md) | Yes | Key code of the key to be released. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [4300001](../errorcode-inputeventclient.md#4300001-status-error) | The key is not pressed. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

**Examples**

```TypeScript
For details, see [pressKey](#presskey).
```
