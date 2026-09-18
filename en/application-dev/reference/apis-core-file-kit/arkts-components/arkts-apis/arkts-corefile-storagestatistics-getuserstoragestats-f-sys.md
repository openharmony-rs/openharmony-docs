# getUserStorageStats (System API)

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getUserStorageStats

```TypeScript
function getUserStorageStats(): Promise<StorageStats>
```

Obtains the storage statistics of this user, in bytes. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[StorageStats](arkts-corefile-storagestatistics-storagestats-i-sys.md)&gt; | Promise used to return the storage statistics (in bytes) obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getUserStorageStats().then((storageStats: storageStatistics.StorageStats) => {
  console.info("getUserStorageStats successfully:" + JSON.stringify(storageStats));
}).catch((err: BusinessError) => {
  console.error("getUserStorageStats failed with error:" + JSON.stringify(err));
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getUserStorageStats((error: BusinessError, storageStats: storageStatistics.StorageStats) => {
  if (error) {
    console.error("getUserStorageStats failed with error:" + JSON.stringify(error));
  } else {
    // Do something.
    console.info("getUserStorageStats successfully:" + JSON.stringify(storageStats));
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let userId: number = 100;
storageStatistics.getUserStorageStats(userId).then((storageStats: storageStatistics.StorageStats) => {
  console.info("getUserStorageStats successfully:" + JSON.stringify(storageStats));
}).catch((err: BusinessError) => {
  console.error("getUserStorageStats failed with error:" + JSON.stringify(err));
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let userId: number = 100;
storageStatistics.getUserStorageStats(userId, (error: BusinessError, storageStats: storageStatistics.StorageStats) => {
  if (error) {
    console.error("getUserStorageStats failed with error:" + JSON.stringify(error));
  } else {
    // Do something.
    console.info("getUserStorageStats successfully:" + JSON.stringify(storageStats));
  }
});
```


## getUserStorageStats

```TypeScript
function getUserStorageStats(callback: AsyncCallback<StorageStats>): void
```

Obtains the storage statistics of this user, in bytes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[StorageStats](arkts-corefile-storagestatistics-storagestats-i-sys.md)&gt; | Yes | Callback used to return the storage statistics obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

See [getUserStorageStats](#getuserstoragestats)


## getUserStorageStats

```TypeScript
function getUserStorageStats(userId: number): Promise<StorageStats>
```

Obtains the storage statistics of the specified user, in bytes. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[StorageStats](arkts-corefile-storagestatistics-storagestats-i-sys.md)&gt; | Promise used to return the storage statistics (in bytes) obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600009 | User if out of range. |
| 13900042 | Unknown error. |

**Examples**

See [getUserStorageStats](#getuserstoragestats)


## getUserStorageStats

```TypeScript
function getUserStorageStats(userId: number, callback: AsyncCallback<StorageStats>): void
```

Obtains the storage statistics of the specified user, in bytes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[StorageStats](arkts-corefile-storagestatistics-storagestats-i-sys.md)&gt; | Yes | Callback used to return the storage statistics obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600009 | User if out of range. |
| 13900042 | Unknown error. |

**Examples**

See [getUserStorageStats](#getuserstoragestats)
