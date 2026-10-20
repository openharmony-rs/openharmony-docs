# getFreeSize

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getFreeSize

```TypeScript
function getFreeSize(callback: AsyncCallback<number>): void
```

Obtains the available space (in bytes) of the built-in storage. This API uses an asynchronous callback to return the result.

**Since:** 15

<!--Device-storageStatistics-function getFreeSize(callback: AsyncCallback<long>): void--><!--Device-storageStatistics-function getFreeSize(callback: AsyncCallback<long>): void-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the available space of the built-in storage obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getFreeSize((error: BusinessError, number: number) => {
  if (error) {
    console.error("getFreeSize failed with error:" + JSON.stringify(error));
  } else {
    // Do something.
    console.info("getFreeSize successfully:" + number);
  }
});
```


## getFreeSize

```TypeScript
function getFreeSize(): Promise<number>
```

Obtains the available space (in bytes) of the built-in storage. This API uses a promise to return the result.

**Since:** 15

<!--Device-storageStatistics-function getFreeSize(): Promise<long>--><!--Device-storageStatistics-function getFreeSize(): Promise<long>-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the available space of the built-in storage obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getFreeSize().then((number: number) => {
  console.info("getFreeSize successfully:" + JSON.stringify(number));
}).catch((err: BusinessError) => {
  console.error("getFreeSize failed with error:" + JSON.stringify(err));
});
```
