# Scan_PictureScanProgress
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Scan_PictureScanProgress
```

## 概述

表示扫描仪扫描图片的进度

**起始版本：** 12

**相关模块：** [OH_Scan](capi-oh-scan.md)

**所在头文件：** [ohscan.h](capi-ohscan-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| int32_t [progress](#progress) | 图片的扫描进度，从0到100，单位：百分比。 | 
| int32_t [fd](#fd) | 扫描仪文件句柄 | 
| bool [isFinal](#isfinal) | 指示该图像是否为最后扫描的图像。<br>true表示该图像是最后扫描的图像，false表示该图像不是最后扫描的图像。 | 


## 结构体成员变量说明


### progress

```
int32_t Scan_PictureScanProgress::progress
```
**描述**

图片扫描进度，范围0~100。


### fd

```
int32_t Scan_PictureScanProgress::fd
```
**描述**

图片文件句柄。


### isFinal

```
bool Scan_PictureScanProgress::isFinal
```
**描述**

是否有下一张图片。