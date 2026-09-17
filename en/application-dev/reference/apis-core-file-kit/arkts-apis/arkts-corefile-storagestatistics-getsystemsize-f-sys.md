# getSystemSize (System API)

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getSystemSize

```TypeScript
function getSystemSize(callback: AsyncCallback<number>): void
```

Get the system size.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | callback<br>Unit: Byte. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getSystemSize().then((number: number) => {
  console.info("getSystemSize successfully:" + number);
}).catch((err: BusinessError) => {
  console.error("getSystemSize failed with error:" + JSON.stringify(err));
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getSystemSize((error: BusinessError, number: number) => {
  if (error) {
    console.error("getSystemSize failed with error:" + JSON.stringify(error));
  } else {
    // Do something.
    console.info("getSystemSize successfully:" + number);
  }
});
```


## getSystemSize

```TypeScript
function getSystemSize(): Promise<number>
```

Get the system size.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | return Promise (Unit: Byte) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

See [getSystemSize](#getsystemsize)
