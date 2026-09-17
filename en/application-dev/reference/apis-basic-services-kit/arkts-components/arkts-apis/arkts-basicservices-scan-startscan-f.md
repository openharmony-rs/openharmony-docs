# startScan

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## startScan

```TypeScript
function startScan(scannerId: string, batchMode: boolean): Promise<void>
```

Starts scanning. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scannerId | string | Yes | Scanner ID. |
| batchMode | boolean | Yes | Whether to use the batch processing mode. The value **true** indicates that the batch processing mode is used, and **false** indicates the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
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
