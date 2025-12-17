# ohscan.h
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

## Overview

Declares APIs for discovering and connecting to scanners, scanning pictures, querying the scan progress, and setting parameters for scanning.

**Library**: libohscan.so

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [OH_Scan](capi-oh-scan.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md) | Scan_ScannerDevice | Defines scanner information.|
| [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md) | Scan_PictureScanProgress | Defines the progress of scanning a picture by the scanner.|
| [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md) | Scan_ScannerOptions | Defines all parameter options of a scanner.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Scan_ErrorCode](#scan_errorcode) | Scan_ErrorCode | Enumerates the error codes.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)](#scan_scannerdiscoverycallback) | Scan_ScannerDiscoveryCallback | Discovers scanners. The memory pointed to by the pointer registered via [OH_Scan_StartScannerDiscovery](capi-ohscan-h.md#oh_scan_startscannerdiscovery) will be released when the callback function ends.|
| [int32_t OH_Scan_Init()](#oh_scan_init) | - | Initiates the scan service, initializes the scan client, and connects the client to the scan service.|
| [int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)](#oh_scan_startscannerdiscovery) | - | Starts scanner discovery and registers a callback used to process the discovered scanners.|
| [int32_t OH_Scan_OpenScanner(const char* scannerId)](#oh_scan_openscanner) | - | Opens a scanner.|
| [int32_t OH_Scan_CloseScanner(const char* scannerId)](#oh_scan_closescanner) | - | Closes a connected scanner.|
| [Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)](#oh_scan_getscannerparameter) | - | Obtains the scanner setting options. The memory to which the returned struct pointer points is automatically released when [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) is called. Only one copy of each scanner model is stored in the memory.|
| [int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)](#oh_scan_setscannerparameter) | - | Sets the option parameters of a scanner. The option values are obtained through the [OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter) API.|
| [int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)](#oh_scan_startscan) | - | Starts scanning.|
| [int32_t OH_Scan_CancelScan(const char* scannerId)](#oh_scan_cancelscan) | - | Cancels scanning.|
| [int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)](#oh_scan_getpicturescanprogress) | - | Obtains the progress of scanning a picture by the scanner. A non-null value must be passed. The scan progress will be written into the struct pointed to by the pointer.|
| [int32_t OH_Scan_Exit()](#oh_scan_exit) | - | Exits the scan service, releases the memory of the scan framework, and deregisters the scanner discovery callback.|

## Enum Description

### Scan_ErrorCode

```
enum Scan_ErrorCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| SCAN_ERROR_NONE = 0 | Operation successful.|
| SCAN_ERROR_NO_PERMISSION = 201 | Permission verification failed.|
| SCAN_ERROR_INVALID_PARAMETER = 401 | Invalid parameter. For example, the pointer or string is null.|
| SCAN_ERROR_GENERIC_FAILURE = 24300101 | Internal error.|
| SCAN_ERROR_RPC_FAILURE = 24300102 | RPC communication error.|
| SCAN_ERROR_SERVER_FAILURE = 24300103 | Server error.|
| SCAN_ERROR_UNSUPPORTED = 24300104 | Unsupported operation.|
| SCAN_ERROR_CANCELED = 24300105 | Operation canceled.|
| SCAN_ERROR_DEVICE_BUSY = 24300106 | Device busy.|
| SCAN_ERROR_INVALID = 24300107 | Invalid data (for example, no device is available when the scanner is started).|
| SCAN_ERROR_JAMMED = 24300108 | Paper jam in feeder.|
| SCAN_ERROR_NO_DOCS = 24300109 | Out of paper.|
| SCAN_ERROR_COVER_OPEN = 24300110 | Scanner cover open.|
| SCAN_ERROR_IO_ERROR = 24300111 | Scanner I/O error.|
| SCAN_ERROR_NO_MEMORY = 24300112 | Insufficient memory.|


## Function Description

### Scan_ScannerDiscoveryCallback()

```
typedef void (*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)
```

**Description**

Discovers scanners. The memory pointed to by the pointer registered via [OH_Scan_StartScannerDiscovery](capi-ohscan-h.md#oh_scan_startscannerdiscovery) will be released when the callback function ends.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md)** devices | Double pointer to the list of all discovered scanners.|
|  int32_t deviceCount | Number of scanners discovered.|

### OH_Scan_Init()

```
int32_t OH_Scan_Init()
```

**Description**

Initiates the scan service, initializes the scan client, and connects the client to the scan service.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Returns**

| Type| Description                                                                                                                                                                                                                                                                                                   |
| -- |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.|

### OH_Scan_StartScannerDiscovery()

```
int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)
```

**Description**

Starts scanner discovery and registers a callback used to process the discovered scanners.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [Scan_ScannerDiscoveryCallback](capi-ohscan-h.md#scan_scannerdiscoverycallback) callback | Callback used to discover scanners.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.|

### OH_Scan_OpenScanner()

```
int32_t OH_Scan_OpenScanner(const char* scannerId)
```

**Description**

Opens a scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | Pointer to the scanner ID.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.<br>         [SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode): device busy.<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode): invalid parameter.<br>         [SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode): scanner I/O error.<br>         [SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode): insufficient memory.|

### OH_Scan_CloseScanner()

```
int32_t OH_Scan_CloseScanner(const char* scannerId)
```

**Description**

Closes a connected scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | Pointer to the scanner ID.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode): invalid parameter.|

### OH_Scan_GetScannerParameter()

```
Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)
```

**Description**

Obtains the scanner setting options. The memory to which the returned struct pointer points is automatically released when [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) is called. Only one copy of each scanner model is stored in the memory.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description                                                                                                   |
| -- |-------------------------------------------------------------------------------------------------------|
| const char* scannerId | Pointer to the scanner ID.                                                                                         |
| int32_t* errorCode | Pointer to the error code. If the operation is successful, [Scan_ERROR_NONE](#scan_errorcode) is returned; otherwise, a specific error code is returned. For details, see [Print_ErrorCode](capi-ohprint-h.md#print_errorcode).|

**Returns**

| Type| Description|
| -- | -- |
| [Scan_ScannerOptions*](capi-oh-scan-scan-scanneroptions.md) | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode): invalid parameter.|

### OH_Scan_SetScannerParameter()

```
int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)
```

**Description**

Sets the option parameters of a scanner. The option values are obtained through the [OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter) API.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | Pointer to the scanner ID.|
| const int32_t option | ID of the option to be set. The value, obtained from [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md), ranges from 0 to *optionCount* – 1.|
| const char* value | Pointer to the option value to be set. The valid value is obtained from **ranges** of [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode): invalid parameter.|

### OH_Scan_StartScan()

```
int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)
```

**Description**

Starts scanning.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: code ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | Pointer to the scanner ID.|
| bool batchMode | Whether to start the scanner in batch processing mode.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.<br>         [SCAN_ERROR_JAMMED](capi-ohscan-h.md#scan_errorcode): paper jam in feeder.<br>         [SCAN_ERROR_NO_DOCS](capi-ohscan-h.md#scan_errorcode): out of paper.<br>         [SCAN_ERROR_COVER_OPEN](capi-ohscan-h.md#scan_errorcode): scanner cover open.<br>         [SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode): scanner I/O error.<br>         [SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode): insufficient memory.<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode): invalid parameter.<br>         [SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode): device busy.|

### OH_Scan_CancelScan()

```
int32_t OH_Scan_CancelScan(const char* scannerId)
```

**Description**

Cancels scanning.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | Pointer to the scanner ID.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode): invalid parameter.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.|

### OH_Scan_GetPictureScanProgress()

```
int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)
```

**Description**

Obtains the progress of scanning a picture by the scanner. A non-null value must be passed. The scan progress will be written into the struct pointed to by the pointer.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | Pointer to the scanner ID.|
| [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md)* prog | Pointer to [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md). The value cannot be empty.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode): invalid parameter.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.<br>         [SCAN_ERROR_JAMMED](capi-ohscan-h.md#scan_errorcode): paper jam in feeder.<br>         [SCAN_ERROR_NO_DOCS](capi-ohscan-h.md#scan_errorcode): out of paper.<br>         [SCAN_ERROR_COVER_OPEN](capi-ohscan-h.md#scan_errorcode): scanner cover open.<br>         [SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode): scanner I/O error.<br>         [SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode): insufficient memory.<br>         [SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode): device busy.|

### OH_Scan_Exit()

```
int32_t OH_Scan_Exit()
```

**Description**

Exits the scan service, releases the memory of the scan framework, and deregisters the scanner discovery callback.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode): operation successful.<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode): permission denied.<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode): server error.|
