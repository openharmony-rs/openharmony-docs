# Print_PrintJob
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrintJob
```

## 概述

表示打印任务结构体。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *jobName | 任务名称。 |
| uint32_t *fdList | 待打印的文件描述符数组。 |
| uint32_t fdListCount | 待打印的文件描述符数量。 |
| char *printerId | 打印机 ID。 |
| uint32_t copyNumber | 打印份数。 |
| char *paperSource | 纸张来源。 |
| char *mediaType | 介质类型。 |
| char *pageSizeId | 纸张尺寸 ID。 |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) colorMode | 色彩模式。 |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) duplexMode | 双面模式。 |
| [Print_Resolution](capi-oh-print-print-resolution.md) resolution | 以 dpi 为单位的打印分辨率。 |
| [Print_Margin](capi-oh-print-print-margin.md) printMargin | 打印边距。 |
| bool borderless | 无边距。 |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) orientationMode | 方向模式。 |
| [Print_Quality](capi-ohprint-h.md#print_quality) printQuality | 打印质量。 |
| [Print_DocumentFormat](capi-ohprint-h.md#print_documentformat) documentFormat | 文档格式。 |
| char *advancedOptions | JSON 格式的高级选项。<br>支持的键包括：<br>- **isReverse**：布尔类型，表示是否逆序打印。<br>- **isCollate**：布尔类型，表示是否逐份打印。 |


