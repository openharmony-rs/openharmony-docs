# Print_PrintAttributes

```c
typedef struct Print_PrintAttributes {...} Print_PrintAttributes
```

## 概述

表示打印属性结构体，用于配置打印任务的各项属性（如打印范围、纸张尺寸、边距、份数、双面模式、色彩模式、打印方向及打印选项等），适用于需要对打印输出进行精细化控制的场景。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 13

**相关模块：** [Print](capi-others-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Print_Range](capi-print-print-range.md) pageRange | 打印范围。 |
| [Print_PageSize](capi-print-print-pagesize.md) pageSize | 打印纸张尺寸。 |
| [Print_Margin](capi-print-print-margin.md) pageMargin | 以毫米为单位的打印边距。建议根据文档类型和打印机支持的最小边距合理设置，过小的边距可能导致打印内容被裁切。 |
| uint32_t copyNumber | 打印份数。取值原则：大于等于1。 |
| uint32_t duplexMode | 双面模式。单面模式适合单面打印需求，长边翻转双面适合纵向翻页文档（如书籍），短边翻转双面适合横向翻页文档（如日历）。 |
| uint32_t colorMode | 彩色模式。 |
| bool isSequential | 顺序打印。<br>true表示顺序打印，false表示逆序打印。 |
| bool isLandscape | 打印方向（是否横向）。<br>true表示打印方向为横向，false表示打印方向为纵向。 |
| bool hasOption | 打印选项标志。<br>true表示有打印选项（options字段有效），false表示没有打印选项（options字段无效）。 |
| char options[256] | 打印选项，用于传递额外的打印配置参数。仅在hasOption为true时生效，最大长度255个字符。 |


