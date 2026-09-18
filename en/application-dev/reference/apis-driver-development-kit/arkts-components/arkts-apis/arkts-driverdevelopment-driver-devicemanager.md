# @ohos.driver.deviceManager(Peripheral Management)

The **deviceManager** module provides APIs for managing peripheral devices, including querying the peripheral device list and binding or unbinding a peripheral device.

**Since:** 10

**System capability:** SystemCapability.Driver.ExternalDevice

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [bindDevice](arkts-driverdevelopment-devicemanager-binddevice-f.md) | Binds a peripheral device based on the device information returned by **queryDevices()**. You need to use [deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device information and device. |
| [bindDevice](arkts-driverdevelopment-devicemanager-binddevice-f.md) | Binds a peripheral device based on the device information returned by **queryDevices()**. This API uses a promise to return the result. You need to use [deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device information and device. |
| [bindDeviceDriver](arkts-driverdevelopment-devicemanager-binddevicedriver-f.md) | Binds a peripheral device based on the device information returned by **queryDevices()**. You need to use [deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device information and device. |
| [bindDeviceDriver](arkts-driverdevelopment-devicemanager-binddevicedriver-f.md) | Binds a peripheral device based on the device information returned by **queryDevices()**. This API uses a promise to return the result. You need to use [deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device information and device. |
| [bindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-binddriverwithdeviceid-f.md) | Binds a peripheral device based on the device information returned by **queryDevices()**. This API uses a promise to return the result. You need to use [deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md) to obtain the peripheral device list. |
| [queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md) | Queries the list of peripheral devices. If the device has no peripheral device connected, an empty list is returned. |
| [unbindDevice](arkts-driverdevelopment-devicemanager-unbinddevice-f.md) | Unbinds a peripheral device. |
| [unbindDevice](arkts-driverdevelopment-devicemanager-unbinddevice-f.md) | Unbinds a peripheral device. This API uses a promise to return the result. |
| [unbindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-unbinddriverwithdeviceid-f.md) | Unbinds a peripheral device. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [queryDeviceInfo](arkts-driverdevelopment-devicemanager-querydeviceinfo-f-sys.md) | Obtains the list of detailed information about peripherals. If the device has no peripheral device connected, an empty list is returned. |
| [queryDriverInfo](arkts-driverdevelopment-devicemanager-querydriverinfo-f-sys.md) | Obtains the list of detailed information about peripheral drivers. If the device has no peripheral device connected, an empty list is returned. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [Device](arkts-driverdevelopment-devicemanager-device-i.md) | Represents the peripheral device information. |
| [RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md) | Represents information about a remote device driver. |
| [USBDevice](arkts-driverdevelopment-devicemanager-usbdevice-i.md) | USB device information, which is inherited from [Device](arkts-driverdevelopment-devicemanager-querydevices-f.md). |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md) | Defines the detailed information about a device. |
| [DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md) | Defines detailed information about a driver. |
| [USBDeviceInfo](arkts-driverdevelopment-devicemanager-usbdeviceinfo-i-sys.md) | Defines detailed information about the USB device. It is inherited from [DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md). |
| [USBDriverInfo](arkts-driverdevelopment-devicemanager-usbdriverinfo-i-sys.md) | Defines detailed information about the USB device driver. It is inherited from [DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md). |
| [USBInterfaceDesc](arkts-driverdevelopment-devicemanager-usbinterfacedesc-i-sys.md) | Defines the interface descriptor of a USB device. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BusType](arkts-driverdevelopment-devicemanager-bustype-e.md) | Enumerates the device bus types. |
