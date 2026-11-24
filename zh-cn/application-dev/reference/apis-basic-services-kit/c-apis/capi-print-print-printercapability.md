# Print_PrinterCapability

```c
typedef struct Print_PrinterCapability {...} Print_PrinterCapability
```

## 概述

表示打印机能力，包含支持的色彩模式、双面打印模式、纸张尺寸、介质类型、打印质量、纸张来源、份数、分辨率、打印方向模式及高级能力等属性，适用于需要查询或匹配打印机能力的场景，帮助开发者根据打印机能力进行打印任务配置和适配。

<!--Device-typedef struct Print_PrinterCapability {...} Print_PrinterCapability--><!--Device-typedef struct Print_PrinterCapability {...} Print_PrinterCapability-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**相关模块：** [Print](capi-basic-services-kit-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) *supportedColorModes | 支持的色彩模式数组，数组长度由supportedColorModesCount决定。<br><!--Device-Print_ColorMode *supportedColorModes--><!--Device-Print_ColorMode *supportedColorModes-End--> |
| uint32_t supportedColorModesCount | 支持的色彩模式数量，与supportedColorModes数组实际元素数一致。<br><!--Device-uint32_t supportedColorModesCount--><!--Device-uint32_t supportedColorModesCount-End--> |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) *supportedDuplexModes | 支持的双面打印模式数组，数组长度由supportedDuplexModesCount决定。<br><!--Device-Print_DuplexMode *supportedDuplexModes--><!--Device-Print_DuplexMode *supportedDuplexModes-End--> |
| uint32_t supportedDuplexModesCount | 支持的双面打印模式数量，与supportedDuplexModes数组实际元素数一致。<br><!--Device-uint32_t supportedDuplexModesCount--><!--Device-uint32_t supportedDuplexModesCount-End--> |
| [Print_PageSize](capi-print-print-pagesize.md) *supportedPageSizes | 支持的打印纸张尺寸数组，数组长度由supportedPageSizesCount决定。<br><!--Device-Print_PageSize *supportedPageSizes--><!--Device-Print_PageSize *supportedPageSizes-End--> |
| uint32_t supportedPageSizesCount | 支持的打印纸张尺寸数量，与supportedPageSizes数组实际元素数一致。<br><!--Device-uint32_t supportedPageSizesCount--><!--Device-uint32_t supportedPageSizesCount-End--> |
| char *supportedMediaTypes | 支持的打印介质类型，以JSON数组格式字符串表示，具体取值由打印机决定。<br><!--Device-char *supportedMediaTypes--><!--Device-char *supportedMediaTypes-End--> |
| [Print_Quality](capi-ohprint-h.md#print_quality) *supportedQualities | 支持的打印质量数组，数组长度由supportedQualitiesCount决定。<br><!--Device-Print_Quality *supportedQualities--><!--Device-Print_Quality *supportedQualities-End--> |
| uint32_t supportedQualitiesCount | 支持的打印质量数量，与supportedQualities数组实际元素数一致。<br><!--Device-uint32_t supportedQualitiesCount--><!--Device-uint32_t supportedQualitiesCount-End--> |
| char *supportedPaperSources | 支持的纸张来源，以JSON数组格式字符串表示，具体取值由打印机决定。<br><!--Device-char *supportedPaperSources--><!--Device-char *supportedPaperSources-End--> |
| uint32_t supportedCopies | 支持的份数，取值由打印机能力决定。<br><!--Device-uint32_t supportedCopies--><!--Device-uint32_t supportedCopies-End--> |
| [Print_Resolution](capi-print-print-resolution.md) *supportedResolutions | 支持的打印机分辨率数组，数组长度由supportedResolutionsCount决定。<br><!--Device-Print_Resolution *supportedResolutions--><!--Device-Print_Resolution *supportedResolutions-End--> |
| uint32_t supportedResolutionsCount | 支持的打印机分辨率数量，与supportedResolutions数组实际元素数一致。<br><!--Device-uint32_t supportedResolutionsCount--><!--Device-uint32_t supportedResolutionsCount-End--> |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) *supportedOrientations | 支持的打印方向模式数组，数组长度由supportedOrientationsCount决定。<br><!--Device-Print_OrientationMode *supportedOrientations--><!--Device-Print_OrientationMode *supportedOrientations-End--> |
| uint32_t supportedOrientationsCount | 支持的打印方向模式数量，与supportedOrientations数组实际元素数一致。<br><!--Device-uint32_t supportedOrientationsCount--><!--Device-uint32_t supportedOrientationsCount-End--> |
| char *advancedCapability | 高级能力，以JSON对象格式字符串表示，用于描述不属于上述标准能力字段的打印机特性，JSON对象的具体字段名和取值由打印机决定，开发者需根据实际返回的JSON内容进行解析。<br><!--Device-char *advancedCapability--><!--Device-char *advancedCapability-End--> |


