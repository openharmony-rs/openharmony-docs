# getScannerParameter

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## getScannerParameter

```TypeScript
function getScannerParameter(scannerId: string): Promise<ScannerParameter[]>
```

Obtains scanner parameters. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scannerId | string | Yes | Scanner ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ScannerParameter](arkts-basicservices-scan-scannerparameter-i.md)[]&gt; | Promise used to return the scanner parameters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.getScannerParameter(scannerId).then((parameters: scan.ScannerParameter[]) => {
    console.info('get scanner parameters success: ' + JSON.stringify(parameters));
}).catch((error: BusinessError) => {
    console.error(`Failed to get scanner parameters. Code: ${error.code}, message: ${error.message}`);
});
```
