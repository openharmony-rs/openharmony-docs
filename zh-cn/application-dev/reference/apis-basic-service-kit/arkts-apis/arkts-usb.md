# @ohos.usb

本模块主要提供管理USB设备的相关功能，包括查询USB设备列表、批量数据传输、控制命令传输、权限控制等。

> **说明：**
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 从API version 9开始，该接口不再维护，推荐使用新接口[@ohos.usbManager](arkts-usbmanager.md#usbManager)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [usbManager:usbManager](arkts-usbmanager.md#usbManager)

**系统能力：** SystemCapability.USB.USBManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bulkTransfer](arkts-basicservices-usb-bulktransfer-f.md#bulkTransfer-1) | 批量传输。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备信息列表以及endpoint；再调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；<br/>然后调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)接口得到返回数据devicepipe之后，再次获取接口<br/>[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claimInterface-1)；再调用usb.bulkTransfer接口。<br/> |
| [claimInterface](arkts-basicservices-usb-claiminterface-f.md#claimInterface-1) | 注册通信接口。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备信息以及interfaces；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调<br/>用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)接口得到devicepipe作为参数。<br/> |
| [closePipe](arkts-basicservices-usb-closepipe-f.md#closePipe-1) | 关闭设备消息控制通道。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调用<br/>[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)得到devicepipe作为参数。<br/> |
| [connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1) | 打开USB设备。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备信息以及device，再调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限。<br/> |
| [controlTransfer](arkts-basicservices-usb-controltransfer-f.md#controlTransfer-1) | 控制传输。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调用<br/>[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)接口得到devicepipe作为参数。<br/> |
| <!--DelRow-->[getCurrentFunctions](arkts-basicservices-usb-getcurrentfunctions-f-sys.md#getCurrentFunctions-1) | 在设备模式下，获取当前的USB功能列表的数字组合掩码。<br/> |
| [getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1) | 获取USB设备列表。<br/> |
| [getFileDescriptor](arkts-basicservices-usb-getfiledescriptor-f.md#getFileDescriptor-1) | 获取文件描述符。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调用<br/>[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)接口得到devicepipe作为参数。<br/> |
| <!--DelRow-->[getPorts](arkts-basicservices-usb-getports-f-sys.md#getPorts-1) | 获取所有物理USB端口描述信息。<br/> |
| [getRawDescriptor](arkts-basicservices-usb-getrawdescriptor-f.md#getRawDescriptor-1) | 获取原始的USB描述符。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调用<br/>[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)接口得到devicepipe作为参数。<br/> |
| <!--DelRow-->[getSupportedModes](arkts-basicservices-usb-getsupportedmodes-f-sys.md#getSupportedModes-1) | 获取指定的端口支持的模式列表的组合掩码。<br/> |
| [hasRight](arkts-basicservices-usb-hasright-f.md#hasRight-1) | 判断是否有权访问该设备。<br/> |
| [releaseInterface](arkts-basicservices-usb-releaseinterface-f.md#releaseInterface-1) | 释放注册过的通信接口。<br/><br/>需要调用[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claimInterface-1)先获取接口，才能使用此方法释放接口。<br/> |
| [requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1) | 请求软件包的临时权限以访问设备。使用Promise异步回调。系统应用默认拥有访问设备权限，无需调用此接口申请。<br/> |
| [setConfiguration](arkts-basicservices-usb-setconfiguration-f.md#setConfiguration-1) | 设置设备配置。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备信息以及config；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调用<br/>[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)得到devicepipe作为参数。<br/> |
| <!--DelRow-->[setCurrentFunctions](arkts-basicservices-usb-setcurrentfunctions-f-sys.md#setCurrentFunctions-1) | 在设备模式下，设置当前的USB功能列表。<br/> |
| [setInterface](arkts-basicservices-usb-setinterface-f.md#setInterface-1) | 设置设备接口。<br/><br/>需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备列表以及interfaces；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调<br/>用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)得到devicepipe作为参数；调用[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claimInterface-1)注册通信接<br/>口。<br/> |
| <!--DelRow-->[setPortRoles](arkts-basicservices-usb-setportroles-f-sys.md#setPortRoles-1) | 设置指定的端口支持的角色模式，包含充电角色、数据传输角色。<br/> |
| <!--DelRow-->[usbFunctionsFromString](arkts-basicservices-usb-usbfunctionsfromstring-f-sys.md#usbFunctionsFromString-1) | 在设备模式下，将字符串形式的USB功能列表转化为数字掩码。<br/> |
| <!--DelRow-->[usbFunctionsToString](arkts-basicservices-usb-usbfunctionstostring-f-sys.md#usbFunctionsToString-1) | 在设备模式下，将数字掩码形式的USB功能列表转化为字符串。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [USBConfig](arkts-basicservices-usb-usbconfig-i.md) | USB配置，一个[USBDevice](arkts-basicservices-usb-usbdevice-i.md#USBDevice)中可以含有多个配置。<br/> |
| [USBControlParams](arkts-basicservices-usb-usbcontrolparams-i.md) | 控制传输参数。<br/> |
| [USBDevice](arkts-basicservices-usb-usbdevice-i.md) | USB设备信息。<br/> |
| [USBDevicePipe](arkts-basicservices-usb-usbdevicepipe-i.md) | USB设备消息传输通道，用于确定设备。<br/> |
| [USBEndpoint](arkts-basicservices-usb-usbendpoint-i.md) | 通过USB发送和接收数据的端口。通过[USBInterface](arkts-basicservices-usb-usbinterface-i.md#USBInterface)获取。<br/> |
| [USBInterface](arkts-basicservices-usb-usbinterface-i.md) | 一个[USBConfig](arkts-basicservices-usb-usbconfig-i.md#USBConfig)中可以含有多个USBInterface，每个USBInterface提供一个功能。<br/> |
| <!--DelRow-->[USBPort](arkts-basicservices-usb-usbport-i-sys.md) | USB设备端口。<br/> |
| <!--DelRow-->[USBPortStatus](arkts-basicservices-usb-usbportstatus-i-sys.md) | USB设备端口角色信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DataRoleType](arkts-basicservices-usb-dataroletype-e-sys.md) | 数据角色类型。<br/> |
| <!--DelRow-->[FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | USB设备侧功能。<br/> |
| <!--DelRow-->[PortModeType](arkts-basicservices-usb-portmodetype-e-sys.md) | USB端口模式类型。<br/> |
| <!--DelRow-->[PowerRoleType](arkts-basicservices-usb-powerroletype-e-sys.md) | 电源角色类型。<br/> |
| [USBControlRequestType](arkts-basicservices-usb-usbcontrolrequesttype-e.md) | 控制请求类型。<br/> |
| [USBRequestDirection](arkts-basicservices-usb-usbrequestdirection-e.md) | 请求方向。<br/> |
| [USBRequestTargetType](arkts-basicservices-usb-usbrequesttargettype-e.md) | 请求目标类型。<br/> |

