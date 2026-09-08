# ohscan.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->

## Overview

Declares APIs for discovering and connecting to scanners, scanning images, obtaining the image scanning progress, and setting scanner parameters. This module can be used to integrate scanner-related operations into an app.

**File to include**: <BasicServicesKit/ohscan.h>

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
| [typedef void (\*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)](#scan_scannerdiscoverycallback) | Scan_ScannerDiscoveryCallback | Callback for scanner discovery, which is registered using [OH_Scan_StartScannerDiscovery](#oh_scan_startscannerdiscovery). The memory pointed to by the **devices** pointer will be released when the callback ends.|
| [int32_t OH_Scan_Init()](#oh_scan_init) | - | Initiates the scan service, initializes the scan client, and connects the client to the scan service.|
| [int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)](#oh_scan_startscannerdiscovery) | - | Starts scanner discovery and registers a callback used to process the discovered scanners.|
| [int32_t OH_Scan_OpenScanner(const char* scannerId)](#oh_scan_openscanner) | - | Opens a scanner.|
| [int32_t OH_Scan_CloseScanner(const char* scannerId)](#oh_scan_closescanner) | - | Closes a connected scanner.|
| [Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)](#oh_scan_getscannerparameter) | - | Obtains scanner settings. The memory to which the returned struct pointer points is automatically released when [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) is called. Only one copy of each scanner model is stored in the memory.|
| [int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)](#oh_scan_setscannerparameter) | - | Sets the option parameters of the scanner. The input options and values are obtained from [OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter).|
| [int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)](#oh_scan_startscan) | - | Starts a scanning task of the scanner.|
| [int32_t OH_Scan_CancelScan(const char* scannerId)](#oh_scan_cancelscan) | - | Cancels an ongoing scanning task of the scanner.|
| [int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)](#oh_scan_getpicturescanprogress) | - | Obtains the progress of scanning a picture by the scanner. A non-null value must be passed for **prog**. The scan progress will be written into the struct pointed to by the **prog** pointer.|
| [int32_t OH_Scan_Exit()](#oh_scan_exit) | - | Exits the scan service, releases the memory of the scan framework, and deregisters the scanner discovery callback.|

## Enum Description

### Scan_ErrorCode

```cpp
enum Scan_ErrorCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| SCAN_ERROR_NONE = 0 | Operation successful.|
| SCAN_ERROR_NO_PERMISSION = 201 | Permission verification failed. Request the required permissions.|
| SCAN_ERROR_INVALID_PARAMETER = 401 | Invalid parameter. For example, the pointer or string is null. Check whether the input parameter is valid.|
| SCAN_ERROR_GENERIC_FAILURE = 24300101 | A generic internal error occurred. Try again later.|
| SCAN_ERROR_RPC_FAILURE = 24300102 | RPC communication error. Check the scanning service status and try again.|
| SCAN_ERROR_SERVER_FAILURE = 24300103 | An error occurred during scanning. Try again later.|
| SCAN_ERROR_UNSUPPORTED = 24300104 | The operation is not supported. Check whether the current scanner supports this operation.|
| SCAN_ERROR_CANCELED = 24300105 | The operation has been canceled. Start scanning again.|
| SCAN_ERROR_DEVICE_BUSY = 24300106 | The scanner is busy. Try again later.|
| SCAN_ERROR_INVALID = 24300107 | Invalid data (for example, no device is available when the scanner is started). Check the scanner connection status.|
| SCAN_ERROR_JAMMED = 24300108 | Paper jammed at the paper feeder. Remove the jammed paper and try again.|
| SCAN_ERROR_NO_DOCS = 24300109 | Out of paper. Place paper in the feeder and try again.|
| SCAN_ERROR_COVER_OPEN = 24300110 | The scanner cover is open. Close the cover and try again.|
| SCAN_ERROR_IO_ERROR = 24300111 | Scanner I/O error. Check the scanner connection and try again.|
| SCAN_ERROR_NO_MEMORY = 24300112 | Insufficient memory. Release resources and try again.|


## Function Description

### Scan_ScannerDiscoveryCallback()

```cpp
typedef void (*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)
```

**Description**

Callback for scanner discovery, which is registered using [OH_Scan_StartScannerDiscovery](#oh_scan_startscannerdiscovery).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md)** devices | List of all discovered scanners. The memory pointed to by the **devices** pointer will be released when the callback ends.|
|  int32_t deviceCount | Number of scanners discovered.|

### OH_Scan_Init()

```cpp
int32_t OH_Scan_Init()
```

**Description**

Initiates the scan service, initializes the scan client, and connects the client to the scan service. Call this API to initialize the scan service before calling other scan APIs. After using the service, call [OH_Scan_Exit](#oh_scan_exit) to release resources.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Returns**

| Type| Description                                                                                                                                                                                                                                                                                                   |
| -- |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.|

### OH_Scan_StartScannerDiscovery()

```cpp
int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)
```

**Description**

Starts scanner discovery and registers a callback used to process the discovered scanners. Call [OH_Scan_Exit](#oh_scan_exit) to unregister the callback.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [Scan_ScannerDiscoveryCallback](#scan_scannerdiscoverycallback) callback | [Scan_ScannerDiscoveryCallback](#scan_scannerdiscoverycallback) for the scanner discovery event. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.|

### OH_Scan_OpenScanner()

```cpp
int32_t OH_Scan_OpenScanner(const char* scannerId)
```

**Description**

Opens a scanner. After using the scanner, call [OH_Scan_CloseScanner](#oh_scan_closescanner) to close it.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | ID of the scanner to connect. The value must be the ID of a valid scanner that has been discovered.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.<br>         [SCAN_ERROR_DEVICE_BUSY](#scan_errorcode): The scanner is busy.<br>         [SCAN_ERROR_INVALID_PARAMETER](#scan_errorcode): The input parameter is invalid.<br>         [SCAN_ERROR_IO_ERROR](#scan_errorcode): An error occurs during the communication with the scanner.<br>         [SCAN_ERROR_NO_MEMORY](#scan_errorcode): The memory is insufficient.|

### OH_Scan_CloseScanner()

```cpp
int32_t OH_Scan_CloseScanner(const char* scannerId)
```

**Description**

Closes a connected scanner. Generally, this API is called to disconnect the scanner after it is used.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | ID of the scanner to disconnect. The value must be the ID of a valid scanner that has been connected.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.<br>         [SCAN_ERROR_INVALID_PARAMETER](#scan_errorcode): The input parameter is invalid.|

### OH_Scan_GetScannerParameter()

```cpp
Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)
```

**Description**

Obtains scanner settings. The memory to which the returned struct pointer points is automatically released when [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) is called. Only one copy of each scanner model is stored in the memory.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description                                                                                                   |
| -- |-------------------------------------------------------------------------------------------------------|
| const char* scannerId | ID of the scanner whose parameters are to be obtained. The value must be the ID of a valid scanner that has been connected.|
| int32_t* errorCode | The value cannot be null. Pointer to the error code. If the operation is successful, [SCAN_ERROR_NONE](#scan_errorcode) is returned; otherwise, a specific error code is returned. For details, see [Scan_ErrorCode](#scan_errorcode).|

**Returns**

| Type| Description|
| -- | -- |
| [Scan_ScannerOptions*](capi-oh-scan-scan-scanneroptions.md) | Pointer to the scanner parameter struct when the operation is successful, which can be used to obtain and set scanner parameters. **NULL** is returned when the operation fails.|

### OH_Scan_SetScannerParameter()

```cpp
int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)
```

**Description**

Sets the option parameters of the scanner. The input options and values are obtained from [OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter).

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | ID of the scanner whose options are to be set. The value must be the ID of a valid scanner that has been connected.|
| const int32_t option | ID of the option to be set. The value is obtained from [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md). The value ranges from 0 to **optionCount** – 1.|
| const char* value | Pointer to the option value to be set. The valid value is obtained from **ranges** of [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.<br>         [SCAN_ERROR_INVALID_PARAMETER](#scan_errorcode): The input parameter is invalid.|

### OH_Scan_StartScan()

```cpp
int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)
```

**Description**

Starts a scanning task of the scanner. After the scanning service is successfully initialized and parameters have been set after the scanner is connected, you can call this API to start scanning. During scanning, you can call [OH_Scan_GetPictureScanProgress](#oh_scan_getpicturescanprogress) to obtain the scanning progress and call [OH_Scan_CancelScan](#oh_scan_cancelscan) to cancel the scanning.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | ID of the scanner whose scanning task is to be started. The scanner must be a valid scanner that has been connected.|
| bool batchMode | Whether to start the scanner in batch processing mode. **true** indicates that the batch processing mode is enabled, and the scanner can continuously scan multiple pages of documents (usually through the paper feeder). **false** indicates that the batch processing mode is disabled, and only a single page is scanned.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.<br>         [SCAN_ERROR_JAMMED](#scan_errorcode): paper jammed in the feeder.<br>         [SCAN_ERROR_NO_DOCS](#scan_errorcode): out of paper.<br>         [SCAN_ERROR_COVER_OPEN](#scan_errorcode): scanner cover open.<br>         [SCAN_ERROR_IO_ERROR](#scan_errorcode): An error occurs during the communication with the scanner.<br>         [SCAN_ERROR_NO_MEMORY](#scan_errorcode): The memory is insufficient.<br>         [SCAN_ERROR_INVALID_PARAMETER](#scan_errorcode): The input parameter is invalid.<br>         [SCAN_ERROR_DEVICE_BUSY](#scan_errorcode): The scanner is busy. Try again later.|

### OH_Scan_CancelScan()

```cpp
int32_t OH_Scan_CancelScan(const char* scannerId)
```

**Description**

Cancels an ongoing scanning task of the scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | ID of the scanner whose scanning task is to be canceled. The scanner must be a valid scanner that has been connected.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_INVALID_PARAMETER](#scan_errorcode): The input parameter is invalid.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.|

### OH_Scan_GetPictureScanProgress()

```cpp
int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)
```

**Description**

Obtains the progress of scanning a picture by the scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char* scannerId | ID of the scanner whose image scanning progress is to be queried. The scanner must be a valid scanner that has been connected.|
| [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md)* prog | [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md) of the scanned image. A non-null value must be passed. The scanning progress will be written into the struct pointed to by the **prog** pointer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [**SCAN_ERROR_NONE**](#scan_errorcode): The scanner has successfully queried the image scan progress.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_INVALID_PARAMETER](#scan_errorcode): The input parameter is invalid.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.<br>         [SCAN_ERROR_JAMMED](#scan_errorcode): paper jammed in the feeder.<br>         [SCAN_ERROR_NO_DOCS](#scan_errorcode): out of paper.<br>         [SCAN_ERROR_COVER_OPEN](#scan_errorcode): scanner cover open.<br>         [SCAN_ERROR_IO_ERROR](#scan_errorcode): An error occurs during the communication with the scanner.<br>         [SCAN_ERROR_NO_MEMORY](#scan_errorcode): The memory is insufficient.<br>         [SCAN_ERROR_DEVICE_BUSY](#scan_errorcode): The scanner is busy. Try again later.|

### OH_Scan_Exit()

```cpp
int32_t OH_Scan_Exit()
```

**Description**

Exits the scan service, releases the memory of the scan framework, and deregisters the scanner discovery callback. After the scan service exits, other scan APIs cannot be called.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](#scan_errorcode): The operation is successful.<br>         [SCAN_ERROR_NO_PERMISSION](#scan_errorcode): The permission is denied.<br>         [SCAN_ERROR_RPC_FAILURE](#scan_errorcode): RPC communication error.<br>         [SCAN_ERROR_SERVER_FAILURE](#scan_errorcode): An error occurs during the scanning.|
