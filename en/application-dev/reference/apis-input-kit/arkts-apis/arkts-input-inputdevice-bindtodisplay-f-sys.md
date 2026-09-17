# bindToDisplay (System API)

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## bindToDisplay

```TypeScript
function bindToDisplay(inputDeviceId: number, displayId: number): Promise<void>
```

Bind input devices to a display group. Only external USB and Bluetooth mice, touchpads, keyboards, and game controllers are supported. After binding, the device will be fixed to operate on the display group where the specified display is located. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.INPUT_DEVICE_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputDeviceId | number | Yes | ID of the specified input device. If the input service restarts or the input device is reconnects, its ID may change. The value must be an integer greater than or equal to 0. |
| displayId | number | Yes | ID of the target display. The value must be an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. The application does not have the required permission. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Called by non-system application. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |
| [3900001](../errorcode-inputdevice.md#3900001-device-not-exist) | The specified input device does not exist. |
| [3900004](../errorcode-inputdevice.md#3900004-specified-display-does-not-exist) | The specified display does not exist. |
| [3900005](../errorcode-inputdevice.md#3900005-unsupported-input-device) | Unsupported input device. |

**Examples**

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Bind the input device with ID 1 to the display with ID 0.
            inputDevice.bindToDisplay(1, 0).then(() => {
              console.info(`Succeeded in binding input device to display.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to bind input device to display, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to bind input device to display, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
