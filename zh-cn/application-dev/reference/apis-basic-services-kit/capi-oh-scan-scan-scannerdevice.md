# Scan_ScannerDevice
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

```
typedef struct {...} Scan_ScannerDevice
```

## 概述

表示扫描仪设备信息

**起始版本：** 12

**相关模块：** [OH_Scan](capi-oh-scan.md)

**所在头文件：** [ohscan.h](capi-ohscan-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* scannerId | 扫描仪ID |
| const char* manufacturer | 扫描仪制造商 |
| const char* model | 扫描仪型号 |
| const char* discoverMode | 扫描仪发现模式 |
| const char* serialNumber | 扫描仪序列号 |


