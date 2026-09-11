# OH_UsbManager_UsbConfig

```c
typedef struct OH_UsbManager_UsbConfig {...} OH_UsbManager_UsbConfig
```

## 概述

定义USB配置。一个[OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md)可以包含多个<br>**OH_UsbManager_UsbConfig**实例。

**起始版本：** 26.1.0

**相关模块：** [UsbManager](capi-usbmanager.md)

**所在头文件：** [ohusb_manager.h](capi-ohusb-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t id | USB配置的唯一标识。<br>**起始版本：** 26.1.0 |
| uint8_t attributes | 配置属性。<br>**起始版本：** 26.1.0 |
| uint8_t maxPower | 最大功耗。单位：mA。<br>**起始版本：** 26.1.0 |
| const char *name | 配置名称，可以为空。<br>**起始版本：** 26.1.0 |
| bool isRemoteWakeup | 是否支持远程唤醒。true表示支持远程唤醒；false表示不支持。<br>**起始版本：** 26.1.0 |
| bool isSelfPowered | 是否支持独立供电。true表示支持独立供电；false表示不支持。<br>**起始版本：** 26.1.0 |
| [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md) *interfaces | 支持的接口属性。<br>**起始版本：** 26.1.0 |
| uint32_t interfaceCount | 配置中的接口数量。<br>**起始版本：** 26.1.0 |


