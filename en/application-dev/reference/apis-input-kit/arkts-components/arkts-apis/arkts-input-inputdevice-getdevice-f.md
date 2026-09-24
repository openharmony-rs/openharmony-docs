# getDevice

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## getDevice

```TypeScript
function getDevice(deviceId: number, callback: AsyncCallback<InputDeviceData>): void
```

Obtains the information about the input device with the specified ID. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [inputDevice.getDeviceInfo](arkts-input-inputdevice-getdeviceinfo-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getDeviceInfo

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[InputDeviceData](arkts-input-inputdevice-inputdevicedata-i.md)&gt; | Yes | Callback function. If the retrieval is successful, **err** is **undefined**, and **data** is the input device information. Otherwise, **err** is an error object. |

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
          // Obtain the name of the device whose ID is 1.
          inputDevice.getDevice(1, (error: BusinessError, deviceData: inputDevice.InputDeviceData) => {
            if (error) {
              console.error(`Failed to get device info, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              return;
            }
            console.info(`Succeeded in getting device info: ${JSON.stringify(deviceData)}.`);
          });
        })
    }
  }
}
```


<a id="getdevice-1"></a>

## getDevice

```TypeScript
function getDevice(deviceId: number): Promise<InputDeviceData>
```

Obtains the information about the input device with the specified ID. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [inputDevice.getDeviceInfo](arkts-input-inputdevice-getdeviceinfo-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getDeviceInfo

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[InputDeviceData](arkts-input-inputdevice-inputdevicedata-i.md)&gt; | Promise used to return information about the input device, including device ID, name, supported source, physical address, version information, and product information. |

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
          // Obtain the name of the device whose ID is 1.
          inputDevice.getDevice(1).then((deviceData: inputDevice.InputDeviceData) => {
            console.info(`Succeeded in getting device info: ${JSON.stringify(deviceData)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get device info, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          })
        })
    }
  }
}
```
