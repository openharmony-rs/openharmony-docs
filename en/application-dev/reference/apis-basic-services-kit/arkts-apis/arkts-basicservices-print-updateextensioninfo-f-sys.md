# updateExtensionInfo (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## updateExtensionInfo

```TypeScript
function updateExtensionInfo(info: string, callback: AsyncCallback<void>): void
```

Updates the printer extension information. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | string | Yes | New printer extension information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let info : string = 'WIFI_INACTIVE';
print.updateExtensionInfo(info, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to update extension info. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('updateExtensionInfo success');
    }
});
```


<a id="updateextensioninfo-1"></a>

## updateExtensionInfo

```TypeScript
function updateExtensionInfo(info: string): Promise<void>
```

Updates the printer extension information. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | string | Yes | New printer extension information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let info : string = 'WIFI_INACTIVE';
print.updateExtensionInfo(info).then(() => {
    console.info('updateExtensionInfo success');
}).catch((error: BusinessError) => {
    console.error(`Failed to update extension info. Code: ${error.code}, message: ${error.message}`);
});
```
