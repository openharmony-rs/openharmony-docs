# @ohos.driver.deviceManager (Peripheral Management) (System API)
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=3f084ee0cb47efd9eea21a11d5f925de727d9509 translatedAt=2026-10-14T05:05:47.257Z pushedAt=2026-10-22T06:41:42.509Z nl=2 -->

The **deviceManager** module provides the functions of managing peripheral devices, including querying information about peripherals and their drivers.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.driver.deviceManager (Peripheral Management)](js-apis-driver-deviceManager.md).

## Modules to Import

```ts
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## deviceManager.queryDeviceInfo

queryDeviceInfo(deviceId?: number): Array&lt;Readonly&lt;DeviceInfo&gt;&gt;

Obtains the list of detailed information about peripherals. If the device has no peripheral device connected, an empty list is returned.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters**

| Name     | Type    | Mandatory | Description                    |
|----------|--------|-----|------------------------|
| deviceId | number | No | Device ID, which is obtained through [queryDevices](js-apis-driver-deviceManager.md#devicemanagerquerydevices). If no device ID is passed, information about all devices is obtained by default. If no device is connected, an empty list is returned. |

**Return value**

| Type                                                    | Description         |
|--------------------------------------------------------|-------------|
| Array&lt;Readonly&lt;[DeviceInfo](#deviceinfo)&gt;&gt; | List of detailed information about peripherals.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Driver Error Codes](errorcode-deviceManager.md).

| ID   | Error Message                                                                 |
|----------|-----------------------------------------------------------------------|
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. A non-system application cannot call a system API. |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types.        |
| 26300001 | ExternalDeviceManager service exception.                              |

**Example**

```ts
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // For example, deviceId is 12345678. You can use queryDevices() to obtain the deviceId.
  let deviceInfos: Array<deviceManager.DeviceInfo> = deviceManager.queryDeviceInfo(12345678);
  for (let item of deviceInfos) {
    console.info(`Device id is ${item.deviceId}`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to query device info. Code is ${err.code}, message is ${err.message}`);
}
```
## deviceManager.queryDriverInfo

queryDriverInfo(driverUid?: string): Array&lt;Readonly&lt;DriverInfo&gt;&gt;

Obtains the list of detailed information about peripheral drivers. If the device has no peripheral device connected, an empty list is returned.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters**

| Name      | Type    | Mandatory | Description                        |
|-----------|--------|-----|----------------------------|
| driverUid | string | No | Driver UID, which is obtained from the device information returned by [queryDeviceInfo](#devicemanagerquerydeviceinfo). If no driver UID is passed, all driver information is obtained by default. If a UID is passed but the corresponding driver does not exist, an empty list is returned. |

**Return value**

| Type                                                    | Description           |
|--------------------------------------------------------|---------------|
| Array&lt;Readonly&lt;[DriverInfo](#driverinfo)&gt;&gt; | List of detailed information about peripheral drivers.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Driver Error Codes](errorcode-deviceManager.md).

| ID   | Error Message                                                                 |
|----------|-----------------------------------------------------------------------|
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. A non-system application cannot call a system API. |
| 401      | Parameter error. Possible causes: 1.Incorrect parameter types.        |
| 26300001 | ExternalDeviceManager service exception.                              |

**Example**

```ts
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // In this example, driver-12345 is the driver UID. During application development, you can use queryDeviceInfo to query the driver UID and use it as the input parameter.
  let driverInfos: Array<deviceManager.DriverInfo> = deviceManager.queryDriverInfo('driver-12345');
  for (let item of driverInfos) {
    console.info(`driver name is ${item.driverName}`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to query driver info. Code is ${err.code}, message is ${err.message}`);
}
```

## DeviceInfo

Defines the detailed information about a device.

**System API**: This is a system API.

**System capability**: SystemCapability.Driver.ExternalDevice

| Name             | Type     | Read-Only | Optional | Description         |
|-----------------|---------|-----|-----|-------------|
| deviceId        | number  | No  | No  | Device ID.      |
| isDriverMatched | boolean | No  | No  | Whether the device matches the driver. The value `true` indicates the device matches the driver, and the value `false` indicates the opposite.|
| driverUid       | string  | No  | Yes  | UID of the driver matching the device.|

## USBDeviceInfo

Defines detailed information about the USB device. It is inherited from [DeviceInfo](#deviceinfo).

**System API**: This is a system API.

**System capability**: SystemCapability.Driver.ExternalDevice

| Name               | Type                                                                | Read-Only | Optional | Description              |
|-------------------|--------------------------------------------------------------------|-----|-----|------------------|
| vendorId          | number                                                             | No  | No  | Vendor ID of the USB device. |
| productId         | number                                                             | No  | No  | Product ID of the USB device.|
| interfaceDescList | Array&lt;Readonly&lt;[USBInterfaceDesc](#usbinterfacedesc)&gt;&gt; | No   | No   | List of interface descriptors of the USB device.    |

## USBInterfaceDesc

Defines the interface descriptor of a USB device.

**System API**: This is a system API.

**System capability**: SystemCapability.Driver.ExternalDevice

| Name              | Type    | Read-Only | Optional | Description    |
|------------------|--------|-----|-----|--------|
| bInterfaceNumber | number | No  | No  | Interface ID. |
| bClass           | number | No  | No  | Interface class. |
| bSubClass        | number | No  | No  | Interface subclass.|
| bProtocol        | number | No  | No  | Interface protocol. |

## DriverInfo

Defines detailed information about a driver.

**System API**: This is a system API.

**System capability**: SystemCapability.Driver.ExternalDevice

| Name           | Type                                                | Read-Only | Optional | Description            |
|---------------|----------------------------------------------------|-----|-----|----------------|
| busType       | [BusType](js-apis-driver-deviceManager.md#bustype) | No  | No  | Bus type.         |
| driverUid     | string                                             | No   | No   | Driver UID.         |
| driverName    | string                                             | No  | No  | Driver name.         |
| driverVersion | string                                             | No  | No  | Driver version.         |
| driverSize    | string                                             | No   | No   | Size of the driver file, in bytes. It is used to identify the storage space occupied by the driver file. |
| description   | string                                             | No   | No   | Driver description, which provides detailed information about the driver functions, use scenarios, and precautions.         |

## USBDriverInfo

Defines detailed information about the USB device driver. It is inherited from [DriverInfo](#driverinfo).

**System API**: This is a system API.

**System capability**: SystemCapability.Driver.ExternalDevice

| Name           | Type                 | Read-Only | Optional | Description                     |
|---------------|---------------------|-----|-----|-------------------------|
| productIdList | Array&lt;number&gt; | No  | No  | Product ID list of the USB devices supported by the driver.|
| vendorIdList  | Array&lt;number&gt; | No  | No  | Vendor ID list of the USB devices supported by the driver. |