# getScannerCurrentSetting

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## getScannerCurrentSetting

```TypeScript
function getScannerCurrentSetting(scannerId: string, optionIndex: number): Promise<ScannerOptionValue>
```

Obtains the current scanner settings. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scannerId | string | Yes | Scanner ID. |
| optionIndex | number | Yes | Index of the option to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md)&gt; | Promise used to return the scanner option value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
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
