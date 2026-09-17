# PhotoAssetCustomRecordManager (System API)

Provides APIs for custom user behavior recording for Gallery.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addLcdJumpCount

```TypeScript
addLcdJumpCount(ids: Array<number>): Promise<Array<number>>
```

Increases the value of **LcdJumpCount** by 1 for the data in the database based on **fileId** in [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md). This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ids | Array&lt;number&gt; | Yes | Array of file IDs in [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the file ID in the custom user behavior recordings that fail to be updated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario parameters fail to pass the verification.Possible causes:<br>1. The ids list is empty. <br>2. The number of ids lists exceeds 500. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## addShareCount

```TypeScript
addShareCount(ids: Array<number>): Promise<Array<number>>
```

Increases the value of **shareCount** by 1 for the data in the database based on **fileId** in [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md). This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ids | Array&lt;number&gt; | Yes | Array of file IDs in [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the file ID in the custom user behavior recordings that fail to be updated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario parameters fail to pass the verification.Possible causes:<br>1. The ids list is empty. 2. The number of ids lists exceeds 500. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## createCustomRecords

```TypeScript
createCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<void>
```

Adds custom user behavior recordings. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customRecords | Array&lt;[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)&gt; | Yes | Custom user behavior recordings. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario parameters fail to pass the verification.Possible causes:<br>1. The value range of mandatory parameters in photoAssetCustomRecord does not meet the requirements. <br>2. The transferred record already exists. 3. The number of transferred records exceeds 200. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(context: Context) {
  console.info('createCustomRecords');
  let crManager = photoAccessHelper.PhotoAssetCustomRecordManager.getCustomRecordManagerInstance(context);
  let crArray:Array<photoAccessHelper.PhotoAssetCustomRecord> = [
    {fileId:1,shareCount:1,lcdJumpCount:1}
  ];
  crManager.createCustomRecords(crArray).then(() => {
    console.info('createCustomRecords successful');
  }).catch((err: BusinessError) => {
    console.error(`createCustomRecords fail with error: ${err.code}, ${err.message}`);
  });
}
```

## getCustomRecordManagerInstance

```TypeScript
static getCustomRecordManagerInstance(context: Context): PhotoAssetCustomRecordManager
```

Obtains an instance of custom user behavior recording for Gallery.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |

**Return value:**

| Type | Description |
| --- | --- |
| [PhotoAssetCustomRecordManager](arkts-medialibrary-photoaccesshelper-photoassetcustomrecordmanager-c-sys.md) | Custom user behavior recording instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800107](../errorcode-medialibrary.md#23800107-context-is-empty-or-invalid) | Context is invalid |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(context: Context) {
  console.info('getCustomRecordManagerInstance');
  try {
    let crManager = photoAccessHelper.PhotoAssetCustomRecordManager.getCustomRecordManagerInstance(context);
  } catch(err) {
    console.error(`getCustomRecordManagerInstance failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getCustomRecords

```TypeScript
getCustomRecords(optionCheck: FetchOptions): Promise<FetchResult<PhotoAssetCustomRecord>>
```

Obtains custom user behavior recordings based on retrieval options. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| optionCheck | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)&gt;&gt; | Promise used to return the collection of custom user behavior recordings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario parameters fail to pass the verification.Possible causes: 1. The filter criteria or fetchColumns that are not supported by options are transferred. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(context: Context) {
  console.info('getCustomRecords');
  let crManager = photoAccessHelper.PhotoAssetCustomRecordManager.getCustomRecordManagerInstance(context);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('file_id', 1);
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  crManager.getCustomRecords(fetchOption).then(async (fetchResult) => {
    let record = await fetchResult.getFirstObject();
    console.info('record file id is ' + record.fileId);
  }).catch((err: BusinessError) => {
    console.error('getCustomRecords fail with error: ${err.code}, ${err.message}');
  });
}
```

## removeCustomRecords

```TypeScript
removeCustomRecords(optionCheck: FetchOptions): Promise<void>
```

Removes custom user behavior recordings based on retrieval options. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| optionCheck | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario parameters fail to pass the verification.Possible causes:<br>1. The filter criteria or fetchColumns that are not supported by options are transferred. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(context: Context) {
  console.info('removeCustomRecords');
  let crManager = photoAccessHelper.PhotoAssetCustomRecordManager.getCustomRecordManagerInstance(context);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('file_id', 1);
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  crManager.removeCustomRecords(fetchOption).then(() => {
    console.info('removeCustomRecords successful');
  }).catch((err: BusinessError) => {
    console.error(`removeCustomRecords fail with error: ${err.code}, ${err.message}`);
  });
}
```

## setCustomRecords

```TypeScript
setCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<Array<number>>
```

Updates the existing database fields based on custom user behavior recordings. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customRecords | Array&lt;[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)&gt; | Yes | Custom user behavior recordings. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the file ID in the custom user behavior recordings that fail to be updated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario parameters fail to pass the verification.Possible causes:<br>1. The value range of mandatory parameters in photoAssetCustomRecord does not meet the requirements. <br>2. The number of transferred records exceeds 200. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(context: Context) {
  console.info('setCustomRecords');
  let crManager = photoAccessHelper.PhotoAssetCustomRecordManager.getCustomRecordManagerInstance(context);
  let UpdateArray: Array<photoAccessHelper.PhotoAssetCustomRecord> = [
    {fileId:1,shareCount:2,lcdJumpCount:3},
    {fileId:2,shareCount:2,lcdJumpCount:3}
  ];
  crManager.setCustomRecords(UpdateArray).then((failIds) => {
    console.info('setCustomRecords successful');
  }).catch((err: BusinessError) => {
    console.error('setCustomRecords file with err: ${err.code}, ${err.message}');
  });
}
```
