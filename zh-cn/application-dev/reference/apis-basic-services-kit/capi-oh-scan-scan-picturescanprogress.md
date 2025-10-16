# Scan_PictureScanProgress
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

## 概述

表示扫描仪扫描图片的进度

**起始版本：** 12

**相关模块：** [OH_Scan](capi-oh-scan.md)

**所在头文件：** [ohscan.h](capi-ohscan-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t progress | 图片进度，从0到100 |
| int32_t fd | 扫描仪文件句柄 |
| bool isFinal | 指示该图像是否为最后扫描的图像 |


