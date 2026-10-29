# ohprint.h
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

## Overview

Declares APIs for discovering and connecting to printers, printing files, and querying the list of added printers and printer information. This module can be used to integrate the printing capability to an app, helping developers conveniently manage the printing process, including printer discovery, connection, task delivery, and status monitoring.

**File to include**: &lt;BasicServicesKit/ohprint.h&gt;

**Library**: libohprint.so

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-oh-print.md)

## Summary

### Structs

| Name                                                        | typedef Keyword          | Description                           |
| ------------------------------------------------------------ | ----------------------- | ------------------------------- |
| [Print_StringList](capi-oh-print-print-stringlist.md)        | Print_StringList        | Defines a struct for the string list.               |
| [Print_Property](capi-oh-print-print-property.md)            | Print_Property          | Defines a struct for the printer property.               |
| [Print_PropertyList](capi-oh-print-print-propertylist.md)    | Print_PropertyList      | Defines a struct for the printer property list.               |
| [Print_Resolution](capi-oh-print-print-resolution.md)        | Print_Resolution        | Defines a struct for the printing resolution in dpi.|
| [Print_Margin](capi-oh-print-print-margin.md)                | Print_Margin            | Defines a struct for the page margin to print.                 |
| [Print_PageSize](capi-oh-print-print-pagesize.md)            | Print_PageSize          | Defines a struct for the page size.             |
| [Print_PrinterCapability](capi-oh-print-print-printercapability.md) | Print_PrinterCapability | Defines a struct for the printer capabilities.               |
| [Print_DefaultValue](capi-oh-print-print-defaultvalue.md)    | Print_DefaultValue      | Defines a struct for the default property value.                 |
| [Print_PrinterInfo](capi-oh-print-print-printerinfo.md)      | Print_PrinterInfo       | Defines a struct for the printer information.               |
| [Print_PrintJob](capi-oh-print-print-printjob.md)            | Print_PrintJob          | Defines a struct for the print job.           |
| [Print_Range](capi-oh-print-print-range.md)                  | Print_Range             | Defines a struct for the page range to print.           |
| [Print_PrintAttributes](capi-oh-print-print-printattributes.md) | Print_PrintAttributes   | Defines a struct for the print attributes.           |
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) | Print_PrintDocCallback  | Defines a struct for the print job status callback.   |

### Enums

| Name                                                 | typedef Keyword           | Description                        |
| ----------------------------------------------------- | ------------------------ | ---------------------------- |
| [Print_ErrorCode](#print_errorcode)                   | Print_ErrorCode          | Enumerates the error codes.                |
| [Print_PrinterState](#print_printerstate)             | Print_PrinterState       | Enumerates the printer states.            |
| [Print_DiscoveryEvent](#print_discoveryevent)         | Print_DiscoveryEvent     | Enumerates the printer discovery events.        |
| [Print_PrinterEvent](#print_printerevent)             | Print_PrinterEvent       | Enumerates the printer change events.        |
| [Print_DuplexMode](#print_duplexmode)                 | Print_DuplexMode         | Enumerates the duplex modes.          |
| [Print_ColorMode](#print_colormode)                   | Print_ColorMode          | Enumerates the color modes.              |
| [Print_OrientationMode](#print_orientationmode)       | Print_OrientationMode    | Enumerates the orientation modes.              |
| [Print_Quality](#print_quality)                       | Print_Quality            | Enumerates the print qualities.              |
| [Print_DocumentFormat](#print_documentformat)         | Print_DocumentFormat     | Enumerates the MIME types.  |
| [Print_JobDocAdapterState](#print_jobdocadapterstate) | Print_JobDocAdapterState | Enumerates the print job adapter states.|
| [OH_Print_JobState](#oh_print_jobstate)               | OH_Print_JobState        | Enumerates the print job states.|

### Functions

| Name                                                        | typedef Keyword                 | Description                                                        |
| ------------------------------------------------------------ | ------------------------------ | ------------------------------------------------------------ |
| [typedef void(\*Print_WriteResultCallback)(const char *jobId, uint32_t code)](#print_writeresultcallback) | Print_WriteResultCallback      | Defines a callback used to return the file write-back result.                                            |
| [typedef void(\*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)](#print_onstartlayoutwrite) | Print_OnStartLayoutWrite       | Defines a callback to be invoked when the file write-back starts.                                          |
| [typedef void(\*Print_OnJobStateChanged)(const char *jobId, uint32_t state)](#print_onjobstatechanged) | Print_OnJobStateChanged        | Defines a callback to be invoked when the print job state changes.                                          |
| [typedef void (\*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)](#print_printerdiscoverycallback) | Print_PrinterDiscoveryCallback | Defines a callback used to return the discovered printers.                                            |
| [typedef void (\*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)](#print_printerchangecallback) | Print_PrinterChangeCallback    | Defines a callback to be invoked when a printer is changed.                                            |
| [Print_ErrorCode OH_Print_Init()](#oh_print_init)            | -                              | Checks and starts the print service, initializes the print client, and connects it with the print service.|
| [Print_ErrorCode OH_Print_Release()](#oh_print_release)      | -                              | Disconnects from the print service, unregister all registered callbacks, and releases the print client resources.|
| [Print_ErrorCode OH_Print_StartPrinterDiscovery(Print_PrinterDiscoveryCallback callback)](#oh_print_startprinterdiscovery) | -                              | Starts printer discovery.                                     |
| [Print_ErrorCode OH_Print_StopPrinterDiscovery()](#oh_print_stopprinterdiscovery) | -                              | Stops printer discovery.                                     |
| [Print_ErrorCode OH_Print_ConnectPrinter(const char *printerId)](#oh_print_connectprinter) | -                              | Connects to a printer by the printer ID.                           |
| [Print_ErrorCode OH_Print_StartPrintJob(const Print_PrintJob *printJob)](#oh_print_startprintjob) | -                              | Starts a print job.                                   |
| [Print_ErrorCode OH_Print_RegisterPrinterChangeListener(Print_PrinterChangeCallback callback)](#oh_print_registerprinterchangelistener) | -                              | Registers a listener for printer changes.                                 |
| [void OH_Print_UnregisterPrinterChangeListener()](#oh_print_unregisterprinterchangelistener) | -                              | Unregisters this listener for printer changes.                                 |
| [Print_ErrorCode OH_Print_QueryPrinterList(Print_StringList *printerIdList)](#oh_print_queryprinterlist) | -                              | Queries the list of added printers.                             |
| [void OH_Print_ReleasePrinterList(Print_StringList *printerIdList)](#oh_print_releaseprinterlist) | -                              | Releases the memory used to store the printer list.                       |
| [Print_ErrorCode OH_Print_QueryPrinterInfo(const char *printerId, Print_PrinterInfo \*\*printerInfo)](#oh_print_queryprinterinfo) | -                              | Queries printer information by printer ID.                       |
| [void OH_Print_ReleasePrinterInfo(Print_PrinterInfo *printerInfo)](#oh_print_releaseprinterinfo) | -                              | Releases the memory allocated for querying the printer information.                       |
| [Print_ErrorCode OH_Print_LaunchPrinterManager()](#oh_print_launchprintermanager) | -                              | Starts the printer management window of the system.                           |
| [Print_ErrorCode OH_Print_QueryPrinterProperties(const char *printerId, const Print_StringList *propertyKeyList, Print_PropertyList *propertyList)](#oh_print_queryprinterproperties) | -                              | Queries the printer properties based on the list of property keys.           |
| [void OH_Print_ReleasePrinterProperties(Print_PropertyList *propertyList)](#oh_print_releaseprinterproperties) | -                              | Releases the memory used to store the property list.                         |
| [Print_ErrorCode OH_Print_UpdatePrinterProperties(const char *printerId, const Print_PropertyList *propertyList)](#oh_print_updateprinterproperties) | -                              | Updates the printer properties based on the KV pairs.                   |
| [Print_ErrorCode OH_Print_RestorePrinterProperties(const char *printerId, const Print_StringList *propertyKeyList)](#oh_print_restoreprinterproperties) | -                              | Restores printer properties to the default settings based on the property key list.       |
| [Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)](#oh_print_startprintbynative) | -                              | Starts the system printing app.                           |
| [typedef void(*OH_Print_OnJobStateChanged)(const char *jobId, OH_Print_JobState state)](#oh_print_onjobstatechanged) | OH_Print_OnJobStateChanged                              | Defines a callback to be invoked when the print job state changes.                           |
| [Print_ErrorCode OH_Print_StartPrintWithJobStateCallback(const Print_PrintJob *printJob, OH_Print_OnJobStateChanged jobStateChangedCb)](#oh_print_startprintwithjobstatecallback) | -                              | Starts a print job with the callback to be invoked when the print job state changes.                           |

## Enum Description

### Print_ErrorCode

```cpp
enum Print_ErrorCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum Item                                  | Description                   |
| ---------------------------------------- | ----------------------- |
| PRINT_ERROR_NONE = 0                     | Operation successful.      |
| PRINT_ERROR_NO_PERMISSION = 201          | Permission verification failed. Ensure that the corresponding permission has been declared in the app configuration.  |
| PRINT_ERROR_INVALID_PARAMETER = 401      | Invalid parameter. Check the type and value range of the passed parameter.      |
| PRINT_ERROR_GENERIC_FAILURE = 24300001   | Generic internal error. Check the running status of the printing service and try again.  |
| PRINT_ERROR_RPC_FAILURE = 24300002       | RPC communication error. Ensure that the printing service has been started and try again.  |
| PRINT_ERROR_SERVER_FAILURE = 24300003    | Server error. Check the running status of the printing service.    |
| PRINT_ERROR_INVALID_EXTENSION = 24300004 | Invalid extension. Ensure that a valid printing extension has been installed.    |
| PRINT_ERROR_INVALID_PRINTER = 24300005   | Invalid printer. Ensure that the printer is in the list of discovered or connected printers.  |
| PRINT_ERROR_INVALID_PRINT_JOB = 24300006 | Invalid print task. Ensure that the print task information is complete and the printer is connected.|
| PRINT_ERROR_FILE_IO = 24300007           | Failure to read data from or write data to the file. Check the file path and access permission.  |
| PRINT_ERROR_UNKNOWN = 24300255           | Unknown error. Check the printing service status and try again. If the issue persists, contact technical support.      |

### Print_PrinterState

```cpp
enum Print_PrinterState
```

**Description**

Enumerates the printer states.

**Since**: 12

| Enum Item             | Description          |
| ------------------- | -------------- |
| PRINTER_IDLE        | The printer is idle.  |
| PRINTER_BUSY        | The printer is busy.    |
| PRINTER_UNAVAILABLE | The printer is unavailable.|

### Print_DiscoveryEvent

```cpp
enum Print_DiscoveryEvent
```

**Description**

Enumerates the printer discovery events.

**Since**: 12

| Enum Item                | Description            |
| ---------------------- | ---------------- |
| PRINTER_DISCOVERED = 0 | Printer discovered.    |
| PRINTER_LOST = 1       | Printer lost.    |
| PRINTER_CONNECTING = 2 | Printer connecting.|
| PRINTER_CONNECTED = 3  | Printer connected.  |

### Print_PrinterEvent

```cpp
enum Print_PrinterEvent
```

**Description**

Enumerates the printer change events.

**Since**: 12

| Enum Item                   | Description              |
| ------------------------- | ------------------ |
| PRINTER_ADDED = 0         | Printer added.    |
| PRINTER_DELETED = 1       | Printer deleted.    |
| PRINTER_STATE_CHANGED = 2 | Printer changed.|
| PRINTER_INFO_CHANGED = 3  | Printer information changed.|

### Print_DuplexMode

```cpp
enum Print_DuplexMode
```

**Description**

Enumerates the duplex modes.

**Since**: 12

| Enum Item                              | Description              |
| ------------------------------------ | ------------------ |
| DUPLEX_MODE_ONE_SIDED = 0            | Single-sided mode.        |
| DUPLEX_MODE_TWO_SIDED_LONG_EDGE = 1  | Duplex mode with flipping on long edge.|
| DUPLEX_MODE_TWO_SIDED_SHORT_EDGE = 2 | Duplex mode with flipping on short edge.|

### Print_ColorMode

```cpp
enum Print_ColorMode
```

**Description**

Enumerates the color modes.

**Since**: 12

| Enum Item                   | Description      |
| ------------------------- | ---------- |
| COLOR_MODE_MONOCHROME = 0 | B/W mode.|
| COLOR_MODE_COLOR = 1      | Color mode.|
| COLOR_MODE_AUTO = 2       | Auto mode.|

### Print_OrientationMode

```cpp
enum Print_OrientationMode
```

**Description**

Enumerates the orientation modes.

**Since**: 12

| Enum Item                                | Description          |
| -------------------------------------- | -------------- |
| ORIENTATION_MODE_PORTRAIT = 0          | Portrait mode.    |
| ORIENTATION_MODE_LANDSCAPE = 1         | Landscape mode.    |
| ORIENTATION_MODE_REVERSE_LANDSCAPE = 2 | Reverse landscape mode.|
| ORIENTATION_MODE_REVERSE_PORTRAIT = 3  | Reverse portrait mode.|
| ORIENTATION_MODE_NONE = 4              | Not specified.      |

### Print_Quality

```cpp
enum Print_Quality
```

**Description**

Enumerates the print qualities.

**Since**: 12

| Enum Item                  | Description        |
| ------------------------ | ------------ |
| PRINT_QUALITY_DRAFT = 3  | Draft-quality mode.|
| PRINT_QUALITY_NORMAL = 4 | Normal-quality mode.|
| PRINT_QUALITY_HIGH = 5   | High-quality mode.  |

### Print_DocumentFormat

```cpp
enum Print_DocumentFormat
```

**Description**

Enumerates the MIME types.

**Since**: 12

| Enum Item                    | Description                                 |
| -------------------------- | ------------------------------------- |
| DOCUMENT_FORMAT_AUTO       | application/octet-stream.|
| DOCUMENT_FORMAT_JPEG       | image/jpeg.              |
| DOCUMENT_FORMAT_PDF        | application/pdf.         |
| DOCUMENT_FORMAT_POSTSCRIPT | application/postscript.  |
| DOCUMENT_FORMAT_TEXT       | text/plain.              |

### Print_JobDocAdapterState

```cpp
enum Print_JobDocAdapterState
```

**Description**

Enumerates the print job adapter states.

**Since**: 13

| Enum Item                                                    | Description                              |
| ---------------------------------------------------------- | ---------------------------------- |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY = 0              | Print job preview destroyed.            |
| PRINT_DOC_ADAPTER_PRINT_TASK_SUCCEED = 1                   | Successful print job.                    |
| PRINT_DOC_ADAPTER_PRINT_TASK_FAIL = 2                      | Print job failed.                    |
| PRINT_DOC_ADAPTER_PRINT_TASK_CANCEL = 3                    | Print job canceled.                    |
| PRINT_DOC_ADAPTER_PRINT_TASK_BLOCK = 4                     | Print job blocked.                    |
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_CANCELED = 5 | Print job preview destroyed due to cancellation.|
| PRINT_DOC_ADAPTER_PREVIEW_ABILITY_DESTROY_FOR_STARTED = 6  | Print job preview destroyed due to startup.|

### OH_Print_JobState

```cpp
enum OH_Print_JobState
```

**Description**

Enumerates the print job states.

**Since**: 24

| Enum Item                | Description         |
| -------------------- |-------------- |
| OH_PRINT_JOB_SUCCEED = 0 | Successful print job.|
| OH_PRINT_JOB_FAIL = 1    | Print job failed.|
| OH_PRINT_JOB_CANCEL = 2  | Print job canceled.|
| OH_PRINT_JOB_BLOCK = 3   | Print job blocked.|

## Function Description

### Print_WriteResultCallback()

```cpp
typedef void(*Print_WriteResultCallback)(const char *jobId, uint32_t code)
```

**Description**

Defines a callback used to return the file write-back result.

**Since**: 13

**Parameters**

| Name             | Description           |
| ------------------- | --------------- |
| const char \*jobId | Pointer to the print job ID.|
| uint32_t code       | File write-back result. **0**: The file is successfully created. **1**: The file fails to be created. **2**: The file is successfully created but not rendered.|

### Print_OnStartLayoutWrite()

```cpp
typedef void(*Print_OnStartLayoutWrite)(const char *jobId, uint32_t fd, const Print_PrintAttributes *oldAttrs, const Print_PrintAttributes *newAttrs, Print_WriteResultCallback writeCallback)
```

**Description**

Defines a callback to be invoked when the file write-back starts.

**Since**: 13

**Parameters**

| Name                                                      | Description                |
| ------------------------------------------------------------ | -------------------- |
| const char \*jobId                                          | Pointer to the print job ID.     |
| uint32_t fd                                                  | File descriptor to write.|
| [const Print_PrintAttributes](capi-oh-print-print-printattributes.md) \*oldAttrs | Pointer to the print attributes of the previous print job.      |
| [const Print_PrintAttributes](capi-oh-print-print-printattributes.md) \*newAttrs | Pointer to the print attributes of the current print job.        |
| [Print_WriteResultCallback](#print_writeresultcallback) writeCallback | Defines a callback used to return the file write-back result.    |

### Print_OnJobStateChanged()

```cpp
typedef void(*Print_OnJobStateChanged)(const char *jobId, uint32_t state)
```

**Description**

Defines a callback to be invoked when the print job state changes.

**Since**: 13

**Parameters**

| Name             | Description                |
| ------------------- | -------------------- |
| const char \*jobId | Pointer to the print job ID.     |
| uint32_t state      | Status of the current print task. For details about the values and meanings, see [OH_Print_JobState](#oh_print_jobstate).|

### Print_PrinterDiscoveryCallback()

```cpp
typedef void (*Print_PrinterDiscoveryCallback)(Print_DiscoveryEvent event, const Print_PrinterInfo *printerInfo)
```

**Description**

Defines a callback used to return the discovered printers.

**Since**: 12

**Parameters**

| Name                                                      | Description                        |
| ------------------------------------------------------------ | ---------------------------- |
| [Print_DiscoveryEvent](#print_discoveryevent) event                                  | Printer discovery event.|
| [const Print_PrinterInfo](capi-oh-print-print-printerinfo.md) \*printerInfo | Printer information when the discovery event occurs.|

### Print_PrinterChangeCallback()

```cpp
typedef void (*Print_PrinterChangeCallback)(Print_PrinterEvent event, const Print_PrinterInfo *printerInfo)
```

**Description**

Defines a callback to be invoked when a printer is changed.

**Since**: 12

**Parameters**

| Name                                                      | Description                              |
| ------------------------------------------------------------ | ---------------------------------- |
| [Print_PrinterEvent](#print_printerevent) event                                    | Printer change event during the running of the print service.|
| [const Print_PrinterInfo](capi-oh-print-print-printerinfo.md) \*printerInfo | Printer information when the change event occurs.      |

### OH_Print_Init()

```cpp
Print_ErrorCode OH_Print_Init()
```

**Description**

Checks and starts the print service, initializes the print client, and connects it with the print service. Before calling other print APIs, you must call this API to complete initialization. Otherwise, other APIs cannot work properly because the connection to the print service is not established. After using the print service, call **OH_Print_Release()** to terminate the connection and release the print client resources. Otherwise, the connection to the print service will not be closed and the client resource leak may occur.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>             [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>             [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.<br>             [PRINT_ERROR_SERVER_FAILURE](#print_errorcode): The CUPS service fails to be started.|

### OH_Print_Release()

```cpp
Print_ErrorCode OH_Print_Release()
```

**Description**

Disconnects from the print service, unregister all registered callbacks, and releases the print client resources.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         Currently, no other error codes will be returned.|

### OH_Print_StartPrinterDiscovery()

```cpp
Print_ErrorCode OH_Print_StartPrinterDiscovery(Print_PrinterDiscoveryCallback callback)
```

**Description**

Starts printer discovery. During the discovery process, you can use **Print_PrinterDiscoveryCallback** to notify printer discovery events and obtain the printer information from **Print_PrinterInfo**. After the discovery is complete, you can call **OH_Print_StopPrinterDiscovery()** to stop the discovery process. Otherwise, the discovery process will continue, consuming system resources.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_PrinterDiscoveryCallback](#print_printerdiscoverycallback) callback | [Print_PrinterDiscoveryCallback](#print_printerdiscoverycallback) to be invoked when a printer is discovered.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode): The print extension list fails to be obtained from the BMS.<br>         [PRINT_ERROR_INVALID_EXTENSION](#print_errorcode): No available print extension is found.|

### OH_Print_StopPrinterDiscovery()

```cpp
Print_ErrorCode OH_Print_StopPrinterDiscovery()
```

**Description**

Stops printer discovery.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.|

### OH_Print_ConnectPrinter()

```cpp
Print_ErrorCode OH_Print_ConnectPrinter(const char *printerId)
```

**Description**

Connects to a printer by the printer ID.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name               | Description               |
| --------------------- | ------------------- |
| const char *printerId | ID of the printer to connect to. The printer must be in the list of discovered printers. The value cannot be null.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode): Printer does not exist in the list of discovered printers.<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode): The printer extension cannot be found.|

### OH_Print_StartPrintJob()

```cpp
Print_ErrorCode OH_Print_StartPrintJob(const Print_PrintJob *printJob)
```

**Description**

Starts a print job. Before calling this API, ensure that the printer to be used is in the list of connected printers.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [const Print_PrintJob](capi-oh-print-print-printjob.md) *printJob | Pointer to the [Print_PrintJob](capi-oh-print-print-printjob.md) instance. The value cannot be null. The referenced printer must have been connected using **OH_Print_ConnectPrinter**.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode): Printer does not exist in the list of connected printers.<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode): Failed to create a print job in the print service.<br>         [PRINT_ERROR_INVALID_PRINT_JOB](#print_errorcode): Failed to find the specified task in the task queue.|

### OH_Print_RegisterPrinterChangeListener()

```cpp
Print_ErrorCode OH_Print_RegisterPrinterChangeListener(Print_PrinterChangeCallback callback)
```

**Description**

Registers a listener for printer changes. When you no longer need to listen for printer change events, call **OH_Print_UnregisterPrinterChangeListener()** to unregister the listener. If the listener is not unregistered, it may cause unnecessary calls and resource usage.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_PrinterChangeCallback](#print_printerchangecallback) callback | Callback for printer changes, which is used to receive notifications of printer addition, deletion, status change, and information change during the running of the printing service. The value cannot be null.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.|

### OH_Print_UnregisterPrinterChangeListener()

```cpp
void OH_Print_UnregisterPrinterChangeListener()
```

**Description**

Unregisters this listener for printer changes.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

### OH_Print_QueryPrinterList()

```cpp
Print_ErrorCode OH_Print_QueryPrinterList(Print_StringList *printerIdList)
```

**Description**

Queries the list of added printers. After using this API, call **OH_Print_ReleasePrinterList()** to release the memory occupied by the query result. Otherwise, memory leak may occur.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Print_StringList](capi-oh-print-print-stringlist.md) *printerIdList | Pointer to the [Print_StringList](capi-oh-print-print-stringlist.md) instance that stores the queried printer ID list. The value cannot be null.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode): **printerIdList** is null.<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode): Failed to query any connected printers.<br>         [PRINT_ERROR_GENERIC_FAILURE](#print_errorcode): Failed to copy printer ID list.|

### OH_Print_ReleasePrinterList()

```cpp
void OH_Print_ReleasePrinterList(Print_StringList *printerIdList)
```

**Description**

Releases the memory used to store the printer list. The input pointer must come from the query result of **OH_Print_QueryPrinterList()**.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name                                                      | Description                          |
| ------------------------------------------------------------ | ------------------------------ |
| [Print_StringList](capi-oh-print-print-stringlist.md) *printerIdList | Pointer to the queried printer ID list.|

### OH_Print_QueryPrinterInfo()

```cpp
Print_ErrorCode OH_Print_QueryPrinterInfo(const char *printerId, Print_PrinterInfo **printerInfo)
```

**Description**

Queries printer information by printer ID. After using this API, call **OH_Print_ReleasePrinterInfo()** to release the memory occupied by the query result. Otherwise, memory leak may occur.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const char *printerId                                        | ID of the printer to query. The printer must be in the list of connected printers. The value cannot be null.                                         |
| [Print_PrinterInfo](capi-oh-print-print-printerinfo.md) \*\*printerInfo | Double pointer to the [Print_PrinterInfo](capi-oh-print-print-printerinfo.md). The value cannot be null.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode): **printerId** or **printerInfo** is null.<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode): Failed to find the specified printer in the list of connected printers.|

### OH_Print_ReleasePrinterInfo()

```cpp
void OH_Print_ReleasePrinterInfo(Print_PrinterInfo *printerInfo)
```

**Description**

Releases the memory allocated for querying the printer information. The input pointer must come from the query result of **OH_Print_QueryPrinterInfo()**.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name                                                      | Description                          |
| ------------------------------------------------------------ | ------------------------------ |
| [Print_PrinterInfo](capi-oh-print-print-printerinfo.md) *printerInfo | Pointer to the queried printer information.|

### OH_Print_LaunchPrinterManager()

```cpp
Print_ErrorCode OH_Print_LaunchPrinterManager()
```

**Description**

Starts the printer management window of the system.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_GENERIC_FAILURE](#print_errorcode): Failed to start the printer management window.|

### OH_Print_QueryPrinterProperties()

```cpp
Print_ErrorCode OH_Print_QueryPrinterProperties(const char *printerId, const Print_StringList *propertyKeyList, Print_PropertyList *propertyList)
```

**Description**

Queries the printer properties based on the list of property keys. After using this API, call **OH_Print_ReleasePrinterProperties()** to release the memory occupied by the query result. Otherwise, memory leak may occur.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                      |
| ------------------------------------------------------------ | -------------------------- |
| const char *printerId                                        | ID of the printer to query. The printer must be connected. The value cannot be null.       |
| [const Print_StringList](capi-oh-print-print-stringlist.md) *propertyKeyList | List of property keys to query. The value cannot be null, and the internal string array cannot be null.  |
| [Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | Pointer to the queried printer properties. The value cannot be null.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode): One of the parameters is null or the key list is empty.<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode): Failed to find properties of the specified printer.<br>         [PRINT_ERROR_GENERIC_FAILURE](#print_errorcode): Failed to copy printer properties.|

### OH_Print_ReleasePrinterProperties()

```cpp
void OH_Print_ReleasePrinterProperties(Print_PropertyList *propertyList)
```

**Description**

Releases the memory used to store the property list. The input pointer must come from the query result of **OH_Print_QueryPrinterProperties()**.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Parameters**

| Name                                                      | Description                            |
| ------------------------------------------------------------ | -------------------------------- |
| [Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | Pointer to the queried printer properties.|

### OH_Print_UpdatePrinterProperties()

```cpp
Print_ErrorCode OH_Print_UpdatePrinterProperties(const char *printerId, const Print_PropertyList *propertyList)
```

**Description**

Updates the printer properties based on the KV pairs.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                      |
| ------------------------------------------------------------ | -------------------------- |
| const char *printerId                                        | ID of the printer to set. The printer must be in the list of connected printers. The value cannot be null.       |
| [const Print_PropertyList](capi-oh-print-print-propertylist.md) *propertyList | List of printer properties to set. The value cannot be null, and the internal property array cannot be null.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.|

### OH_Print_RestorePrinterProperties()

```cpp
Print_ErrorCode OH_Print_RestorePrinterProperties(const char *printerId, const Print_StringList *propertyKeyList)
```

**Description**

Restores printer properties to the default settings based on the property key list.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 12

**Parameters**

| Name                                                      | Description                    |
| ------------------------------------------------------------ | ------------------------ |
| const char *printerId                                        | ID of the printer to be restored. The printer must be in the list of connected printers. The value cannot be null.     |
| [const Print_StringList](capi-oh-print-print-stringlist.md) *propertyKeyList | List of property keys to be restored. The value cannot be null, and the internal string array cannot be null.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.|

### OH_Print_StartPrintByNative()

```cpp
Print_ErrorCode OH_Print_StartPrintByNative(const char *printJobName, Print_PrintDocCallback printDocCallback, void *context)
```

**Description**

Starts the system printing app. This API enables users to select a printer and set printing parameters (such as the number of copies, double-sided printing, and color) using the system printing app before printing.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 13

**Parameters**

| Name                                                      | Description                |
| ------------------------------------------------------------ | -------------------- |
| const char *printJobName                                     | Pointer to the name of the print job.  |
| [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md) printDocCallback | Callback used to return the file state.  |
| void *context                                                | Pointer to the context of the app that calls the API. If this parameter is set to null, no additional data needs to be passed.|

**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The **ohos.permission.PRINT** permission is required.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.|

### OH_Print_OnJobStateChanged()

```cpp
typedef void(*OH_Print_OnJobStateChanged)(const char *jobId, OH_Print_JobState state)
```

**Description**

Defines a callback to be invoked when the print job state changes. Compared with **Print_OnJobStateChanged** (which uses uint32_t to indicate the state and is available since API version 13), this callback uses the **OH_Print_JobState** enumeration to indicate the job state, which is clearer in semantics and more secure in type.

**Since**: 24

**Parameters**

| Name             | Description                |
| ------------------- | -------------------- |
| const char \*jobId | Pointer to the print job ID.     |
| [OH_Print_JobState](#oh_print_jobstate) state      | Print job state.|

### OH_Print_StartPrintWithJobStateCallback()

```cpp
Print_ErrorCode OH_Print_StartPrintWithJobStateCallback(const Print_PrintJob *printJob, OH_Print_OnJobStateChanged jobStateChangedCb)
```

**Description**

Starts a print job with the callback to be invoked when the print job state changes. This API can be used to listen for the print job execution status, such as success, failure, and cancellation. Before calling this API, ensure that the printer to be used is in the list of connected printers. If you do not need to listen for task status changes, call **OH_Print_StartPrintJob**.

**System capability**: SystemCapability.Print.PrintFramework

**Required permissions**: ohos.permission.PRINT

**Since**: 24

**Parameters**

| Name                                                      | Description                |
| ------------------------------------------------------------ | -------------------- |
| const [Print_PrintJob](capi-oh-print-print-printjob.md) *printJob           | Pointer to the [Print_PrintJob](capi-oh-print-print-printjob.md) instance. The value cannot be null. The referenced printer must have been connected using **OH_Print_ConnectPrinter**.  |
| [OH_Print_OnJobStateChanged](#oh_print_onjobstatechanged) jobStateChangedCb | Callback for the print task status, which is used to listen for status changes of the print task specified by **printJob**. The value cannot be null.|


**Returns**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [Print_ErrorCode](#print_errorcode) | [PRINT_ERROR_NONE](#print_errorcode): The operation is successful.<br>         [PRINT_ERROR_NO_PERMISSION](#print_errorcode): The [ohos.permission.PRINT](../../security/AccessToken/permissions-for-all.md#ohospermissionprint) permission is required.<br>         [PRINT_ERROR_INVALID_PARAMETER](#print_errorcode): **jobStateChangedCb** is null.<br>         [PRINT_ERROR_GENERIC_FAILURE](#print_errorcode): The callback function cannot be copied.<br>         [PRINT_ERROR_RPC_FAILURE](#print_errorcode): The print service fails to be connected.<br>         [PRINT_ERROR_SERVER_FAILURE](#print_errorcode): The print job struct fails to be created in the print service.<br>         [PRINT_ERROR_INVALID_PRINTER](#print_errorcode): Failed to find properties of the specified printer.<br>         [PRINT_ERROR_INVALID_PRINT_JOB](#print_errorcode): **printJob** is null or internal parameters are invalid.|
