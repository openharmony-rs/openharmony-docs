# ohprint.h
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

## Overview

Declares APIs for discovering and connecting to printers, printing files, and querying the list of added printers and printer information.

**File to include**: <BasicServicesKit/ohprint.h>

**Library**: libohprint.so

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Print_Margin](capi-oh-print-print-margin.md) | Print_Margin | Defines the page margin.|
| [Print_PageSize](capi-oh-print-print-pagesize.md) | Print_PageSize | Defines the page size.|
| [Print_Range](capi-oh-print-print-range.md) | Print_Range | Defines the range to print.|
| [Print_PrintAttributes](capi-oh-print-print-printattributes.md) | Print_PrintAttributes | Defines the print attributes.|
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) | Print_PrintDocCallback | Defines the print job callback struct.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Print_ErrorCode](#print_errorcode) | Print_ErrorCode | Enumerates the error codes.|
| [Print_JobDocAdapterState](#print_jobdocadapterstate) | Print_JobDocAdapterState | Enumerates the print job states.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void(\*Print_WriteResultCallback)(const char *jobId, uint32_t code)](#print_writeresultcallback) | Print_WriteResultCallback | Defines a callback used to return the file write-back result.|
| [typedef void(\*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)](#print_onstartlayoutwrite) | Print_OnStartLayoutWrite | Defines a callback to be invoked when the file write-back starts.|
| [typedef void(\*Print_OnJobStateChanged)(const char *jobId, uint32_t state)](#print_onjobstatechanged) | Print_OnJobStateChanged | Defines a callback to be invoked when the print job state changes.|
| [Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)](#oh_print_startprintbynative) | - | Defines a callback used to open the print preview page.|

## Enum Description

### Print_ErrorCode

```c
enum Print_ErrorCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| PRINT_ERROR_NONE = 0 | Operation successful.|
| PRINT_ERROR_NO_PERMISSION = 201 | Permission denied.|
| PRINT_ERROR_INVALID_PARAMETER = 401 | Invalid parameter.|
| PRINT_ERROR_GENERIC_FAILURE = 24300001 | Internal error.|
| PRINT_ERROR_RPC_FAILURE = 24300002 | RPC transmission failed.|
| PRINT_ERROR_SERVER_FAILURE = 24300003 | Print service failed.|
| PRINT_ERROR_INVALID_EXTENSION = 24300004 | Invalid print extension.|
| PRINT_ERROR_INVALID_PRINTER = 24300005 | Invalid printer.|
| PRINT_ERROR_INVALID_PRINT_JOB = 24300006 | Invalid print job.|
| PRINT_ERROR_FILE_IO = 24300007 | File I/O error.|
| PRINT_ERROR_UNKNOWN = 24300255 | Unknown error.|

### Print_JobDocAdapterState

```c
enum Print_JobDocAdapterState
```

**Description**

Enumerates the print job states.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY = 0 | Print preview page destroyed.|
| PRINT_DOC_ADAPTER_PRINT_TASK_SUCCEED = 1 | Print job succeeded.|
| PRINT_DOC_ADAPTER_PRINT_TASK_FAIL = 2 | Print job failed.|
| PRINT_DOC_ADAPTER_PRINT_TASK_CANCEL = 3 | Print job canceled.|
| PRINT_DOC_ADAPTER_PRINT_TASK_BLOCK = 4 | Print job blocked.|
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_CANCELED = 5 | Print preview page closed by the cancel button click.|
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_STARTED = 6 | Print preview page closed by the print button click.|


## Function Description

### Print_WriteResultCallback()

```c
typedef void(*Print_WriteResultCallback)(const char *jobId, uint32_t code)
```

**Description**

Defines a callback used to return the file write-back result.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| const char *jobId | Print job ID.|
|  uint32_t code | File write-back result.|

### Print_OnStartLayoutWrite()

```c
typedef void(*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)
```

**Description**

Defines a callback to be invoked when the file write-back starts.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| const char *jobId | Print job ID.|
|  uint32_t fd | File handle for write-back.|
| [ const Print_PrintAttributes](capi-oh-print-print-printattributes.md) *oldAttrs | Print parameter before change.|
| [ const Print_PrintAttributes](capi-oh-print-print-printattributes.md) *newAttrs | Print parameter after change.|
| [ Print_WriteResultCallback](capi-ohprint-h.md#print_writeresultcallback) writeCallback | Callback used to return the file write-back result.|

### Print_OnJobStateChanged()

```c
typedef void(*Print_OnJobStateChanged)(const char *jobId, uint32_t state)
```

**Description**

Defines a callback to be invoked when the print job state changes.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| const char *jobId | Print job ID.|
|  uint32_t state | Current print job state.|

### OH_Print_StartPrintByNative()

```c
Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)
```

**Description**

Defines a callback used to open the print preview page.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| const char *printJobName | Print job name.|
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) printDocCallback | Print job callback struct.|
| void *context | Context of the ability that calls the API.|

**Returns**

| Type| Description                                                                                                                                                                                                                                                               |
| -- |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Print_ErrorCode](capi-ohprint-h.md#print_errorcode) | [Print_ErrorCode](capi-ohprint-h.md#print_errorcode): operation successful.<br>[PRINT_ERROR_NO_PERMISSION](capi-ohprint-h.md#print_errorcode): no permission. The ohos.permission.PRINT permission is required.<br>[PRINT_ERROR_RPC_FAILURE](capi-ohprint-h.md#print_errorcode): Failed to connect to the print service.|
