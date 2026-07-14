# Usb_NonRootHubArray

```c
typedef struct Usb_NonRootHubArray {...} Usb_NonRootHubArray
```

## 概述

非根集线器列表，用于存放{@link OH_Usb_GetNonRootHubs}接口获取到的非根集线器设备ID列表和数量。

**起始版本：** 26.0.0

**相关模块：** [UsbDdk](capi-usbddk.md)

**所在头文件：** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t* nonRootHubIds |  |
| uint32_t num |  |


