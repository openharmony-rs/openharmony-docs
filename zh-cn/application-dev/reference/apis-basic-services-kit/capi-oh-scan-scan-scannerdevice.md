# Scan_ScannerDevice
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Scan_ScannerDevice;
```

## 概述

Scan_ScannerDevice表示扫描仪设备信息，包含扫描仪 ID、制造商、型号、发现模式和序列号等属性，用于在扫描仪发现流程中获取设备详情，开发者可通过扫描仪发现相关接口获取该结构体以选择目标扫描仪设备进行扫描操作。相关模块设计逻辑请参见[OH_Scan](capi-oh-scan.md)。

**起始版本：** 12

**相关模块：** [OH_Scan](capi-oh-scan.md)

**所在头文件：** [ohscan.h](capi-ohscan-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* scannerId | 扫描仪 ID |
| const char* manufacturer | 扫描仪制造商 |
| const char* model | 扫描仪型号 |
| const char* discoverMode | 扫描仪发现模式，表示扫描仪设备被系统发现的方式。
| const char* serialNumber | 扫描仪序列号 |


