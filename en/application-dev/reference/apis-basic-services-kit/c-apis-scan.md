# ohscan.h

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @RayShih-->

## Overview

Enables applications to use CAPI to access scanners.

**Since**: 12

**Library**: libohscan.so

**System capability**: SystemCapability.Print.PrintFramework


## Summary


### Types

| Name| Description|
| -------- | -------- |
| [Scan_ScannerDevice](#scan_scannerdevice) | Defines the device information of a scanner.|
| [Scan_PictureScanProgress](#scan_picturescanprogress) | Defines the image scanning progress.|
| [Scan_ScannerOptions](#scan_scanneroptions) | Defines the scanner options.|
| [Scan_ScannerDiscoveryCallback](#scan_scannerdiscoverycallback) | Defines a callback to be invoked when a scanner is discovered.|


### Enums

| Name| Description|
| -------- | -------- |
| [Scan_ErrorCode](#scan_errorcode) | Enumerates the error codes.|


### Functions

| Name| Description|
| -------- | -------- |
| [OH_Scan_Init](#oh_scan_init) | Starts the scanning service, initializes the client, and establishes a connection with the scanning service.|
| [OH_Scan_StartScannerDiscovery](#oh_scan_startscannerdiscovery) | Searches for scanners and registers a callback function to process the found scanners.|
| [OH_Scan_OpenScanner](#oh_scan_openscanner) | Connects to a scanner.|
| [OH_Scan_CloseScanner](#oh_scan_closescanner) | Disconnects from the scanner.|
| [OH_Scan_GetScannerParameter](#oh_scan_getscannerparameter) | Obtains scanner settings.|
| [OH_Scan_SetScannerParameter](#oh_scan_setscannerparameter) | Sets the option parameters of the scanner.|
| [OH_Scan_StartScan](#oh_scan_startscan) | Starts the scanner.|
| [OH_Scan_CancelScan](#oh_scan_cancelscan) | Cancels scanning.|
| [OH_Scan_GetPictureScanProgress](#oh_scan_getpicturescanprogress) | Queries the image scanning progress.|
| [OH_Scan_Exit](#oh_scan_exit) | Exits the scanning service and releases the client memory.|


## Type Description


### Scan_ScannerDevice

**Description**

Defines the device information of a scanner.

**Since**: 12

| Member        | Description    |
| ------------ | -------- |
| scannerId    | Scanner ID.|
| manufacturer | Manufacturer.  |
| model        | Device model.|
| discoverMode | Device discovery mode.|
| serialNumber | Serial number.  |

### Scan_PictureScanProgress

**Description**

Defines the image scanning progress.

**Since**: 12

| Member    | Description                   |
| -------- | ----------------------- |
| progress | Image scanning progress. The value ranges from 0 to 100.|
| fd       | Image file handle.           |
| isFinal  | Whether the next image is available.       |

### Scan_ScannerOptions

**Description**

Defines the scanner options.

**Since**: 12

| Member        | Description        |
| ------------ | ------------ |
| titles       | Option titles.    |
| descriptions | Descriptions of options.|
| ranges       | Option ranges.    |
| optionCount  | Number of options.    |

### Scan_ScannerDiscoveryCallback

**Description**

Defines a callback to be invoked when a scanner is discovered.

**Since**: 12

| Parameter       | Description      |
| ----------- | ---------- |
| devices     | Scanner.|
| deviceCount | Number of scanners.  |



## Enum Description


### Scan_ErrorCode

**Description**

Enumerates the error codes.

**Since**: 12

| Value| Description|
| -- | -- |
| SCAN_ERROR_NONE = 0 | Operation successful.|
| SCAN_ERROR_NO_PERMISSION = 201 | Permission denied.|
| SCAN_ERROR_INVALID_PARAMETER = 401 | Invalid parameter.|
| SCAN_ERROR_GENERIC_FAILURE = 24300101 | Internal error.|
| SCAN_ERROR_RPC_FAILURE = 24300102 | RPC communication error.|
| SCAN_ERROR_SERVER_FAILURE = 24300103 | Server error.|
| SCAN_ERROR_UNSUPPORTED = 24300104 | Operation not supported.|
| SCAN_ERROR_CANCELED = 24300105 | Operation canceled.|
| SCAN_ERROR_DEVICE_BUSY = 24300106 | Device busy.|
| SCAN_ERROR_INVALID = 24300107 | Invalid operation.|
| SCAN_ERROR_JAMMED = 24300108 | Paper jam in feeder.|
| SCAN_ERROR_NO_DOCS = 24300109 | Out of paper.|
| SCAN_ERROR_COVER_OPEN = 24300110 | Scanner cover opened.|
| SCAN_ERROR_IO_ERROR = 24300111 | Scanner I/O operation error.|
| SCAN_ERROR_NO_MEMORY = 24300112 | Insufficient memory.|


## Function Description


### OH_Scan_Init()

```cpp
int32_t OH_Scan_Init();
```

**Description**

Starts the scanning service, initializes the client, and establishes a connection with the scanning service.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

### OH_Scan_StartScannerDiscovery()

```cpp
int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback);
```

**Description**

Searches for scanners and registers a callback function to process the found scanners.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name    | Description                      |
| -------- | -------------------------- |
| callback | Callback function for scanner discovery.|

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

### OH_Scan_OpenScanner()

```cpp
int32_t OH_Scan_OpenScanner(const char* scannerId);
```

**Description**

Connects to a scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name     | Description      |
| --------- | ---------- |
| scannerId | Scanner ID.|

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_DEVICE_BUSY**: Scanner busy.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.

**SCAN_ERROR_IO_ERROR**: Scanner I/O operation error.

**SCAN_ERROR_NO_MEMORY**: Insufficient scanner memory.

### OH_Scan_CloseScanner()

```cpp
int32_t OH_Scan_CloseScanner(const char* scannerId);
```

**Description**

Disconnects from the scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name     | Description      |
| --------- | ---------- |
| scannerId | Scanner ID.|

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.

### OH_Scan_GetScannerParameter()

```cpp
Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode);
```

**Description**

Obtains the scanner setting options. The memory is automatically released when returned structure points to [OH_Scan_Exit](#oh_scan_exit). Only one copy of each scanner model is stored in the memory.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name     | Description      |
| --------- | ---------- |
| scannerId | Scanner ID.|
| errorCode | Error code.    |

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.

### OH_Scan_SetScannerParameter()

```cpp
int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value);
```

**Description**

Sets the option parameters of the scanner. The option values are obtained through the [OH_Scan_GetScannerParameter](#oh_scan_getscannerparameter) API.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name     | Description      |
| --------- | ---------- |
| scannerId | Scanner ID.|
| option    | Option Number.  |
| value     | Option value.    |

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.

### OH_Scan_StartScan()

```cpp
int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode);
```

**Description**

Starts a scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name     | Description      |
| --------- | ---------- |
| scannerId | Scanner ID.|
| batchMode | Batch processing mode.|

**Returns**

**SCAN_ERROR_NONE**: Operation successful.
**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.

**SCAN_ERROR_JAMMED**: Paper jam in feeder.

**SCAN_ERROR_NO_DOCS**: Scanner out of paper.

**SCAN_ERROR_COVER_OPEN**: Scanner cover opened.

**SCAN_ERROR_IO_ERROR**: Scanner I/O operation error.

**SCAN_ERROR_NO_MEMORY**: Insufficient scanner memory.

**SCAN_ERROR_DEVICE_BUSY**: Scanner busy.

### OH_Scan_CancelScan()

```cpp
int32_t OH_Scan_CancelScan(const char* scannerId);
```

**Description**

Cancels scanning.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name     | Description      |
| --------- | ---------- |
| scannerId | Scanner ID.|

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.

### OH_Scan_GetPictureScanProgress()

```cpp
int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog);
```

**Description**

Queries the image scanning progress.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name     | Description        |
| --------- | ------------ |
| scannerId | Scanner ID.  |
| prog      | Image scanning progress.|

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.

**SCAN_ERROR_JAMMED**: Paper jam in feeder.

**SCAN_ERROR_NO_DOCS**: Scanner out of paper.

**SCAN_ERROR_COVER_OPEN**: Scanner cover opened.

**SCAN_ERROR_IO_ERROR**: Scanner I/O operation error.

**SCAN_ERROR_NO_MEMORY**: Insufficient scanner memory.

**SCAN_ERROR_DEVICE_BUSY**: Scanner busy.

### OH_Scan_Exit()

```cpp
int32_t OH_Scan_Exit();
```

**Description**

Exits the scanning service, clear the client memory, and cancel the registered scanning callback function.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Returns**

**SCAN_ERROR_NONE**: Operation successful.

**SCAN_ERROR_NO_PERMISSION**: Permission denied.

**SCAN_ERROR_RPC_FAILURE**: RPC communication error.

**SCAN_ERROR_SERVER_FAILURE**: Server error.

**SCAN_ERROR_INVALID_PARAMETER**: Invalid parameter.
