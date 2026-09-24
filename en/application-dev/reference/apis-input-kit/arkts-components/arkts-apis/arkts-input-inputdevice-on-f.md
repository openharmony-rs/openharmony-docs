# on

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## on('change')

```TypeScript
function on(type: 'change', listener: Callback<DeviceListener>): void
```

Registers a listener for input device hot-swap events. This feature requires connecting external devices such as a mouse, keyboard, or touchscreen. This API uses an asynchronous callback to return the result. You are advised to execute this operation on the main application thread and unregister the listener before the thread exits.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. This field has a fixed value of **change**. |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceListener](arkts-input-inputdevice-devicelistener-i.md)&gt; | Yes | Callback used to return the input device hot swap events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  @State isPhysicalKeyboardExist: boolean = false;
  @State message: string = 'Click to obtain the device list and monitor device hot-plug events';
  keyboards: Map<number, inputDevice.KeyboardType> = new Map();

  build() {
    RelativeContainer() {
      Column() {
        Text(this.message)
          .onClick(() => {
            try {
              // 1. Obtain the list of input devices and check whether a physical keyboard is connected.
              inputDevice.getDeviceList().then(data => {
                for (let i = 0; i < data.length; ++i) {
                  // Get Keyboard Type
                  inputDevice.getKeyboardType(data[i]).then(type => {
                    if (type === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD) {
                      // The physical keyboard is connected.
                      this.isPhysicalKeyboardExist = true;
                      this.keyboards.set(data[i], type);
                    }
                  }).catch((error: BusinessError) => {
                    console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                  });
                }
              }).catch((error: BusinessError) => {
                console.error(`Failed to get Device List, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              });
              // 2. Listen for device hot-swap events.
              inputDevice.on('change', (data) => {
                // Print Log
                hilog.info(DOMAIN, 'InputDevice', `Device event info: %{public}s`, JSON.stringify(data));
                // Get Keyboard Type
                inputDevice.getKeyboardType(data.deviceId).then((type) => {
                  // Print Log
                  hilog.info(DOMAIN, 'InputDevice', 'The keyboard type is: %{public}d', type);
                  if (type === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type === 'add') {
                    // The physical keyboard is inserted.
                    this.isPhysicalKeyboardExist = true;
                    this.keyboards.set(data.deviceId, type);
                  }
                }).catch((error: BusinessError) => {
                  console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                });
                if (this.keyboards.get(data.deviceId) === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD &&
                  data.type === 'remove') {
                  // The physical keyboard is removed.
                  this.isPhysicalKeyboardExist = false;
                  this.keyboards.delete(data.deviceId);
                }
              });
              this.message = 'Device monitoring enabled successfully'
            } catch (error) {
              // Print Error Log
              hilog.error(DOMAIN, 'InputDevice', `Execute failed, error: %{public}s`,
                JSON.stringify(error, ['code', 'message']));
              this.message = `Failed to enable device monitoring. Click to retry. Error message:${JSON.stringify(error,
                ["code", "message"])}`
            }
          })
      }
    }
  }
}
```
