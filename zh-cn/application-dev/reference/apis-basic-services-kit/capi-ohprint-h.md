# ohprint.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

## 概述

声明用于发现和连接打印机、从打印机打印文件、查询已添加打印机的列表及其中的打印机信息等API。

**引用文件：** <BasicServicesKit/ohprint.h>

**库：** libohprint.so

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Print_Margin](capi-oh-print-print-margin.md) | Print_Margin | 打印边距。 |
| [Print_PageSize](capi-oh-print-print-pagesize.md) | Print_PageSize | 纸张大小信息。 |
| [Print_Range](capi-oh-print-print-range.md) | Print_Range | 打印范围。 |
| [Print_PrintAttributes](capi-oh-print-print-printattributes.md) | Print_PrintAttributes | 打印属性结构体。 |
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) | Print_PrintDocCallback | 打印文档任务回调结构体。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Print_ErrorCode](#print_errorcode) | Print_ErrorCode | 枚举错误码。 |
| [Print_JobDocAdapterState](#print_jobdocadapterstate) | Print_JobDocAdapterState | 打印文档任务的状态。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void(\*Print_WriteResultCallback)(const char *jobId, uint32_t code)](#print_writeresultcallback) | Print_WriteResultCallback | 文件回写回调。 |
| [typedef void(\*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)](#print_onstartlayoutwrite) | Print_OnStartLayoutWrite | 文件开始回写回调函数。 |
| [typedef void(\*Print_OnJobStateChanged)(const char *jobId, uint32_t state)](#print_onjobstatechanged) | Print_OnJobStateChanged | 打印任务状态回调。 |
| [Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)](#oh_print_startprintbynative) | - | 拉起打印预览界面接口。 |

## 枚举类型说明

### Print_ErrorCode

```c
enum Print_ErrorCode
```

**描述**

枚举错误码。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PRINT_ERROR_NONE = 0 | 成功。 |
| PRINT_ERROR_NO_PERMISSION = 201 | 没有权限。 |
| PRINT_ERROR_INVALID_PARAMETER = 401 | 无效参数。 |
| PRINT_ERROR_GENERIC_FAILURE = 24300001 | 内部错误。 |
| PRINT_ERROR_RPC_FAILURE = 24300002 | rpc传输错误。 |
| PRINT_ERROR_SERVER_FAILURE = 24300003 | 打印服务错误。 |
| PRINT_ERROR_INVALID_EXTENSION = 24300004 | 无效打印扩展。 |
| PRINT_ERROR_INVALID_PRINTER = 24300005 | 无效打印机。 |
| PRINT_ERROR_INVALID_PRINT_JOB = 24300006 | 无效打印任务。 |
| PRINT_ERROR_FILE_IO = 24300007 | 文件读写错误。 |
| PRINT_ERROR_UNKNOWN = 24300255 | 未知错误。 |

### Print_JobDocAdapterState

```c
enum Print_JobDocAdapterState
```

**描述**

打印文档任务的状态。

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY = 0 | 打印预览界面销毁。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_SUCCEED = 1 | 打印任务执行成功。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_FAIL = 2 | 打印任务执行失败。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_CANCEL = 3 | 打印任务被取消。 |
| PRINT_DOC_ADAPTER_PRINT_TASK_BLOCK = 4 | 打印任务阻塞。 |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_CANCELED = 5 | 预览界面点击取消按钮界面退出。 |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_STARTED = 6 | 预览界面点击打印按钮界面退出。 |


## 函数说明

### Print_WriteResultCallback()

```c
typedef void(*Print_WriteResultCallback)(const char *jobId, uint32_t code)
```

**描述**

文件回写回调。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *jobId | 打印任务id。 |
|  uint32_t code | 文件回写结果。 |

### Print_OnStartLayoutWrite()

```c
typedef void(*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)
```

**描述**

文件开始回写回调函数。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *jobId | 打印任务id。 |
|  uint32_t fd | 回写的文件句柄。 |
| [ const Print_PrintAttributes](capi-oh-print-print-printattributes.md) *oldAttrs | 用户设置打印参数变化前的参数。 |
| [ const Print_PrintAttributes](capi-oh-print-print-printattributes.md) *newAttrs | 用户设置打印参数变化后的参数。 |
| [ Print_WriteResultCallback](capi-ohprint-h.md#print_writeresultcallback) writeCallback | 使用方回写完文件后调用回调函数通知打印服务。 |

### Print_OnJobStateChanged()

```c
typedef void(*Print_OnJobStateChanged)(const char *jobId, uint32_t state)
```

**描述**

打印任务状态回调。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *jobId | 打印任务id。 |
|  uint32_t state | 当前任务状态。 |

### OH_Print_StartPrintByNative()

```c
Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)
```

**描述**

拉起打印预览界面接口。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *printJobName | 打印任务名称。 |
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) printDocCallback | 打印文档任务回调结构体。 |
| void *context | 调用接口的ability的上下文。 |

**返回：**

| 类型 | 说明                                                                                                                                                                                                                                                                |
| -- |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | 返回 [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) 执行成功。<br>         [PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode) 需要配置 ohos.permission.PRINT 权限。<br>         [PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode) 无法连接打印服务。 |


