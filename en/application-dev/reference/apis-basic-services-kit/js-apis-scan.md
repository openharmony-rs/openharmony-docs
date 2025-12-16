# @ohos.scan (Scan)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

This module provides JavaScript APIs of the scan framework for discovering and connecting to scanners.

> **NOTE** 
> The initial APIs of this module are supported since API version 20.
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
| SCAN_ERROR_NO_PERMISSION | 201 | No permission.|
| SCAN_ERROR_NOT_SYSTEM_APPLICATION | 202 | Non-system application.|
| SCAN_ERROR_INVALID_PARAMETER | 401 | Invalid parameter.|
| SCAN_ERROR_GENERIC_FAILURE | 13100001 | Generic failure.|
| SCAN_ERROR_RPC_FAILURE | 13100002 | RPC failure.|
| SCAN_ERROR_SERVER_FAILURE | 13100003 | Service failure.|
| SCAN_ERROR_UNSUPPORTED | 13100004 | Unsupported operation.|
| SCAN_ERROR_CANCELED | 13100005 | Operation canceled.|
| SCAN_ERROR_DEVICE_BUSY | 13100006 | Device busy.|
| SCAN_ERROR_INVALID | 13100007 | Invalid operation.|
| SCAN_ERROR_JAMMED | 13100008 | Paper jammed.|
| SCAN_ERROR_NO_DOCS | 13100009 | Out of paper.|
| SCAN_ERROR_COVER_OPEN | 13100010 | Cover open.|
| SCAN_ERROR_IO_ERROR | 13100011 | I/O error.|
| SCAN_ERROR_NO_MEMORY | 13100012 | Insufficient memory.|

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

Enumerates the scanner sync codes.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Value**| **Description**|
| -------- | ------ | -------- |
| UPDATE_STR | 'update' | Update code, which indicates that the scanner ID changes.|
| DELETE_STR | 'delete' | Deletion code, which indicates that the scanner is offline.|

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
| quantValue | number | No| No| Quantized value.|

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
| optionConstraintType | [ConstraintType](#constrainttype) | No| No| Constraint type of the option.|
| optionConstraintString | string[] | No| Yes| String constraints of the option.|
| optionConstraintInt | number[] | No| Yes| Integer constraints of the option.|
| optionConstraintRange | [Range](#range) | No| Yes| Range constraint of the option.|

## ScannerOptionValue

Defines the scanner option value.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| valueType | [OptionValueType](#optionvaluetype) | No| No| Value type.|
| numValue | number | No| Yes| Value of the number type.|
| strValue | string | No| Yes| Value of the string type.|
| boolValue | boolean | No| Yes| Value of the Boolean type.|

## PictureScanProgress

Defines the progress of scanning pictures.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| progress | number | No| No| Progress percentage, whose value ranges from 0 to 100.|
| pictureFd | number | No| No| File descriptor of the scanned picture.|
| isFinal | boolean | No| No| Whether the picture is the last one to be scanned. The value **true** indicates that the picture is the last one to be scanned, and **false** indicates that the picture is not the last one.|

## ScannerDevice

Defines the scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Properties**
| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| scannerId | string | No| No| Unique identifier of the scanner.|
| discoveryMode | [ScannerDiscoveryMode](#scannerdiscoverymode) | No| No| Discovery mode of the scanner.|
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
| discoveryMode | [ScannerDiscoveryMode](#scannerdiscoverymode) | No| No| Discovery mode.|
| uniqueId | string | No| No| Unique ID.|
| syncMode | [ScannerSyncMode](#scannersyncmode) | No| No| Sync mode.|
| oldScannerId | string | No| Yes| Old scanner ID, which is valid only when **syncMode** is set to **update**.|

## scan.init

init(): Promise&lt;void&gt;

Initializes the scan service. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('scan init failed: ' + JSON.stringify(error));
})
```

## scan.exit

exit(): Promise&lt;void&gt;

Exits the scan service. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('scan exit failed: ' + JSON.stringify(error));
})
```

## scan.startScannerDiscovery

startScannerDiscovery(): Promise&lt;void&gt;

Starts scanner discovery. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('start scanner discovery failed: ' + JSON.stringify(error));
})
```

## scan.openScanner

openScanner(scannerId: string): Promise&lt;void&gt;

Opens a scanner. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner to be opened.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('open scanner failed: ' + JSON.stringify(error));
})
```

## scan.closeScanner

closeScanner(scannerId: string): Promise&lt;void&gt;

Closes a scanner. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| ID of the scanner to be closed.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('close scanner failed: ' + JSON.stringify(error));
})
```

## scan.getScannerParameter

getScannerParameter(scannerId: string): Promise&lt;ScannerParameter[]&gt;

Obtains scanner parameters. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[ScannerParameter](#scannerparameter)[]&gt; | Promise used to return the scanner parameters.|

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
    console.error('get scanner parameters failed: ' + JSON.stringify(error));
})
```

## scan.setScannerParameter

setScannerParameter(scannerId: string, optionIndex: number, value: ScannerOptionValue): Promise&lt;void&gt;

Sets scanner parameters. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID.|
| optionIndex | number | Yes| Index of the option to be set.|
| value | [ScannerOptionValue](#scanneroptionvalue) | Yes| Value to be set.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('set scanner parameter failed: ' + JSON.stringify(error));
})
```

## scan.setScanAutoOption

setScanAutoOption(scannerId: string, optionIndex: number): Promise&lt;void&gt;

Sets the scan option to auto mode. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID.|
| optionIndex | number | Yes| Index of the option to be set to auto mode.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('set scan auto option failed: ' + JSON.stringify(error));
})
```

## scan.getScannerCurrentSetting

getScannerCurrentSetting(scannerId: string, optionIndex: number): Promise&lt;ScannerOptionValue&gt;

Obtains the current scanner settings. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID.|
| optionIndex | number | Yes| Index of the option to be obtained.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[ScannerOptionValue](#scanneroptionvalue)&gt; | Promise used to return the scanner option value.|

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
    console.error('get scanner current setting failed: ' + JSON.stringify(error));
})
```

## scan.startScan

startScan(scannerId: string, batchMode: boolean): Promise&lt;void&gt;

Starts scanning. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID.|
| batchMode | boolean | Yes| Whether to use the batch processing mode. The value **true** indicates that the batch processing mode is used, and **false** indicates the opposite.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('start scan failed: ' + JSON.stringify(error));
})
```

## scan.cancelScan

cancelScan(scannerId: string): Promise&lt;void&gt;

Cancels scanning. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('cancel scan failed: ' + JSON.stringify(error));
})
```

## scan.getPictureScanProgress

getPictureScanProgress(scannerId: string): Promise&lt;PictureScanProgress&gt;

Obtains the progress of scanning a picture. This API uses a promise to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| scannerId | string | Yes| Scanner ID.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[PictureScanProgress](#picturescanprogress)&gt; | Promise used to return the progress.|

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
    console.error('get picture scan progress failed: ' + JSON.stringify(error));
})
```

## scan.on

on(type: 'scanDeviceFound', callback: Callback&lt;ScannerDevice&gt;): void

Registers a callback used to listen for the scanner discovery event. This API uses an asynchronous callback to return the result.

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
})
```

## scan.off

off(type: 'scanDeviceFound', callback?: Callback&lt;ScannerDevice&gt;): void

Unregisters a callback used to listen for the scanner discovery event. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.PRINT

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceFound' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](#scannerdevice)&gt; | No| Callback to unregister.|

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

Registers a callback used to listen for the scanner sync event. This API uses an asynchronous callback to return the result.

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
})
```

## scan.off

off(type: 'scanDeviceSync', callback?: Callback&lt;ScannerSyncDevice&gt;): void

Unregisters a callback used to listen for the scanner sync event. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceSync' | Yes| Event type.|
| callback | Callback&lt;[ScannerSyncDevice](#scannersyncdevice)&gt; | No| Callback to unregister.|

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
