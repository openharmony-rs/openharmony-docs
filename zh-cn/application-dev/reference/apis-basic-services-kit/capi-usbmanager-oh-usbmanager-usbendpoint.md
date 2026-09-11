# OH_UsbManager_UsbEndpoint

```c
typedef struct OH_UsbManager_UsbEndpoint {...} OH_UsbManager_UsbEndpoint
```

## 概述

定义用于发送或接收数据的USB端点。端点从[OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md)获取。

**起始版本：** 26.1.0

**相关模块：** [UsbManager](capi-usbmanager.md)

**所在头文件：** [ohusb_manager.h](capi-ohusb-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t address | 端点地址。<br>**起始版本：** 26.1.0 |
| uint8_t attributes | 端点属性。<br>**起始版本：** 26.1.0 |
| uint8_t interval | 端点数据传输间隔。对于中断端点，单位为毫秒。对于等时端点，<br>单位取决于设备速度。<br>**起始版本：** 26.1.0 |
| uint16_t maxPacketSize | 端点上数据包的最大大小。单位：字节。<br>**起始版本：** 26.1.0 |
| [OH_UsbManager_RequestDirection](capi-ohusb-manager-h.md#oh_usbmanager_requestdirection) direction | 端点方向。<br>**起始版本：** 26.1.0 |
| uint8_t number | 端点号。<br>**起始版本：** 26.1.0 |
| uint8_t type | 端点类型。<br>**起始版本：** 26.1.0 |
| uint8_t interfaceId | 端点所属接口的唯一标识。<br>**起始版本：** 26.1.0 |


