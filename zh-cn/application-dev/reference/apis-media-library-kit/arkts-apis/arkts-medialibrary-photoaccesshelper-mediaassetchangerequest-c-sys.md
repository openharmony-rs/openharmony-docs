# MediaAssetChangeRequest

MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md). 资产变更请求。 > **说明：** > > - 本Class首批接口从API version 11开始支持。

**继承/实现关系：** MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**起始版本：** 23

<!--Device-photoAccessHelper-class MediaAssetChangeRequest--><!--Device-photoAccessHelper-class MediaAssetChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addResource

```TypeScript
addResource(type: ResourceType, proxy: PhotoProxy): void
```

通过PhotoProxy数据添加资源。 > **注意：** > > 对于同一个资产变更请求，不支持在成功添加资源后，重复调用该接口。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-addResource(type: ResourceType, proxy: PhotoProxy): void--><!--Device-MediaAssetChangeRequest-addResource(type: ResourceType, proxy: PhotoProxy): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | ResourceType | 是 | 待添加资源的类型。 |
| proxy | [PhotoProxy](arkts-medialibrary-photoaccesshelper-photoproxy-i.md) | 是 | 待添加资源的PhotoProxy 数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000016 | Operation Not Support |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
class PhotoProxyImpl implements photoAccessHelper.PhotoProxy {
  // 应用实现PhotoProxy。
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, asset: photoAccessHelper.PhotoAsset, context: Context) {
  console.info('addResourceByPhotoProxyDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context, photoType, extension);
    let photoProxy: PhotoProxyImpl = new PhotoProxyImpl();
    assetChangeRequest.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, photoProxy);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('addResourceByPhotoProxy successfully');
  } catch (err) {
    console.error(`addResourceByPhotoProxyDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## addResourceForPicker

```TypeScript
addResourceForPicker(type: ResourceType, fileUri: string): void
```

通过[fileUri](../../apis-core-file-kit/arkts-apis/arkts-file-fileuri.md)从应用沙箱添加资源。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

<!--Device-MediaAssetChangeRequest-addResourceForPicker(type: ResourceType, fileUri: string): void--><!--Device-MediaAssetChangeRequest-addResourceForPicker(type: ResourceType, fileUri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | ResourceType | 是 | 待加载的图片或者视频类型 |
| fileUri | string | 是 | 待加载图片或者视频的路径 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## createAssetRequest

```TypeScript
static createAssetRequest(context: Context, displayName: string, options?: PhotoCreateOptions): MediaAssetChangeRequest
```

指定待创建的图片或者视频的文件名，创建资产变更请求。 待创建的文件名参数规格为： - 应包含有效文件主名和图片或视频扩展名。 - 文件名字符串长度为1~255。 - 文件主名中不允许出现的非法英文字符。 API18开始，非法字符包括： \ / : * ? " &lt; &gt; | API10-17，非法字符包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 11

<!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, displayName: string, options?: PhotoCreateOptions): MediaAssetChangeRequest--><!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, displayName: string, options?: PhotoCreateOptions): MediaAssetChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| displayName | string | 是 | 待创建的图片或者视频文件名。 |
| options | [PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | 否 | 图片或视频的创建选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | 返回创建资产的变更请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000001 | Invalid display name |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('createAssetRequestDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context, testFileName);
    // 需要确保fileUri对应的资源存在。
    let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
    assetChangeRequest.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, fileUri);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply createAssetRequest successfully');
  } catch (err) {
    console.error(`createAssetRequestDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## createAssetRequest

```TypeScript
static createAssetRequest(context: Context, displayName: string, options?: PhotoCreateOptions): MediaAssetChangeRequest | null
```

指定待创建的图片或者视频的文件名，创建资产变更请求。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, displayName: string, options?: PhotoCreateOptions): MediaAssetChangeRequest | null--><!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, displayName: string, options?: PhotoCreateOptions): MediaAssetChangeRequest | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Context of the ability instance. |
| displayName | string | 是 | File name of the image or video to create. |
| options | [PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | 否 | Options for creating an image or video asset. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | Returns a MediaAssetChangeRequest instance. if the operation fails, returns null |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 23800102 | The format or length of the display name does not meet the specifications. |

## deleteAssetsPermanentlyWithUri

```TypeScript
static deleteAssetsPermanentlyWithUri(context: Context, assetUris: string[]): Promise<void>
```

通过资产URI批量彻底删除照片或视频，不经过回收站。使用promise异步回调。 > **说明：** > > - 对仅存在于本端设备的资产、仅存在于云端的资产、存在于本端设备和云端的资产，均可以彻底删除，不经过回收站。 > > - 此操作不可逆。执行此操作后文件资源将被彻底删除，请谨慎操作。

**起始版本：** 24

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAssetChangeRequest-static deleteAssetsPermanentlyWithUri(context: Context, assetUris: string[]): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteAssetsPermanentlyWithUri(context: Context, assetUris: string[]): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| assetUris | string[] | 是 | 待删除的图片或视频URI数组，数组中元素个数不超过500个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by nonsystem application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The context is empty; <br>2. Asset uri array size is empty or bigger than 500 . |

**示例**

```TypeScript
async function example(context: Context, assetUri: string) {
    console.info('deleteAssetsPermanentlyWithUri');
    try {
      await photoAccessHelper.MediaAssetChangeRequest.deleteAssetsPermanentlyWithUri(context, [assetUri]);
      console.info('deleteAssetsPermanentlyWithUri success.');
    } catch (err) {
      console.error(`deleteAssetsPermanentlyWithUri failed with error: ${err.code}, ${err.message}`);
    }
}
```

## deleteCloudAssetsWithUri

```TypeScript
static deleteCloudAssetsWithUri(context: Context, assetUris: string[]): Promise<void>
```

批量删除云端状态的媒体资产（照片或视频）到回收站。使用promise异步回调。 > **说明：** > > - 对仅存在于本端设备的资产，不做任何处理。 > > - 对仅存在于云端的资产，直接删除到回收站。 > > - 对存在于本端设备和云端的资产，删除后变化为本地资产，云端资产进入回收站。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-static deleteCloudAssetsWithUri(context: Context, assetUris: string[]): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteCloudAssetsWithUri(context: Context, assetUris: string[]): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| assetUris | string[] | 是 | 待删除的图片或者视频Uri数组，数组中元素个数不超过500个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The context is empty; <br>2. Asset uri array size is empty or bigger than 500 . |

**示例**

```TypeScript
async function example(context: Context, assetUri: string) {
    console.info('deleteCloudAssetsWithUriDemo');
    try {
      await photoAccessHelper.MediaAssetChangeRequest.deleteCloudAssetsWithUri(context, [assetUri]);
    } catch (err) {
      console.error(`deleteCloudAssetsWithUri failed with error: ${err.code}, ${err.message}`);
    }
}
```

## deleteLocalAssetsPermanently

```TypeScript
static deleteLocalAssetsPermanently(context: Context, assets: Array<PhotoAsset>): Promise<void>
```

批量彻底删除照片或者视频。使用Promise异步回调。 > **注意：** > > 此操作不可逆，执行此操作后文件资源将彻底删除，请谨慎操作。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-static deleteLocalAssetsPermanently(context: Context, assets: Array<PhotoAsset>): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteLocalAssetsPermanently(context: Context, assets: Array<PhotoAsset>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| assets | Array&lt;PhotoAsset&gt; | 是 | 待彻底删除的图片或者视频数组，数组中元素个数不超过500个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('deleteAssetsPermanentlyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAssetList: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
    await photoAccessHelper.MediaAssetChangeRequest.deleteLocalAssetsPermanently(context, photoAssetList);
  } catch (err) {
    console.error(`deleteAssetsPermanentlyDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## deleteLocalAssetsPermanentlyWithUri

```TypeScript
static deleteLocalAssetsPermanentlyWithUri(context: Context, assetUris: Array<string>): Promise<void>
```

通过资产Uri批量彻底删除照片或者视频。使用promise异步回调。 > **注意：** > > 此操作不可逆，执行此操作后文件资源将被彻底删除，请谨慎操作。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-static deleteLocalAssetsPermanentlyWithUri(context: Context, assetUris: Array<string>): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteLocalAssetsPermanentlyWithUri(context: Context, assetUris: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| assetUris | Array&lt;string&gt; | 是 | 待彻底删除的图片或者视频Uri数组，数组中元素个数不超过500个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## deleteLocalAssetsWithUri

```TypeScript
static deleteLocalAssetsWithUri(context: Context, assetUris: string[]): Promise<void>
```

批量删除本地状态的媒体资产（照片或视频）到回收站。使用promise异步回调。 > **说明：** > > - 对仅存在于本端设备的资产，直接删除到回收站。 > > - 对仅存在于云端的资产，不做任何处理。 > > - 对存在于本端设备和云端的资产，删除后变化为云端资产，本地资产进入回收站。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-static deleteLocalAssetsWithUri(context: Context, assetUris: string[]): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteLocalAssetsWithUri(context: Context, assetUris: string[]): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| assetUris | string[] | 是 | 待删除的图片或者视频Uri数组，数组中元素个数不超过500个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1.Database corrupted; <br>2.The file system is abnormal; <br>3.The IPC request timed out; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The context is empty; <br>2. Asset uri array size is empty or bigger than 500 . |

**示例**

```TypeScript
async function example(context: Context, assetUri: string) {
    console.info('deleteLocalAssetsWithUriDemo');
    try {
      await photoAccessHelper.MediaAssetChangeRequest.deleteLocalAssetsWithUri(context, [assetUri]);
    } catch (err) {
      console.error(`deleteLocalAssetsWithUri failed with error: ${err.code}, ${err.message}`);
    }
}
```

## setAppLinkInfo

```TypeScript
setAppLinkInfo(appLink: string): void
```

设置文件记忆链接的信息。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setAppLinkInfo(appLink: string): void--><!--Device-MediaAssetChangeRequest-setAppLinkInfo(appLink: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appLink | string | 是 | 设置文件记忆链接的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The input parameter's length is not within the valid range. |

**示例**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';


async function example(asset: photoAccessHelper.PhotoAsset, appLinkInfo: string, context: Context) {
    try {
      let phAccessHelper: photoAccessHelper.PhotoAccessHelper =
        photoAccessHelper.getPhotoAccessHelper(context);
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
        new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setAppLinkInfo(appLinkInfo);
      await phAccessHelper.applyChanges(assetChangeRequest);
    } catch (error) {
      console.error('set appLinkInfo error: ' + error);
      return;
    }
}
```

## setAppLinkState

```TypeScript
setAppLinkState(appLinkState: AppLinkState): void
```

设置文件记忆链接的状态信息。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAssetChangeRequest-setAppLinkState(appLinkState: AppLinkState): void--><!--Device-MediaAssetChangeRequest-setAppLinkState(appLinkState: AppLinkState): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appLinkState | [AppLinkState](arkts-medialibrary-photoaccesshelper-applinkstate-e-sys.md) | 是 | 设置文件记忆链接的状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Invoked by non-system applications |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The input parameter is not within the valid range. |

**示例**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(asset: photoAccessHelper.PhotoAsset, context: Context) {
    try {
      let phAccessHelper: photoAccessHelper.PhotoAccessHelper =
        photoAccessHelper.getPhotoAccessHelper(context);
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
        new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setAppLinkState(photoAccessHelper.AppLinkState.HAS_NO_LINK);
      await phAccessHelper.applyChanges(assetChangeRequest);
    } catch (error) {
      console.error('set appLink state error: ' + error);
      return;
    }
}
```

## setCameraEditData

```TypeScript
setCameraEditData(editData: MediaAssetEditData): void
```

保存资产的摄像机编辑数据。

**起始版本：** 26.1.0

<!--Device-MediaAssetChangeRequest-setCameraEditData(editData: MediaAssetEditData): void--><!--Device-MediaAssetChangeRequest-setCameraEditData(editData: MediaAssetEditData): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editData | [MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md) | 是 | 要保存的编辑数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The input parameter is not within the valid range. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setCameraEditDataDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);

  let assetEditData: photoAccessHelper.MediaAssetEditData = new photoAccessHelper.MediaAssetEditData('system', '1.0');
  // 当前仅为示意，使用时请替换为实际应用沙箱资源，需要确保fileUri对应的资源存在。
  let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
  assetChangeRequest.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, fileUri);
  assetEditData.data = '123456';
  assetChangeRequest.setCameraEditData(assetEditData);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setCameraEditData successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setCameraEditData failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setCameraShotKey

```TypeScript
setCameraShotKey(cameraShotKey: string): void
```

设置锁屏相机拍照或录像的标记字段。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setCameraShotKey(cameraShotKey: string): void--><!--Device-MediaAssetChangeRequest-setCameraShotKey(cameraShotKey: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraShotKey | string | 是 | 锁屏相机拍照或录像的标记字段（仅开放给系统相机，其key值由系统相机定义）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, asset: photoAccessHelper.PhotoAsset) {
  console.info('setCameraShotKeyDemo');
  try {
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    let cameraShotKey: string = 'test_MediaAssetChangeRequest_setCameraShotKey';
    assetChangeRequest.setCameraShotKey(cameraShotKey);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply setCameraShotKey successfully');
  } catch (err) {
    console.error(`apply setCameraShotKey failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setCompositeDisplayMode

```TypeScript
setCompositeDisplayMode(compositeDisplayMode: CompositeDisplayMode): Promise<void>
```

设置复合图的展示模式。使用Promise异步回调。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setCompositeDisplayMode(compositeDisplayMode: CompositeDisplayMode): Promise<void>--><!--Device-MediaAssetChangeRequest-setCompositeDisplayMode(compositeDisplayMode: CompositeDisplayMode): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compositeDisplayMode | [CompositeDisplayMode](arkts-medialibrary-photoaccesshelper-compositedisplaymode-e-sys.md) | 是 | 设置复合图的展示模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameter verification failed. Possible causes: <br>1. The compositeDisplayMode is not within the supported range. <br>2. The original file does not exist locally in PhotoAsset. <br>3. The PhotoAsset is not a composite asset. <br>4. The original file format is not within the supported range. <br>5. The original file has been edited. |

**示例**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
    console.info('setCompositeDisplayModeDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    try {
      let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
      let asset = await fetchResult.getFirstObject();
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setCompositeDisplayMode(photoAccessHelper.CompositeDisplayMode.DEFAULT);
      await phAccessHelper.applyChanges(assetChangeRequest);
      console.info('apply setCompositeDisplayModeDemo successfully');
    } catch (err) {
      console.error(`apply setCompositeDisplayModeDemo failed with error: ${err.code}, ${err.message}`);
    }
}
```

## setEditData

```TypeScript
setEditData(editData: MediaAssetEditData): void
```

保存资产的编辑数据。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setEditData(editData: MediaAssetEditData): void--><!--Device-MediaAssetChangeRequest-setEditData(editData: MediaAssetEditData): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editData | [MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md) | 是 | 待保存的资产编辑数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setEditDataDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);

  let assetEditData: photoAccessHelper.MediaAssetEditData = new photoAccessHelper.MediaAssetEditData('system', '1.0');
  let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
  assetChangeRequest.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, fileUri);
  assetEditData.data = '123456';
  assetChangeRequest.setEditData(assetEditData);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setEditData successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setEditData failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setEffectMode

```TypeScript
setEffectMode(mode: MovingPhotoEffectMode): void
```

设置动态照片的效果模式。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setEffectMode(mode: MovingPhotoEffectMode): void--><!--Device-MediaAssetChangeRequest-setEffectMode(mode: MovingPhotoEffectMode): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | MovingPhotoEffectMode | 是 | 动态照片效果模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000016 | Operation Not Support |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, asset: photoAccessHelper.PhotoAsset) {
  console.info('setEffectModeDemo');
  try {
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.setEffectMode(photoAccessHelper.MovingPhotoEffectMode.LONG_EXPOSURE);
    // 需要确保fileUri对应的资源存在。
    let imageFileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/long_exposure.jpg';
    let videoFileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/long_exposure.mp4';
    assetChangeRequest.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, imageFileUri);
    assetChangeRequest.addResource(photoAccessHelper.ResourceType.VIDEO_RESOURCE, videoFileUri);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply setEffectMode successfully');
  } catch (err) {
    console.error(`apply setEffectMode failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean): void
```

将文件设置为收藏文件。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setFavorite(favoriteState: boolean): void--><!--Device-MediaAssetChangeRequest-setFavorite(favoriteState: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| favoriteState | boolean | 是 | 是否设置为收藏文件， true：设置为收藏文件；false：取消收藏。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | System inner fail |

## setHasAppLink

```TypeScript
setHasAppLink(hasAppLink: int): void
```

设置文件记忆链接的状态信息。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setHasAppLink(hasAppLink: int): void--><!--Device-MediaAssetChangeRequest-setHasAppLink(hasAppLink: int): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hasAppLink | int | 是 | 设置文件记忆链接的状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The input parameter is not within the valid range. |

**示例**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

enum linkType {
  NOT_DECODED = 0,
  LINK_NOT_EXIST = 1,
  LINK_EXIST = 2
}

async function example(asset: photoAccessHelper.PhotoAsset, hasAppLink: linkType, context: Context) {
    try {
      let phAccessHelper: photoAccessHelper.PhotoAccessHelper =
        photoAccessHelper.getPhotoAccessHelper(context);
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
        new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setHasAppLink(hasAppLink);
      await phAccessHelper.applyChanges(assetChangeRequest);
    } catch (error) {
      console.error('set hasAppLink error: ' + error);
      return;
    }
}
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean): void
```

将文件设置为隐藏文件。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setHidden(hiddenState: boolean): void--><!--Device-MediaAssetChangeRequest-setHidden(hiddenState: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hiddenState | boolean | 是 | 是否设置为隐藏文件，true：将文件资产放入隐藏相册；false：从隐藏相册中恢复。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
  assetChangeRequest.setHidden(true);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setHidden successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setHidden failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setHiddenAttribute

```TypeScript
setHiddenAttribute(hiddenState: boolean): void
```

设置资产的UI隐藏属性

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAssetChangeRequest-setHiddenAttribute(hiddenState: boolean): void--><!--Device-MediaAssetChangeRequest-setHiddenAttribute(hiddenState: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hiddenState | boolean | 是 | 资产的隐藏状态 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The asset is not exist; |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setHiddenAttributeDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset = await fetchResult.getFirstObject();
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.setHiddenAttribute(true);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('setHiddenAttribute successfully');
  } catch (err) {
    console.error(`setHiddenAttribute failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setIsRecentShow

```TypeScript
setIsRecentShow(isRencentShow: boolean): void
```

Set recentShow state of the asset.

**起始版本：** 18

<!--Device-MediaAssetChangeRequest-setIsRecentShow(isRencentShow: boolean): void--><!--Device-MediaAssetChangeRequest-setIsRecentShow(isRencentShow: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isRencentShow | boolean | 是 | the new recentShow state of the asset |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

## setLivePhoto4dStatus

```TypeScript
setLivePhoto4dStatus(status: LivePhoto4dStatus, livephoto_4d_latest_pair?: string): void
```

子弹时间状态

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAssetChangeRequest-setLivePhoto4dStatus(status: LivePhoto4dStatus, livephoto_4d_latest_pair?: string): void--><!--Device-MediaAssetChangeRequest-setLivePhoto4dStatus(status: LivePhoto4dStatus, livephoto_4d_latest_pair?: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | [LivePhoto4dStatus](arkts-medialibrary-photoaccesshelper-livephoto4dstatus-e-sys.md) | 是 | 子弹时间状态 |
| livephoto_4d_latest_pair | string | 否 | 该动图生成的最近的子弹时间 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

## setLocation

```TypeScript
setLocation(longitude: double, latitude: double): void
```

设置文件的经纬度信息。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setLocation(longitude: double, latitude: double): void--><!--Device-MediaAssetChangeRequest-setLocation(longitude: double, latitude: double): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| longitude | double | 是 | 经度。 |
| latitude | double | 是 | 纬度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setLocationDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
  assetChangeRequest.setLocation(120.52, 30.40);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setLocation successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setLocation failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setMovingPhotoVersion

```TypeScript
setMovingPhotoVersion(version: int): void
```

保存动态照片的版本号。

**起始版本：** 26.0.0

<!--Device-MediaAssetChangeRequest-setMovingPhotoVersion(version: int): void--><!--Device-MediaAssetChangeRequest-setMovingPhotoVersion(version: int): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| version | int | 是 | 动图版本号<br>取值范围为全体整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Parameter error, only supports 9. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setMovingPhotoVersionDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);

  let movingPhotoVersion: number = 9;
  assetChangeRequest.setMovingPhotoVersion(movingPhotoVersion);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setMovingPhotoVersion successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setMovingPhotoVersion failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setSupportedWatermarkType

```TypeScript
setSupportedWatermarkType(watermarkType: WatermarkType): void
```

设置拍照照片支持的水印类型。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setSupportedWatermarkType(watermarkType: WatermarkType): void--><!--Device-MediaAssetChangeRequest-setSupportedWatermarkType(watermarkType: WatermarkType): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watermarkType | [WatermarkType](arkts-medialibrary-photoaccesshelper-watermarktype-e-sys.md) | 是 | 水印可编辑标识。 <br>**注意：** <br>不支持传入WatermarkType.DEFAULT。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setSupportedWatermarkTypeDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset = await fetchResult.getFirstObject();
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.setSupportedWatermarkType(photoAccessHelper.WatermarkType.BRAND_COMMON);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply setSupportedWatermarkType successfully');
  } catch (err) {
    console.error(`apply setSupportedWatermarkType failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setTitleByFile

```TypeScript
setTitleByFile(name: string): void
```

设置文件名，支持文管规则.命名

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAssetChangeRequest-setTitleByFile(name: string): void--><!--Device-MediaAssetChangeRequest-setTitleByFile(name: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 资产修改名称。 <br>取值范围:1-255 <br>不应包含扩展名。 文件名字符串长度为1~255。 不允许出现的非法英文字符，包括： . \ / : ? " ' ` &lt; &gt; \| { } [ ] 不允许仅命名.或者.. 文管目录下不允许重名 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The asset is not exist; |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset = await fetchResult.getFirstObject();
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.setTitleByFile('new_file_name');
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('setTitleByFile successfully');
  } catch (err) {
    console.error(`setTitleByFile failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setUserComment

```TypeScript
setUserComment(userComment: string): void
```

修改媒体资产的备注信息。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setUserComment(userComment: string): void--><!--Device-MediaAssetChangeRequest-setUserComment(userComment: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userComment | string | 是 | 待修改的资产备注信息，备注信息最长为420字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setUserCommentDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
  let userComment: string = 'test_set_user_comment';
  assetChangeRequest.setUserComment(userComment);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setUserComment successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setUserComment failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setVideoEnhancementAttr

```TypeScript
setVideoEnhancementAttr(videoEnhancementType: VideoEnhancementType, photoId: string): void
```

设置视频的二阶段增强处理类型。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setVideoEnhancementAttr(videoEnhancementType: VideoEnhancementType, photoId: string): void--><!--Device-MediaAssetChangeRequest-setVideoEnhancementAttr(videoEnhancementType: VideoEnhancementType, photoId: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| videoEnhancementType | [VideoEnhancementType](arkts-medialibrary-photoaccesshelper-videoenhancementtype-e-sys.md) | 是 | The type of video enhancement |
| photoId | string | 是 | The photo id of video |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000016 | Operation Not Support |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

