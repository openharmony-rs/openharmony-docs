# UsbDeviceDescriptor

```c
struct UsbDeviceDescriptor {...}
```

## 概述

标准设备描述符，对应USB协议中Standard Device Descriptor。

<!--Device-struct UsbDeviceDescriptor {...}--><!--Device-struct UsbDeviceDescriptor {...}-End-->

**系统能力：** SystemCapability.Driver.USB.Extension

**起始版本：** 10

**相关模块：** [UsbDdk](capi-driver-development-kit-usbddk.md)

**所在头文件：** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t bLength | 该描述符的大小，单位：Byte。<br><!--Device-uint8_t bLength--><!--Device-uint8_t bLength-End--> |
| uint8_t bDescriptorType | 描述符类型。<br><!--Device-uint8_t bDescriptorType--><!--Device-uint8_t bDescriptorType-End--> |
| uint16_t bcdUSB | USB协议版本号。<br><!--Device-uint16_t bcdUSB--><!--Device-uint16_t bcdUSB-End--> |
| uint8_t bDeviceClass | 由USB标准化组织（USB-IF）分配的设备类代码。<br><!--Device-uint8_t bDeviceClass--><!--Device-uint8_t bDeviceClass-End--> |
| uint8_t bDeviceSubClass | 由USB标准化组织（USB-IF）分配的子类代码，其值由bDeviceClass的值限定。<br><!--Device-uint8_t bDeviceSubClass--><!--Device-uint8_t bDeviceSubClass-End--> |
| uint8_t bDeviceProtocol | 由USB标准化组织（USB-IF）分配的协议代码，其值由bDeviceClass和bDeviceSubClass的值限定。<br><!--Device-uint8_t bDeviceProtocol--><!--Device-uint8_t bDeviceProtocol-End--> |
| uint8_t bMaxPacketSize0 | 端点零（控制端点）的最大包大小，只有8、16、32、64字节是合法的。<br><!--Device-uint8_t bMaxPacketSize0--><!--Device-uint8_t bMaxPacketSize0-End--> |
| uint16_t idVendor | 由USB标准化组织（USB-IF）分配的厂商编号。<br><!--Device-uint16_t idVendor--><!--Device-uint16_t idVendor-End--> |
| uint16_t idProduct | 由厂商分配的产品编号。<br><!--Device-uint16_t idProduct--><!--Device-uint16_t idProduct-End--> |
| uint16_t bcdDevice | 设备版本编号。<br><!--Device-uint16_t bcdDevice--><!--Device-uint16_t bcdDevice-End--> |
| uint8_t iManufacturer | 厂商字符串描述符的索引。<br><!--Device-uint8_t iManufacturer--><!--Device-uint8_t iManufacturer-End--> |
| uint8_t iProduct | 产品字符串描述符的索引。<br><!--Device-uint8_t iProduct--><!--Device-uint8_t iProduct-End--> |
| uint8_t iSerialNumber | 设备序列号字符串描述符的索引。<br><!--Device-uint8_t iSerialNumber--><!--Device-uint8_t iSerialNumber-End--> |
| uint8_t bNumConfigurations | 配置数量。<br><!--Device-uint8_t bNumConfigurations--><!--Device-uint8_t bNumConfigurations-End--> |


