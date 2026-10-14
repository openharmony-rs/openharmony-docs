# @ohos.scan (Scan) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester:@baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a077482f26289b96749dbeb1a0c6856695ebea0a translatedAt=2026-09-01T04:06:35.232Z pushedAt=2026-09-05T08:47:01.812Z -->

This module provides JavaScript APIs of the scan framework for discovering, adding, and deleting scanners, obtaining the list of added scanners, and listening for scanner addition and deletion events. This module can be used to integrate scanner management into your app and detect device status changes in real time. The scan framework discovers scanners in discovery mode. After a scanner is added, you can listen for the addition and deletion events of the scanner. After the scanning task is complete, you can delete the scanner. This helps you easily integrate scanners and manage their lifecycle.

> **NOTE**
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.scan (Scan)](./js-apis-scan.md).

## Modules to Import

```ts
import { scan } from '@kit.BasicServicesKit';
```
## scan.addScanner

addScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise&lt;void&gt;

Adds a scanner. This is a system API. This method can be used to discover and add a scanner based on the specified discovery mode. After the scanner is added, the **scanDeviceAdd event** is triggered. You can use **on('scanDeviceAdd')** to listen for the device addition event. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| uniqueId | string | Yes | Unique ID of a scanner, which is specified by the caller and is used to identify the scanner to be added. |
| discoveryMode | [ScannerDiscoveryMode](./js-apis-scan.md#scannerdiscoverymode) | Yes | Discovery mode of the scanner. |

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. **resolve** indicates that the API is successfully called, and **reject** indicates that the API fails to be called. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the unique ID of the added scanner through getAddedScanners() or from the scan.on('scanDeviceAdd') event callback.
let uniqueId: string = 'unique_scanner_001';
let discoveryMode: scan.ScannerDiscoveryMode = scan.ScannerDiscoveryMode.TCP_STR;
scan.addScanner(uniqueId, discoveryMode).then(() => {
    console.info('add scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to add scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.deleteScanner

deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise&lt;void&gt;

Deletes a scanner. This is a system API. This method can be used to remove a scanner when it is offline or no longer needed. After the scanner is deleted, the **scanDeviceDel** event is triggered. You can use **on('scanDeviceDel')** to listen for the device deletion event. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| uniqueId | string | Yes | Unique ID of a scanner, which can be obtained by calling **getAddedScanners()** or from the **scan.on('scanDeviceAdd')** event callback. |
| discoveryMode | [ScannerDiscoveryMode](./js-apis-scan.md#scannerdiscoverymode) | Yes | Discovery mode of the scanner, which must be the same as that used when the scanner is added. |

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. **resolve** indicates that the API is successfully called, and **reject** indicates that the API fails to be called. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the unique ID of the added scanner through getAddedScanners() or from the scan.on('scanDeviceAdd') event callback.
let uniqueId: string = 'unique_scanner_001';
let discoveryMode: scan.ScannerDiscoveryMode = scan.ScannerDiscoveryMode.TCP_STR;
scan.deleteScanner(uniqueId, discoveryMode).then(() => {
    console.info('delete scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to delete scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getAddedScanners

getAddedScanners(): Promise&lt;ScannerDevice[]&gt;

Obtains the added scanners. This is a system API. This API can be used to query the list of available scanners for users to select one. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)[]&gt; | Promise used to return the result. **resolve** returns the array of added scanners; **reject** indicates that the scanners fail to be obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.getAddedScanners().then((scanners: scan.ScannerDevice[]) => {
    console.info('get added scanners success: ' + JSON.stringify(scanners));
}).catch((error: BusinessError) => {
    console.error(`Failed to get added scanners. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.on

on(type: 'scanDeviceAdd', callback: Callback&lt;ScannerDevice&gt;): void

Registers a callback used to listen for the scanner addition event. This is a system API. This callback is triggered when a scanner is successfully added and returns the information of the added scanner. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceAdd' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | Yes | Callback for the scanner device addition event. This callback is triggered when a scanner is added and returns the information of the added scanner. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceAdd', (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceAdd', callback?: Callback&lt;ScannerDevice&gt;): void

Unregisters the callback used to listen for the scanner addition event. This is a system API.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceAdd' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | No | Callback to unregister. If this parameter is not passed, all registered callbacks of the caller will be unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
};
scan.on('scanDeviceAdd', callback);
// Unregister the callback.
scan.off('scanDeviceAdd', callback);
```

## scan.on

on(type: 'scanDeviceDel', callback: Callback&lt;ScannerDevice&gt;): void

Registers a callback used to listen for the scanner deletion event. This is a system API. This callback is triggered when a scanner is deleted and returns the information of the deleted scanner. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceDel' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | Yes | Callback for the scanner device deletion event. This callback is triggered when a scanner is deleted and returns the information of the deleted scanner. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceDel', (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceDel', callback?: Callback&lt;ScannerDevice&gt;): void

Unregisters the callback used to listen for the scanner deletion event. This is a system API.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceDel' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | No | Callback to unregister. If this parameter is not passed, all registered callbacks of the caller will be unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
};
scan.on('scanDeviceDel', callback);
// Unregister the callback.
scan.off('scanDeviceDel', callback);
```