# usb_ddk_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

## 概述

提供USB DDK中的枚举变量、结构体定义与宏定义。

**引用文件：** <usb/usb_ddk_types.h>

**库：** libusb_ndk.z.so

**系统能力：** SystemCapability.Driver.USB.Extension

**起始版本：** 10

**相关模块：** [UsbDdk](capi-usbddk.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) | UsbControlRequestSetup | 控制传输setup包，对应USB协议中的Setup Data。 |
| [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md) | UsbDeviceDescriptor | 标准设备描述符，对应USB协议中Standard Device Descriptor。 |
| [UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) | UsbConfigDescriptor | 标准配置描述符，对应USB协议中Standard Configuration Descriptor。 |
| [UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) | UsbInterfaceDescriptor | 标准接口描述符，对应USB协议中Standard Interface Descriptor。 |
| [UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) | UsbEndpointDescriptor | 标准端点描述符，对应USB协议中Standard Endpoint Descriptor。 |
| [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) | UsbDdkEndpointDescriptor | 端点描述符。 |
| [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md) | UsbDdkInterfaceDescriptor | 接口描述符。 |
| [UsbDdkInterface](capi-usbddk-usbddkinterface.md) | UsbDdkInterface | USB接口，是特定接口下备用设置的集合。 |
| [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) | UsbDdkConfigDescriptor | 配置描述符。 |
| [UsbRequestPipe](capi-usbddk-usbrequestpipe.md) | UsbRequestPipe | 请求管道，是USB数据传输请求的抽象。 |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) | UsbDeviceMemMap | 设备内存映射，通过[OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap)创建设备内存映射，使用内存映射后的缓冲区，获得更好的性能。 |
| [Usb_DeviceArray](capi-usbddk-usb-devicearray.md) | Usb_DeviceArray | 设备ID清单，用于存放[OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices)接口获取到的设备ID列表和设备数量。开发者申请设备ID数组，使用完结构体后需释放成员内存，否则会造成资源泄漏。 |
| [Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) | Usb_NonRootHubArray | 非根集线器列表，用于存放[OH_Usb_GetNonRootHubs](capi-usb-ddk-api-h.md#OH_Usb_GetNonRootHubs)接口获取到的非根集线器设备ID列表和数量。开发者申请非根集线器ID数组，使用完结构体后需释放成员内存，否则会造成资源泄漏。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [UsbDdkErrCode](#usbddkerrcode) | UsbDdkErrCode | USB DDK 错误码定义。 |

## 枚举类型说明

### UsbDdkErrCode

```c
enum UsbDdkErrCode
```

**描述**

USB DDK 错误码定义。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| USB_DDK_SUCCESS = 0 | 操作成功。 |
| USB_DDK_FAILED = -1 | 操作失败。 <br> **废弃版本：** 16 |
| USB_DDK_NO_PERM = 201 | 没有权限。表示调用者没有足够的权限执行该操作。请确认已申请SystemCapability.Driver.USB.Extension系统能力。<br> **起始版本：** 14 |
| USB_DDK_INVALID_PARAMETER = 401 | 非法参数，如参数为空、参数类型错误或参数超出范围等，在API version 16之前值为-2。 |
| USB_DDK_MEMORY_ERROR = 27400001 | 内存相关的错误，包括：内存不足、内存数据拷贝失败、内存申请失败等，在API version 16之前值为-3。 <br> **废弃版本：** 16 |
| USB_DDK_INVALID_OPERATION = 27400002 | 非法操作，如在设备未初始化时调用接口、在错误状态下执行操作等，在API version 16之前值为-4。 <br> **废弃版本：** 16 |
| USB_DDK_NULL_PTR = -5 | 空指针异常，如传入的指针参数为NULL或内部使用空指针访问。 <br> **废弃版本：** 16 |
| USB_DDK_DEVICE_BUSY = -6 | 设备忙，如设备正在执行其他操作或设备资源被占用。 <br> **废弃版本：** 16 |
| USB_DDK_IO_FAILED = 27400003 | 设备I/O操作失败。请检查设备连接是否正常、设备是否支持该操作或数据传输是否超时。<br> **起始版本：** 14 |
| USB_DDK_TIMEOUT = 27400004 | 传输超时。请检查设备响应是否正常或适当增加超时时间，在API version 16之前值为-7。 <br> **废弃版本：** 16 |


