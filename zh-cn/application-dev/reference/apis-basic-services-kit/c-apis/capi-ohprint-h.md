# ohprint.h

## 概述

声明用于发现和连接打印机、通过打印机打印文件、查询已添加打印机列表及其内部打印机信息等功能的API。适用于需要在应用内集成打印能力的场景，帮助开发者便捷地实现打印机发现、连接、任务下发及状态监控等打印流程管理。

**引用文件：** <ohprint.h>

**库：** libohprint.so

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**相关模块：** [Print](capi-basic-services-kit-print.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Print_StringList](capi-print-print-stringlist.md) | Print_StringList | 表示字符串列表，用于在打印模块中传递多个字符串数据。该结构体通过count字段记录字符串数量、list字段指向字符串数组，适用于需要批量传递多个字符串数据的场景。相关接口请参见OH_Print。 |
| [Print_Property](capi-print-print-property.md) | Print_Property | Print_Property表示打印机属性，以键值对形式描述打印机的各类属性信息，开发者可通过该结构体获取或设置打印机的属性参数。 |
| [Print_PropertyList](capi-print-print-propertylist.md) | Print_PropertyList | 打印机属性列表，用于存储和管理打印机属性，支持通过属性数量和属性数组的指针对打印机属性进行批量访问和操作。其中count表示属性数量，list为指向属性数组的指针，两者配合表示一组完整的打印机属性， 适用于需要查询或设置打印机多项属性信息的场景。 |
| [Print_Resolution](capi-print-print-resolution.md) | Print_Resolution | Print_Resolution用于表示以dpi为单位的打印分辨率，可控制打印输出的精细度与质量。 |
| [Print_Margin](capi-print-print-margin.md) | Print_Margin | Print_Margin用于表示打印页面的边距信息，支持设置左、上、右、下四个方向的边距，控制可打印内容区域。适用于需要在打印时精确控制内容与纸张边缘距离的场景，通过合理配置边距可以避免内容溢出或被裁剪。 |
| [Print_PageSize](capi-print-print-pagesize.md) | Print_PageSize | Print_PageSize用于表示打印任务中的纸张尺寸信息，包含纸张ID、名称、宽度与高度等关键属性，适用于需要在打印配置流程中指定或查询纸张规格的场景。 |
| [Print_PrinterCapability](capi-print-print-printercapability.md) | Print_PrinterCapability | 表示打印机能力，包含支持的色彩模式、双面打印模式、纸张尺寸、介质类型、打印质量、纸张来源、份数、分辨率、打印方向模式及高级能力等属性，适用于需要查询或匹配打印机能力的场景，帮助开发者根据打印机能力进行打印任务配置和适配。 |
| [Print_DefaultValue](capi-print-print-defaultvalue.md) | Print_DefaultValue | 表示打印机的默认属性值，包含色彩模式、双面模式、介质类型、纸张尺寸、边距、纸张来源、打印质量、份数、分辨率、方向等默认打印参数。 |
| [Print_PrinterInfo](capi-print-print-printerinfo.md) | Print_PrinterInfo | Print_PrinterInfo表示打印机信息，包含打印机的状态、能力、默认属性以及标识信息（如打印机ID、名称、描述、位置、品牌型号、URI等），适用于应用在打印场景中获取和展示打印机详细信息的场景， 帮助开发者根据打印机能力与属性选择合适的打印设备。可通过 [OH_Print_StartPrinterDiscovery](capi-ohprint-h.md#oh_print_startprinterdiscovery) 或 [OH_Print_QueryPrinterInfo](capi-ohprint-h.md#oh_print_queryprinterinfo) 获取。 |
| [Print_PrintJob](capi-print-print-printjob.md) | Print_PrintJob | 表示打印任务结构体，用于配置打印任务的各项属性参数（如打印份数、纸张来源、色彩模式、双面模式、分辨率、边距、方向模式、打印质量、文档格式及高级选项等）。开发者通过填充该结构体并向打印模块接口提交以发起打印任务。 |
| [Print_Range](capi-print-print-range.md) | Print_Range | 表示打印范围结构体，用于指定打印任务中的页码范围。可通过startPage和endPage指定连续页码范围，或通过pagesArray和pagesArrayLen指定不连续的打印页码数组。 |
| [Print_PrintAttributes](capi-print-print-printattributes.md) | Print_PrintAttributes | 表示打印属性结构体，用于配置打印任务的各项属性（如打印范围、纸张尺寸、边距、份数、双面模式、色彩模式、打印方向及打印选项等），适用于需要对打印输出进行精细化控制的场景。 |
| [Print_PrintDocCallback](capi-print-print-printdoccallback.md) | Print_PrintDocCallback | 表示打印文档回调结构体。用于C/C++原生应用向打印框架提供文件生成和任务状态接收能力。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Print_ErrorCode](#print_errorcode) | Print_ErrorCode | 定义错误码。 |
| [Print_PrinterState](#print_printerstate) | Print_PrinterState | 表示打印机状态。 |
| [Print_DiscoveryEvent](#print_discoveryevent) | Print_DiscoveryEvent | 表示打印机发现事件。 |
| [Print_PrinterEvent](#print_printerevent) | Print_PrinterEvent | 表示打印机变更事件。 |
| [Print_DuplexMode](#print_duplexmode) | Print_DuplexMode | 表示双面打印模式。 |
| [Print_ColorMode](#print_colormode) | Print_ColorMode | 表示色彩模式。 |
| [Print_OrientationMode](#print_orientationmode) | Print_OrientationMode | 表示方向模式。 |
| [Print_Quality](#print_quality) | Print_Quality | 表示打印质量。 |
| [Print_DocumentFormat](#print_documentformat) | Print_DocumentFormat | 表示文档的MIME媒体类型。 |
| [Print_JobDocAdapterState](#print_jobdocadapterstate) | Print_JobDocAdapterState | 表示打印任务文档适配器状态。 |
| [OH_Print_JobState](#oh_print_jobstate) | OH_Print_JobState | 表示打印任务状态。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void(\*Print_WriteResultCallback)(const char *jobId, uint32_t code)](#print_writeresultcallback) | Print_WriteResultCallback | 写文件结果回调。 |
| [typedef void(\*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)](#print_onstartlayoutwrite) | Print_OnStartLayoutWrite | 打印开始布局回调。 |
| [typedef void(\*Print_OnJobStateChanged)(const char *jobId, uint32_t state)](#print_onjobstatechanged) | Print_OnJobStateChanged | 打印任务状态回调。 |
| [typedef void (\*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)](#print_printerdiscoverycallback) | Print_PrinterDiscoveryCallback | 打印机发现回调。 |
| [typedef void (\*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)](#print_printerchangecallback) | Print_PrinterChangeCallback | 打印机变更回调。 |
| [Print_ErrorCode OH_Print_Init()](#oh_print_init) | - | 此API用于检查并拉起打印服务，初始化打印客户端，并建立与打印服务的连接。调用其它打印API前，必须先调用此方法完成初始化，否则将因打印服务连接未建立而导致其他API无法正常工作。在使用完毕后， 需调用OH_Print_Release()关闭连接并释放打印客户端资源，否则会导致打印服务连接未关闭及客户端资源泄漏。 |
| [Print_ErrorCode OH_Print_Release()](#oh_print_release) | - | 此API用于关闭与打印服务的连接，注销所有已注册的回调，并释放打印客户端资源。 |
| [Print_ErrorCode OH_Print_StartPrinterDiscovery(Print_PrinterDiscoveryCallback callback)](#oh_print_startprinterdiscovery) | - | 此API用于开始发现打印机。发现过程中，可通过传入的Print_PrinterDiscoveryCallback回调通知打印机发现事件和获取Print_PrinterInfo打印机信息。 完成发现后可调用OH_Print_StopPrinterDiscovery()停止发现流程，否则导致发现流程持续运行，消耗系统资源。 |
| [Print_ErrorCode OH_Print_StopPrinterDiscovery()](#oh_print_stopprinterdiscovery) | - | 此API用于停止发现打印机。 |
| [Print_ErrorCode OH_Print_ConnectPrinter(const char *printerId)](#oh_print_connectprinter) | - | 此API用于使用打印机ID连接打印机。 |
| [Print_ErrorCode OH_Print_StartPrintJob(const Print_PrintJob *printJob)](#oh_print_startprintjob) | - | 此API用于开始发起打印任务。调用此API前，待使用的打印机应在已连接的打印机列表中。 |
| [Print_ErrorCode OH_Print_RegisterPrinterChangeListener(Print_PrinterChangeCallback callback)](#oh_print_registerprinterchangelistener) | - | 此API用于注册打印机变更回调。当不再需要监听打印机变更事件时，需调用OH_Print_UnregisterPrinterChangeListener()注销回调。未注销回调会导致回调持续生效， 可能引发不必要的回调调用和资源占用。 |
| [void OH_Print_UnregisterPrinterChangeListener()](#oh_print_unregisterprinterchangelistener) | - | 此API用于注销打印机变更回调。 |
| [Print_ErrorCode OH_Print_QueryPrinterList(Print_StringList *printerIdList)](#oh_print_queryprinterlist) | - | 此API用于查询已添加的打印机列表。在使用完毕后，需调用OH_Print_ReleasePrinterList()释放查询结果所占内存，否则可能导致内存泄漏。 |
| [void OH_Print_ReleasePrinterList(Print_StringList *printerIdList)](#oh_print_releaseprinterlist) | - | 此API用于释放打印机列表内存。传入的指针应来自OH_Print_QueryPrinterList()的查询结果。 |
| [Print_ErrorCode OH_Print_QueryPrinterInfo(const char *printerId, Print_PrinterInfo **printerInfo)](#oh_print_queryprinterinfo) | - | 此API用于根据打印机ID查询打印机信息。使用完毕后，需调用OH_Print_ReleasePrinterInfo()释放查询结果所占内存，否则可能导致内存泄漏。 |
| [void OH_Print_ReleasePrinterInfo(Print_PrinterInfo *printerInfo)](#oh_print_releaseprinterinfo) | - | 此API用于释放打印机信息内存。传入的指针应来自OH_Print_QueryPrinterInfo()的查询结果。 |
| [Print_ErrorCode OH_Print_LaunchPrinterManager()](#oh_print_launchprintermanager) | - | 此API用于启动系统的打印机管理窗口。 |
| [Print_ErrorCode OH_Print_QueryPrinterProperties(const char *printerId, const Print_StringList *propertyKeyList, Print_PropertyList *propertyList)](#oh_print_queryprinterproperties) | - | 此API用于根据属性关键字列表查询对应的打印机属性值。在使用完毕后，需调用OH_Print_ReleasePrinterProperties()释放查询结果所占内存，否则可能会导致内存泄漏。 |
| [void OH_Print_ReleasePrinterProperties(Print_PropertyList *propertyList)](#oh_print_releaseprinterproperties) | - | 此API用于释放属性列表内存。传入的指针应来自OH_Print_QueryPrinterProperties()的查询结果。 |
| [Print_ErrorCode OH_Print_UpdatePrinterProperties(const char *printerId, const Print_PropertyList *propertyList)](#oh_print_updateprinterproperties) | - | 此API用于根据属性键值对列表设置打印机属性。 |
| [Print_ErrorCode OH_Print_RestorePrinterProperties(const char *printerId, const Print_StringList *propertyKeyList)](#oh_print_restoreprinterproperties) | - | 此API用于根据属性关键字列表将打印机属性恢复为默认设置。 |
| [Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)](#oh_print_startprintbynative) | - | 此API用于启动系统打印应用，适用于需要用户在打印前通过系统打印应用选择打印机和设置打印参数（如份数、双面、色彩等）的场景。 |
| [typedef void(\*OH_Print_OnJobStateChanged)(const char *jobId, OH_Print_JobState state)](#oh_print_onjobstatechanged) | OH_Print_OnJobStateChanged | 打印任务状态回调。与Print_OnJobStateChanged（使用uint32_t表示状态，起始版本13）相比，本回调使用OH_Print_JobState枚举表示任务状态，语义更清晰、类型更安全。 |
| [Print_ErrorCode OH_Print_StartPrintWithJobStateCallback(const Print_PrintJob *printJob, OH_Print_OnJobStateChanged jobStateChangedCb)](#oh_print_startprintwithjobstatecallback) | - | 此API用于下发打印任务，并附带任务状态变更回调功能，适合需要监听打印任务执行状态（如成功、失败、取消等）的场景。调用此API前，待使用的打印机应在已连接的打印机列表中；如无需监听任务状态变化， 可使用OH_Print_StartPrintJob。 |

## 枚举类型说明

### Print_ErrorCode

```c
enum Print_ErrorCode
```

**描述：**

定义错误码。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRINT_ERROR_NONE = 0 | 操作成功。 |
| PRINT_ERROR_NO_PERMISSION = 201 | 权限校验失败，请确认已在应用配置中声明对应的权限。 |
| PRINT_ERROR_INVALID_PARAMETER = 401 | 参数无效，请检查传入参数的类型和取值范围。 |
| PRINT_ERROR_GENERIC_FAILURE = 24300001 | 通用内部错误，请检查打印服务运行状态后重试。 |
| PRINT_ERROR_RPC_FAILURE = 24300002 | RPC通信错误，请确认打印服务已正常启动后重试。 |
| PRINT_ERROR_SERVER_FAILURE = 24300003 | 服务端错误，请检查打印服务运行状态。 |
| PRINT_ERROR_INVALID_EXTENSION = 24300004 | 无效的扩展，请确认已安装有效的打印扩展。 |
| PRINT_ERROR_INVALID_PRINTER = 24300005 | 无效的打印机，请确认打印机已在已发现或已连接的打印机列表中。 |
| PRINT_ERROR_INVALID_PRINT_JOB = 24300006 | 无效的打印任务，请确认打印任务信息完整且打印机已连接。 |
| PRINT_ERROR_FILE_IO = 24300007 | 读写文件失败，请检查文件路径及访问权限。 |
| PRINT_ERROR_UNKNOWN = 24300255 | 未知错误，请检查打印服务状态后重试，若问题持续请联系技术支持。 |

### Print_PrinterState

```c
enum Print_PrinterState
```

**描述：**

表示打印机状态。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRINTER_IDLE | 打印机空闲。 |
| PRINTER_BUSY | 打印机忙。 |
| PRINTER_UNAVAILABLE | 打印机不可用。 |

### Print_DiscoveryEvent

```c
enum Print_DiscoveryEvent
```

**描述：**

表示打印机发现事件。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRINTER_DISCOVERED = 0 | 发现打印机。 |
| PRINTER_LOST = 1 | 丢失打印机。 |
| PRINTER_CONNECTING = 2 | 正在连接打印机。 |
| PRINTER_CONNECTED = 3 | 打印机已连接。 |

### Print_PrinterEvent

```c
enum Print_PrinterEvent
```

**描述：**

表示打印机变更事件。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRINTER_ADDED = 0 | 打印机已添加。 |
| PRINTER_DELETED = 1 | 打印机已删除。 |
| PRINTER_STATE_CHANGED = 2 | 打印机状态已变更。 |
| PRINTER_INFO_CHANGED = 3 | 打印机信息已变更。 |

### Print_DuplexMode

```c
enum Print_DuplexMode
```

**描述：**

表示双面打印模式。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DUPLEX_MODE_ONE_SIDED = 0 | 单面模式。 |
| DUPLEX_MODE_TWO_SIDED_LONG_EDGE = 1 | 长边翻转双面模式。 |
| DUPLEX_MODE_TWO_SIDED_SHORT_EDGE = 2 | 短边翻转双面模式。 |

### Print_ColorMode

```c
enum Print_ColorMode
```

**描述：**

表示色彩模式。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| COLOR_MODE_MONOCHROME = 0 | 黑白模式。 |
| COLOR_MODE_COLOR = 1 | 彩色模式。 |
| COLOR_MODE_AUTO = 2 | 自动模式。 |

### Print_OrientationMode

```c
enum Print_OrientationMode
```

**描述：**

表示方向模式。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ORIENTATION_MODE_PORTRAIT = 0 | 纵向模式。 |
| ORIENTATION_MODE_LANDSCAPE = 1 | 横向模式。 |
| ORIENTATION_MODE_REVERSE_LANDSCAPE = 2 | 反向横向模式。 |
| ORIENTATION_MODE_REVERSE_PORTRAIT = 3 | 反向纵向模式。 |
| ORIENTATION_MODE_NONE = 4 | 未指定。 |

### Print_Quality

```c
enum Print_Quality
```

**描述：**

表示打印质量。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRINT_QUALITY_DRAFT = 3 | 草稿质量模式。 |
| PRINT_QUALITY_NORMAL = 4 | 正常质量模式。 |
| PRINT_QUALITY_HIGH = 5 | 高质量模式。 |

### Print_DocumentFormat

```c
enum Print_DocumentFormat
```

**描述：**

表示文档的MIME媒体类型。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DOCUMENT_FORMAT_AUTO | MIME类型：application/octet-stream。 |
| DOCUMENT_FORMAT_JPEG | MIME类型：image/jpeg。 |
| DOCUMENT_FORMAT_PDF | MIME类型：application/pdf。 |
| DOCUMENT_FORMAT_POSTSCRIPT | MIME类型：application/postscript。 |
| DOCUMENT_FORMAT_TEXT | MIME类型：text/plain。 |

### Print_JobDocAdapterState

```c
enum Print_JobDocAdapterState
```

**描述：**

表示打印任务文档适配器状态。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY = 0 | 打印任务预览能力销毁。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_SUCCEED = 1 | 打印任务成功。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_FAIL = 2 | 打印任务失败。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_CANCEL = 3 | 打印任务取消。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_BLOCK = 4 | 打印任务阻塞。 |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_CANCELED = 5 | 因取消导致的打印任务预览能力销毁。 |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_STARTED = 6 | 因启动导致的打印任务预览能力销毁。 |

### OH_Print_JobState

```c
enum OH_Print_JobState
```

**描述：**

表示打印任务状态。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_PRINT_JOB_SUCCEED = 0 | 打印任务成功。 |
| OH_PRINT_JOB_FAIL = 1 | 打印任务失败。 |
| OH_PRINT_JOB_CANCEL = 2 | 打印任务取消。 |
| OH_PRINT_JOB_BLOCK = 3 | 打印任务阻塞。 |


## 函数说明

### Print_WriteResultCallback()

```c
typedef void(*Print_WriteResultCallback)(const char *jobId, uint32_t code)
```

**描述：**

写文件结果回调。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *jobId | 打印任务的ID。 |
| uint32_t code | 写文件的结果。0表示文件创建成功；1表示文件创建失败；2表示文件创建成功但未渲染。 |

### Print_OnStartLayoutWrite()

```c
typedef void(*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)
```

**描述：**

打印开始布局回调。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *jobId | 打印任务的ID。 |
| uint32_t fd | 待写入的文件描述符。 |
| [const Print_PrintAttributes](capi-print-print-printattributes.md) *oldAttrs | 上一次打印任务的打印属性。 |
| [const Print_PrintAttributes](capi-print-print-printattributes.md) *newAttrs | 当前打印任务的打印属性。 |
| [Print_WriteResultCallback](capi-ohprint-h.md#print_writeresultcallback) writeCallback | 写文件结果回调。 |

### Print_OnJobStateChanged()

```c
typedef void(*Print_OnJobStateChanged)(const char *jobId, uint32_t state)
```

**描述：**

打印任务状态回调。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *jobId | 打印任务的ID。 |
| uint32_t state | 当前打印任务的状态，取值及各状态含义可参考 [OH_Print_JobState](capi-ohprint-h.md#oh_print_jobstate) 枚举。 |

### Print_PrinterDiscoveryCallback()

```c
typedef void (*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)
```

**描述：**

打印机发现回调。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_DiscoveryEvent](capi-ohprint-h.md#print_discoveryevent) event | 打印机发现过程中的发现事件。 |
| [const Print_PrinterInfo](capi-print-print-printerinfo.md) *printerInfo | 发现事件发生时的打印机信息。 |

### Print_PrinterChangeCallback()

```c
typedef void (*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)
```

**描述：**

打印机变更回调。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_PrinterEvent](capi-ohprint-h.md#print_printerevent) event | 打印服务运行期间的打印机变更事件。 |
| [const Print_PrinterInfo](capi-print-print-printerinfo.md) *printerInfo | 变更事件发生时的打印机信息。 |

### OH_Print_Init()

```c
Print_ErrorCode OH_Print_Init()
```

**描述：**

此API用于检查并拉起打印服务，初始化打印客户端，并建立与打印服务的连接。调用其它打印API前，必须先调用此方法完成初始化，否则将因打印服务连接未建立而导致其他API无法正常工作。在使用完毕后， 需调用OH_Print_Release()关闭连接并释放打印客户端资源，否则会导致打印服务连接未关闭及客户端资源泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>[PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) cups服务无法启动。 |

### OH_Print_Release()

```c
Print_ErrorCode OH_Print_Release()
```

**描述：**

此API用于关闭与打印服务的连接，注销所有已注册的回调，并释放打印客户端资源。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>当前不会返回其他错误码。 |

### OH_Print_StartPrinterDiscovery()

```c
Print_ErrorCode OH_Print_StartPrinterDiscovery(Print_PrinterDiscoveryCallback callback)
```

**描述：**

此API用于开始发现打印机。发现过程中，可通过传入的Print_PrinterDiscoveryCallback回调通知打印机发现事件和获取Print_PrinterInfo打印机信息。 完成发现后可调用OH_Print_StopPrinterDiscovery()停止发现流程，否则导致发现流程持续运行，消耗系统资源。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_PrinterDiscoveryCallback](capi-ohprint-h.md#print_printerdiscoverycallback) callback | 打印机发现事件的 [Print_PrinterDiscoveryCallback](capi-ohprint-h.md#print_printerdiscoverycallback)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>[PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) 从BMS查询打印扩展列表失败。<br>[PRINT_ERROR_INVALID_EXTENSION](capi-ohprint-h.md#print_errorcode) 未找到可用的打印扩展。 |

### OH_Print_StopPrinterDiscovery()

```c
Print_ErrorCode OH_Print_StopPrinterDiscovery()
```

**描述：**

此API用于停止发现打印机。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_ConnectPrinter()

```c
Print_ErrorCode OH_Print_ConnectPrinter(const char *printerId)
```

**描述：**

此API用于使用打印机ID连接打印机。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *printerId | 待连接的打印机ID，应为已发现的打印机列表中的打印机，不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>[PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 打印机应在已发现的打印机列表中。<br>[PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) 无法找到负责该打印机的扩展。 |

### OH_Print_StartPrintJob()

```c
Print_ErrorCode OH_Print_StartPrintJob(const Print_PrintJob *printJob)
```

**描述：**

此API用于开始发起打印任务。调用此API前，待使用的打印机应在已连接的打印机列表中。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const Print_PrintJob](capi-print-print-printjob.md) *printJob | 指向指定打印任务信息的 [Print_PrintJob](capi-print-print-printjob.md) 实例的指针，不能为NULL，其中引用的打印机需已通过OH_Print_ConnectPrinter连接。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>[PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 打印机应在已连接的打印机列表中。<br>[PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) 无法在打印服务中创建打印任务。<br>[PRINT_ERROR_INVALID_PRINT_JOB](capi-ohprint-h.md#print_errorcode) 无法在任务队列中找到该任务。 |

### OH_Print_RegisterPrinterChangeListener()

```c
Print_ErrorCode OH_Print_RegisterPrinterChangeListener(Print_PrinterChangeCallback callback)
```

**描述：**

此API用于注册打印机变更回调。当不再需要监听打印机变更事件时，需调用OH_Print_UnregisterPrinterChangeListener()注销回调。未注销回调会导致回调持续生效， 可能引发不必要的回调调用和资源占用。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_PrinterChangeCallback](capi-ohprint-h.md#print_printerchangecallback) callback | 打印机变更回调，用于在打印服务运行期间接收打印机添加、删除、状态变更、信息变更等事件通知，不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_UnregisterPrinterChangeListener()

```c
void OH_Print_UnregisterPrinterChangeListener()
```

**描述：**

此API用于注销打印机变更回调。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

### OH_Print_QueryPrinterList()

```c
Print_ErrorCode OH_Print_QueryPrinterList(Print_StringList *printerIdList)
```

**描述：**

此API用于查询已添加的打印机列表。在使用完毕后，需调用OH_Print_ReleasePrinterList()释放查询结果所占内存，否则可能导致内存泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_StringList](capi-print-print-stringlist.md) *printerIdList | 用于存储查询到的打印机ID列表的 [Print_StringList](capi-print-print-stringlist.md) 实例指针，不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_INVALID_PARAMETER](capi-ohprint-h.md#print_errorcode) printerIdList为NULL。<br>[PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 无法查询任何已连接的打印机。<br>[PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法复制打印机ID列表。 |

### OH_Print_ReleasePrinterList()

```c
void OH_Print_ReleasePrinterList(Print_StringList *printerIdList)
```

**描述：**

此API用于释放打印机列表内存。传入的指针应来自OH_Print_QueryPrinterList()的查询结果。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_StringList](capi-print-print-stringlist.md) *printerIdList | 待释放的已查询打印机ID列表。 |

### OH_Print_QueryPrinterInfo()

```c
Print_ErrorCode OH_Print_QueryPrinterInfo(const char *printerId, Print_PrinterInfo **printerInfo)
```

**描述：**

此API用于根据打印机ID查询打印机信息。使用完毕后，需调用OH_Print_ReleasePrinterInfo()释放查询结果所占内存，否则可能导致内存泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *printerId | 待查询的打印机ID，应为已连接的打印机列表中的打印机ID，不能为NULL。 |
| [Print_PrinterInfo](capi-print-print-printerinfo.md) **printerInfo | 用于存储打印机信息的 [Print_PrinterInfo](capi-print-print-printerinfo.md) 指针的指针，不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>[PRINT_ERROR_INVALID_PARAMETER](capi-ohprint-h.md#print_errorcode) printerId为NULL或printerInfo为NULL。<br>[PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 无法在已连接的打印机列表中找到该打印机。 |

### OH_Print_ReleasePrinterInfo()

```c
void OH_Print_ReleasePrinterInfo(Print_PrinterInfo *printerInfo)
```

**描述：**

此API用于释放打印机信息内存。传入的指针应来自OH_Print_QueryPrinterInfo()的查询结果。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_PrinterInfo](capi-print-print-printerinfo.md) *printerInfo | 待释放的已查询打印机信息指针。 |

### OH_Print_LaunchPrinterManager()

```c
Print_ErrorCode OH_Print_LaunchPrinterManager()
```

**描述：**

此API用于启动系统的打印机管理窗口。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法启动打印机管理窗口。 |

### OH_Print_QueryPrinterProperties()

```c
Print_ErrorCode OH_Print_QueryPrinterProperties(const char *printerId, const Print_StringList *propertyKeyList, Print_PropertyList *propertyList)
```

**描述：**

此API用于根据属性关键字列表查询对应的打印机属性值。在使用完毕后，需调用OH_Print_ReleasePrinterProperties()释放查询结果所占内存，否则可能会导致内存泄漏。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *printerId | 待查询的打印机ID，必须是已连接的打印机ID，不能为NULL。 |
| [const Print_StringList](capi-print-print-stringlist.md) *propertyKeyList | 待查询的属性关键字列表，不能为NULL且内部的字符串数组不能为NULL。 |
| [Print_PropertyList](capi-print-print-propertylist.md) *propertyList | 查询到的打印机属性值列表，不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_INVALID_PARAMETER](capi-ohprint-h.md#print_errorcode) 参数之一为NULL或关键字列表为空。<br>[PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 无法找到指定打印机的属性。<br>[PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法复制打印机属性。 |

### OH_Print_ReleasePrinterProperties()

```c
void OH_Print_ReleasePrinterProperties(Print_PropertyList *propertyList)
```

**描述：**

此API用于释放属性列表内存。传入的指针应来自OH_Print_QueryPrinterProperties()的查询结果。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Print_PropertyList](capi-print-print-propertylist.md) *propertyList | 待释放的已查询打印机属性值指针。 |

### OH_Print_UpdatePrinterProperties()

```c
Print_ErrorCode OH_Print_UpdatePrinterProperties(const char *printerId, const Print_PropertyList *propertyList)
```

**描述：**

此API用于根据属性键值对列表设置打印机属性。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *printerId | 待设置的打印机ID，必须是已连接的打印机列表中的打印机ID，不能为NULL。 |
| [const Print_PropertyList](capi-print-print-propertylist.md) *propertyList | 待设置的打印机属性值列表，不能为NULL且内部的属性数组不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_RestorePrinterProperties()

```c
Print_ErrorCode OH_Print_RestorePrinterProperties(const char *printerId, const Print_StringList *propertyKeyList)
```

**描述：**

此API用于根据属性关键字列表将打印机属性恢复为默认设置。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *printerId | 待恢复的打印机ID，必须是已连接的打印机列表中的打印机ID，不能为NULL。 |
| [const Print_StringList](capi-print-print-stringlist.md) *propertyKeyList | 待恢复的属性关键字列表，不能为NULL且内部的字符串数组不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_StartPrintByNative()

```c
Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)
```

**描述：**

此API用于启动系统打印应用，适用于需要用户在打印前通过系统打印应用选择打印机和设置打印参数（如份数、双面、色彩等）的场景。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *printJobName | 此打印任务的名称。 |
| [Print_PrintDocCallback](capi-print-print-printdoccallback.md) printDocCallback | 打印文档状态回调。 |
| void *context | 调用方应用的上下文指针，传入NULL表示不需要传递额外数据。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要ohos.permission.PRINT权限。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。 |

### OH_Print_OnJobStateChanged()

```c
typedef void(*OH_Print_OnJobStateChanged)(const char *jobId, OH_Print_JobState state)
```

**描述：**

打印任务状态回调。与Print_OnJobStateChanged（使用uint32_t表示状态，起始版本13）相比，本回调使用OH_Print_JobState枚举表示任务状态，语义更清晰、类型更安全。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *jobId | 打印任务的ID。 |
| [OH_Print_JobState](capi-ohprint-h.md#oh_print_jobstate) state | 当前打印任务的状态。 |

### OH_Print_StartPrintWithJobStateCallback()

```c
Print_ErrorCode OH_Print_StartPrintWithJobStateCallback(const Print_PrintJob *printJob, OH_Print_OnJobStateChanged jobStateChangedCb)
```

**描述：**

此API用于下发打印任务，并附带任务状态变更回调功能，适合需要监听打印任务执行状态（如成功、失败、取消等）的场景。调用此API前，待使用的打印机应在已连接的打印机列表中；如无需监听任务状态变化， 可使用OH_Print_StartPrintJob。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const Print_PrintJob](capi-print-print-printjob.md) *printJob | 指向指定打印任务信息的 [Print_PrintJob](capi-print-print-printjob.md) 实例的指针，不能为NULL，其中引用的打印机需已通过OH_Print_ConnectPrinter连接。 |
| [OH_Print_OnJobStateChanged](capi-ohprint-h.md#oh_print_onjobstatechanged) jobStateChangedCb | 打印任务状态回调，用于监听printJob参数指定的打印任务的状态变更，不能为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [PRINT_ERROR_NONE](capi-ohprint-h.md#print_errorcode) 表示执行成功。<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要 ohos.permission.PRINT 权限。<br>[PRINT_ERROR_INVALID_PARAMETER](capi-ohprint-h.md#print_errorcode) jobStateChangedCb为NULL。<br>[PRINT_ERROR_GENERIC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法复制回调函数。<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接到打印服务。<br>[PRINT_ERROR_SERVER_FAILURE](capi-ohprint-h.md#print_errorcode) 打印服务中创建打印任务结构体失败。<br>[PRINT_ERROR_INVALID_PRINTER](capi-ohprint-h.md#print_errorcode) 无法找到指定打印机的属性。<br>[PRINT_ERROR_INVALID_PRINT_JOB](capi-ohprint-h.md#print_errorcode) printJob为NULL或内部参数不合法。 |


