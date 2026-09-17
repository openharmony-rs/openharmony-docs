# releaseDeviceManager

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## releaseDeviceManager

```TypeScript
function releaseDeviceManager(deviceManager: DeviceManager): void
```

Releases a **DeviceManager** instance that is no longer used.

**Since:** 10

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceManager | [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md) | Yes | **DeviceManager** instance to release. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  distributedDeviceManager.releaseDeviceManager(dmInstance);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('release device manager errCode:' + e.code + ',errMessage:' + e.message);
}
```
