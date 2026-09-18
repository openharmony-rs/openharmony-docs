# queryDevices

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## queryDevices

```TypeScript
function queryDevices(busType?: number): Array<Readonly<Device>>
```

Queries the list of peripheral devices. If the device has no peripheral device connected, an empty list is returned.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| busType | number | No | Device bus type specified by [BusType](arkts-driverdevelopment-devicemanager-bustype-e.md). If this parameter is left empty, all types of devices are searched. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Readonly&lt;[Device](arkts-driverdevelopment-devicemanager-device-i.md)&gt;&gt; | List of peripheral devices obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [22900001](../errorcode-deviceManager.md#22900001-externaldevicemanager-service-exception-or-bustype-parameter-error) | ExternalDeviceManager service exception or busType parameter error. |

**Examples**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';

try {
  let devices : Array<deviceManager.Device> = deviceManager.queryDevices(deviceManager.BusType.USB);
  for (let item of devices) {
    let device : deviceManager.USBDevice = item as deviceManager.USBDevice;
    console.info(`Device id is ${device.deviceId}`);
  }
} catch (error) {
  console.error(`Failed to query device. Code is ${error.code}, message is ${error.message}`);
}
```
