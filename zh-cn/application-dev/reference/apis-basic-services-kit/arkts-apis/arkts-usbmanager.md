# @ohos.usbManager

本模块主要提供管理USB设备的相关功能，包括主机端的查询USB设备列表、批量数据传输、控制命令传输、权限控制等；设备端的端口管理、功能切换及查询等。适用于需要与USB设备进行数据交互、管理USB设备权限、动态切换USB设备模式等场景。

## 使用说明 凡是参数类型为[USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md)的接口，都需要执行如下操作： **在使用接口前：** 1. 调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备列表。 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)获取请求权限。 3. 调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)得到USBDevicePipe作为参数。 **在使用接口后：** 调用[usbManager.closePipe](arkts-basicservices-usbmanager-closepipe-f.md)关闭设备连接通道。 

**起始版本：** 23

<!--Device-unnamed-declare namespace usbManager--><!--Device-unnamed-declare namespace usbManager-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bulkTransfer](arkts-basicservices-usbmanager-bulktransfer-f.md) | 批量传输。调用成功后完成批量数据传输，返回实际传输或接收到的数据块大小。使用Promise异步回调。与usbSubmitTransfer相比， bulkTransfer适合简单的批量传输场景，通过独立参数直接传递数据和端点，使用Promise异步返回结果； usbSubmitTransfer适合需要更灵活控制的场景，通过UsbDataTransferParams对象封装参数，支持异步callback回调， 并可通过usbCancelTransfer取消传输请求。 |
| [cancelAccessoryRight](arkts-basicservices-usbmanager-cancelaccessoryright-f.md) | 取消当前应用访问USB配件的权限。与requestAccessoryRight()方法配合使用，用于取消此前通过requestAccessoryRight()申请的配件访问权限。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，得到 [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。 |
| [claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) | 声明对USB设备某个接口的控制权。调用成功后应用获得该接口的独占控制权可以进行数据传输等操作，其他程序无法访问该接口。使用完后需调用 [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md)释放该接口的控制权。 **使用场景**：在需要进行USB数据传输时，需要先声明接口控制权以独占访问该接口。例如，在USB存储设备读写、USB摄像头数据采集、USB串口通信等场景中，都需要先声明接口控制权。 |
| [closeAccessory](arkts-basicservices-usbmanager-closeaccessory-f.md) | 关闭配件文件描述符。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，然后调用 [usbManager.requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md)请求访问配件权限，权限申请成功后调用 [usbManager.openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md)获取配件句柄，得到 [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md)作为参数。 |
| [closePipe](arkts-basicservices-usbmanager-closepipe-f.md) | 关闭设备连接通道。 1. 调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备列表； 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)获取设备请求权限； 3. 调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)得到devicepipe作为参数。 |
| [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) | 根据getDevices()返回的设备信息打开USB设备，调用成功后建立设备连接通道，可以进行后续的数据传输和设备控制操作。使用完后需要调用 [usbManager.closePipe](arkts-basicservices-usbmanager-closepipe-f.md)关闭设备连接通道。如果USB服务异常，会返回`undefined`，注意需要对接口返回值做判空处理。 1. 调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备信息以及USBDevice; 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)请求使用该设备的权限。 |
| [controlTransfer](arkts-basicservices-usbmanager-controltransfer-f.md) | 控制传输。使用Promise异步回调。 |
| [getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md) | 获取当前已接入主机的USB配件列表。 |
| [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) | 获取接入主设备的USB设备列表。调用成功后返回已连接设备的详细信息列表包括设备名称、厂商产品信息等。 |
| [getFileDescriptor](arkts-basicservices-usbmanager-getfiledescriptor-f.md) | 获取文件描述符。如果USB服务异常，可能返回错误码，注意需要对接口返回值做判空或错误码检查处理。 |
| [getRawDescriptor](arkts-basicservices-usbmanager-getrawdescriptor-f.md) | 获取原始的USB描述符。如果USB服务异常，可能返回`undefined`，注意需要对接口返回值做判空处理。 |
| [hasAccessoryRight](arkts-basicservices-usbmanager-hasaccessoryright-f.md) | 检查应用是否有权访问USB配件。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，得到 [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。 |
| [hasRight](arkts-basicservices-usbmanager-hasright-f.md) | 判断是否有权访问该设备。 如果应用有权访问设备则返回true；无权访问设备则返回false。 |
| [openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md) | 获取配件句柄并打开配件文件描述符。之后可以通过CoreFileKit提供的read/write接口和配件进行通信。使用完后需要调用[closeAccessory](arkts-basicservices-usbmanager-closeaccessory-f.md)接 口关闭文件描述符。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，得到 [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。调用前需先调用 [usbManager.requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md)请求访问配件权限，权限申请成功（返回true）后方可调用本接口打开配件。 |
| [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md) | 释放claim过的通信接口。 |
| [removeRight](arkts-basicservices-usbmanager-removeright-f.md) | 移除应用访问设备的权限。系统应用默认拥有访问设备权限，调用此接口不会产生影响。 |
| [requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md) | 为指定应用申请访问USB配件的访问权限。使用Promise异步回调。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，得到 [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。 |
| [requestRight](arkts-basicservices-usbmanager-requestright-f.md) | 请求应用访问设备的临时权限。使用Promise异步回调返回结果。系统应用默认拥有访问设备权限，无需调用此接口。 |
| [resetUsbDevice](arkts-basicservices-usbmanager-resetusbdevice-f.md) | 重置USB设备。适用于USB设备出现通信异常需要恢复的场景，如设备固件升级后需要重新初始化、设备状态异常需要恢复、调试过程中需要重置设备状态等。调用成功后设备将被重置为初始状态，此前设置的配置和接口设置将被清除，设备需要重新初始 化。 |
| [setConfiguration](arkts-basicservices-usbmanager-setconfiguration-f.md) | 设置设备配置。适用于多功能USB设备需要切换工作模式的场景，如打印机+扫描仪组合设备切换为打印模式或扫描模式、设备从低功耗配置切换到高功耗配置以启用全部功能等。调用成功后设备的配置将被切换为指定的配置，后续的数据传输和设备操作将基 于新配置进行。 |
| [setInterface](arkts-basicservices-usbmanager-setinterface-f.md) | 设置设备接口。调用成功后接口将被切换到指定的备用设置，端点配置将随之改变以匹配传输类型要求。 |
| [usbCancelTransfer](arkts-basicservices-usbmanager-usbcanceltransfer-f.md) | 取消异步传输请求。适用于需要主动终止未完成USB数据传输的场景，如用户手动取消长时间数据传输、传输超时后的错误恢复、应用切换时中止当前传输等。 |
| [usbControlTransfer](arkts-basicservices-usbmanager-usbcontroltransfer-f.md) | 控制传输。调用成功后完成控制命令的传输，返回传输或接收到的数据块大小。适用于需要与USB设备进行控制命令交互的场景，如获取设备描述符、设置设备地址、发送厂商自定义命令、配置HID设备特性等。使用Promise异步回调。 |
| [usbSubmitTransfer](arkts-basicservices-usbmanager-usbsubmittransfer-f.md) | 提交异步传输请求，调用后立即返回，实际读写操作的结果以回调的方式返回。可通过调用[usbCancelTransfer](arkts-basicservices-usbmanager-usbcanceltransfer-f.md)接口取消异步传输请求。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addAccessoryRight](arkts-basicservices-usbmanager-addaccessoryright-f-sys.md) | 为应用添加访问USB配件权限。适用于系统应用需要为第三方应用授权访问USB配件的场景。usbManager.requestAccessoryRight会触发弹窗请求用户授权；addAccessoryRight不会触发弹窗，而是直接 添加应用访问USB配件的权限。授权立即生效并持久化存储，设备重启后仍然有效。授权范围为指定的USB配件实例，多个应用可以同时获得同一配件的访问权限。与requestAccessoryRight相比， addAccessoryRight不需要用户交互，适用于系统应用自动授权场景。 |
| [addDeviceAccessRight](arkts-basicservices-usbmanager-adddeviceaccessright-f-sys.md) | 添加应用访问设备的权限。系统应用默认拥有访问设备权限，调用此接口不会产生影响。适用于系统设置应用、设备管理应用等需要为第三方应用授权访问USB设备的场景。授权立即生效并持久化存储，设备重启后仍然有效。授权范围为指定的USB设备实 例，多个应用可以同时获得同一设备的访问权限。 [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)会触发弹窗请求用户授权；addDeviceAccessRight不会触发弹窗，而是直接添加应用程序访问设备的权限。 |
| [getCurrentFunctions](arkts-basicservices-usbmanager-getcurrentfunctions-f-sys.md) | 在设备模式下，获取当前的USB功能列表的数字组合掩码。适用于需要检查当前USB功能状态、确认功能配置、或在功能切换前后进行状态对比的场景。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判 空处理。 |
| [getDeviceFunctions](arkts-basicservices-usbmanager-getdevicefunctions-f-sys.md) | 在设备模式下，获取当前的USB功能列表的数字组合掩码。适用于需要检查当前USB功能状态、确认功能配置、或在功能切换前后进行状态对比的场景。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判 空处理。 |
| [getDeviceFunctions](arkts-basicservices-usbmanager-getdevicefunctions-f-sys.md) | Obtains the numeric mask combination for the current USB function list in Device mode. |
| [getFunctionsFromString](arkts-basicservices-usbmanager-getfunctionsfromstring-f-sys.md) | 在设备模式下，将字符串形式的USB功能列表转换为数字掩码。适用于需要将配置文件或用户输入的字符串形式USB功能列表转换为系统内部使用的数字掩码的场景，以便后续调用setDeviceFunctions等接口设置USB功能。 |
| [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md) | 获取所有物理USB端口描述信息。适用于需要枚举USB端口、进行端口管理、设备连接诊断、或查询端口配置信息的场景。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。 |
| [getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md) | 获取指定的端口支持的模式列表的组合掩码。适用于系统应用需要查询USB-C端口能力判断是否支持特定模式（如UFP、DFP或DRP模式）的场景。开发者模式关闭时，如果没有设备接入，接口返回undefined，注意需要对接口返回值做判空 处理。详细枚举值参见[PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md)。 |
| [getPorts](arkts-basicservices-usbmanager-getports-f-sys.md) | 获取所有物理USB端口描述信息。适用于需要枚举USB端口、进行端口管理、设备连接诊断、或查询端口配置信息的场景。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。 |
| [getStringFromFunctions](arkts-basicservices-usbmanager-getstringfromfunctions-f-sys.md) | 在设备模式下，将数字掩码形式的USB功能列表转换为字符串。适用于需要将当前USB功能状态以字符串形式显示或保存的场景，如在日志中记录当前功能配置、在UI界面展示当前功能等。 |
| [getStringFromFunctions](arkts-basicservices-usbmanager-getstringfromfunctions-f-sys.md) | Converts the numeric mask combination of a given USB function list to a string descriptor. |
| [getSupportedModes](arkts-basicservices-usbmanager-getsupportedmodes-f-sys.md) | 获取指定的端口支持的模式列表的组合掩码。适用于系统应用需要查询USB-C端口能力判断是否支持特定模式（如UFP、DFP或DRP模式）的场景。返回值为PortModeType的组合掩码，可通过位运算判断端口是否支持特定模式。 PortModeType包括：NONE（0，无模式）、UFP（1，上行端口模式，dataRole为DEVICE）、DFP（2，下行端口模式，dataRole为HOST）、DRP（3，双角色模式，可在UFP和DFP间切换）、 NUM_MODES（4，当前不支持）。开发者可根据返回值判断端口是否支持所需的电源角色和数据传输角色组合。 |
| [setCurrentFunctions](arkts-basicservices-usbmanager-setcurrentfunctions-f-sys.md) | 在设备模式下，设置当前的USB功能列表。使用Promise异步回调。调用成功后，设备的USB功能将切换为指定的功能列表。适用于系统应用需要动态切换设备USB功能、配置设备工作模式的场景。 |
| [setDeviceFunctions](arkts-basicservices-usbmanager-setdevicefunctions-f-sys.md) | 在设备模式下，设置当前的USB功能列表。使用Promise异步回调。调用成功后，设备的USB功能将切换为指定的功能列表。部分USB功能可能不被当前设备支持，设置前建议先查询设备支持的功能列表。开发者模式关闭时，如果没有设备接入，操 作可能会失败，调用失败时抛出异常。功能切换会触发USB设备的重新枚举，已连接的主机可能需要重新识别设备。多个功能可通过位运算组合设置，但某些功能可能互斥或存在优先级，具体约束请参考设备规格。功能设置失败可能由于设备不支持、权限不足 或系统限制，详见错误码说明。 |
| [setDeviceFunctions](arkts-basicservices-usbmanager-setdevicefunctions-f-sys.md) | Sets the current USB function list in Device mode. |
| [setPortRoleTypes](arkts-basicservices-usbmanager-setportroletypes-f-sys.md) | 设置指定端口当前的角色类型，包含电源角色、数据传输角色。使用Promise异步回调。调用成功后端口的电源角色和数据传输角色将切换为指定的角色。适用于系统应用需要动态切换USB端口角色的场景。开发者模式关闭时，如果没有设备接入，操作 可能会失败，调用失败时抛出异常。角色约束详情参见[USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md)。 **使用建议：** - 建议先调用getPortList获取端口列表，得到有效的portId - 建议调用[getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md)查询端口支持的模式，确保设置的角色配置在支持范围内 - 如果设置的角色不被端口支持，调用会失败并返回错误码14400003 |
| [setPortRoles](arkts-basicservices-usbmanager-setportroles-f-sys.md) | 设置指定端口当前的角色模式，包含电源角色、数据传输角色。使用Promise异步回调。调用成功后端口角色将切换为指定的角色。适用于系统应用需要动态切换USB端口角色的场景。开发者模式关闭时，如果没有设备接入，操作可能会失败，调用失败 时抛出异常。 |
| [usbFunctionsFromString](arkts-basicservices-usbmanager-usbfunctionsfromstring-f-sys.md) | 在设备模式下，将字符串形式的USB功能列表转换为数字掩码。适用于需要将配置文件或用户输入的字符串形式USB功能列表转换为系统内部使用的数字掩码的场景，以便后续调用setDeviceFunctions等接口设置USB功能。 |
| [usbFunctionsToString](arkts-basicservices-usbmanager-usbfunctionstostring-f-sys.md) | 在设备模式下，将数字掩码形式的USB功能列表转换为字符串。适用于需要将当前USB功能状态以字符串形式显示或保存的场景，如在日志中记录当前功能配置、在UI界面展示当前功能等。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [SubmitTransferCallback](arkts-basicservices-usbmanager-submittransfercallback-i.md) | USB异步传输回调。 |
| [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | USB配件信息。 |
| [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | USB配件句柄，包含配件文件描述符，用于通过CoreFileKit提供的read/write接口和配件进行通信。 |
| [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) | USB配置，一个[USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md)中可以含有多个配置。 |
| [USBControlParams](arkts-basicservices-usbmanager-usbcontrolparams-i.md) | 控制传输参数。 |
| [USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md) | USB设备信息。 |
| [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | USB设备连接通道，用于确定总线地址和设备地址。 |
| [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md) | 控制传输参数。 |
| [USBEndpoint](arkts-basicservices-usbmanager-usbendpoint-i.md) | USB端点，用于主机与设备之间数据传输的通信端点。通过[USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md)获取。 |
| [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md) | 一个[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)中可以含有多个USBInterface，每个USBInterface提供一个功能。 |
| [UsbDataTransferParams](arkts-basicservices-usbmanager-usbdatatransferparams-i.md) | USB数据传输参数对象，包含USB数据传输所需的所有参数，用于usbSubmitTransfer和usbCancelTransfer接口发起传输请求。 |
| [UsbIsoPacketDescriptor](arkts-basicservices-usbmanager-usbisopacketdescriptor-i.md) | 实时传输模式回调返回的分包信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [USBPort](arkts-basicservices-usbmanager-usbport-i-sys.md) | USB设备端口。 |
| [USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md) | USB设备端口角色信息。currentMode表示端口的当前USB模式，其值应在USBPort的supportedModes范围内。currentPowerRole表示当前电源角色，currentDataRole表示当前数据传输角 色。这些字段之间存在对应关系：在DFP模式下，dataRole通常为HOST、powerRole通常为SOURCE；在UFP模式下，dataRole通常为DEVICE、powerRole通常为SINK。端口状态变更受硬件和系统约 束，某些模式或角色组合可能不被支持。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [USBControlRequestType](arkts-basicservices-usbmanager-usbcontrolrequesttype-e.md) | 控制请求类型，用于指定具体的USB控制请求命令（如获取描述符、设置地址等）。 |
| [USBRequestDirection](arkts-basicservices-usbmanager-usbrequestdirection-e.md) | 请求方向。 |
| [USBRequestTargetType](arkts-basicservices-usbmanager-usbrequesttargettype-e.md) | 请求目标类型。 |
| [UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md) | USB传输类型。 |
| [UsbTransferFlags](arkts-basicservices-usbmanager-usbtransferflags-e.md) | USB传输标志。 |
| [UsbTransferStatus](arkts-basicservices-usbmanager-usbtransferstatus-e.md) | 数据处理完成后通过回调返回的状态码。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md) | 数据角色类型。 |
| [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | USB设备侧功能。 |
| [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md) | USB端口模式类型。 |
| [PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md) | 电源角色类型。 |
<!--DelEnd-->

