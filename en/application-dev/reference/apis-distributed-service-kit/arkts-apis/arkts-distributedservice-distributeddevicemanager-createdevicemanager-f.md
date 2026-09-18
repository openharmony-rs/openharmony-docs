# createDeviceManager

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## createDeviceManager

```TypeScript
function createDeviceManager(bundleName: string): DeviceManager
```

Creates a **DeviceManager** instance. The **DeviceManager** instance is the entry for invoking the APIs for distributed device management. It can be used to obtain information about trusted devices and local devices.

**Since:** 10

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. The value is a string of 1 to 255 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md) | **DeviceManager** instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
} catch(err) {
  let e: BusinessError = err as BusinessError;
  console.error('createDeviceManager errCode:' + e.code + ',errMessage:' + e.message);
}
```
