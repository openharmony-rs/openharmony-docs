# Print_PrinterCapability
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_PrinterCapability;
```

## 概述

表示打印机能力，包含支持的色彩模式、双面打印模式、纸张尺寸、介质类型、打印质量、纸张来源、份数、分辨率、打印方向模式及高级能力等属性，适用于需要查询或匹配打印机能力的场景，帮助开发者根据打印机能力进行打印任务配置和适配。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) *supportedColorModes | 支持的色彩模式数组，数组长度由 supportedColorModesCount 决定。 |
| uint32_t supportedColorModesCount | 支持的色彩模式数量，与 supportedColorModes 数组实际元素数一致。 |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) *supportedDuplexModes | 支持的双面打印模式数组，数组长度由 supportedDuplexModesCount 决定。 |
| uint32_t supportedDuplexModesCount | 支持的双面打印模式数量，与 supportedDuplexModes 数组实际元素数一致。 |
| [Print_PageSize](capi-oh-print-print-pagesize.md) *supportedPageSizes | 支持的打印纸张尺寸数组，数组长度由 supportedPageSizesCount 决定。 |
| uint32_t supportedPageSizesCount | 支持的打印纸张尺寸数量，与 supportedPageSizes 数组实际元素数一致。 |
| char *supportedMediaTypes | 支持的打印介质类型，以 JSON 数组格式字符串表示，具体取值由打印机决定。 |
| [Print_Quality](capi-ohprint-h.md#print_quality) *supportedQualities | 支持的打印质量数组，数组长度由 supportedQualitiesCount 决定。 |
| uint32_t supportedQualitiesCount | 支持的打印质量数量，与 supportedQualities 数组实际元素数一致。 |
| char *supportedPaperSources | 支持的纸张来源，以 JSON 数组格式字符串表示，具体取值由打印机决定。 |
| uint32_t supportedCopies | 支持的份数，取值由打印机能力决定。 |
| [Print_Resolution](capi-oh-print-print-resolution.md) *supportedResolutions | 支持的打印机分辨率数组，数组长度由 supportedResolutionsCount 决定。 |
| uint32_t supportedResolutionsCount | 支持的打印机分辨率数量，与 supportedResolutions 数组实际元素数一致。 |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) *supportedOrientations | 支持的打印方向模式数组，数组长度由 supportedOrientationsCount 决定。 |
| uint32_t supportedOrientationsCount | 支持的打印方向模式数量，与 supportedOrientations 数组实际元素数一致。 |
| char *advancedCapability | 高级能力，以 JSON 格式表示，用于描述不属于上述标准能力字段的额外打印机特性，具体取值由打印机决定。 |


