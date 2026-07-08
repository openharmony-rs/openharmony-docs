# ohprint.h
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

## 概述

声明用于发现和连接打印机、通过打印机打印文件、查询已添加打印机列表及其内部打印机信息等功能的 API。适用于需要在应用内集成打印能力的场景，帮助开发者便捷地实现打印机发现、连接、任务下发及状态监控等打印流程管理。

**引用文件：** &lt;BasicServicesKit/ohprint.h&gt;

**库：** libohprint.so

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**相关模块：** [Print](capi-oh-print.md)

## 汇总

### 结构体

| 名称                                                         | typedef关键字           | 描述                            |
| ------------------------------------------------------------ | ----------------------- | ------------------------------- |
| [Print_StringList](capi-oh-print-print-stringlist.md)        | Print_StringList        | 表示字符串列表。                |
| [Print_Property](capi-oh-print-print-property.md)            | Print_Property          | 表示打印机属性。                |
| [Print_PropertyList](capi-oh-print-print-propertylist.md)    | Print_PropertyList      | 表示打印机属性列表。                |
| [Print_Resolution](capi-oh-print-print-resolution.md)        | Print_Resolution        | 表示以 dpi 为单位的打印分辨率。 |
| [Print_Margin](capi-oh-print-print-margin.md)                | Print_Margin            | 表示打印边距。                  |
| [Print_PageSize](capi-oh-print-print-pagesize.md)            | Print_PageSize          | 表示纸张尺寸信息。              |
| [Print_PrinterCapability](capi-oh-print-print-printercapability.md) | Print_PrinterCapability | 表示打印机能力。                |
| [Print_DefaultValue](capi-oh-print-print-defaultvalue.md)    | Print_DefaultValue      | 表示默认属性。                  |
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
| [OH_Print_JobState](#oh_print_jobstate)               | OH_Print_JobState        | 表示打印任务状态。 |

### 函数

| 名称                                                         | typedef关键字                  | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------ | ------------------------------------------------------------ |
| [typedef void(\*Print_WriteResultCallback)(const char *jobId, uint32_t code)](#print_writeresultcallback) | Print_WriteResultCallback      | 写文件结果回调。                                             |
| [typedef void(\*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)](#print_onstartlayoutwrite) | Print_OnStartLayoutWrite       | 打印开始布局回调。                                           |
| [typedef void(\*Print_OnJobStateChanged)(const char *jobId, uint32_t state)](#print_onjobstatechanged) | Print_OnJobStateChanged        | 打印任务状态回调。                                           |
| [typedef void (\*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)](#print_printerdiscoverycallback) | Print_PrinterDiscoveryCallback | 打印机发现回调。                                             |
| [typedef void (\*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)](#print_printerchangecallback) | Print_PrinterChangeCallback    | 打印机变更回调。                                             |
| [Print_ErrorCode OH_Print_Init()](#oh_print_init)            | -                              | 此 API 检查并拉起打印服务，初始化打印客户端，并建立与打印服务的连接。 |
| [Print_ErrorCode OH_Print_Release()](#oh_print_release)      | -                              | 此 API 关闭与打印服务的连接，注销先前的回调，并释放打印客户端资源。 |
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
| [typedef void(*OH_Print_OnJobStateChanged)(const char *jobId, OH_Print_JobState state)](#oh_print_onjobstatechanged) | -                              | 打印任务状态回调。                            |
| [Print_ErrorCode OH_Print_StartPrintWithJobStateCallback(const Print_PrintJob *printJob, OH_Print_OnJobStateChanged jobStateChangedCb)](#oh_print_startprintwithjobstatecallback) | -                              | 此 API 下发打印任务，并附带任务状态变更回调功能。                            |

## 枚举类型说明

### Print_ErrorCode

```cpp
enum Print_ErrorCode
```

**描述**

定义错误码。

**起始版本：** 12

| 枚举项                                   | 描述                    |
| ---------------------------------------- | ----------------------- |
| PRINT_ERROR_NONE = 0                     | 操作成功。       |
| PRINT_ERROR_NO_PERMISSION = 201          | 权限校验失败，请确认已在应用配置中声明对应的权限。   |
| PRINT_ERROR_INVALID_PARAMETER = 401      | 参数无效，请检查传入参数的类型和取值范围。       |
| PRINT_ERROR_GENERIC_FAILURE = 24300001   | 通用内部错误，请检查打印服务运行状态后重试。   |
| PRINT_ERROR_RPC_FAILURE = 24300002       | RPC 通信错误，请确认打印服务已正常启动后重试。   |
| PRINT_ERROR_SERVER_FAILURE = 24300003    | 服务端错误，请检查打印服务运行状态。     |
| PRINT_ERROR_INVALID_EXTENSION = 24300004 | 无效的扩展，请确认已安装有效的打印扩展服务。     |
| PRINT_ERROR_INVALID_PRINTER = 24300005   | 无效的打印机，请确认打印机已在已发现或已连接的打印机列表中。   |
| PRINT_ERROR_INVALID_PRINT_JOB = 24300006 | 无效的打印任务，请确认打印任务信息完整且打印机已连接。 |
| PRINT_ERROR_FILE_IO = 24300007           | 读写文件失败，请检查文件路径及访问权限。   |
| PRINT_ERROR_UNKNOWN = 24300255           | 未知错误，请检查打印服务状态后重试，若问题持续请联系技术支持。       |

### Print_PrinterState

```cpp
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

```cpp
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

```cpp
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

```cpp
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

```cpp
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

```cpp
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

```cpp
enum Print_Quality
```

**描述**

表示打印质量。

**起始版本：** 12

| 枚举项                   | 描述         |
| ------------------------ | ------------ |
| PRINT_QUALITY_DRAFT = 3  | 草稿质量模式。 |
| PRINT_QUALITY_NORMAL = 4 | 正常质量模式。 |
| PRINT_QUALITY_HIGH = 5   | 高质量模式。   |

### Print_DocumentFormat

```cpp
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

```cpp
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

### OH_Print_JobState

```cpp
enum OH_Print_JobState
```

**描述**

表示打印任务状态。

**起始版本：** 24

| 枚举项                 | 描述          |
| -------------------- |-------------- |
| OH_PRINT_JOB_SUCCEED = 0 | 打印任务成功。 |
| OH_PRINT_JOB_FAIL = 1    | 打印任务失败。 |
| OH_PRINT_JOB_CANCEL = 2  | 打印任务取消。 |
| OH_PRINT_JOB_BLOCK = 3   | 打印任务阻塞。 |

## 函数说明

### Print_WriteResultCallback()

```cpp
typedef void(*Print_WriteResultCallback)(const char *jobId, uint32_t code)
```

**描述**

写文件结果回调。

**起始版本：** 13

**参数：**

| 参数项              | 描述            |
| ------------------- | --------------- |
| const char \*jobId | 打印任务的 ID。 |
| uint32_t code       | 写文件的结果。  |

### Print_OnStartLayoutWrite()

```cpp
typedef void(*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)
```

**描述**

打印开始布局回调。

**起始版本：** 13

**参数：**

| 参数项                                                       | 描述                 |
| ------------------------------------------------------------ | -------------------- |
| const char \*jobId                                          | 打印任务的 ID。      |
| uint32_t fd                                                  | 待写入的文件描述符。 |
| [const Print_PrintAttributes](capi-oh-print-print-printattributes.md) \*oldAttrs | 上一次打印任务的打印属性。       |
| [const Print_PrintAttributes](capi-oh-print-print-printattributes.md) \*newAttrs | 当前打印任务的打印属性。         |
| [Print_WriteResultCallback](#print_writeresultcallback) writeCallback | 写文件结果回调。     |

### Print_OnJobStateChanged()

```cpp
typedef void(*Print_OnJobStateChanged)(const char *jobId, uint32_t state)
```

**描述**

打印任务状态回调。

**起始版本：** 13

**参数：**

| 参数项              | 描述                 |
| ------------------- | -------------------- |
| const char \*jobId | 打印任务的 ID。      |
| uint32_t state      | 当前打印任务的状态。 |

### Print_PrinterDiscoveryCallback()

```cpp
typedef void (*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)
```

**描述**

打印机发现回调。

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                         |
| ------------------------------------------------------------ | ---------------------------- |
| [Print_DiscoveryEvent](#print_discoveryevent) event                                  | 打印机发现过程中的发现事件。 |
| [const Print_PrinterInfo](capi-oh-print-print-printerinfo.md) \*printerInfo | 发现事件发生时的打印机信息。 |

### Print_PrinterChangeCallback()

```cpp
typedef void (*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)
```

**描述**

打印机变更回调。

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                               |
| ------------------------------------------------------------ | ---------------------------------- |
| [Print_PrinterEvent](#print_printerevent) event                                    | 打印服务运行期间的打印机变更事件。 |
| [const Print_PrinterInfo](capi-oh-print-print-printerinfo.md) \*printerInfo | 变更事件发生时的打印机信息。       |

### OH_Print_Init()

```cpp
Print_ErrorCode OH_Print_Init()
```

**描述**

此 API 检查并拉起打印服务，初始化打印客户端，并建立与打印服务的连接。在使用完毕后，需调用OH_Print_Release()关闭连接并释放打印客户端资源，否则会导致打印服务连接未关闭及客户端资源泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>             [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>             [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。<br>             [PRINT_ERROR_SERVER_FAILURE](#print_errorcode) cups 服务无法启动。 |

### OH_Print_Release()

```cpp
Print_ErrorCode OH_Print_Release()
```

**描述**

此 API 关闭与打印服务的连接，注销所有已注册的回调，并释放打印客户端资源。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         当前不会返回其他错误码。 |

### OH_Print_StartPrinterDiscovery()

```cpp
Print_ErrorCode OH_Print_StartPrinterDiscovery(Print_PrinterDiscoveryCallback callback)
```

**描述**

此 API 用于开始发现打印机。发现过程中，可通过传入的 Print_PrinterDiscoveryCallback 回调通知打印机发现事件和获取 Print_PrinterInfo 打印机信息。完成发现后可调用OH_Print_StopPrinterDiscovery()停止发现流程，否则导致发现流程持续运行，消耗系统资源。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_PrinterDiscoveryCallback](#print_printerdiscoverycallback) callback | 打印机发现事件的 [Print_PrinterDiscoveryCallback](#print_printerdiscoverycallback)。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode) 从 BMS 查询打印扩展列表失败。<br>         [PRINT_ERROR_INVALID_EXTENSION](#print_errorcode) 未找到可用的打印扩展。 |

### OH_Print_StopPrinterDiscovery()

```cpp
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
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。 |

### OH_Print_ConnectPrinter()

```cpp
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
| const char *printerId | 待连接的打印机 ID，应为已发现的打印机列表中的打印机。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode) 打印机应在已发现的打印机列表中。<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode) 无法找到负责该打印机的扩展。 |

### OH_Print_StartPrintJob()

```cpp
Print_ErrorCode OH_Print_StartPrintJob(const Print_PrintJob *printJob)
```

**描述**

此 API 开始发起打印任务。调用此 API 前，待使用的打印机应在已连接的打印机列表中。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [const Print_PrintJob](capi-oh-print-print-printjob.md) *printJob | 指向指定打印任务信息的 [Print_PrintJob](capi-oh-print-print-printjob.md) 实例的指针，其中引用的打印机需已通过 OH_Print_ConnectPrinter 连接。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode) 打印机应在已连接的打印机列表中。<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode) 无法在打印服务中创建打印任务。<br>         [PRINT_ERROR_INVALID_PRINT_JOB](#print_errorcode) 无法在任务队列中找到该任务。 |

### OH_Print_RegisterPrinterChangeListener()

```cpp
Print_ErrorCode OH_Print_RegisterPrinterChangeListener(Print_PrinterChangeCallback callback)
```

**描述**

此 API 用于注册打印机变更回调。当不再需要监听打印机变更事件时，需调用OH_Print_UnregisterPrinterChangeListener()注销回调。未注销回调会导致回调持续生效，可能引发不必要的回调调用和资源占用。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_PrinterChangeCallback](#print_printerchangecallback) callback | 待注册的 [Print_PrinterChangeCallback](#print_printerchangecallback)。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务能力。 |

### OH_Print_UnregisterPrinterChangeListener()

```cpp
void OH_Print_UnregisterPrinterChangeListener()
```

**描述**

此 API 注销打印机变更回调。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

### OH_Print_QueryPrinterList()

```cpp
Print_ErrorCode OH_Print_QueryPrinterList(Print_StringList *printerIdList)
```

**描述**

此 API 用于查询已添加的打印机列表。在使用完毕后，需调用OH_Print_ReleasePrinterList()释放查询结果所占内存，否则可能导致内存泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_StringList](capi-oh-print-print-stringlist.md) *printerIdList | 用于存储查询到的打印机 ID 列表的 [Print_StringList](capi-oh-print-print-stringlist.md) 实例指针，不能为NULL。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode) printerIdList 为 NULL。<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode) 无法查询任何已连接的打印机。<br>         [PRINT_ERROR_GENERIC_FAILURE](#print_errorcode) 无法复制打印机 ID 列表。 |

### OH_Print_ReleasePrinterList()

```cpp
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

```cpp
Print_ErrorCode OH_Print_QueryPrinterInfo(const char *printerId, Print_PrinterInfo **printerInfo)
```

**描述**

此 API 根据打印机 ID 查询打印机信息。使用完毕后，需调用OH_Print_ReleasePrinterInfo()释放查询结果所占内存，否则可能导致内存泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const char *printerId                                        | 待查询的打印机 ID，应为已连接的打印机列表中的打印机ID，不能为NULL。                                          |
| [Print_PrinterInfo](capi-oh-print-print-printerinfo.md) **printerInfo | 用于存储打印机信息的 [Print_PrinterInfo](capi-oh-print-print-printerinfo.md) 指针的指针，不能为NULL。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode) printerId 为 NULL 或 printerInfo 为 NULL。<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode) 无法在已连接的打印机列表中找到该打印机。 |

### OH_Print_ReleasePrinterInfo()

```cpp
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

```cpp
Print_ErrorCode OH_Print_LaunchPrinterManager()
```

**描述**

此 API 用于启动系统的打印机管理窗口。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法启动打印机管理窗口。 |

### OH_Print_QueryPrinterProperties()

```cpp
Print_ErrorCode OH_Print_QueryPrinterProperties(const char *printerId, const Print_StringList *propertyKeyList, Print_PropertyList *propertyList)
```

**描述**

此 API 根据属性关键字列表查询对应的打印机属性值。在使用完毕后，需调用OH_Print_ReleasePrinterProperties()释放查询结果所占内存，否则可能会导致内存泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项                                                       | 描述                       |
| ------------------------------------------------------------ | -------------------------- |
| const char *printerId                                        | 待查询的打印机 ID，必须是已连接的打印机ID，不能为NULL。        |
| [const Print_StringList](capi-oh-print-print-stringlist.md) *propertyKeyList | 待查询的属性关键字列表，不能为NULL且内部的字符串数组不能为NULL。   |
| [Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | 查询到的打印机属性值列表，不能为NULL。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode) 参数之一为 NULL 或关键字列表为空。<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode) 无法找到指定打印机的属性。<br>         [PRINT_ERROR_GENERIC_FAILURE](#print_errorcode) 无法复制打印机属性。 |

### OH_Print_ReleasePrinterProperties()

```cpp
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

```cpp
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
| const char *printerId                                        | 待设置的打印机 ID，必须是已连接的打印机列表中的打印机ID。        |
| [const Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | 待设置的打印机属性值列表。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。 |

### OH_Print_RestorePrinterProperties()

```cpp
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
| const char *printerId                                        | 待恢复的打印机 ID，必须是已连接的打印机列表中的打印机ID。      |
| [const Print_StringList](capi-oh-print-print-stringlist.md) *propertyKeyList | 待恢复的属性关键字列表。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。 |

### OH_Print_StartPrintByNative()

```cpp
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
| void *context                                                | 调用方应用的上下文指针，传入NULL表示不需要传递额外数据。 |

**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。 |

### OH_Print_OnJobStateChanged()

```cpp
typedef void(*OH_Print_OnJobStateChanged)(const char *jobId, OH_Print_JobState state)
```

**描述**

打印任务状态回调。与Print_OnJobStateChanged（使用uint32_t表示状态，起始版本13）相比，本回调使用OH_Print_JobState枚举表示任务状态，语义更清晰、类型更安全。

**起始版本：** 24

**参数：**

| 参数项              | 描述                 |
| ------------------- | -------------------- |
| const char \*jobId | 打印任务的 ID。      |
| [OH_Print_JobState](#oh_print_jobstate) state      | 当前打印任务的状态。 |

### OH_Print_StartPrintWithJobStateCallback()

```cpp
Print_ErrorCode OH_Print_StartPrintWithJobStateCallback(const Print_PrintJob *printJob, OH_Print_OnJobStateChanged jobStateChangedCb)
```

**描述**

此 API 用于下发打印任务，并附带任务状态变更回调功能，适合需要监听打印任务执行状态（如成功、失败、取消等）的场景；如无需监听任务状态变化，可使用OH_Print_StartPrintJob。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 24

**参数：**

| 参数项                                                       | 描述                 |
| ------------------------------------------------------------ | -------------------- |
| const [Print_PrintJob](capi-oh-print-print-printjob.md) *printJob           | 指向指定打印任务信息的 [Print_PrintJob](capi-oh-print-print-printjob.md) 实例的指针，包含打印机ID、打印属性、文件列表等任务相关信息，其中引用的打印机需已通过 OH_Print_ConnectPrinter 连接。   |
| [OH_Print_OnJobStateChanged](#oh_print_onjobstatechanged) jobStateChangedCb | 打印任务状态回调，用于监听printJob参数指定的打印任务的状态变更。 |


**返回：**

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | 返回 [PRINT_ERROR_NONE](#print_errorcode) 表示执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode) 需要 [ohos.permission.PRINT](../../security/AccessToken/permissions-for-all.md#ohospermissionprint) 权限。<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode) jobStateChangedCb为NULL。<br>         [PRINT_ERROR_GENERIC_FAILURE](#print_errorcode) 无法复制回调函数。<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode) 无法连接到打印服务。<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode) 打印服务中创建打印任务结构体失败。<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode) 无法找到指定打印机的属性。<br>         [PRINT_ERROR_INVALID_PRINT_JOB](#print_errorcode) printJob为NULL或内部参数不合法。 |
