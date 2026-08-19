# PhotoAssetCustomRecordManager（系统接口）

媒体库支持图库自定义用户统计行为。

**起始版本：** 23

<!--Device-photoAccessHelper-class PhotoAssetCustomRecordManager--><!--Device-photoAccessHelper-class PhotoAssetCustomRecordManager-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addLcdJumpCount

```TypeScript
addLcdJumpCount(ids: Array<int>): Promise<Array<int>>
```

根据[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)中的fileId给数据库中对应数据的LcdJumpCount加1。使用Promise异步回调。

**起始版本：** 23

<!--Device-PhotoAssetCustomRecordManager-addLcdJumpCount(ids: Array<int>): Promise<Array<int>>--><!--Device-PhotoAssetCustomRecordManager-addLcdJumpCount(ids: Array<int>): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ids | Array&lt;int&gt; | 是 | [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)中的fileId集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | 更新失败的自定义用户统计行为数据中的fileId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario parameters fail to pass the verification.Possible causes: <br>1. The ids list is empty. <br>2. The number of ids lists exceeds 500. |

## addShareCount

```TypeScript
addShareCount(ids: Array<int>): Promise<Array<int>>
```

根据[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)中的fileId给数据库中对应数据的shareCount加1。使用Promise异步回调。

**起始版本：** 23

<!--Device-PhotoAssetCustomRecordManager-addShareCount(ids: Array<int>): Promise<Array<int>>--><!--Device-PhotoAssetCustomRecordManager-addShareCount(ids: Array<int>): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ids | Array&lt;int&gt; | 是 | [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)中的fileId集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | 更新失败的自定义用户统计行为数据中的fileId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario parameters fail to pass the verification.Possible causes: <br>1. The ids list is empty. 2. The number of ids lists exceeds 500. |

## createCustomRecords

```TypeScript
createCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<void>
```

新增自定义用户统计行为数据。使用Promise异步回调。

**起始版本：** 23

<!--Device-PhotoAssetCustomRecordManager-createCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<void>--><!--Device-PhotoAssetCustomRecordManager-createCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customRecords | Array&lt;[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)&gt; | 是 | 新增自定义用户统计行为数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario parameters fail to pass the verification.Possible causes: <br>1. The value range of mandatory parameters in photoAssetCustomRecord does not meet the requirements. <br>2. The transferred record already exists. 3. The number of transferred records exceeds 200. |

**示例**

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

获取图库自定义用户统计行为实例。

**起始版本：** 20

<!--Device-PhotoAssetCustomRecordManager-static getCustomRecordManagerInstance(context: Context): PhotoAssetCustomRecordManager--><!--Device-PhotoAssetCustomRecordManager-static getCustomRecordManagerInstance(context: Context): PhotoAssetCustomRecordManager-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PhotoAssetCustomRecordManager](arkts-medialibrary-photoaccesshelper-photoassetcustomrecordmanager-c-sys.md) | 用户自定义行为统计实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800107](../errorcode-medialibrary.md#23800107-context为空或者无效) | Context is invalid |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

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

## getCustomRecordManagerInstance

```TypeScript
static getCustomRecordManagerInstance(context: Context): PhotoAssetCustomRecordManager | null
```

获取图库自定义用户统计行为实例。

**起始版本：** 23

<!--Device-PhotoAssetCustomRecordManager-static getCustomRecordManagerInstance(context: Context): PhotoAssetCustomRecordManager | null--><!--Device-PhotoAssetCustomRecordManager-static getCustomRecordManagerInstance(context: Context): PhotoAssetCustomRecordManager | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Context of the ability instance. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PhotoAssetCustomRecordManager](arkts-medialibrary-photoaccesshelper-photoassetcustomrecordmanager-c-sys.md) | Returns media asset custom record manager instance if operation fails, return null. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800107](../errorcode-medialibrary.md#23800107-context为空或者无效) | Context is invalid |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

## getCustomRecords

```TypeScript
getCustomRecords(optionCheck: FetchOptions): Promise<FetchResult<PhotoAssetCustomRecord>>
```

根据检索选项获取自定义用户统计行为数据。使用Promise异步回调。

**起始版本：** 23

<!--Device-PhotoAssetCustomRecordManager-getCustomRecords(optionCheck: FetchOptions): Promise<FetchResult<PhotoAssetCustomRecord>>--><!--Device-PhotoAssetCustomRecordManager-getCustomRecords(optionCheck: FetchOptions): Promise<FetchResult<PhotoAssetCustomRecord>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optionCheck | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)&gt;&gt; | Promise对象，返回自定义用户统计行为数据集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario parameters fail to pass the verification.Possible causes: 1. The filter criteria or fetchColumns that are not supported by options are transferred. |

**示例**

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

根据检索选项删除自定义用户统计行为数据。使用Promise异步回调。

**起始版本：** 23

<!--Device-PhotoAssetCustomRecordManager-removeCustomRecords(optionCheck: FetchOptions): Promise<void>--><!--Device-PhotoAssetCustomRecordManager-removeCustomRecords(optionCheck: FetchOptions): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optionCheck | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario parameters fail to pass the verification.Possible causes: <br>1. The filter criteria or fetchColumns that are not supported by options are transferred. |

**示例**

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
setCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<Array<int>>
```

根据自定义用户统计行为数据，更新已存在的数据库字段。使用Promise异步回调。

**起始版本：** 23

<!--Device-PhotoAssetCustomRecordManager-setCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<Array<int>>--><!--Device-PhotoAssetCustomRecordManager-setCustomRecords(customRecords: Array<PhotoAssetCustomRecord>): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customRecords | Array&lt;[PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md)&gt; | 是 | 自定义用户统计行为数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | 更新失败的自定义用户统计行为数据中的fileId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario parameters fail to pass the verification.Possible causes: <br>1. The value range of mandatory parameters in photoAssetCustomRecord does not meet the requirements. <br>2. The number of transferred records exceeds 200. |

**示例**

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

