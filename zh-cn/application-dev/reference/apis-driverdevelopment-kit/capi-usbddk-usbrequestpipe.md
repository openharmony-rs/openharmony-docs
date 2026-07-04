# UsbRequestPipe
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct UsbRequestPipe {...} __attribute__((aligned(8))) UsbRequestPipe
```

## 概述

请求管道，是USB数据传输请求的抽象。

**起始版本：** 10

**相关模块：** [UsbDdk](capi-usbddk.md)

**所在头文件：** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t interfaceHandle | 接口操作句柄。 |
| uint8_t endpoint | 要通信的端点的地址。 |
| uint32_t timeout | 超时时间，单位是毫秒。值为0表示等待直到操作完成。 |


