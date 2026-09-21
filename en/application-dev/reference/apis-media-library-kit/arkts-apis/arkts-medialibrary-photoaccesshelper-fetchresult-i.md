# FetchResult

```TypeScript
interface FetchResult<T>
```

FetchResult provides APIs to manage the file retrieval result.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## close

```TypeScript
close(): void
```

Closes this FetchResult instance to invalidate it. After this instance is released, the APIs in this instance cannot be invoked.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('fetchResultCloseDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    fetchResult.close();
    console.info('close succeed.');
  } catch (err) {
    console.error(`close fail. error: ${err.code}, ${err.message}`);
  }
}
```

## contains

```TypeScript
contains(object: T): Promise<boolean>
```

Checks whether the specified file asset is contained in the result set. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| object | T | Yes | Specified file asset. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** indicates that the specified file asset is contained in the result set, and **false** indicates the opposite. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('fetchResultContainsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let ret: boolean = await fetchResult.contains(asset);
    console.info(`succeed. ${ret}`);
  } catch (err) {
    console.error(`fail. error: ${err.code}, ${err.message}`);
  }
}
```

## getAllObjects

```TypeScript
getAllObjects(callback: AsyncCallback<Array<T>>): void
```

Obtains all the file assets in the result set. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;T&gt;&gt; | Yes | Callback function. If all file assets in the result set are successfully obtained, **err** is **undefined**, and **data** is the specific search result. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAllObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  fetchResult.getAllObjects((err, photoAssetList) => {
    if (photoAssetList !== undefined) {
      console.info('photoAssetList length: ', photoAssetList.length);
    } else {
      console.error(`photoAssetList failed with err:${err.code}, ${err.message}`);
    }
  });
}
```

<a id="getallobjects-1"></a>

## getAllObjects

```TypeScript
getAllObjects(): Promise<Array<T>>
```

Obtains all the file assets in the result set. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Promise used to return an array of all file assets. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAllObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAssetList: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
  console.info('photoAssetList length: ', photoAssetList.length);
}
```

## getCount

```TypeScript
getCount(): number
```

Obtains the total number of files in the result set.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Total number of files obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getCountDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let fetchCount = fetchResult.getCount();
  console.info('fetchCount = ', fetchCount);
}
```

## getFirstObject

```TypeScript
getFirstObject(callback: AsyncCallback<T>): void
```

Obtains the first file asset in the result set. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback function. If the first file asset in the result set is successfully obtained, **err** is **undefined**, and **data** is the specific search result. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getFirstObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  fetchResult.getFirstObject((err, photoAsset) => {
    if (photoAsset !== undefined) {
      console.info('photoAsset displayName: ', photoAsset.displayName);
    } else {
      console.error(`photoAsset failed with err:${err.code}, ${err.message}`);
    }
  });
}
```

<a id="getfirstobject-1"></a>

## getFirstObject

```TypeScript
getFirstObject(): Promise<T>
```

Obtains the first file asset in the result set. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the first object in the result set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getFirstObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  console.info('photoAsset displayName: ', photoAsset.displayName);
}
```

## getIndex

```TypeScript
getIndex(object: T): Promise<number>
```

Obtains the index of a specified file asset in the result set. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| object | T | Yes | Specified file asset. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. If the object exists in the result set, the corresponding index is returned. Otherwise, **-1** is returned. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('fetchResultGetIndexDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let ret: number = await fetchResult.getIndex(asset);
    console.info(`succeed. ${ret}`);
  } catch (err) {
    console.error(`fail. error: ${err.code}, ${err.message}`);
  }
}
```

## getLastObject

```TypeScript
getLastObject(callback: AsyncCallback<T>): void
```

Obtains the last file asset in the result set. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback function. If the last file asset in the result set is successfully obtained, **err** is **undefined**, and **data** is the specific search result. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getLastObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  fetchResult.getLastObject((err, photoAsset) => {
    if (photoAsset !== undefined) {
      console.info('photoAsset displayName: ', photoAsset.displayName);
    } else {
      console.error(`photoAsset failed with err: ${err.code}, ${err.message}`);
    }
  });
}
```

<a id="getlastobject-1"></a>

## getLastObject

```TypeScript
getLastObject(): Promise<T>
```

Obtains the last file asset in the result set. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the last object in the result set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getLastObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getLastObject();
  console.info('photoAsset displayName: ', photoAsset.displayName);
}
```

## getNextObject

```TypeScript
getNextObject(callback: AsyncCallback<T>): void
```

Obtains the next file asset in the result set. This API uses an asynchronous callback to return the result.

Before using this API, you must use [isAfterLast()](#isafterlast) to check whether the current position is the end of the result set.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback function. If the next file asset in the result set is successfully obtained, **err** is **undefined**, and **data** is the specific search result. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getNextObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  await fetchResult.getFirstObject();
  if (!fetchResult.isAfterLast()) {
    fetchResult.getNextObject((err, photoAsset) => {
      if (photoAsset !== undefined) {
        console.info('photoAsset displayName: ', photoAsset.displayName);
      } else {
        console.error(`photoAsset failed with err: ${err.code}, ${err.message}`);
      }
    });
  }
}
```

<a id="getnextobject-1"></a>

## getNextObject

```TypeScript
getNextObject(): Promise<T>
```

Obtains the next file asset in the result set. This API uses a promise to return the result.

Before using this API, you must use [isAfterLast()](#isafterlast) to check whether the current position is the end of the result set.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the next object in the result set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getNextObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  await fetchResult.getFirstObject();
  if (!fetchResult.isAfterLast()) {
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getNextObject();
    console.info('photoAsset displayName: ', photoAsset.displayName);
  }
}
```

## getObjectByPosition

```TypeScript
getObjectByPosition(index: number, callback: AsyncCallback<T>): void
```

Obtains a file asset with the specified index in the result set. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the file asset to obtain. The value starts from **0**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback function. If the file asset with the specified index in the result set is successfully obtained, **err** is **undefined**, and **data** is the specific search result. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getObjectByPositionDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  fetchResult.getObjectByPosition(0, (err, photoAsset) => {
    if (photoAsset !== undefined) {
      console.info('photoAsset displayName: ', photoAsset.displayName);
    } else {
      console.error(`photoAsset failed with err: ${err.code}, ${err.message}`);
    }
  });
}
```

<a id="getobjectbyposition-1"></a>

## getObjectByPosition

```TypeScript
getObjectByPosition(index: number): Promise<T>
```

Obtains a file asset with the specified index in the result set. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the file asset to obtain. The value starts from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the file asset obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getObjectByPositionDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  if (fetchResult === undefined) {
    console.error('fetchResult is undefined');
    return;
  }
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getObjectByPosition(0);
  console.info('photoAsset displayName: ', photoAsset.displayName);
}
```

## getObjectsByIndexSet

```TypeScript
getObjectsByIndexSet(indexSet: number[]): Promise<T[]>
```

Obtains the file asset array corresponding to the specified index set in the result set. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indexSet | number[] | Yes | Specified index set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T[]&gt; | Promise object, which returns the file asset array corresponding to the specified index set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1.The indexSet is null, undefined or empty. <br>2.The indexSet length is bigger than 500. <br>3.The max value of indexSet is equal or bigger than the fetch result length. <br>4.The min value of indexSet is less than 0. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('fetchResultGetObjectsByIndexSetDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let indexSet: number[] = [0, 1];
    let ret: photoAccessHelper.PhotoAsset[] = await fetchResult.getObjectsByIndexSet(indexSet);
    console.info(`succeed. ${ret.length}`);
  } catch (err) {
    console.error(`fail. error: ${err.code}, ${err.message}`);
  }
}
```

## getRangeObjects

```TypeScript
getRangeObjects(index: number, offset: number): Promise<T[]>
```

Obtains the file asset array of a specified length (second parameter) from the specified index (first parameter) in the result set. This API uses a promise to return the result.

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the file asset to be obtained. The value must be greater than or equal to 0 and less than the number of objects in the result set. |
| offset | number | Yes | Number of file assets to be obtained. The value must be greater than 0.<br>The sum of **index** and **offset** must be less than the total number of objects in the result set. Otherwise, error code **23800151** is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T[]&gt; | Promise array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application<br>**Applicable version:** 21 - 22 |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails.<br>Possible causes: index or offset validity check failed. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. You are advised to retry and check the logs.<br>Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper} from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getRangeObjectsDemo');
  type PhotoAsset = photoAccessHelper.PhotoAsset;
  let testNum: string = "getRangeObjects_test_003";
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
  };
  let fetchResult1: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
      await phAccessHelper.getAssets(fetchOptions);
  let fetchResult2: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
      await phAccessHelper.getAssets(fetchOptions);
  let count: number = fetchResult1.getCount();
  const half: number = Math.ceil(count / 2);
  let promises: Promise<PhotoAsset[]>[] = [];
  promises[0] = fetchResult1.getRangeObjects(0, half);
  promises[1] = fetchResult2.getRangeObjects(half, count - half);
  let photoAssetsArray: PhotoAsset[][] = await Promise.all(promises);
  let photoAssets: PhotoAsset[] = photoAssetsArray[0].concat(photoAssetsArray[1]);
  console.info('photoAssets length: ', photoAssets.length);
}
```

## isAfterLast

```TypeScript
isAfterLast(): boolean
```

Checks whether the cursor is in the last row of the result set.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** is returned if the cursor is in the last row of the result set; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let fetchCount = fetchResult.getCount();
  console.info('count:' + fetchCount);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getLastObject();
  if (fetchResult.isAfterLast()) {
    console.info('photoAsset isAfterLast displayName = ', photoAsset.displayName);
  } else {
    console.info('photoAsset not isAfterLast.');
  }
}
```
