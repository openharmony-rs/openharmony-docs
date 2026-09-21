# off

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## off('change')

```TypeScript
function off(type: 'change', listener?: Callback<DeviceListener>): void
```

Disables listening for device hot swap events. This API is called before the application exits. This API uses an asynchronous callback to return the result. Listener unregistration must be performed on the same thread used for registration.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. This field has a fixed value of **change**. |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceListener](arkts-input-inputdevice-devicelistener-i.md)&gt; | No | Callback to unregister. If this parameter is left unspecified, listening for hot swap events of all input devices will be canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
          let callback = (data: inputDevice.DeviceListener) => {
            console.info(`Succeeded in listening to device change, data: ${JSON.stringify(data, [`type`, `deviceId`])}.`);
          };

          try {
            // Listen for Device Hot Swap Events
            inputDevice.on('change', callback);
          } catch (error) {
            console.error(`Failed to listen to device event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }

          // Disable this listener.
          try {
            // Cancel Listening for Device Hot Swap Events
            inputDevice.off('change', callback);
          } catch (error) {
            console.error(`Failed to cancel listening to device event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }

          // Disable all listeners.
          try {
            // Cancel Listening for Device Hot Swap Events
            inputDevice.off('change');
          } catch (error) {
            console.error(`Failed to cancel all listening device event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
