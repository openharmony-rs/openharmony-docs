# ohprint.h
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

## 概述

声明用于发现和连接打印机、通过打印机打印文件、查询已添加打印机列表及其内部打印机信息等功能的 API。

**引用文件：** <BasicServicesKit/ohprint.h>

**库：** libohprint.so

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

## 汇总

### 结构体

| 名称                                                         | typedef关键字           | 描述                            |
| ------------------------------------------------------------ | ----------------------- | ------------------------------- |
| [Print_StringList](capi-oh-print-print-stringlist.md)        | Print_StringList        | 表示字符串列表。                |
| [Print_Property](capi-oh-print-print-property.md)            | Print_Property          | 表示打印机属性。                |
| [Print_PropertyList](capi-oh-print-print-propertylist.md)    | Print_PropertyList      | 打印机属性列表。                |
| [Print_Resolution](capi-oh-print-print-resolution.md)        | Print_Resolution        | 表示以 dpi 为单位的打印分辨率。 |
| [Print_Margin](capi-oh-print-print-margin.md)                | Print_Margin            | 表示打印边距。                  |
| [Print_PageSize](capi-oh-print-print-pagesize.md)            | Print_PageSize          | 表示纸张尺寸信息。              |
| [Print_PrinterCapability](capi-oh-print-print-printercapability.md) | Print_PrinterCapability | 表示打印机能力。                |
| [Print_DefaultValue](capi-oh-print-print-defaultvalue.md)    | Print_DefaultValue      | 表示当前属性。                  |
| [Print_PrinterInfo](capi-oh-print-print-printerinfo.md)      | Print_PrinterInfo       | 表示打印机信息。                |
| [Print_PrintJob](capi-oh-print-print-printjob.md)            | Print_PrintJob          | 表示打印任务结构体。            |
| [Print_Range](capi-oh-print-print-range.md)                  | Print_Range             | 表示打印范围结构体。            |
| [Print_PrintAttributes](capi-oh-print-print-printattributes.md) | Print_PrintAttributes   | 表示打印属性结构体。            |
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) | Print_PrintDocCallback  | 表示打印文档状态回调结构体。    |

### 枚举

| 名称                                                  | typedef关键字            | 描述                         |
| ----------------------------------------------------- | ------------------------ | ---------------------------- |
| [Print_ErrorCode](#print_errorcode)                   | Print_ErrorCode          | 定义错误码。                 |
| [Print_PrinterState](#print_printerstate)             | Print_PrinterState       | 表示打印机状态。             |
| [Print_DiscoveryEvent](#print_discoveryevent)         | Print_DiscoveryEvent     | 表示打印机发现事件。         |
| [Print_PrinterEvent](#print_printerevent)             | Print_PrinterEvent       | 表示打印机变更事件。         |
| [Print_DuplexMode](#print_duplexmode)                 | Print_DuplexMode         | 表示双面打印模式。           |
| [Print_ColorMode](#print_colormode)                   | Print_ColorMode          | 表示色彩模式。               |
| [Print_OrientationMode](#print_orientationmode)       | Print_OrientationMode    | 表示方向模式。               |
| [Print_Quality](#print_quality)                       | Print_Quality            | 表示打印质量。               |
| [Print_DocumentFormat](#print_documentformat)         | Print_DocumentFormat     | 表示文档的 MIME 媒体类型。   |
| [Print_JobDocAdapterState](#print_jobdocadapterstate) | Print_JobDocAdapterState | 表示打印任务文档适配器状态。 |

### 函数

| 名称                                                         | typedef关键字                  | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------ | ------------------------------------------------------------ |
| [typedef void(\*Print_WriteResultCallback)(const char *jobId, uint32_t code)](#print_writeresultcallback) | Print_WriteResultCallback      | 写文件结果回调。                                             |
| [typedef void(\*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)](#print_onstartlayoutwrite) | Print_OnStartLayoutWrite       | 打印开始布局回调。                                           |
| [typedef void(\*Print_OnJobStateChanged)(const char *jobId, uint32_t state)](#print_onjobstatechanged) | Print_OnJobStateChanged        | 打印任务状态回调。                                           |
| [typedef void (\*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)](#print_printerdiscoverycallback) | Print_PrinterDiscoveryCallback | 打印机发现回调。                                             |
| [typedef void (\*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)](#print_printerchangecallback) | Print_PrinterChangeCallback    | 打印机变更回调。                                             |
| [Print_ErrorCode OH_Print_Init()](#oh_print_init)            | -                              | 此 API 检查并拉起打印服务，初始化打印客户端，并建立与打印服务的连接。 |
| [Print_ErrorCode OH_Print_Release()](#oh_print_release)      | -                              | 此 API 关闭与打印服务的连接，解散先前的回调，并释放打印客户端资源。 |
| [Print_ErrorCode OH_Print_StartPrinterDiscovery(Print_PrinterDiscoveryCallback callback)](#oh_print_startprinterdiscovery) | -                              | 此 API 开始发现打印机。                                      |
| [Print_ErrorCode OH_Print_StopPrinterDiscovery()](#oh_print_stopprinterdiscovery) | -                              | 此 API 停止发现打印机。                                      |
| [Print_ErrorCode OH_Print_ConnectPrinter(const char *printerId)](#oh_print_connectprinter) | -                              | 此 API 使用打印机 ID 连接打印机。                            |
| [Print_ErrorCode OH_Print_StartPrintJob(const Print_PrintJob *printJob)](#oh_print_startprintjob) | -                              | 此 API 开始发起打印任务。                                    |
| [Print_ErrorCode OH_Print_RegisterPrinterChangeListener(Print_PrinterChangeCallback callback)](#oh_print_registerprinterchangelistener) | -                              | 此 API 注册打印机变更回调。                                  |
| [void OH_Print_UnregisterPrinterChangeListener()](#oh_print_unregisterprinterchangelistener) | -                              | 此 API 注销打印机变更回调。                                  |
| [Print_ErrorCode OH_Print_QueryPrinterList(Print_StringList *printerIdList)](#oh_print_queryprinterlist) | -                              | 此 API 查询已添加的打印机列表。                              |
| [void OH_Print_ReleasePrinterList(Print_StringList *printerIdList)](#oh_print_releaseprinterlist) | -                              | 此 API 释放用于查询的打印机列表内存。                        |
| [Print_ErrorCode OH_Print_QueryPrinterInfo(const char *printerId, Print_PrinterInfo **printerInfo)](#oh_print_queryprinterinfo) | -                              | 此 API 根据打印机 ID 查询打印机信息。                        |
| [void OH_Print_ReleasePrinterInfo(Print_PrinterInfo *printerInfo)](#oh_print_releaseprinterinfo) | -                              | 此 API 释放用于查询的打印机信息内存。                        |
| [Print_ErrorCode OH_Print_LaunchPrinterManager()](#oh_print_launchprintermanager) | -                              | 此 API 启动系统的打印机管理窗口。                            |
| [Print_ErrorCode OH_Print_QueryPrinterProperties(const char *printerId, const Print_StringList *propertyKeyList, Print_PropertyList *propertyList)](#oh_print_queryprinterproperties) | -                              | 此 API 根据属性关键字列表查询对应的打印机属性值。            |
| [void OH_Print_ReleasePrinterProperties(Print_PropertyList *propertyList)](#oh_print_releaseprinterproperties) | -                              | 此 API 释放用于查询的属性列表内存。                          |
| [Print_ErrorCode OH_Print_UpdatePrinterProperties(const char *printerId, const Print_PropertyList *propertyList)](#oh_print_updateprinterproperties) | -                              | 此 API 根据属性键值对列表设置打印机属性。                    |
| [Print_ErrorCode OH_Print_RestorePrinterProperties(const char *printerId, const Print_StringList *propertyKeyList)](#oh_print_restoreprinterproperties) | -                              | 此 API 根据属性关键字列表将打印机属性恢复为默认设置。        |
| [Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)](#oh_print_startprintbynative) | -                              | 此 API 提供启动打印对话框的能力。                            |

## 枚举类型说明

### Print_ErrorCode

```c
enum Print_ErrorCode
```

**描述**

定义错误码。

**起始版本：** 12

| 枚举项                                   | 描述                    |
| ---------------------------------------- | ----------------------- |
| PRINT_ERROR_NONE = 0                     | 操作成功。       |
| PRINT_ERROR_NO_PERMISSION = 201          | 权限校验失败。   |
| PRINT_ERROR_INVALID_PARAMETER = 401      | 参数无效。       |
| PRINT_ERROR_GENERIC_FAILURE = 24300001   | 通用内部错误。   |
| PRINT_ERROR_RPC_FAILURE = 24300002       | RPC 通信错误。   |
| PRINT_ERROR_SERVER_FAILURE = 24300003    | 服务端错误。     |
| PRINT_ERROR_INVALID_EXTENSION = 24300004 | 无效的扩展。     |
| PRINT_ERROR_INVALID_PRINTER = 24300005   | 无效的打印机。   |
| PRINT_ERROR_INVALID_PRINT_JOB = 24300006 | 无效的打印任务。 |
| PRINT_ERROR_FILE_IO = 24300007           | 读写文件失败。   |
| PRINT_ERROR_UNKNOWN = 24300255           | 未知错误。       |

### Print_PrinterState

```c
enum Print_PrinterState
```

**描述**

表示打印机状态。

**起始版本：** 12

| 枚举项              | 描述           |
| ------------------- | -------------- |
| PRINTER_IDLE        | 打印机空闲。   |
| PRINTER_BUSY        | 打印机忙。     |
| PRINTER_UNAVAILABLE | 打印机不可用。 |

### Print_DiscoveryEvent

```c
enum Print_DiscoveryEvent
```

**描述**

表示打印机发现事件。

**起始版本：** 12

| 枚举项                 | 描述             |
| ---------------------- | ---------------- |
| PRINTER_DISCOVERED = 0 | 发现打印机。     |
| PRINTER_LOST = 1       | 丢失打印机。     |
| PRINTER_CONNECTING = 2 | 正在连接打印机。 |
| PRINTER_CONNECTED = 3  | 打印机已连接。   |

### Print_PrinterEvent

```c
enum Print_PrinterEvent
```

**描述**

表示打印机变更事件。

**起始版本：** 12

| 枚举项                    | 描述               |
| ------------------------- | ------------------ |
| PRINTER_ADDED = 0         | 打印机已添加。     |
| PRINTER_DELETED = 1       | 打印机已删除。     |
| PRINTER_STATE_CHANGED = 2 | 打印机状态已变更。 |
| PRINTER_INFO_CHANGED = 3  | 打印机信息已变更。 |

### Print_DuplexMode

```c
enum Print_DuplexMode
```

**描述**

表示双面打印模式。

**起始版本：** 12

| 枚举项                               | 描述               |
| ------------------------------------ | ------------------ |
| DUPLEX_MODE_ONE_SIDED = 0            | 单面模式。         |
| DUPLEX_MODE_TWO_SIDED_LONG_EDGE = 1  | 长边翻转双面模式。 |
| DUPLEX_MODE_TWO_SIDED_SHORT_EDGE = 2 | 短边翻转双面模式。 |

### Print_ColorMode

```c
enum Print_ColorMode
```

**描述**

表示色彩模式。

**起始版本：** 12

| 枚举项                    | 描述       |
| ------------------------- | ---------- |
| COLOR_MODE_MONOCHROME = 0 | 黑白模式。 |
| COLOR_MODE_COLOR = 1      | 彩色模式。 |
| COLOR_MODE_AUTO = 2       | 自动模式。 |

### Print_OrientationMode

```c
enum Print_OrientationMode
```

**描述**

表示方向模式。

**起始版本：** 12

| 枚举项                                 | 描述           |
| -------------------------------------- | -------------- |
| ORIENTATION_MODE_PORTRAIT = 0          | 纵向模式。     |
| ORIENTATION_MODE_LANDSCAPE = 1         | 横向模式。     |
| ORIENTATION_MODE_REVERSE_LANDSCAPE = 2 | 反向横向模式。 |
| ORIENTATION_MODE_REVERSE_PORTRAIT = 3  | 反向纵向模式。 |
| ORIENTATION_MODE_NONE = 4              | 未指定。       |

### Print_Quality

```c
enum Print_Quality
```

**描述**

表示打印质量。

**起始版本：** 12

| 枚举项                   | 描述         |
| ------------------------ | ------------ |
| PRINT_QUALITY_DRAFT = 3  | 草稿质量模式 |
| PRINT_QUALITY_NORMAL = 4 | 正常质量模式 |
| PRINT_QUALITY_HIGH = 5   | 高质量模式   |

### Print_DocumentFormat

```c
enum Print_DocumentFormat
```

**描述**

表示文档的 MIME 媒体类型。

**起始版本：** 12

| 枚举项                     | 描述                                  |
| -------------------------- | ------------------------------------- |
| DOCUMENT_FORMAT_AUTO       | MIME 类型：application/octet-stream。 |
| DOCUMENT_FORMAT_JPEG       | MIME 类型：image/jpeg。               |
| DOCUMENT_FORMAT_PDF        | MIME 类型：application/pdf。          |
| DOCUMENT_FORMAT_POSTSCRIPT | MIME 类型：application/postscript。   |
| DOCUMENT_FORMAT_TEXT       | MIME 类型：text/plain。               |

### Print_JobDocAdapterState

```c
enum Print_JobDocAdapterState
```

**描述**

表示打印任务文档适配器状态。

**起始版本：** 13

| 枚举项                                                     | 描述                               |
| ---------------------------------------------------------- | ---------------------------------- |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY = 0              | 打印任务预览能力销毁。             |
| PRINT_DOC_ADAPTER_PRINT_TASK_SUCCEED = 1                   | 打印任务成功。                     |
| PRINT_DOC_ADAPTER_PRINT_TASK_FAIL = 2                      | 打印任务失败。                     |
| PRINT_DOC_ADAPTER_PRINT_TASK_CANCEL = 3                    | 打印任务取消。                     |
| PRINT_DOC_ADAPTER_PRINT_TASK_BLOCK = 4                     | 打印任务阻塞。                     |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_CANCELED = 5 | 因取消导致的打印任务预览能力销毁。 |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_STARTED = 6  | 因启动导致的打印任务预览能力销毁。 |


## 函数说明

### Print_WriteResultCallback()

```c
typedef void(*Print_WriteResultCallback)(const char *jobId, uint32_t code)
```

**描述**

写文件结果回调。

**起始版本：** 13

**参数：**

| 参数项              | 描述            |
| ------------------- | --------------- |
| (const char \*jobId | 打印任务的 ID。 |
| uint32_t code       | 写文件的结果。  |

### Print_OnStartLayoutWrite()

```c
typedef void(*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)
```

**描述**

打印开始布局回调。

**起始版本：** 13

**参数：**

| 参数项                                                       | 描述                 |
| ------------------------------------------------------------ | -------------------- |
| (const char \*jobId                                          | 打印任务的 ID。      |
| uint32_t fd                                                  | 待写入的文件描述符。 |
| [const Print_PrintAttributes](capi-oh-print-print-printattributes.md) \*oldAttrs | 上一次的属性。       |
| [const Print_PrintAttributes](capi-oh-print-print-printattributes.md) \*newAttrs | 当前的属性。         |
| [Print_WriteResultCallback](capi-ohprint-h.md#print_writeresultcallback) writeCallback | 写文件结果回调。     |

### Print_OnJobStateChanged()

```c
typedef void(*Print_OnJobStateChanged)(const char *jobId, uint32_t state)
```

**描述**

打印任务状态回调。

**起始版本：** 13

**参数：**

| 参数项              | 描述                 |
| ------------------- | -------------------- |
| (const char \*jobId | 打印任务的 ID。      |
| uint32_t state      | 当前打印任务的状态。 |

### Print_PrinterDiscoveryCallback()

```c
typedef void (*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)
```

**描述**

打印机发现回调。

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                         |
| ------------------------------------------------------------ | ---------------------------- |
| (Print_DiscoveryEvent event                                  | 打印机发现过程中的发现事件。 |
| [const Print_PrinterInfo](capi-oh-print-print-printerinfo.md) \*printerInfo | 发现事件发生时的打印机信息。 |

### Print_PrinterChangeCallback()

```c
typedef void (*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)
```

**描述**

打印机变更回调。

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                               |
| ------------------------------------------------------------ | ---------------------------------- |
| (Print_PrinterEvent event                                    | 打印服务运行期间的打印机变更事件。 |
| [const Print_PrinterInfo](capi-oh-print-print-printerinfo.md) \*printerInfo | 变更事件发生时的打印机信息。       |

### OH_Print_Init()

```c
Print_ErrorCode OH_Print_Init()
```

**描述**

此 API 检查并拉起打印服务，初始化打印客户端，并建立与打印服务的连接。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>             [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>             [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>             [PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) cups 服务无法启动。 |

### OH_Print_Release()

```c
Print_ErrorCode OH_Print_Release()
```

**描述**

此 API 关闭与打印服务的连接，解散先前的回调，并释放打印客户端资源。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         当前不会返回其他错误码。 |

### OH_Print_StartPrinterDiscovery()

```c
Print_ErrorCode OH_Print_StartPrinterDiscovery(Print_PrinterDiscoveryCallback callback)
```

**描述**

此 API 开始发现打印机。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_PrinterDiscoveryCallback](capi-ohprint-h.md#print_printerdiscoverycallback) callback | 打印机发现事件的 [Print_PrinterDiscoveryCallback](capi-ohprint-h.md#print_printerdiscoverycallback)。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务能力。<br>         [PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) 从 BMS 查询打印扩展列表失败。<br>         [PRINT_ERROR_INVALID_EXTENSION](capi-ohprint-h.md#print_errorcode) 未找到可用的打印扩展。 |

### OH_Print_StopPrinterDiscovery()

```c
Print_ErrorCode OH_Print_StopPrinterDiscovery()
```

**描述**

此 API 停止发现打印机。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_ConnectPrinter()

```c
Print_ErrorCode OH_Print_ConnectPrinter(const char *printerId)
```

**描述**

此 API 使用打印机 ID 连接打印机。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                | 描述                |
| --------------------- | ------------------- |
| const char *printerId | 待连接的打印机 ID。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 打印机应在已发现的打印机列表中。<br>         [PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) 无法找到负责该打印机的扩展。 |

### OH_Print_StartPrintJob()

```c
Print_ErrorCode OH_Print_StartPrintJob(const Print_PrintJob *printJob)
```

**描述**

此 API 开始发起打印任务。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [const Print_PrintJob](capi-oh-print-print-printjob.md) *printJob | 指向指定打印任务信息的 [Print_PrintJob](capi-oh-print-print-printjob.md) 实例的指针。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 打印机应在已连接的打印机列表中。<br>         [PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) 无法在打印服务中创建打印任务。<br>         [PRINT_ERROR_INVALID_PRINT_JOB](capi-ohprint-h.md#print_errorcode) 无法在任务队列中找到该任务。 |

### OH_Print_RegisterPrinterChangeListener()

```c
Print_ErrorCode OH_Print_RegisterPrinterChangeListener(Print_PrinterChangeCallback callback)
```

**描述**

此 API 注册打印机变更回调。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_PrinterChangeCallback](capi-ohprint-h.md#print_printerchangecallback) callback | 待注册的 [Print_PrinterChangeCallback](capi-ohprint-h.md#print_printerchangecallback)。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务能力。 |

### OH_Print_UnregisterPrinterChangeListener()

```c
void OH_Print_UnregisterPrinterChangeListener()
```

**描述**

此 API 注销打印机变更回调。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

### OH_Print_QueryPrinterList()

```c
Print_ErrorCode OH_Print_QueryPrinterList(Print_StringList *printerIdList)
```

**描述**

此 API 查询已添加的打印机列表。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_StringList](capi-oh-print-print-stringlist.md) *printerIdList | 用于存储查询到的打印机 ID 列表的 [Print_StringList](capi-oh-print-print-stringlist.md) 实例指针。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_INVALID_PARAMETER](capi-ohprint-h.md#print_errorcode) printerIdList 为 NULL。<br>         [PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 无法查询任何已连接的打印机。<br>         [PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法复制打印机 ID 列表。 |

### OH_Print_ReleasePrinterList()

```c
void OH_Print_ReleasePrinterList(Print_StringList *printerIdList)
```

**描述**

此 API 释放用于查询的打印机列表内存。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                           |
| ------------------------------------------------------------ | ------------------------------ |
| [Print_StringList](capi-oh-print-print-stringlist.md) *printerIdList | 待释放的已查询打印机 ID 列表。 |

### OH_Print_QueryPrinterInfo()

```c
Print_ErrorCode OH_Print_QueryPrinterInfo(const char *printerId, Print_PrinterInfo **printerInfo)
```

**描述**

此 API 根据打印机 ID 查询打印机信息。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const char *printerId                                        | 待查询的打印机 ID。                                          |
| [Print_PrinterInfo](capi-oh-print-print-printerinfo.md) **printerInfo | 用于存储打印机信息的 [Print_PrinterInfo](capi-oh-print-print-printerinfo.md) 指针的指针。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_INVALID_PARAMETER](capi-ohprint-h.md#print_errorcode) printerId 为 NULL 或 printerInfo 为 NULL。<br>         [PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 无法在已连接的打印机列表中找到该打印机。 |

### OH_Print_ReleasePrinterInfo()

```c
void OH_Print_ReleasePrinterInfo(Print_PrinterInfo *printerInfo)
```

**描述**

此 API 释放用于查询的打印机信息内存。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                           |
| ------------------------------------------------------------ | ------------------------------ |
| [Print_PrinterInfo](capi-oh-print-print-printerinfo.md) *printerInfo | 待释放的已查询打印机信息指针。 |

### OH_Print_LaunchPrinterManager()

```c
Print_ErrorCode OH_Print_LaunchPrinterManager()
```

**描述**

此 API 启动系统的打印机管理窗口。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法启动打印机管理窗口。 |

### OH_Print_QueryPrinterProperties()

```c
Print_ErrorCode OH_Print_QueryPrinterProperties(const char *printerId, const Print_StringList *propertyKeyList, Print_PropertyList *propertyList)
```

**描述**

此 API 根据属性关键字列表查询对应的打印机属性值。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                       |
| ------------------------------------------------------------ | -------------------------- |
| const char *printerId                                        | 待查询的打印机 ID。        |
| [const Print_StringList](capi-oh-print-print-stringlist.md) *propertyKeyList | 待查询的属性关键字列表。   |
| [Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | 查询到的打印机属性值列表。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_INVALID_PARAMETER](capi-ohprint-h.md#print_errorcode) 参数之一为 NULL 或关键字列表为空。<br>         [PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 无法找到指定打印机的属性。<br>         [PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法复制打印机属性。 |

### OH_Print_ReleasePrinterProperties()

```c
void OH_Print_ReleasePrinterProperties(Print_PropertyList *propertyList)
```

**描述**

此 API 释放用于查询的属性列表内存。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                             |
| ------------------------------------------------------------ | -------------------------------- |
| [Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | 待释放的已查询打印机属性值指针。 |

### OH_Print_UpdatePrinterProperties()

```c
Print_ErrorCode OH_Print_UpdatePrinterProperties(const char *printerId, const Print_PropertyList *propertyList)
```

**描述**

此 API 根据属性键值对列表设置打印机属性。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                       |
| ------------------------------------------------------------ | -------------------------- |
| const char *printerId                                        | 待设置的打印机 ID。        |
| [const Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | 待设置的打印机属性值列表。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_RestorePrinterProperties()

```c
Print_ErrorCode OH_Print_RestorePrinterProperties(const char *printerId, const Print_StringList *propertyKeyList)
```

**描述**

此 API 根据属性关键字列表将打印机属性恢复为默认设置。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                     |
| ------------------------------------------------------------ | ------------------------ |
| const char *printerId                                        | 待恢复的打印机 ID。      |
| [const Print_StringList](capi-oh-print-print-stringlist.md) *propertyKeyList | 待恢复的属性关键字列表。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_StartPrintByNative()

```c
Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)
```

**描述**

此 API 提供启动打印对话框的能力。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 13

**参数：**

| 参数项                                                       | 描述                 |
| ------------------------------------------------------------ | -------------------- |
| const char *printJobName                                     | 此打印任务的名称。   |
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) printDocCallback | 打印文档状态回调。   |
| void *context                                                | 调用方应用的上下文。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |
