# getCurrentBundleStats

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getCurrentBundleStats

```TypeScript
function getCurrentBundleStats(callback: AsyncCallback<BundleStats>): void
```

Obtains the storage space (in bytes) of this application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | Yes | Callback used to return the application space obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getCurrentBundleStats().then((BundleStats: storageStatistics.BundleStats) => {
  console.info("getCurrentBundleStats successfully:" + JSON.stringify(BundleStats));
}).catch((err: BusinessError) => {
  console.error("getCurrentBundleStats failed with error:"+ JSON.stringify(err));
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getCurrentBundleStats((error: BusinessError, bundleStats: storageStatistics.BundleStats) => {
  if (error) {
    console.error("getCurrentBundleStats failed with error:" + JSON.stringify(error));
  } else {
    // Do something.
    console.info("getCurrentBundleStats successfully:" + JSON.stringify(bundleStats));
  }
});
```


## getCurrentBundleStats

```TypeScript
function getCurrentBundleStats(): Promise<BundleStats>
```

Obtains the storage space (in bytes) of this application. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | Promise used to return the application storage space obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

See [getCurrentBundleStats](#getcurrentbundlestats)
