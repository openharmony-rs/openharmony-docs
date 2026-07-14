# @ohos.usb

本模块主要提供管理USB设备的相关功能，包括查询USB设备列表、批量数据传输、控制命令传输、权限控制等。

> **说明：**
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 从API version 9开始，该接口不再维护，推荐使用新接口[@ohos.usbManager](arkts-usbmanager.md)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [usbManager:usbManager](arkts-usbmanager.md)

**系统能力：** SystemCapability.USB.USBManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bulkTransfer](arkts-basicservices-bulktransfer-f.md#bulktransfer-1) | 批量传输。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备信息列表以及endpoint；再调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；然后调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)接口得到返回数据devicepipe之后，再次获取接口[usb.claimInterface](arkts-basicservices-claiminterface-f.md#claiminterface-1)；再调用usb.bulkTransfer接口。 |
| [claimInterface](arkts-basicservices-claiminterface-f.md#claiminterface-1) | 注册通信接口。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备信息以及interfaces；调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)接口得到devicepipe作为参数。 |
| [closePipe](arkts-basicservices-closepipe-f.md#closepipe-1) | 关闭设备消息控制通道。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)得到devicepipe作为参数。 |
| [connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1) | 打开USB设备。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备信息以及device，再调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限。 |
| [controlTransfer](arkts-basicservices-controltransfer-f.md#controltransfer-1) | 控制传输。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)接口得到devicepipe作为参数。 |
| [getDevices](arkts-basicservices-getdevices-f.md#getdevices-1) | 获取USB设备列表。 |
| [getFileDescriptor](arkts-basicservices-getfiledescriptor-f.md#getfiledescriptor-1) | 获取文件描述符。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)接口得到devicepipe作为参数。 |
| [getRawDescriptor](arkts-basicservices-getrawdescriptor-f.md#getrawdescriptor-1) | 获取原始的USB描述符。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)接口得到devicepipe作为参数。 |
| [hasRight](arkts-basicservices-hasright-f.md#hasright-1) | 判断是否有权访问该设备。 |
| [releaseInterface](arkts-basicservices-releaseinterface-f.md#releaseinterface-1) | 释放注册过的通信接口。需要调用[usb.claimInterface](arkts-basicservices-claiminterface-f.md#claiminterface-1)先获取接口，才能使用此方法释放接口。 |
| [requestRight](arkts-basicservices-requestright-f.md#requestright-1) | 请求软件包的临时权限以访问设备。使用Promise异步回调。系统应用默认拥有访问设备权限，无需调用此接口申请。 |
| [setConfiguration](arkts-basicservices-setconfiguration-f.md#setconfiguration-1) | 设置设备配置。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备信息以及config；调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)得到devicepipe作为参数。 |
| [setInterface](arkts-basicservices-setinterface-f.md#setinterface-1) | 设置设备接口。需要调用[usb.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备列表以及interfaces；调用[usb.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)得到devicepipe作为参数；调用[usb.claimInterface](arkts-basicservices-claiminterface-f.md#claiminterface-1)注册通信接口。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCurrentFunctions](arkts-basicservices-getcurrentfunctions-f-sys.md#getcurrentfunctions-1) | 在设备模式下，获取当前的USB功能列表的数字组合掩码。 |
| [getPorts](arkts-basicservices-getports-f-sys.md#getports-1) | 获取所有物理USB端口描述信息。 |
| [getSupportedModes](arkts-basicservices-getsupportedmodes-f-sys.md#getsupportedmodes-1) | 获取指定的端口支持的模式列表的组合掩码。 |
| [setCurrentFunctions](arkts-basicservices-setcurrentfunctions-f-sys.md#setcurrentfunctions-1) | 在设备模式下，设置当前的USB功能列表。 |
| [setPortRoles](arkts-basicservices-setportroles-f-sys.md#setportroles-1) | 设置指定的端口支持的角色模式，包含充电角色、数据传输角色。 |
| [usbFunctionsFromString](arkts-basicservices-usbfunctionsfromstring-f-sys.md#usbfunctionsfromstring-1) | 在设备模式下，将字符串形式的USB功能列表转化为数字掩码。 |
| [usbFunctionsToString](arkts-basicservices-usbfunctionstostring-f-sys.md#usbfunctionstostring-1) | 在设备模式下，将数字掩码形式的USB功能列表转化为字符串。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [USBConfig](arkts-basicservices-usbconfig-i.md) | USB配置，一个[USBDevice](arkts-basicservices-usbdevice-i.md)中可以含有多个配置。 |
| [USBControlParams](arkts-basicservices-usbcontrolparams-i.md) | 控制传输参数。 |
| [USBDevice](arkts-basicservices-usbdevice-i.md) | USB设备信息。 |
| [USBDevicePipe](arkts-basicservices-usbdevicepipe-i.md) | USB设备消息传输通道，用于确定设备。 |
| [USBEndpoint](arkts-basicservices-usbendpoint-i.md) | 通过USB发送和接收数据的端口。通过[USBInterface](arkts-basicservices-usbinterface-i.md)获取。 |
| [USBInterface](arkts-basicservices-usbinterface-i.md) | 一个[USBConfig](arkts-basicservices-usbconfig-i.md)中可以含有多个USBInterface，每个USBInterface提供一个功能。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [USBPort](arkts-basicservices-usbport-i-sys.md) | USB设备端口。 |
| [USBPortStatus](arkts-basicservices-usbportstatus-i-sys.md) | USB设备端口角色信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [USBControlRequestType](arkts-basicservices-usbcontrolrequesttype-e.md) | 控制请求类型。 |
| [USBRequestDirection](arkts-basicservices-usbrequestdirection-e.md) | 请求方向。 |
| [USBRequestTargetType](arkts-basicservices-usbrequesttargettype-e.md) | 请求目标类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataRoleType](arkts-basicservices-dataroletype-e-sys.md) | 数据角色类型。 |
| [FunctionType](arkts-basicservices-functiontype-e-sys.md) | USB设备侧功能。 |
| [PortModeType](arkts-basicservices-portmodetype-e-sys.md) | USB端口模式类型。 |
| [PowerRoleType](arkts-basicservices-powerroletype-e-sys.md) | 电源角色类型。 |
<!--DelEnd-->

