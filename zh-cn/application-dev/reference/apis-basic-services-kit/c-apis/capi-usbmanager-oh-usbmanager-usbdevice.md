# OH_UsbManager_UsbDevice

```c
typedef struct OH_UsbManager_UsbDevice {...} OH_UsbManager_UsbDevice
```

## 概述

定义USB设备的扁平化表示。

<!--Device-struct OH_UsbManager_UsbDevice {...}--><!--Device-struct OH_UsbManager_UsbDevice {...}-End-->

**系统能力：** SystemCapability.USB.USBManager

**起始版本：** 26.0.1

**相关模块：** [UsbManager](capi-basic-services-kit-usbmanager.md)

**所在头文件：** [ohusb_manager.h](capi-ohusb-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t busNum | USB设备的总线编号。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t busNum--><!--Device-uint8_t busNum-End--> |
| uint8_t devAddress | 设备在总线上的地址。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t devAddress--><!--Device-uint8_t devAddress-End--> |
| const char *name | 设备名称，格式为<总线编号>-<设备地址>。<br>**起始版本：** 26.0.1<br><!--Device-const char *name--><!--Device-const char *name-End--> |
| const char *manufacturerName | 制造商名称。<br>**起始版本：** 26.0.1<br><!--Device-const char *manufacturerName--><!--Device-const char *manufacturerName-End--> |
| const char *productName | 产品名称。<br>**起始版本：** 26.0.1<br><!--Device-const char *productName--><!--Device-const char *productName-End--> |
| const char *version | 设备版本。<br>**起始版本：** 26.0.1<br><!--Device-const char *version--><!--Device-const char *version-End--> |
| uint16_t vendorId | 厂商ID。<br>**起始版本：** 26.0.1<br><!--Device-uint16_t vendorId--><!--Device-uint16_t vendorId-End--> |
| uint16_t productId | 产品ID。<br>**起始版本：** 26.0.1<br><!--Device-uint16_t productId--><!--Device-uint16_t productId-End--> |
| uint8_t clazz | 设备类。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t clazz--><!--Device-uint8_t clazz-End--> |
| uint8_t subClass | 设备子类。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t subClass--><!--Device-uint8_t subClass-End--> |
| uint8_t protocol | 设备协议。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) *configs | 设备配置描述符信息。<br>**起始版本：** 26.0.1<br><!--Device-OH_UsbManager_UsbConfig *configs--><!--Device-OH_UsbManager_UsbConfig *configs-End--> |
| uint32_t configCount | 设备中的配置数量。<br>**起始版本：** 26.0.1<br><!--Device-uint32_t configCount--><!--Device-uint32_t configCount-End--> |


