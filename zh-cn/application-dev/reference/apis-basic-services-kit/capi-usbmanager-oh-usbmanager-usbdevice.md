# OH_UsbManager_UsbDevice

```c
typedef struct OH_UsbManager_UsbDevice {...} OH_UsbManager_UsbDevice
```

## 概述

定义USB设备的扁平化表示。

**起始版本：** 26.1.0

**相关模块：** [UsbManager](capi-usbmanager.md)

**所在头文件：** [ohusb_manager.h](capi-ohusb-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t busNum | USB设备的总线编号。<br>**起始版本：** 26.1.0 |
| uint8_t devAddress | 设备在总线上的地址。<br>**起始版本：** 26.1.0 |
| const char *name | 设备名称，格式为<总线编号>-<设备地址>。<br>**起始版本：** 26.1.0 |
| const char *manufacturerName | 制造商名称。<br>**起始版本：** 26.1.0 |
| const char *productName | 产品名称。<br>**起始版本：** 26.1.0 |
| const char *version | 设备版本。<br>**起始版本：** 26.1.0 |
| uint16_t vendorId | 厂商ID。<br>**起始版本：** 26.1.0 |
| uint16_t productId | 产品ID。<br>**起始版本：** 26.1.0 |
| uint8_t clazz | 设备类。<br>**起始版本：** 26.1.0 |
| uint8_t subClass | 设备子类。<br>**起始版本：** 26.1.0 |
| uint8_t protocol | 设备协议。<br>**起始版本：** 26.1.0 |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) *configs | 设备配置描述符信息。<br>**起始版本：** 26.1.0 |
| uint32_t configCount | 设备中的配置数量。<br>**起始版本：** 26.1.0 |


