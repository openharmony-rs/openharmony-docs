# getAddedPrinters

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## getAddedPrinters

```TypeScript
function getAddedPrinters(): Promise<Array<string>>
```

Obtains the list of printers added to the system. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a list of all added printers. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.getAddedPrinters().then((printers: string[]) => {
    console.info('getAddedPrinters success ' + JSON.stringify(printers));
    // ...
}).catch((error: BusinessError) => {
    console.error(`Failed to getAddedPrinters. Code: ${error.code}, message: ${error.message}`);
})
```
