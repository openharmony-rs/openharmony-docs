# @ohos.scan (Scan)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester:@baozewei-->
<!--Adviser: @fang-jinxu-->

This module provides JavaScript APIs of the scan framework, which support scanner discovery and management, scanning execution, and device event listening. It is applicable to scenarios where an app needs to integrate a scanner for digital document collection and device management.

> **NOTE**
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only public APIs provided by the module.

## Modules to Import

```ts
import { scan } from '@kit.BasicServicesKit';
```

## ScanErrorCode

Enumerates the scan error codes.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Value**| **Description**|
| -------- | ------ | -------- |
| SCAN_ERROR_NO_PERMISSION | 201 | No permission. Request the required permission based on the permission requirements of the corresponding API and declare the permission in the configuration file.|
| SCAN_ERROR_NOT_SYSTEM_APPLICATION | 202 | Not a system app. Check whether the app is a system app.|
| SCAN_ERROR_INVALID_PARAMETER | 401 | Invalid parameter. Check the parameter type and value range.|
| SCAN_ERROR_GENERIC_FAILURE | 13100001 | General failure. Check the running status of the scan service and try again.|
| SCAN_ERROR_RPC_FAILURE | 13100002 | RPC failure. Check the RPC communication status and try again.|
| SCAN_ERROR_SERVER_FAILURE | 13100003 | Service failure. Check whether the scan service is running properly and try again.|
| SCAN_ERROR_UNSUPPORTED | 13100004 | The operation is not supported. Check whether the current operation is supported by the scanner.|
| SCAN_ERROR_CANCELED | 13100005 | Operation canceled. Check whether **cancelScan** is called or the operation is interrupted by the system.|
| SCAN_ERROR_DEVICE_BUSY | 13100006 | The device is busy. Wait until the device is idle and try again.|
| SCAN_ERROR_INVALID | 13100007 | Invalid operation. Check whether the current operation is valid in the scanner state.|
| SCAN_ERROR_JAMMED | 13100008 | Paper jammed. Remove the jammed paper from the scanner and try again.|
| SCAN_ERROR_NO_DOCS | 13100009 | No paper. Place paper in the scanner and try again.|
| SCAN_ERROR_COVER_OPEN | 13100010 | The scanner cover is open. Close the cover and try again.|
| SCAN_ERROR_IO_ERROR | 13100011 | I/O error. Check the device I/O connection and try again.|
| SCAN_ERROR_NO_MEMORY | 13100012 | Insufficient memory. Release system memory and try again.|

## ConstraintType

Enumerates the parameter constraint types.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Value**| **Description**|
| -------- | ------ | -------- |
| SCAN_CONSTRAINT_NONE | 0 | No constraint.|
| SCAN_CONSTRAINT_RANGE | 1 | Range.|
| SCAN_CONSTRAINT_WORD_LIST | 2 | Number list.|
| SCAN_CONSTRAINT_STRING_LIST | 3 | String list.|

## PhysicalUnit

Enumerates the physical units.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Value**| **Description**|
| -------- | ------ | -------- |
| SCAN_UNIT_NONE | 0 | No unit.|
| SCAN_UNIT_PIXEL | 1 | Pixel unit.|
| SCAN_UNIT_BIT | 2 | Bit unit.|
| SCAN_UNIT_MM | 3 | Millimeter unit.|
| SCAN_UNIT_DPI | 4 | DPI unit.|
| SCAN_UNIT_PERCENT | 5 | Percentage unit.|
| SCAN_UNIT_MICROSECOND | 6 | Microsecond unit.|

## OptionValueType

Enumerates the option value types.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Value**| **Description**|
| -------- | ------ | -------- |
| SCAN_TYPE_BOOL | 0 | Boolean.|
| SCAN_TYPE_INT | 1 | Integer.|
| SCAN_TYPE_FIXED | 2 | Fixed-point number.|
| SCAN_TYPE_STRING | 3 | String.|

## ScannerSyncMode

Enumerates the scanner sync modes.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Value**| **Description**|
| -------- | ------ | -------- |
| UPDATE_STR | 'update' | Update mode, which indicates that the scanner ID changes.|
| DELETE_STR | 'delete' | Deletion mode, which indicates that the scanner is offline.|

## ScannerDiscoveryMode

Enumerates the scanner discovery modes.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Value**| **Description**|
| -------- | ------ | -------- |
| TCP_STR | 'TCP' | Discovery mode of the network scanner.|
| USB_STR | 'USB' | Discovery mode of the USB scanner.|

## Range

Defines the range.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| minValue | number | No| No| Minimum value.|
| maxValue | number | No| No| Maximum value.|
| quantValue | number | No| No| Quantized value of the range, which indicates the step between valid values within the range.|

## ScannerParameter

Defines the scanner parameters.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| optionName | string | No| No| Option name.|
| optionIndex | number | No| No| Option index.|
| optionTitle | string | No| No| Option title.|
| optionDesc | string | No| No| Option description.|
| optionType | [OptionValueType](#optionvaluetype) | No| No| Option value type.|
| optionUnit | [PhysicalUnit](#physicalunit) | No| No| Physical unit of the option.|
| optionConstraintType | [ConstraintType](#constrainttype) | No| No| Constraint type of the option, which determines the valid constraint field. If this parameter is set to **SCAN_CONSTRAINT_NONE**, there is no constraint.|
| optionConstraintString | string[] | No| Yes| String constraint of the option. This parameter is valid only when **optionConstraintType** is set to **SCAN_CONSTRAINT_STRING_LIST**. The default value is an empty array.|
| optionConstraintInt | number[] | No| Yes| String constraint of the option. This parameter is valid only when **optionConstraintType** is set to **SCAN_CONSTRAINT_WORD_LIST**. The default value is an empty array.|
| optionConstraintRange | [Range](#range) | No| Yes| Option range constraint. This parameter is valid only when **optionConstraintType** is set to **SCAN_CONSTRAINT_RANGE**.|

## ScannerOptionValue

Defines the scanner option value. When the constraint type of the option is **SCAN_CONSTRAINT_STRING_LIST**, the option value must be a string in the **optionConstraintString** set.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| valueType | [OptionValueType](#optionvaluetype) | No| No| Value type, which determines the value field to be used.|
| numValue | number | No| Yes| Numeric value. This parameter is valid only when **valueType** is set to **SCAN_TYPE_INT** or **SCAN_TYPE_FIXED**.|
| strValue | string | No| Yes| String value. This parameter is valid only when **valueType** is set to **SCAN_TYPE_STRING**.|
| boolValue | boolean | No| Yes| Boolean. This parameter is valid only when **valueType** is set to **SCAN_TYPE_BOOL**.|

## PictureScanProgress

Defines the progress of scanning pictures.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| progress | number | No| No| Processing progress, in percentage. The value ranges from 0 to 100.|
| pictureFd | number | No| No| File descriptor of the scanned picture.|
| isFinal | boolean | No| No| Whether the picture is the last one to be scanned. The value **true** indicates that the picture is the last one to be scanned, and **false** indicates that the picture is not the last one.|

## ScannerDevice

Defines the scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| scannerId | string | No| No| Scanner ID.|
| discoveryMode | [ScannerDiscoveryMode](#scannerdiscoverymode) | No| No| Discovery mode of the scanner, indicating how the scanner is discovered.|
| uniqueId | string | No| No| Unique ID of the scanner.|
| manufacturer | string | No| No| Manufacturer of the scanner.|
| model | string | No| No| Model of the scanner.|
| deviceName | string | No| No| Name of the scanner.|

## ScannerSyncDevice

Defines the device to be synced from the scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| scannerId | string | No| No| Scanner ID.|
| discoveryMode | [ScannerDiscoveryMode](#scannerdiscoverymode) | No| No| Discovery mode of the scanner, indicating how the scanner is discovered.|
| uniqueId | string | No| No| Unique ID of the scanner.|
| syncMode | [ScannerSyncMode](#scannersyncmode) | No| No| Synchronization mode, which determines whether **oldScannerId** is valid. When **syncMode** is set to **'update'**, **oldScannerId** is valid. When **syncMode** is set to **'delete'**, **oldScannerId** is invalid.|
| oldScannerId | string | No| Yes| Old scanner ID, which is valid only when **syncMode** is set to **'update'**. The default value is an empty string.|

## scan.init

init(): Promise&lt;void&gt;

Initializes the scan service. This API must be called before other scanning APIs. This API uses a promise to return the result. After using the service, call **exit()** to exit the scan service and release resources.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scan service is initialized successfully, **resolve** will be called. If the initialization fails, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.init().then(() => {
    console.info('scan init success');
}).catch((error: BusinessError) => {
    console.error(`Failed to init scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.exit

exit(): Promise&lt;void&gt;

Exits the scan service. This API uses a promise to return the result. After the scan service exits, other scan methods are unavailable. To use them again, call **init()** again.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scan service is exited successfully, **resolve** will be called. If the exit fails, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.exit().then(() => {
    console.info('scan exit success');
}).catch((error: BusinessError) => {
    console.error(`Failed to exit scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.startScannerDiscovery

startScannerDiscovery(): Promise&lt;void&gt;

Starts scanner discovery. The discovered scanner information is returned through the **on('scanDeviceFound')** event callback. This API can be used only after initialization is complete by calling **init()**. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the discovery starts successfully, **resolve** will be called. If the discovery fails to start, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.startScannerDiscovery().then(() => {
    console.info('start scanner discovery success');
}).catch((error: BusinessError) => {
    console.error(`Failed to start scanner discovery. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.openScanner

openScanner(scannerId: string): Promise&lt;void&gt;

Opens a scanner. This API can be used only after initialization is complete by calling **init()**. This API uses a promise to return the result. After using the scanner, call **closeScanner()** to close the scanner and release resources.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner to be opened, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scanner is opened successfully, **resolve** will be called. If the scanner fails to be opened, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.openScanner(scannerId).then(() => {
    console.info('open scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to open scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.closeScanner

closeScanner(scannerId: string): Promise&lt;void&gt;

Closes a scanner. This API uses a promise to return the result. After a scanner is closed, you cannot obtain or set parameters for the scanner or perform scanning operations on the scanner. To use the scanner again, call **openScanner()**.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner to be closed, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scanner is closed successfully, **resolve** will be called. If the scanner fails to be closed, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.closeScanner(scannerId).then(() => {
    console.info('close scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to close scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getScannerParameter

getScannerParameter(scannerId: string): Promise&lt;ScannerParameter[]&gt;

Obtains scanner parameters. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**. Your app can use this method to obtain the parameter index (**optionIndex**), which is used to call methods such as **setScannerParameter**, **setScanAutoOption**, and **getScannerCurrentSetting**.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[ScannerParameter](#scannerparameter)[]&gt; | Promise used to return the result. If the scanner parameters are obtained successfully, **resolve** returns the scanner parameter array. If the scanner parameters fail to be obtained, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.getScannerParameter(scannerId).then((parameters: scan.ScannerParameter[]) => {
    console.info('get scanner parameters success: ' + JSON.stringify(parameters));
}).catch((error: BusinessError) => {
    console.error(`Failed to get scanner parameters. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.setScannerParameter

setScannerParameter(scannerId: string, optionIndex: number, value: ScannerOptionValue): Promise&lt;void&gt;

Sets scanner parameters. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner whose parameter is to be set. The ID can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|
| optionIndex | number | Yes| Index of the option to be set, which can be obtained using **getScannerParameter()**.|
| value | [ScannerOptionValue](#scanneroptionvalue) | Yes| Scanner option value to be set, including the value type (**valueType**) and the corresponding numeric value (**numValue**), string value (**strValue**), or Boolean value (**boolValue**).|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scanner parameters are set successfully, **resolve** will be called. If the scanner parameters fail to be set, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
let value: scan.ScannerOptionValue = {
    valueType: scan.OptionValueType.SCAN_TYPE_INT,
    numValue: 100
};
scan.setScannerParameter(scannerId, optionIndex, value).then(() => {
    console.info('set scanner parameter success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set scanner parameter. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.setScanAutoOption

setScanAutoOption(scannerId: string, optionIndex: number): Promise&lt;void&gt;

Sets the scan option to auto mode, in which the scanner automatically determines the value of this option. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|
| optionIndex | number | Yes| Index of the option to be set to automatic mode, which can be obtained using **getScannerParameter()**.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scanning option is set to automatic mode successfully, **resolve** will be called. If the scanning option fails to be set to automatic mode, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
scan.setScanAutoOption(scannerId, optionIndex).then(() => {
    console.info('set scan auto option success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set scan auto option. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getScannerCurrentSetting

getScannerCurrentSetting(scannerId: string, optionIndex: number): Promise&lt;ScannerOptionValue&gt;

Obtains the current scanner settings. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner to be obtained, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|
| optionIndex | number | Yes| Index of the option to be obtained, which can be obtained using **getScannerParameter()**.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[ScannerOptionValue](#scanneroptionvalue)&gt; | Promise used to return the result. If the scanner settings are obtained successfully, **resolve** returns the scanner option value. If the scanner settings fail to be obtained, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
scan.getScannerCurrentSetting(scannerId, optionIndex).then((value: scan.ScannerOptionValue) => {
    console.info('get scanner current setting success: ' + JSON.stringify(value));
}).catch((error: BusinessError) => {
    console.error(`Failed to get scanner current setting. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.startScan

startScan(scannerId: string, batchMode: boolean): Promise&lt;void&gt;

Starts scanning. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**. During the scanning, you can call **getPictureScanProgress()** to obtain the scanning progress. To cancel the scanning, call **cancelScan()**.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|
| batchMode | boolean | Yes| Whether to use the batch processing mode. **true** indicates that the batch processing mode is used, and multiple pages of documents can be continuously scanned. **false** indicates that the batch processing mode is not used, and only a single page is scanned.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scanning starts successfully, **resolve** will be called. If the scanning fails to start, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let batchMode: boolean = true;
scan.startScan(scannerId, batchMode).then(() => {
    console.info('start scan success');
}).catch((error: BusinessError) => {
    console.error(`Failed to start scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.cancelScan

cancelScan(scannerId: string): Promise&lt;void&gt;

Cancels scanning. This API uses a promise to return the result. This method can be called only after scanning starts.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. If the scanning is canceled successfully, **resolve** will be called. If the scanning fails to start, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.cancelScan(scannerId).then(() => {
    console.info('cancel scan success');
}).catch((error: BusinessError) => {
    console.error(`Failed to cancel scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getPictureScanProgress

getPictureScanProgress(scannerId: string): Promise&lt;PictureScanProgress&gt;

Obtains the progress of scanning a picture. This API uses a promise to return the result. This method can be called only after scanning starts.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID, which can be obtained using the **scanDeviceFound** callback after **startScannerDiscovery** is called.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[PictureScanProgress](#picturescanprogress)&gt; | Promise used to return the result. If the image scanning progress is obtained successfully, **resolve** returns the image scanning progress. If the image scanning progress fails to be obtained, **reject** will be called.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.getPictureScanProgress(scannerId).then((progress: scan.PictureScanProgress) => {
    console.info('get picture scan progress success: ' + JSON.stringify(progress));
}).catch((error: BusinessError) => {
    console.error(`Failed to get picture scan progress. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.on

on(type: 'scanDeviceFound', callback: Callback&lt;ScannerDevice&gt;): void

Registers a callback to listen for the scanner discovery event. This callback is triggered when a new scanner is discovered by calling **startScannerDiscovery**. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceFound' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](#scannerdevice)&gt; | Yes| Callback used to return the discovered scanner.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceFound', (device: scan.ScannerDevice) => {
    console.info('scan device found: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceFound', callback?: Callback&lt;ScannerDevice&gt;): void

Unregisters a callback used to listen for the scanner discovery event.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceFound' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](#scannerdevice)&gt; | No| Callback to unregister. If this parameter is not passed, all registered callbacks of the caller will be unregistered.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device found: ' + JSON.stringify(device));
};
scan.on('scanDeviceFound', callback);
// Unregister the callback.
scan.off('scanDeviceFound', callback);
```

## scan.on

on(type: 'scanDeviceSync', callback: Callback&lt;ScannerSyncDevice&gt;): void

Registers a callback to listen for the scanner sync event. This callback is triggered when the scanner status changes (for example, the scanner ID changes or the scanner goes offline), notifying the app to update the scanner list. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where your app needs to continuously track scanner status changes, for example, updating local device information when a scanner is reconnected.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceSync' | Yes| Event type.|
| callback | Callback&lt;[ScannerSyncDevice](#scannersyncdevice)&gt; | Yes| Callback used to return the synced scanner.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceSync', (device: scan.ScannerSyncDevice) => {
    console.info('scan device sync: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceSync', callback?: Callback&lt;ScannerSyncDevice&gt;): void

Unregisters a callback used to listen for the scanner sync event.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceSync' | Yes| Event type.|
| callback | Callback&lt;[ScannerSyncDevice](#scannersyncdevice)&gt; | No| Callback to unregister. If this parameter is not passed, all registered callbacks of the caller will be unregistered.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerSyncDevice) => {
    console.info('scan device sync: ' + JSON.stringify(device));
};
scan.on('scanDeviceSync', callback);
// Unregister the callback.
scan.off('scanDeviceSync', callback);
```
