# UsbConfigDescriptor

```c
struct UsbConfigDescriptor {...}
```

## 概述

标准配置描述符，对应USB协议中Standard Configuration Descriptor。

<!--Device-struct UsbConfigDescriptor {...}--><!--Device-struct UsbConfigDescriptor {...}-End-->

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
| uint16_t wTotalLength | 该配置描述符的总长度，包含配置、接口、端点和特定于类或供应商的描述符，单位：Byte。<br><!--Device-uint16_t wTotalLength--><!--Device-uint16_t wTotalLength-End--> |
| uint8_t bNumInterfaces | 该配置所支持的接口数量。<br><!--Device-uint8_t bNumInterfaces--><!--Device-uint8_t bNumInterfaces-End--> |
| uint8_t bConfigurationValue | 用于设置配置的参数，用来选择当前配置。<br><!--Device-uint8_t bConfigurationValue--><!--Device-uint8_t bConfigurationValue-End--> |
| uint8_t iConfiguration | 描述该配置的字符串描述符的索引。<br><!--Device-uint8_t iConfiguration--><!--Device-uint8_t iConfiguration-End--> |
| uint8_t bmAttributes | 配置属性，包含供电模式、远程唤醒等。<br><!--Device-uint8_t bmAttributes--><!--Device-uint8_t bmAttributes-End--> |
| uint8_t bMaxPower | 总线供电的USB设备的最大功耗，以2mA为单位。<br><!--Device-uint8_t bMaxPower--><!--Device-uint8_t bMaxPower-End--> |


