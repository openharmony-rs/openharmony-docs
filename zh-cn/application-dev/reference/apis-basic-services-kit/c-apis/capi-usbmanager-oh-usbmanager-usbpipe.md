# OH_UsbManager_UsbPipe

```c
typedef struct OH_UsbManager_UsbPipe {...} OH_UsbManager_UsbPipe
```

## 概述

定义用于与已打开设备通信的USB设备管道。

**起始版本：** 26.1.0

**相关模块：** [UsbManager](capi-usbmanager.md)

**所在头文件：** [ohusb_manager.h](capi-ohusb-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t busNum | 所连接设备的总线编号。<br>**起始版本：** 26.1.0 |
| uint8_t devAddress | 所连接设备的设备地址。<br>**起始版本：** 26.1.0 |


