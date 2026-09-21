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
| -- | -- |
| int32_t progress | 图片的扫描进度，取值范围[0, 100]，单位：百分比。0 表示扫描刚开始，100 表示扫描完成。 |
| int32_t fd | 扫描仪扫描图片的文件描述符，用于读取扫描仪传输的图片数据。仅当 progress 为 100 时，该 fd 为有效文件描述符。 |
| bool isFinal | 指示该图片是否为最后扫描的图片。true 表示是最后扫描的图片，false 表示不是最后扫描的图片。仅当 progress 为 100 时，该 isFinal 为有效标识符。 |


