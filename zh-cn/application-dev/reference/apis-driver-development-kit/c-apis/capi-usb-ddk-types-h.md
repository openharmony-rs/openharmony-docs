# usb_ddk_types.h

## 概述

提供USB DDK中的枚举变量、结构体定义与宏定义。

**库：** libusb_ndk.z.so

**系统能力：** SystemCapability.Driver.USB.Extension

**起始版本：** 10

**相关模块：** [UsbDdk](capi-usbddk.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) | __attribute__((aligned(8))) UsbControlRequestSetup | 控制传输setup包，对应USB协议中的Setup Data。 |
| [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md) | __attribute__((aligned(8))) UsbDeviceDescriptor | 标准设备描述符，对应USB协议中Standard Device Descriptor。 |
| [UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) | __attribute__((packed)) UsbConfigDescriptor | 标准配置描述符，对应USB协议中Standard Configuration Descriptor。 |
| [UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) | __attribute__((packed)) UsbInterfaceDescriptor | 标准接口描述符，对应USB协议中Standard Interface Descriptor。 |
| [UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) | __attribute__((packed)) UsbEndpointDescriptor | 标准端点描述符，对应USB协议中Standard Endpoint Descriptor。 |
| [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) | UsbDdkEndpointDescriptor | 端点描述符。 |
| [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md) | UsbDdkInterfaceDescriptor | 接口描述符。 |
| [UsbDdkInterface](capi-usbddk-usbddkinterface.md) | UsbDdkInterface | USB接口，是特定接口下备用设置的集合。 |
| [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) | UsbDdkConfigDescriptor | 配置描述符。 |
| [UsbRequestPipe](capi-usbddk-usbrequestpipe.md) | __attribute__((aligned(8))) UsbRequestPipe | 请求管道。 |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) | UsbDeviceMemMap | 设备内存映射，通过{@link OH_Usb_CreateDeviceMemMap}创建设备内存映射，使用内存映射后的缓冲区，可提升数据传输性能。 |
| [Usb_DeviceArray](capi-usbddk-usb-devicearray.md) | Usb_DeviceArray | 设备ID清单，用于存放{@link OH_Usb_GetDevices}接口获取到的设备ID列表和设备数量。 |
| [Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) | Usb_NonRootHubArray | 非根集线器列表，用于存放{@link OH_Usb_GetNonRootHubs}接口获取到的非根集线器设备ID列表和数量。 |

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
| USB_DDK_FAILED = -1 |  |
| USB_DDK_NO_PERM = 201 |  |
| USB_DDK_INVALID_PARAMETER = 401 | 非法参数，在API version 16之前值为-2。 |
| USB_DDK_MEMORY_ERROR = 27400001 | 内存相关的错误，包括：内存不足、内存数据拷贝失败、内存申请失败等，在API version 16之前值为-3。 |
| USB_DDK_NULL_PTR = -5 |  |
| USB_DDK_DEVICE_BUSY = -6 |  |
| USB_DDK_INVALID_OPERATION = 27400002 | 非法操作，在API version 16之前值为-4。 |
| USB_DDK_IO_FAILED = 27400003 |  |
| USB_DDK_TIMEOUT = 27400004 | 传输超时，在API version 16之前值为-7。 |


