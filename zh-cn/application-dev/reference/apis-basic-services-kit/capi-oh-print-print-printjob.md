# Print_PrintJob
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_PrintJob;
```

## 概述

表示打印任务结构体，用于配置打印任务的各项属性参数（如打印份数、纸张来源、色彩模式、双面模式、分辨率、边距、方向模式、打印质量、文档格式及高级选项等）。开发者通过填充该结构体并向打印模块接口提交以发起打印任务。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *jobName | 任务名称，用于标识和区分不同的打印任务。 |
| uint32_t *fdList | 待打印的文件描述符数组。需与fdListCount配合使用，fdListCount应等于该数组的元素数量。 |
| uint32_t fdListCount | 待打印的文件描述符数量。取值原则：大于等于1，且需与fdList数组长度一致。 |
| char *printerId | 打印机 ID，用于指定目标打印机，可通过相关查询接口（如[OH_Print_QueryPrinterList](capi-ohprint-h.md#OH_Print_QueryPrinterList)）获取有效的打印机 ID。 |
| uint32_t copyNumber | 打印份数。取值原则：大于等于1。 |
| char *paperSource | 纸张来源，用于指定打印纸张的进纸方式。具体可选取值取决于打印机支持的纸张来源选项。 |
| char *mediaType | 介质类型，用于指定打印介质的种类，如普通纸、光面纸、照片纸等。具体可选取值取决于打印机支持的介质类型选项。 |
| char *pageSizeId | 纸张尺寸 ID，用于指定打印纸张的尺寸规格，如 ISO A4、Letter、A3 等。具体可选取值取决于打印机支持的尺寸。 |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) colorMode | 色彩模式。彩色模式适合需要色彩呈现的文档（如图片），黑白模式适合纯文本或草稿打印以节省耗材。 |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) duplexMode | 双面模式。单面模式适合单面打印需求，长边翻转双面适合纵向翻页文档（如书籍），短边翻转双面适合横向翻页文档（如日历）。 |
| [Print_Resolution](capi-oh-print-print-resolution.md) resolution | 以 dpi 为单位的打印分辨率。高分辨率适合图片等精细内容，较低分辨率适合纯文本或草稿打印以节省耗材与打印时间。 |
| [Print_Margin](capi-oh-print-print-margin.md) printMargin | 以毫米为单位的打印边距。 |
| bool borderless | 是否无边距打印。true表示无边距打印，false表示有边距打印。 |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) orientationMode | 方向模式。纵向模式适合常规文档打印，横向模式适合表格、图表等宽幅内容。 |
| [Print_Quality](capi-ohprint-h.md#print_quality) printQuality | 打印质量。高质量模式适合最终输出或正式文档，正常模式适合日常打印，草稿模式适合快速预览以节省耗材。 |
| [Print_DocumentFormat](capi-ohprint-h.md#print_documentformat) documentFormat | 文档的 MIME 媒体类型，如 PDF（application/pdf）、JPEG（image/jpeg）等。 |
| char *advancedOptions | JSON 格式的高级选项。<br>支持的键为以下两种：<br>- **isReverse**：布尔类型，表示是否逆序打印。<br>- **isCollate**：布尔类型，表示是否逐份打印。 |


