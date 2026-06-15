# Print_PrinterInfo
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @Q-haosu-->
 <!--Tester: @Q-haosu-->
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrinterInfo
```

## 概述

表示打印机信息。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Print_PrinterState](capi-ohprint-h.md#print_printerstate) printerState | 打印机状态。 |
| [Print_PrinterCapability](capi-oh-print-print-printercapability.md) capability | 打印机能力。 |
| [Print_DefaultValue](capi-oh-print-print-defaultvalue.md) defaultValue | 打印机当前属性。 |
| bool isDefaultPrinter | 默认打印机。 |
| char *printerId | 打印机 ID。 |
| char *printerName | 打印机名称。 |
| char *description | 打印机描述。 |
| char *location | 打印机位置。 |
| char *makeAndModel | 打印机品牌和型号信息。 |
| char *printerUri | 打印机 URI。 |
| char *detailInfo | JSON 格式的详细信息。<br>支持的键包括：<br>- **printerAlias**：string类型，表示打印机别名，**起始版本：** 24。<br>- **vendorId**：int类型，表示USB打印机的VID，**起始版本：** 12。<br>- **productId**：int类型，表示USB打印机的PID，**起始版本：** 12。<br>- **protocol**：string数组，表示探测到的打印机支持的协议列表，**起始版本：** 24。<br>- **ipp**：string类型，表示探测到的IPP协议对应的打印机URI，**起始版本：** 24。<br>- **ipps**：string类型，表示探测到的IPPS协议对应的打印机URI，**起始版本：** 24。<br>- **lpd**：string类型，表示探测到的LPD协议对应的打印机URI，**起始版本：** 24。<br>- **socket**：string类型，表示探测到的Socket协议对应的打印机URI，**起始版本：** 24。 |

