# @ohos.scan (Scan) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

This module provides JavaScript APIs of the scan framework for discovering and connecting to scanners.

> **NOTE** 
> The initial APIs of this module are supported since API version 20.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.scan (Scan)](./js-apis-scan.md).

## Modules to Import

```ts
import { scan } from '@kit.BasicServicesKit';
```
## scan.addScanner

addScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise&lt;void&gt;

Adds a scanner. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| uniqueId | string | Yes| Unique ID of the scanner.|
| discoveryMode | [ScannerDiscoveryMode](./js-apis-scan.md#scannerdiscoverymode) | Yes| Discovery mode.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uniqueId: string = 'unique_scanner_001';
let discoveryMode: scan.ScannerDiscoveryMode = scan.ScannerDiscoveryMode.TCP_STR;
scan.addScanner(uniqueId, discoveryMode).then(() => {
    console.info('add scanner success');
}).catch((error: BusinessError) => {
    console.error('add scanner failed: ' + JSON.stringify(error));
})
```

## scan.deleteScanner

deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise&lt;void&gt;

Deletes a scanner. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| uniqueId | string | Yes| Unique ID of the scanner.|
| discoveryMode | [ScannerDiscoveryMode](./js-apis-scan.md#scannerdiscoverymode) | Yes| Discovery mode.|

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uniqueId: string = 'unique_scanner_001';
let discoveryMode: scan.ScannerDiscoveryMode = scan.ScannerDiscoveryMode.TCP_STR;
scan.deleteScanner(uniqueId, discoveryMode).then(() => {
    console.info('delete scanner success');
}).catch((error: BusinessError) => {
    console.error('delete scanner failed: ' + JSON.stringify(error));
})
```

## scan.getAddedScanners

getAddedScanners(): Promise&lt;ScannerDevice[]&gt;

Obtains the added scanners. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**
| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)[]&gt; | Promise used to return the array of added scanners.|

**Error codes**

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
    console.error('get added scanners failed: ' + JSON.stringify(error));
})
```

## scan.on

on(type: 'scanDeviceAdd', callback: Callback&lt;ScannerDevice&gt;): void

Registers a callback used to listen for the scanner addition event. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceAdd' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | Yes| Callback used to return the added scanner.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceAdd', (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
})
```

## scan.off

off(type: 'scanDeviceAdd', callback?: Callback&lt;ScannerDevice&gt;): void

Unregisters the callback used to listen for the scanner addition event. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceAdd' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | Yes| Callback used to return the added scanner.|

**Error codes**

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

Registers a callback used to listen for the scanner deletion event. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceDel' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | Yes| Callback used to return the deleted scanner.|

**Error codes**

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceDel', (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
})
```

## scan.off

off(type: 'scanDeviceDel', callback?: Callback&lt;ScannerDevice&gt;): void

Unregisters the callback used to listen for the scanner deletion event. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**
| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceDel' | Yes| Event type.|
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | No| Callback used to return the deleted scanner.|

**Error codes**

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
