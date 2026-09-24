# getTotalSize

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getTotalSize

```TypeScript
function getTotalSize(callback: AsyncCallback<number>): void
```

Obtains the total size (in bytes) of the built-in storage. This API uses an asynchronous callback to return the result.

**Since:** 15

**Required permissions:** 
- API version 15 and later: N/A
- API versions 9 to 14: ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the built-in storage space obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br>**Applicable version:** 9 - 14 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application.<br>**Applicable version:** 9 - 14 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize((error: BusinessError, number: number) => {
  if (error) {
    console.error("getTotalSize failed with error:" + JSON.stringify(error));
  } else {
    // Do something.
    console.info("getTotalSize successfully:" + number);
  }
});
```


<a id="gettotalsize-1"></a>

## getTotalSize

```TypeScript
function getTotalSize(): Promise<number>
```

Obtains the total size (in bytes) of the built-in storage. This API uses a promise to return the result.

**Since:** 15

**Required permissions:** 
- API version 15 and later: N/A
- API versions 9 to 14: ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the total built-in storage space obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br>**Applicable version:** 9 - 14 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application.<br>**Applicable version:** 9 - 14 |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize().then((number: number) => {
  console.info("getTotalSize successfully:" + JSON.stringify(number));
}).catch((err: BusinessError) => {
  console.error("getTotalSize failed with error:"+ JSON.stringify(err));
});
```
