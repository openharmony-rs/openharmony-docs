# @ohos.driver.deviceManager

本模块主要提供管理外部设备的相关功能，包括查询设备列表、绑定设备和解除绑定设备。

**起始版本：** 10

<!--Device-unnamed-declare namespace deviceManager--><!--Device-unnamed-declare namespace deviceManager-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bindDevice](arkts-driverdevelopment-devicemanager-binddevice-f.md#binddevice-1) | 根据queryDevices()返回的设备信息绑定设备。需要调用[deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)获取设备信息以及device。 |
| [bindDevice](arkts-driverdevelopment-devicemanager-binddevice-f.md#binddevice-2) | 根据queryDevices()返回的设备信息绑定设备。需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)获取设备信息以及device。 |
| [bindDeviceDriver](arkts-driverdevelopment-devicemanager-binddevicedriver-f.md#binddevicedriver-1) | 根据queryDevices()返回的设备信息绑定设备。需要调用[deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)获取设备信息以及device。 |
| [bindDeviceDriver](arkts-driverdevelopment-devicemanager-binddevicedriver-f.md#binddevicedriver-2) | 根据queryDevices()返回的设备信息绑定设备。需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)获取设备信息以及device。 |
| [bindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-binddriverwithdeviceid-f.md#binddriverwithdeviceid-1) | 根据queryDevices()返回的设备信息绑定设备。使用Promise异步回调。需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)获取设备信息列表。 |
| [queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1) | 获取接入主设备的外部设备列表。如果没有设备接入，那么将会返回一个空的列表。 |
| [unbindDevice](arkts-driverdevelopment-devicemanager-unbinddevice-f.md#unbinddevice-1) | 解除设备绑定。 |
| [unbindDevice](arkts-driverdevelopment-devicemanager-unbinddevice-f.md#unbinddevice-2) | 解除设备绑定。 |
| [unbindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-unbinddriverwithdeviceid-f.md#unbinddriverwithdeviceid-1) | 解除设备绑定。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [queryDeviceInfo](arkts-driverdevelopment-devicemanager-querydeviceinfo-f-sys.md#querydeviceinfo-1) | 查询扩展外设详细信息列表。如果没有设备接入，那么将会返回一个空的列表。 |
| [queryDriverInfo](arkts-driverdevelopment-devicemanager-querydriverinfo-f-sys.md#querydriverinfo-1) | 查询扩展外设驱动详细信息列表。如果没有设备接入，那么将会返回一个空的列表。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Device](arkts-driverdevelopment-devicemanager-device-i.md) | 外设信息。 |
| [RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md) | 远程设备驱动。 |
| [USBDevice](arkts-driverdevelopment-devicemanager-usbdevice-i.md) | USB设备信息，继承自[Device](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md) | 设备详细信息。 |
| [DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md) | 驱动详细信息。 |
| [USBDeviceInfo](arkts-driverdevelopment-devicemanager-usbdeviceinfo-i-sys.md) | USB设备详细信息，继承自[DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md)。 |
| [USBDriverInfo](arkts-driverdevelopment-devicemanager-usbdriverinfo-i-sys.md) | USB设备驱动详细信息，继承自[DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md)。 |
| [USBInterfaceDesc](arkts-driverdevelopment-devicemanager-usbinterfacedesc-i-sys.md) | USB设备接口描述符。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BusType](arkts-driverdevelopment-devicemanager-bustype-e.md) | 设备总线类型。 |

