# Usb_NonRootHubArray

```c
typedef struct Usb_NonRootHubArray {...} Usb_NonRootHubArray
```

## 概述

非根集线器数组，用于存放{@link OH_Usb_GetNonRootHubs}接口获取到的非根集线器设备ID数组和数量。开发者申请非根集线器ID数组，使用完结构体后需释放申请的内存，否则会造成资源泄漏。

**起始版本：** 26.0.0

**相关模块：** [UsbDdk](capi-usbddk.md)

**所在头文件：** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t* nonRootHubIds |  |
| uint32_t num |  |


