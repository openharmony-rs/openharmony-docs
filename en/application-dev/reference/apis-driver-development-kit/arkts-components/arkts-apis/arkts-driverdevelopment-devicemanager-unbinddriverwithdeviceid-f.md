# unbindDriverWithDeviceId

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## unbindDriverWithDeviceId

```TypeScript
function unbindDriverWithDeviceId(deviceId: number): Promise<number>
```

Unbinds a peripheral device. This API uses a promise to return the result.

**Since:** 19

**Required permissions:** ohos.permission.ACCESS_DDK_DRIVERS

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Device ID, which can be obtained via [queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the ID of the unbound device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [26300001](../errorcode-deviceManager.md#26300001-externaldevicemanager-service-exception) | ExternalDeviceManager service exception. |
| [26300003](../errorcode-deviceManager.md#26300003-driver-client-not-bound-to-any-driver-server) | There is no binding relationship. |

**Examples**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // For example, deviceId is 12345678. You can use queryDevices() to obtain the deviceId.
  deviceManager.unbindDriverWithDeviceId(12345678).then((data : number) => {
    console.info(`unbindDriverWithDeviceId success, Device_Id is ${data}.`);
  }, (error : BusinessError) => {
    console.error(`unbindDriverWithDeviceId async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`unbindDriverWithDeviceId fail. Code is ${error.code}, message is ${error.message}`);
}
```
