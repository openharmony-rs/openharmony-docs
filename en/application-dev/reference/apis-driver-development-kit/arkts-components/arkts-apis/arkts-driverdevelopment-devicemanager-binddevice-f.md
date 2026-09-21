# bindDevice

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## bindDevice

```TypeScript
function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>,
    callback: AsyncCallback<{deviceId: number; remote: rpc.IRemoteObject;}>): void
```

Binds a peripheral device based on the device information returned by **queryDevices()**. You need to use [deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device information and device.

**Since:** 10

**Deprecated since:** 19

**Substitutes:** [bindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-binddriverwithdeviceid-f.md)(deviceId: number, onDisconnect: AsyncCallback&lt;number&gt;)

**Required permissions:** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Device ID, which can be obtained via **queryDevices()**. |
| onDisconnect | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. When the bound device is disconnected, the value of **err** is **undefined** and the value of **data** is the ID of the unbound device. Otherwise, **err** is an error object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{deviceId: number; remote: rpc.IRemoteObject;}&gt; | Yes | Callback used to return the result. When the device is bound successfully, **err** is **undefined**, and **data** contains the device ID and the bound device driver communication object. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [22900001](../errorcode-deviceManager.md#22900001-externaldevicemanager-service-exception-or-bustype-parameter-error) | ExternalDeviceManager service exception. |

**Examples**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

interface DataType {
  deviceId : number;
  remote : rpc.IRemoteObject;
}

try {
  // For example, deviceId is 12345678. You can use queryDevices() to obtain the deviceId.
  deviceManager.bindDevice(12345678, (error : BusinessError, data : number) => {
    console.error(`Device is disconnected`);
  }, (error : BusinessError, data : DataType) => {
    if (error) {
      console.error(`bindDevice async fail. Code is ${error.code}, message is ${error.message}`);
      return;
    }
    console.info(`bindDevice success`);
  });
} catch (error) {
  console.error(`bindDevice fail. Code is ${error.code}, message is ${error.message}`);
}
```


<a id="binddevice-1"></a>

## bindDevice

```TypeScript
function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<{deviceId: number;
    remote: rpc.IRemoteObject;}>
```

Binds a peripheral device based on the device information returned by **queryDevices()**. This API uses a promise to return the result. You need to use [deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device information and device.

**Since:** 10

**Deprecated since:** 19

**Substitutes:** [bindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-binddriverwithdeviceid-f.md)(deviceId: number, onDisconnect: AsyncCallback&lt;number&gt;)

**Required permissions:** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Device ID, which can be obtained via **queryDevices()**. |
| onDisconnect | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. When the bound device is disconnected, the value of **err** is **undefined** and the value of **data** is the ID of the unbound device. Otherwise, **err** is an error object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{deviceId: number; remote: rpc.IRemoteObject;}&gt; | Promise used to return an object containing the device ID and **IRemoteObject**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [22900001](../errorcode-deviceManager.md#22900001-externaldevicemanager-service-exception-or-bustype-parameter-error) | ExternalDeviceManager service exception. |

**Examples**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // For example, deviceId is 12345678. You can use queryDevices() to obtain the deviceId.
  deviceManager.bindDevice(12345678, (error : BusinessError, data : number) => {
    console.error(`Device is disconnected`);
  }).then(data => {
    console.info(`bindDevice success, Device_Id is ${data.deviceId}.
    remote is ${data.remote != null ? data.remote.getDescriptor() : "null"}`);
  }, (error: BusinessError) => {
    console.error(`bindDevice async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`bindDevice fail. Code is ${error.code}, message is ${error.message}`);
}
```
