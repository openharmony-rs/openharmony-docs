# @ohos.driver.deviceManager

本模块主要提供管理外部设备的相关功能，包括查询设备列表、绑定设备和解除绑定设备。

**起始版本：** 10

**系统能力：** SystemCapability.Driver.ExternalDevice

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bindDevice](arkts-driverdevelopment-devicemanager-binddevice-f.md#bindDevice-1) | 根据queryDevices()返回的设备信息绑定设备。<br/>需要调用[deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)获取设备信息以及device。<br/> |
| [bindDevice](arkts-driverdevelopment-devicemanager-binddevice-f.md#bindDevice-2) | 根据queryDevices()返回的设备信息绑定设备。<br/>需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)获取设备信息以及device。<br/> |
| [bindDeviceDriver](arkts-driverdevelopment-devicemanager-binddevicedriver-f.md#bindDeviceDriver-1) | 根据queryDevices()返回的设备信息绑定设备。<br/>需要调用[deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)获取设备信息以及device。<br/> |
| [bindDeviceDriver](arkts-driverdevelopment-devicemanager-binddevicedriver-f.md#bindDeviceDriver-2) | 根据queryDevices()返回的设备信息绑定设备。<br/>需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)获取设备信息以及device。<br/> |
| [bindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-binddriverwithdeviceid-f.md#bindDriverWithDeviceId-1) | 根据queryDevices()返回的设备信息绑定设备。使用Promise异步回调。<br/>需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)获取设备信息列表。<br/> |
| <!--DelRow-->[queryDeviceInfo](arkts-driverdevelopment-devicemanager-querydeviceinfo-f-sys.md#queryDeviceInfo-1) | 查询扩展外设详细信息列表。如果没有设备接入，那么将会返回一个空的列表。<br/> |
| [queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1) | 获取接入主设备的外部设备列表。如果没有设备接入，那么将会返回一个空的列表。<br/> |
| <!--DelRow-->[queryDriverInfo](arkts-driverdevelopment-devicemanager-querydriverinfo-f-sys.md#queryDriverInfo-1) | 查询扩展外设驱动详细信息列表。如果没有设备接入，那么将会返回一个空的列表。<br/> |
| [unbindDevice](arkts-driverdevelopment-devicemanager-unbinddevice-f.md#unbindDevice-1) | 解除设备绑定。<br/> |
| [unbindDevice](arkts-driverdevelopment-devicemanager-unbinddevice-f.md#unbindDevice-2) | 解除设备绑定。<br/> |
| [unbindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-unbinddriverwithdeviceid-f.md#unbindDriverWithDeviceId-1) | 解除设备绑定。使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Device](arkts-driverdevelopment-devicemanager-device-i.md) | 外设信息。<br/> |
| <!--DelRow-->[DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md) | 设备详细信息。<br/> |
| <!--DelRow-->[DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md) | 驱动详细信息。<br/> |
| [RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md) | 远程设备驱动。<br/> |
| [USBDevice](arkts-driverdevelopment-devicemanager-usbdevice-i.md) | USB设备信息，继承自[Device](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)。<br/> |
| <!--DelRow-->[USBDeviceInfo](arkts-driverdevelopment-devicemanager-usbdeviceinfo-i-sys.md) | USB设备详细信息，继承自[DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md#DeviceInfo)。<br/> |
| <!--DelRow-->[USBDriverInfo](arkts-driverdevelopment-devicemanager-usbdriverinfo-i-sys.md) | USB设备驱动详细信息，继承自[DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md#DriverInfo)。<br/> |
| <!--DelRow-->[USBInterfaceDesc](arkts-driverdevelopment-devicemanager-usbinterfacedesc-i-sys.md) | USB设备接口描述符。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BusType](arkts-driverdevelopment-devicemanager-bustype-e.md) | 设备总线类型。<br/> |

