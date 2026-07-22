# @ohos.usb

本模块主要提供管理USB设备的相关功能，包括查询USB设备列表、批量数据传输、控制命令传输、权限控制等。
> **说明：**  
>  
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
> 从API version 9开始，该接口不再维护，推荐使用新接口[@ohos.usbManager](arkts-usbmanager.md)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [usbManager:usbManager](arkts-usbmanager.md)

<!--Device-unnamed-declare namespace usb--><!--Device-unnamed-declare namespace usb-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bulkTransfer](arkts-basicservices-usb-bulktransfer-f.md#bulktransfer) | 批量传输。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备信息列表以及endpoint；再调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；然后调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)接口得到返回数据devicepipe之后，再次获取接口[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claiminterface)；再调用usb.bulkTransfer接口。 |
| [claimInterface](arkts-basicservices-usb-claiminterface-f.md#claiminterface) | 注册通信接口。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备信息以及interfaces；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)接口得到devicepipe作为参数。 |
| [closePipe](arkts-basicservices-usb-closepipe-f.md#closepipe) | 关闭设备消息控制通道。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)得到devicepipe作为参数。 |
| [connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice) | 打开USB设备。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备信息以及device，再调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限。 |
| [controlTransfer](arkts-basicservices-usb-controltransfer-f.md#controltransfer) | 控制传输。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)接口得到devicepipe作为参数。 |
| [getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices) | 获取USB设备列表。 |
| [getFileDescriptor](arkts-basicservices-usb-getfiledescriptor-f.md#getfiledescriptor) | 获取文件描述符。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)接口得到devicepipe作为参数。 |
| [getRawDescriptor](arkts-basicservices-usb-getrawdescriptor-f.md#getrawdescriptor) | 获取原始的USB描述符。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)接口得到devicepipe作为参数。 |
| [hasRight](arkts-basicservices-usb-hasright-f.md#hasright) | 判断是否有权访问该设备。 |
| [releaseInterface](arkts-basicservices-usb-releaseinterface-f.md#releaseinterface) | 释放注册过的通信接口。  需要调用[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claiminterface)先获取接口，才能使用此方法释放接口。 |
| [requestRight](arkts-basicservices-usb-requestright-f.md#requestright) | 请求软件包的临时权限以访问设备。使用Promise异步回调。系统应用默认拥有访问设备权限，无需调用此接口申请。 |
| [setConfiguration](arkts-basicservices-usb-setconfiguration-f.md#setconfiguration) | 设置设备配置。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备信息以及config；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)得到devicepipe作为参数。 |
| [setInterface](arkts-basicservices-usb-setinterface-f.md#setinterface) | 设置设备接口。  需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备列表以及interfaces；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)得到devicepipe作为参数；调用[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claiminterface)注册通信接口。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCurrentFunctions](arkts-basicservices-usb-getcurrentfunctions-f-sys.md#getcurrentfunctions) | 在设备模式下，获取当前的USB功能列表的数字组合掩码。 |
| [getPorts](arkts-basicservices-usb-getports-f-sys.md#getports) | 获取所有物理USB端口描述信息。 |
| [getSupportedModes](arkts-basicservices-usb-getsupportedmodes-f-sys.md#getsupportedmodes) | 获取指定的端口支持的模式列表的组合掩码。 |
| [setCurrentFunctions](arkts-basicservices-usb-setcurrentfunctions-f-sys.md#setcurrentfunctions) | 在设备模式下，设置当前的USB功能列表。 |
| [setPortRoles](arkts-basicservices-usb-setportroles-f-sys.md#setportroles) | 设置指定的端口支持的角色模式，包含充电角色、数据传输角色。 |
| [usbFunctionsFromString](arkts-basicservices-usb-usbfunctionsfromstring-f-sys.md#usbfunctionsfromstring) | 在设备模式下，将字符串形式的USB功能列表转化为数字掩码。 |
| [usbFunctionsToString](arkts-basicservices-usb-usbfunctionstostring-f-sys.md#usbfunctionstostring) | 在设备模式下，将数字掩码形式的USB功能列表转化为字符串。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [USBConfig](arkts-basicservices-usb-usbconfig-i.md) | USB配置，一个[USBDevice](arkts-basicservices-usb-usbdevice-i.md)中可以含有多个配置。 |
| [USBControlParams](arkts-basicservices-usb-usbcontrolparams-i.md) | 控制传输参数。 |
| [USBDevice](arkts-basicservices-usb-usbdevice-i.md) | USB设备信息。 |
| [USBDevicePipe](arkts-basicservices-usb-usbdevicepipe-i.md) | USB设备消息传输通道，用于确定设备。 |
| [USBEndpoint](arkts-basicservices-usb-usbendpoint-i.md) | 通过USB发送和接收数据的端口。通过[USBInterface](arkts-basicservices-usb-usbinterface-i.md)获取。 |
| [USBInterface](arkts-basicservices-usb-usbinterface-i.md) | 一个[USBConfig](arkts-basicservices-usb-usbconfig-i.md)中可以含有多个USBInterface，每个USBInterface提供一个功能。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [USBPort](arkts-basicservices-usb-usbport-i-sys.md) | USB设备端口。 |
| [USBPortStatus](arkts-basicservices-usb-usbportstatus-i-sys.md) | USB设备端口角色信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [USBControlRequestType](arkts-basicservices-usb-usbcontrolrequesttype-e.md) | 控制请求类型。 |
| [USBRequestDirection](arkts-basicservices-usb-usbrequestdirection-e.md) | 请求方向。 |
| [USBRequestTargetType](arkts-basicservices-usb-usbrequesttargettype-e.md) | 请求目标类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataRoleType](arkts-basicservices-usb-dataroletype-e-sys.md) | 数据角色类型。 |
| [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | USB设备侧功能。 |
| [PortModeType](arkts-basicservices-usb-portmodetype-e-sys.md) | USB端口模式类型。 |
| [PowerRoleType](arkts-basicservices-usb-powerroletype-e-sys.md) | 电源角色类型。 |
<!--DelEnd-->

