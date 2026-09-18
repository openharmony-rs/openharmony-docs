# getDeviceIds

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## getDeviceIds

```TypeScript
function getDeviceIds(callback: AsyncCallback<Array<number>>): void
```

Obtains the IDs of all input devices. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [inputDevice.getDeviceList](arkts-input-inputdevice-getdevicelist-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getDeviceList

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback function. If the operation is successful, **err** is **undefined**, and **data** is the ID list of all input devices. Otherwise, **err** is an error object. |

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
          // Obtaining the Input Device ID List
          inputDevice.getDeviceIds((error: BusinessError, ids: Array<number>) => {
            if (error) {
              console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              return;
            }
            console.info(`Succeeded in getting device id list: ${JSON.stringify(ids)}.`);
          });
        })
    }
  }
}
```

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
          // Obtaining the Input Device ID List
          inputDevice.getDeviceIds().then((ids: Array<number>) => {
            console.info(`Succeeded in getting device id list: ${JSON.stringify(ids)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          })
        })
    }
  }
}
```


## getDeviceIds

```TypeScript
function getDeviceIds(): Promise<Array<number>>
```

Obtains the IDs of all input devices. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [inputDevice.getDeviceList](arkts-input-inputdevice-getdevicelist-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getDeviceList

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the IDs of all input devices. **id** is the unique ID of an input device. |

**Examples**

See [getDeviceIds](#getdeviceids)
