# bindDriverWithDeviceId

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## bindDriverWithDeviceId

```TypeScript
function bindDriverWithDeviceId(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<RemoteDeviceDriver>
```

Binds a peripheral device based on the device information returned by **queryDevices()**. This API uses a promise to return the result. You need to use [deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device list.

**Since:** 19

**Required permissions:** ohos.permission.ACCESS_DDK_DRIVERS

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Device ID, which can be obtained via **queryDevices()**. |
| onDisconnect | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. When the bound device is disconnected, the value of **err** is **undefined** and the value of **data** is the ID of the unbound device. Otherwise, **err** is an error object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md)&gt; | Promise used to return a **RemoteDeviceDriver** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [26300001](../errorcode-deviceManager.md#26300001-externaldevicemanager-service-exception) | ExternalDeviceManager service exception. |
| [26300002](../errorcode-deviceManager.md#26300002-binding-driver-client-to-driver-server-failed) | The driver service does not allow any client to bind. |

**Examples**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // For example, deviceId is 12345678. You can use queryDevices() to obtain the deviceId.
  deviceManager.bindDriverWithDeviceId(12345678, (error : BusinessError, data : number) => {
    console.error(`Device is disconnected`);
  }).then((data: deviceManager.RemoteDeviceDriver) => {
    console.info(`bindDriverWithDeviceId success, Device_Id is ${data.deviceId}.
    remote is ${data.remote != null ? data.remote.getDescriptor() : "null"}`);
  }, (error: BusinessError) => {
    console.error(`bindDriverWithDeviceId async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`bindDriverWithDeviceId fail. Code is ${error.code}, message is ${error.message}`);
}
```
