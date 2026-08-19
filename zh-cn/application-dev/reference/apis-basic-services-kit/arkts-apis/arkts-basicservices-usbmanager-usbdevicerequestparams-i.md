# USBDeviceRequestParams

控制传输参数。

**起始版本：** 23

<!--Device-usbManager-interface USBDeviceRequestParams--><!--Device-usbManager-interface USBDeviceRequestParams-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## bRequest

```TypeScript
bRequest: int
```

请求类型，用于指定具体的USB控制请求命令（如获取描述符，设置地址等）。

**类型：** int

**起始版本：** 23

<!--Device-USBDeviceRequestParams-bRequest: int--><!--Device-USBDeviceRequestParams-bRequest: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## bmRequestType

```TypeScript
bmRequestType: int
```

请求控制类型，用于指定控制传输的方向和类型，取值需遵循USB协议规范，常见取值示例：0x00（标准请求，主机向设备）、0x20（类请求，主机向设备）、0x40（厂商请求，主机向设备）、0x80（标准请求，设备向主机）。

**类型：** int

**起始版本：** 23

<!--Device-USBDeviceRequestParams-bmRequestType: int--><!--Device-USBDeviceRequestParams-bmRequestType: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## data

```TypeScript
data: Uint8Array
```

用于写入或读取的缓冲区，数组长度对应wLength参数指定的数据字节数。用于控制传输时发送或接收数据。

**类型：** Uint8Array

**起始版本：** 23

<!--Device-USBDeviceRequestParams-data: Uint8Array--><!--Device-USBDeviceRequestParams-data: Uint8Array-End-->

**系统能力：** SystemCapability.USB.USBManager

## wIndex

```TypeScript
wIndex: int
```

请求参数wValue对应的索引值，用于指定控制请求的目标接口或端点。

**类型：** int

**起始版本：** 23

<!--Device-USBDeviceRequestParams-wIndex: int--><!--Device-USBDeviceRequestParams-wIndex: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## wLength

```TypeScript
wLength: int
```

请求数据的长度，用于指定控制传输中期望接收或发送的数据字节数。

**类型：** int

**起始版本：** 23

<!--Device-USBDeviceRequestParams-wLength: int--><!--Device-USBDeviceRequestParams-wLength: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## wValue

```TypeScript
wValue: int
```

请求参数，用于向USB设备传递控制请求所需的参数内容。

**类型：** int

**起始版本：** 23

<!--Device-USBDeviceRequestParams-wValue: int--><!--Device-USBDeviceRequestParams-wValue: int-End-->

**系统能力：** SystemCapability.USB.USBManager

