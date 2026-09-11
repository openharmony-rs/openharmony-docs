# OH_UsbManager_UsbInterface

```c
typedef struct OH_UsbManager_UsbInterface {...} OH_UsbManager_UsbInterface
```

## 概述

定义USB接口。一个[OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md)可以包含多个<br>OH_UsbManager_UsbInterface实例，每个实例提供特定功能。

**起始版本：** 26.1.0

**相关模块：** [UsbManager](capi-usbmanager.md)

**所在头文件：** [ohusb_manager.h](capi-ohusb-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t id | USB接口的唯一标识。<br>**起始版本：** 26.1.0 |
| uint8_t protocol | 接口协议。<br>**起始版本：** 26.1.0 |
| uint8_t clazz | 接口类。<br>**起始版本：** 26.1.0 |
| uint8_t subClass | 接口子类。<br>**起始版本：** 26.1.0 |
| uint8_t alternateSetting | 此USB接口的交替设置编号，由USB接口描述符定义。值0表示<br>默认的交替设置。<br>**起始版本：** 26.1.0 |
| const char *name | 接口名称。<br>**起始版本：** 26.1.0 |
| [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md) *endpoints | 属于该USB接口的端点。<br>**起始版本：** 26.1.0 |
| uint32_t endpointCount | 接口中的端点数量。<br>**起始版本：** 26.1.0 |


