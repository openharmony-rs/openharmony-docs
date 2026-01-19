# Print_DefaultValue
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_DefaultValue
```

## 概述

表示当前属性。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) defaultColorMode | 默认色彩模式。 |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) defaultDuplexMode | 默认双面模式。 |
| char *defaultMediaType | 默认介质类型。 |
| char *defaultPageSizeId | 默认纸张尺寸 ID。 |
| [Print_Margin](capi-oh-print-print-margin.md) defaultMargin | 默认边距。 |
| char *defaultPaperSource | 默认纸张来源。 |
| [Print_Quality](capi-ohprint-h.md#print_quality) defaultPrintQuality | 默认打印质量。 |
| uint32_t defaultCopies | 默认份数。 |
| [Print_Resolution](capi-oh-print-print-resolution.md) defaultResolution | 默认打印机分辨率。 |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) defaultOrientation | 默认方向。 |
| char *otherDefaultValues | JSON 格式的其他默认值。 |


