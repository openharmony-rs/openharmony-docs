# @ohos.usbManager

本模块主要提供管理USB设备的相关功能，包括主设备上查询USB设备列表、批量数据传输、控制命令传输、权限控制等；从设备上端口管理、功能切换及查询等。

> **使用说明**
>
> 凡是参数类型为[usbManager.USBDevicePipe](arkts-basicservices-usbdevicepipe-i.md)的接口,都需要执行如下操作：
> **在使用接口前：**
> 1. 调用[usbManager.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备列表。
> 2. 调用[usbManager.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取请求权限。
> 3. 调用[usbManager.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)得到[usbManager.USBDevicePipe](arkts-basicservices-usbdevicepipe-i.md)作为参数。
> **在使用接口后：**
> 调用[usbManager.closePipe](usbManager.closePipe(USBDevicePipe: pipe))关闭设备消息控制通道。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bulkTransfer](arkts-basicservices-bulktransfer-f.md#bulktransfer-1) | 批量传输。使用Promise异步回调。@link usbManager.claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean)}&gt; claim通信接口。 |
| [cancelAccessoryRight](arkts-basicservices-cancelaccessoryright-f.md#cancelaccessoryright-1) | 取消当前应用程序访问USB配件的权限。需要调用[usbManager.getAccessoryList](arkts-basicservices-getaccessorylist-f.md#getaccessorylist-1)获取配件列表，得到[USBAccessory](arkts-basicservices-usbaccessory-i.md)作为参数。 |
| [claimInterface](arkts-basicservices-claiminterface-f.md#claiminterface-1) | 声明对USB设备某个接口的控制权。 |
| [closeAccessory](arkts-basicservices-closeaccessory-f.md#closeaccessory-1) | 关闭配件文件描述符。需要调用[usbManager.openAccessory](arkts-basicservices-openaccessory-f.md#openaccessory-1)获取配件列表，得到[USBAccessoryHandle](arkts-basicservices-usbaccessoryhandle-i.md)作为参数。 |
| [closePipe](arkts-basicservices-closepipe-f.md#closepipe-1) | 关闭设备消息控制通道。1. 需要调用[usbManager.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备列表；2. 调用[usbManager.requestRight](arkts-basicservices-requestright-f.md#requestright-1)获取设备请求权限；3. 调用[usbManager.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)得到devicepipe作为参数。 |
| [connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1) | 根据getDevices()返回的设备信息打开USB设备。如果USB服务异常，可能返回`undefined`，注意需要对接口返回值做判空处理。1. 需要调用[usbManager.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备信息以及device;2. 调用[usbManager.requestRight](arkts-basicservices-requestright-f.md#requestright-1)请求使用该设备的权限。 |
| [controlTransfer](arkts-basicservices-controltransfer-f.md#controltransfer-1) | 控制传输。使用Promise异步回调。 |
| [getAccessoryList](arkts-basicservices-getaccessorylist-f.md#getaccessorylist-1) | 获取当前已接入主机的USB配件列表。 |
| [getDevices](arkts-basicservices-getdevices-f.md#getdevices-1) | 获取接入主设备的USB设备列表。@link usbManager.requestRight(deviceName: string)}申请权限后，自行发起控制传输获取。 |
| [getFileDescriptor](arkts-basicservices-getfiledescriptor-f.md#getfiledescriptor-1) | 获取文件描述符。 |
| [getRawDescriptor](arkts-basicservices-getrawdescriptor-f.md#getrawdescriptor-1) | 获取原始的USB描述符。如果USB服务异常，可能返回`undefined`，注意需要对接口返回值做判空处理。 |
| [hasAccessoryRight](arkts-basicservices-hasaccessoryright-f.md#hasaccessoryright-1) | 检查应用程序是否有权访问USB配件。需要调用[usbManager.getAccessoryList](arkts-basicservices-getaccessorylist-f.md#getaccessorylist-1)获取配件列表，得到[USBAccessory](arkts-basicservices-usbaccessory-i.md)作为参数。 |
| [hasRight](arkts-basicservices-hasright-f.md#hasright-1) | 判断是否有权访问该设备。如果“使用者”（如各种App或系统）有权访问设备则返回true；无权访问设备则返回false。 |
| [openAccessory](arkts-basicservices-openaccessory-f.md#openaccessory-1) | 获取配件句柄并打开配件文件描述符。之后可以通过CoreFileKit提供的read/write接口和配件进行通信。需要调用[usbManager.getAccessoryList](arkts-basicservices-getaccessorylist-f.md#getaccessorylist-1)获取配件列表，得到[USBAccessory](arkts-basicservices-usbaccessory-i.md)作为参数。 |
| [releaseInterface](arkts-basicservices-releaseinterface-f.md#releaseinterface-1) | 释放claim过的通信接口。@link usbManager.claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean)}&gt; claim通信接口。 |
| [removeRight](arkts-basicservices-removeright-f.md#removeright-1) | 移除软件包访问设备的权限。系统应用默认拥有访问设备权限，调用此接口不会产生影响。 |
| [requestAccessoryRight](arkts-basicservices-requestaccessoryright-f.md#requestaccessoryright-1) | 为指定应用程序申请访问USB配件的访问权限。使用Promise异步回调。需要调用[usbManager.getAccessoryList](arkts-basicservices-getaccessorylist-f.md#getaccessorylist-1)获取配件列表，得到[USBAccessory](arkts-basicservices-usbaccessory-i.md)作为参数。 |
| [requestRight](arkts-basicservices-requestright-f.md#requestright-1) | 请求软件包的临时权限以访问设备。使用Promise异步回调。系统应用默认拥有访问设备权限，无需调用此接口申请。 |
| [resetUsbDevice](arkts-basicservices-resetusbdevice-f.md#resetusbdevice-1) | 重置USB外设。 |
| [setConfiguration](arkts-basicservices-setconfiguration-f.md#setconfiguration-1) | 设置设备配置。 |
| [setInterface](arkts-basicservices-setinterface-f.md#setinterface-1) | 设置设备接口。@link usbManager.claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean)}&gt; claim通信接口。 |
| [usbCancelTransfer](arkts-basicservices-usbcanceltransfer-f.md#usbcanceltransfer-1) | 取消异步传输请求。@link usbManager.claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean)}&gt; claim通信接口。 |
| [usbControlTransfer](arkts-basicservices-usbcontroltransfer-f.md#usbcontroltransfer-1) | 控制传输。使用Promise异步回调。 |
| [usbSubmitTransfer](arkts-basicservices-usbsubmittransfer-f.md#usbsubmittransfer-1) | 提交异步传输请求。@link usbManager.claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean)}&gt; claim通信接口。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addAccessoryRight](arkts-basicservices-addaccessoryright-f-sys.md#addaccessoryright-1) | 为应用程序添加访问USB配requestAccessoryRight件权限。[usbManager.]{(@link usbManager.requestAccessoryRight)}会触发弹窗请求用户授权；addAccessoryRight不会触发弹窗，而是直接添加应用程序访问设备的权限。 |
| [addDeviceAccessRight](arkts-basicservices-adddeviceaccessright-f-sys.md#adddeviceaccessright-1) | 添加软件包访问设备的权限。系统应用默认拥有访问设备权限，调用此接口不会产生影响。[usbManager.requestRight]{(@link usbManager.requestRight)}会触发弹框请求用户授权；addDeviceAccessRight不会触发弹框，而是直接添加软件包访问设备的权限。 |
| [getCurrentFunctions](arkts-basicservices-getcurrentfunctions-f-sys.md#getcurrentfunctions-1) | 在设备模式下，获取当前的USB功能列表的数字组合掩码。开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`，注意需要对接口返回值做判空处理。 |
| [getDeviceFunctions](arkts-basicservices-getdevicefunctions-f-sys.md#getdevicefunctions-1) | 在设备模式下，获取当前的USB功能列表的数字组合掩码。开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`，注意需要对接口返回值做判空处理。 |
| [getFunctionsFromString](arkts-basicservices-getfunctionsfromstring-f-sys.md#getfunctionsfromstring-1) | 在设备模式下，将字符串形式的USB功能列表转化为数字掩码。 |
| [getPortList](arkts-basicservices-getportlist-f-sys.md#getportlist-1) | 获取所有物理USB端口描述信息。开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`，注意需要对接口返回值做判空处理。 |
| [getPortSupportModes](arkts-basicservices-getportsupportmodes-f-sys.md#getportsupportmodes-1) | 获取指定的端口支持的模式列表的组合掩码。 |
| [getPorts](arkts-basicservices-getports-f-sys.md#getports-1) | 获取所有物理USB端口描述信息。开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`，注意需要对接口返回值做判空处理。 |
| [getStringFromFunctions](arkts-basicservices-getstringfromfunctions-f-sys.md#getstringfromfunctions-1) | 在设备模式下，将数字掩码形式的USB功能列表转化为字符串。 |
| [getSupportedModes](arkts-basicservices-getsupportedmodes-f-sys.md#getsupportedmodes-1) | 获取指定的端口支持的模式列表的组合掩码。 |
| [setCurrentFunctions](arkts-basicservices-setcurrentfunctions-f-sys.md#setcurrentfunctions-1) | 在设备模式下，设置当前的USB功能列表。使用Promise异步回调。 |
| [setDeviceFunctions](arkts-basicservices-setdevicefunctions-f-sys.md#setdevicefunctions-1) | 在设备模式下，设置当前的USB功能列表。使用Promise异步回调。 |
| [setPortRoleTypes](arkts-basicservices-setportroletypes-f-sys.md#setportroletypes-1) | 设置指定的端口支持的角色模式，包含充电角色、数据传输角色。使用Promise异步回调。 |
| [setPortRoles](arkts-basicservices-setportroles-f-sys.md#setportroles-1) | 设置指定的端口支持的角色模式，包含充电角色、数据传输角色。使用Promise异步回调。 |
| [usbFunctionsFromString](arkts-basicservices-usbfunctionsfromstring-f-sys.md#usbfunctionsfromstring-1) | 在设备模式下，将字符串形式的USB功能列表转化为数字掩码。 |
| [usbFunctionsToString](arkts-basicservices-usbfunctionstostring-f-sys.md#usbfunctionstostring-1) | 在设备模式下，将数字掩码形式的USB功能列表转化为字符串。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [SubmitTransferCallback](arkts-basicservices-submittransfercallback-i.md) | Usb异步传输回调。 |
| [USBAccessory](arkts-basicservices-usbaccessory-i.md) | USB配件信息。 |
| [USBAccessoryHandle](arkts-basicservices-usbaccessoryhandle-i.md) | USB配件句柄。 |
| [USBConfiguration](arkts-basicservices-usbconfiguration-i.md) | USB配置，一个[USBDevice](arkts-basicservices-usbdevice-i.md)中可以含有多个配置。 |
| [USBControlParams](arkts-basicservices-usbcontrolparams-i.md) | 控制传输参数。 |
| [USBDevice](arkts-basicservices-usbdevice-i.md) | USB设备信息。 |
| [USBDevicePipe](arkts-basicservices-usbdevicepipe-i.md) | USB设备消息传输通道，用于确定设备。 |
| [USBDeviceRequestParams](arkts-basicservices-usbdevicerequestparams-i.md) | 控制传输参数。 |
| [USBEndpoint](arkts-basicservices-usbendpoint-i.md) | 通过USB发送和接收数据的端口。通过[USBInterface](arkts-basicservices-usbinterface-i.md)获取。 |
| [USBInterface](arkts-basicservices-usbinterface-i.md) | 一个[USBConfiguration](arkts-basicservices-usbconfiguration-i.md)中可以含有多个USBInterface，每个USBInterface提供一个功能。 |
| [UsbDataTransferParams](arkts-basicservices-usbdatatransferparams-i.md) | 作为通用USB数据传输接口，客户端需要填充这个对象中的参数，用以发起传输请求。 |
| [UsbIsoPacketDescriptor](arkts-basicservices-usbisopacketdescriptor-i.md) | 实时传输模式回调返回的分包信息。 |

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
| [USBControlRequestType](arkts-basicservices-usbcontrolrequesttype-e.md) | Enumerates control request types. |
| [USBRequestDirection](arkts-basicservices-usbrequestdirection-e.md) | Enumerates request directions. |
| [USBRequestTargetType](arkts-basicservices-usbrequesttargettype-e.md) | Enumerates request target types. |
| [UsbEndpointTransferType](arkts-basicservices-usbendpointtransfertype-e.md) | Enumerates USB transfer types. |
| [UsbTransferFlags](arkts-basicservices-usbtransferflags-e.md) | Enumerates USB transfer flags. |
| [UsbTransferStatus](arkts-basicservices-usbtransferstatus-e.md) | Enumerates the status code returned after data processing is complete. |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataRoleType](arkts-basicservices-dataroletype-e-sys.md) | Enumerates data role types. |
| [FunctionType](arkts-basicservices-functiontype-e-sys.md) | Enumerates USB device function types. |
| [PortModeType](arkts-basicservices-portmodetype-e-sys.md) | Enumerates USB port mode types. |
| [PowerRoleType](arkts-basicservices-powerroletype-e-sys.md) | Enumerates power role types. |
<!--DelEnd-->

