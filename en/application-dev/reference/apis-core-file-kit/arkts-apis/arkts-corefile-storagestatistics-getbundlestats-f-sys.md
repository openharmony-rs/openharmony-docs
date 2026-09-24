# getBundleStats (System API)

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getBundleStats

```TypeScript
function getBundleStats(packageName: string, callback: AsyncCallback<BundleStats>, index?: number): void
```

Obtains the storage space of an application, in bytes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| packageName | string | Yes | Package name of the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | Yes | Callback used to return the application storage space obtained. |
| index | number | No | Index of an application clone. The default value is **0**, which indicates the application itself. When an application clone is created, an index is assigned from 1 sequentially to **appIndex** of [BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md) The index can be obtained by [getBundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md)<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, (err: BusinessError, BundleStats: storageStatistics.BundleStats) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getBundleStats failed with error: %{public}s', JSON.stringify(err));
    } else {
      hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
    }
  }, index);

} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed: %{public}s', message);
}
```


<a id="getbundlestats-1"></a>

## getBundleStats

```TypeScript
function getBundleStats(packageName: string, index?: number): Promise<BundleStats>
```

Obtains the storage space of an application, in bytes. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.STORAGE_MANAGER

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| packageName | string | Yes | Package name of the application. |
| index | number | No | Index of an application clone. The default value is **0**, which indicates the application itself. When an application clone is created, an index is assigned from 1 sequentially to **appIndex** of [BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md) The index can be obtained by [getBundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md)<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | Promise used to return the application storage space (in bytes) obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, index).then((BundleStats: storageStatistics.BundleStats) => {
    hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getBundleStats failed with error: %{public}s', JSON.stringify(err));
  });

} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed with error: %{public}s', message);
}
```


<a id="getbundlestats-2"></a>

## getBundleStats

```TypeScript
function getBundleStats(packageName: string, option?: BundleStatsOptions): Promise<BundleStats>
```

Obtains the storage space of an application, in bytes. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.STORAGE_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| packageName | string | Yes | Package name of the application. |
| option | [BundleStatsOptions](arkts-corefile-storagestatistics-bundlestatsoptions-i-sys.md) | No | Options for obtaining the bundle statistics. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | Promise used to return the application storage space (in bytes) obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600008 | No such object. |

**Examples**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, index).then((BundleStats: storageStatistics.BundleStats) => {
    hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getBundleStats failed with error: %{public}s', JSON.stringify(err));
  });

} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed with error: %{public}s', message);
}
```

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, (err: BusinessError, BundleStats: storageStatistics.BundleStats) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getBundleStats failed with error: %{public}s', JSON.stringify(err));
    } else {
      hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
    }
  }, index);

} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed: %{public}s', message);
}
```
