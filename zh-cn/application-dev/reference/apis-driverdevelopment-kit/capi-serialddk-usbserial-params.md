# UsbSerial_Params
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct UsbSerial_Params {...} __attribute__((aligned(8))) UsbSerial_Params
```

## 概述

定义USB Serial DDK使用的USB串口参数。

**起始版本：** 18

**相关模块：** [USBSerialDDK](capi-serialddk.md)

**所在头文件：** [usb_serial_types.h](capi-usb-serial-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t baudRate | 波特率，单位为波特。 |
| uint8_t nDataBits | 数据位比特数。 |
| uint8_t nStopBits | 停止位比特数。 |
| uint8_t parity | 校验参数设置（0：无校验；1：奇校验；2：偶校验；3：1校验；4：0校验；）。 |


