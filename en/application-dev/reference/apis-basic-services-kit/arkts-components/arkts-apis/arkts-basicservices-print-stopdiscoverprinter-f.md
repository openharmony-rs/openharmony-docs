# stopDiscoverPrinter

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## stopDiscoverPrinter

```TypeScript
function stopDiscoverPrinter(callback: AsyncCallback<void>): void
```

Stops discovering printers. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API versions 10 to 19: ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback to be invoked when printer discovery is stopped. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 19 |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.stopDiscoverPrinter((error: BusinessError) => {
    if (error) {
        console.error(`Failed to stopDiscoverPrinter. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('stop Discover Printer success');
    }
})
```

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.stopDiscoverPrinter().then(() => {
    console.info('stop Discovery success');
}).catch((error: BusinessError) => {
    console.error(`Failed to stopDiscoverPrinter. Code: ${error.code}, message: ${error.message}`);
})
```


## stopDiscoverPrinter

```TypeScript
function stopDiscoverPrinter(): Promise<void>
```

Stops discovering printers. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API versions 10 to 19: ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 19 |

**Examples**

See [stopDiscoverPrinter](#stopdiscoverprinter)
