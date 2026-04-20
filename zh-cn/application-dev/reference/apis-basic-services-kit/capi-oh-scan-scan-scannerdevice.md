# Scan_ScannerDevice
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

```c
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
| -------- | -------- |
| const char* [scannerId](#scannerid) | 扫描仪ID | 
| const char* [manufacturer](#manufacturer) | 扫描仪制造商 | 
| const char* [model](#model) | 扫描仪型号 | 
| const char* [discoverMode](#discovermode) | 扫描仪发现模式 | 
| const char* [serialNumber](#serialnumber) | 扫描仪序列号 | 


## 结构体成员变量说明


### scannerId

```
const char* Scan_ScannerDevice::scannerId
```
**描述**

扫描仪id。


### manufacturer

```
const char* Scan_ScannerDevice::manufacturer
```
**描述**

制造商。


### model

```
const char* Scan_ScannerDevice::model
```
**描述**

设备型号。


### discoverMode

```
const char* Scan_ScannerDevice::discoverMode
```
**描述**

发现模式。


### serialNumber

```
const char* Scan_ScannerDevice::serialNumber
```
**描述**

序列号。