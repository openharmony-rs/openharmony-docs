# deleteScanner (System API)

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## deleteScanner

```TypeScript
function deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise<void>
```

Deletes a scanner. This is a system API. This method can be used to remove a scanner when it is offline or no longer needed. After the scanner is deleted, the **scanDeviceDel** event is triggered. You can use **on('scanDeviceDel')** to listen for the device deletion event. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise<void>--><!--Device-scan-function deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise<void>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uniqueId | string | Yes | Unique ID of a scanner, which can be obtained by calling **getAddedScanners()** or from the **scan.on('scanDeviceAdd')** event callback. |
| discoveryMode | [ScannerDiscoveryMode](arkts-basicservices-scan-scannerdiscoverymode-e.md) | Yes | Discovery mode of the scanner, which must be the same as that used when the scanner is added. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

<!--Del-->
**Examples**

```TypeScript
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

<!--DelEnd-->
