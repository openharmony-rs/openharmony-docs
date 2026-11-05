# USBSerialDDK

## 概述

Provides USB SERIAL DDK types and declares the macros, enumerated variables, and data structures required by the USB SERIAL DDK APIs.

**系统能力：** SystemCapability.Driver.UsbSerial.Extension

**起始版本：** 18

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [usb_serial_api.h](capi-usb-serial-api-h.md) | 声明用于主机侧通过USB接口访问串口设备的USB Serial DDK接口，提供串口读写操作和参数配置的能力，适用于工业控制、嵌入式设备通信等需要通过USB访问串口设备的场景。 |
| [usb_serial_types.h](capi-usb-serial-types-h.md) | 提供USB Serial DDK中的枚举类型与结构体的定义，用于USB串口驱动开发，简化串口设备参数配置、返回码处理和流量控制等操作，提升驱动开发效率。 |
