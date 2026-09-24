# MediaAssetChangeRequest

```TypeScript
class MediaAssetChangeRequest implements MediaChangeRequest
```

MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md).

资产变更请求。

> **说明：** 
> 
> - 本Class首批接口从API version 11开始支持。

**继承/实现关系：** MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addResource

```TypeScript
addResource(type: ResourceType, fileUri: string): void
```

通过文件URI从应用沙箱添加资源，待添加资源的数据来源可参考[@ohos.file.fileuri (File URI)](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileuri.md).

> **注意：**
> 
> 对于同一个资产变更请求，成功添加资源后不支持重复调用该接口。对于动态照片，可调用两次该接口分别添加图片和视频资源。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**测试接口：** 此接口仅在自动化测试脚本中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e.md) | 是 | 待添加资源的类型。 |
| fileUri | string | 是 | 待添加资源的数据来源，在应用沙箱下的uri。示例fileUri：'file://com.example.temptest/data/storage/el2/base/ haps/entry/files/test.jpg'。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900002 | The file corresponding to the URI is not in the app sandbox. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |
| 14000016 | Operation type not support. Possible causes:<br>1. A previous asset creation or modification request has not been applied yet. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('addResourceByFileUriDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context, photoType, extension);
    // 需要确保fileUri对应的资源存在。
    let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
    assetChangeRequest.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, fileUri);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('addResourceByFileUri successfully');
  } catch (err) {
    console.error(`addResourceByFileUriDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

<a id="addresource-1"></a>

## addResource

```TypeScript
addResource(type: ResourceType, data: ArrayBuffer): void
```

通过ArrayBuffer数据添加资源。

> **注意：**
> 
> 对于同一个资产变更请求，成功添加资源后不支持重复调用该接口。对于动态照片，可调用两次该接口分别添加图片和视频资源。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e.md) | 是 | 待添加资源的类型。 |
| data | ArrayBuffer | 是 | 待添加资源的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |
| 14000016 | Operation type not support. Possible causes:<br>1. A previous asset creation or modification request has not been applied yet. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('addResourceByArrayBufferDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context, photoType, extension);
    let buffer: ArrayBuffer = new ArrayBuffer(2048);
    assetChangeRequest.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, buffer);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('addResourceByArrayBuffer successfully');
  } catch (err) {
    console.error(`addResourceByArrayBufferDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## constructor

```TypeScript
constructor(asset: PhotoAsset)
```

构造函数，用于初始化资产变更请求。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 是 | 需要变更的资产。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The constructor was not called with the new keyword; <br>2. Parameter parsing failed, please check the number and types of parameters; <br>3. The asset parameter is not a valid PhotoAsset object; <br>4. System memory insufficient, please retry; <br>5. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('MediaAssetChangeRequest constructorDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(photoAsset);
}
```

<a id="createassetrequest-2"></a>

## createAssetRequest

```TypeScript
static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest
```

指定文件类型和扩展名，创建资产变更请求。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| photoType | [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | 是 | 待创建的文件类型，IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件扩展名，例如：'jpg'。 |
| options | [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | 否 | 创建选项，例如：{title: 'testPhoto'}。<br>文件名中不允许出现非法英文字符，包括：. .. \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | **MediaAssetChangeRequest** created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2. User file service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is valid and retry; <br>3. System memory insufficient, please retry; <br>4. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('createAssetRequestDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let options: photoAccessHelper.CreateOptions = {
      title: 'testPhoto'
    }
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context, photoType, extension, options);
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

## createImageAssetRequest

```TypeScript
static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest
```

创建图片资产变更请求。

指定待创建资产的数据来源，可参考[@ohos.file.fileuri (File URI)](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileuri.md).

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**测试接口：** 此接口仅在自动化测试脚本中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| fileUri | string | 是 | fileUri - 图片资产的数据来源，在应用沙箱下的uri。示例fileUri：'file://com.example.temptest/data/storage/ el2/base/haps/entry/files/test.jpg'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | 返回创建资产的变更请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900002 | The file corresponding to the URI is not in the app sandbox. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2. IPC communication error, please retry; <br>3. System memory insufficient, please retry; <br>4. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('createImageAssetRequestDemo');
  try {
    // 需要确保fileUri对应的资源存在。
    let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createImageAssetRequest(context, fileUri);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply createImageAssetRequest successfully');
  } catch (err) {
    console.error(`createImageAssetRequestDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## createVideoAssetRequest

```TypeScript
static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest
```

创建视频资产变更请求。

指定待创建资产的数据来源，可参考[@ohos.file.fileuri (File URI)](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileuri.md).

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**测试接口：** 此接口仅在自动化测试脚本中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| fileUri | string | 是 | 视频资产的数据来源，在应用沙箱下的uri。示例fileUri：'file://com.example.temptest/data/storage/ el2/base/haps/entry/files/test.mp4'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | 返回创建资产的变更请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900002 | The file corresponding to the URI is not in the app sandbox. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2. IPC communication error, please retry; <br>3. System memory insufficient, please retry; <br>4. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('createVideoAssetRequestDemo');
  try {
    // 需要确保fileUri对应的资源存在。
    let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.mp4';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createVideoAssetRequest(context, fileUri);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply createVideoAssetRequest successfully');
  } catch (err) {
    console.error(`createVideoAssetRequestDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## deleteAssets

```TypeScript
static deleteAssets(context: Context, assets: Array<PhotoAsset>): Promise<void>
```

通过PhotoAsset对象删除媒体文件（删除的文件会进入到回收站）。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 待删除的媒体文件数组，数组中元素个数不超过300个。<!--Del-->系统应用对此无限制。<!--DelEnd--> |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2. User file service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is valid and retry; <br>3. The assets array contains elements that are not valid PhotoAsset objects; <br>4. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5. System memory insufficient, please retry. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('deleteAssetsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAssetList: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
    await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, photoAssetList);
    console.info('deleteAssets successfully');
  } catch (err) {
    console.error(`deleteAssetsDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

<a id="deleteassets-1"></a>

## deleteAssets

```TypeScript
static deleteAssets(context: Context, uriList: Array<string>): Promise<void>
```

通过uri删除媒体文件（删除的文件会进入到回收站）。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| uriList | Array&lt;string&gt; | 是 | 待删除的媒体文件uri数组，数组中元素个数不超过300个。<!--Del-->系统应用对此无限制。<!--DelEnd--> |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000002 | The URI format is incorrect or the URI does not exist. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2. User file service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is valid and retry; <br>3. The uriList array contains elements that are not valid string URIs, each element must be a valid file URI string; <br>4. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5. System memory insufficient, please retry. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('deleteAssetsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [asset.uri]);
    console.info('deleteAssets successfully');
  } catch (err) {
    console.error(`deleteAssetsDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## discardCameraPhoto

```TypeScript
discardCameraPhoto(): void
```

删除相机拍摄的照片。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System internal error, IPC communication error, please retry. |
| 14000016 | Operation type not support. Possible causes:<br>1. The operation type is not supported, the asset is a moving photo which does not support this operation; <br>2. A previous asset creation or modification request has not been applied yet, please call applyChanges first; <br>3. The asset is not a moving photo, this operation is only supported for moving photos. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, asset: photoAccessHelper.PhotoAsset) {
  console.info('discardCameraPhotoDemo');
  try {
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.discardCameraPhoto();
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply discardCameraPhoto successfully');
  } catch (err) {
    console.error(`apply discardCameraPhoto failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getAsset

```TypeScript
getAsset(): PhotoAsset
```

获取当前资产变更请求中的资产。

> **注意：**
> 
> 对于创建资产的变更请求，在调用接口
> 
> [applyChanges](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#applychanges)
> 
> 的提交生效之前，该接口会返回null。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 返回当前资产变更请求中的资产。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System memory insufficient, please retry; <br>3. PC timeout, please retry. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('getAssetDemo');
  try {
    // 需要确保fileUri对应的资源存在。
    let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createImageAssetRequest(context, fileUri);
    await phAccessHelper.applyChanges(assetChangeRequest);
    let asset: photoAccessHelper.PhotoAsset = assetChangeRequest.getAsset();
    console.info('create asset successfully with uri = ' + asset.uri);
  } catch (err) {
    console.error(`getAssetDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getWriteCacheHandler

```TypeScript
getWriteCacheHandler(): Promise<number>
```

获取临时文件写句柄。使用Promise异步回调。

> **注意：**
> 
> 对于同一个资产变更请求，不支持在成功获取临时文件写句柄后，重复调用该接口。

**起始版本：** 11

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回临时文件写句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |
| 14000016 | Operation type not support. Possible causes:<br>1. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs <br>2. A previous asset creation or modification request has not been applied yet. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('getWriteCacheHandlerDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.VIDEO;
    let extension: string = 'mp4';
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context, photoType, extension);
    // 获取临时文件写句柄，用于写入数据。
    let fd: number = await assetChangeRequest.getWriteCacheHandler();
    console.info('getWriteCacheHandler successfully');
    // write data into fd..
    await fileIo.close(fd);
    await phAccessHelper.applyChanges(assetChangeRequest);
  } catch (err) {
    console.error(`getWriteCacheHandlerDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## saveCameraPhoto

```TypeScript
saveCameraPhoto(): void
```

保存相机拍摄的照片。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |
| 14000016 | Operation type not support. Possible causes:<br>1. A previous asset creation or modification request has not been applied yet. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, asset: photoAccessHelper.PhotoAsset) {
  console.info('saveCameraPhotoDemo');
  try {
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.saveCameraPhoto();
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply saveCameraPhoto successfully');
  } catch (err) {
    console.error(`apply saveCameraPhoto failed with error: ${err.code}, ${err.message}`);
  }
}
```

<a id="savecameraphoto-1"></a>

## saveCameraPhoto

```TypeScript
saveCameraPhoto(imageFileType: ImageFileType): void
```

保存相机拍摄的照片。需要指定保存的类型。

**起始版本：** 13

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageFileType | [ImageFileType](arkts-medialibrary-photoaccesshelper-imagefiletype-e.md) | 是 | 需要保存的类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |
| 14000016 | Operation type not support. Possible causes:<br>1. The operation type is not supported, the asset is a moving photo which does not support this operation; <br>2. A previous asset creation or modification request has not been applied yet, please call applyChanges first; <br>3. The asset is not a moving photo, this operation is only supported for moving photos. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context, asset: photoAccessHelper.PhotoAsset) {
  console.info('saveCameraPhotoDemo');
  try {
    let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.saveCameraPhoto(photoAccessHelper.ImageFileType.JPEG);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply saveCameraPhoto successfully');
  } catch (err) {
    console.error(`apply saveCameraPhoto failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean): void
```

将文件设置为收藏文件。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| favoriteState | boolean | 是 | 是否设置为收藏文件， true：设置为收藏文件；false：取消收藏。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | System inner fail. Possible causes:<br>1. This operation is not supported for assets in shared albums. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setFavoriteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
  // 将文件设置为收藏文件（入参为true表示收藏，false表示取消收藏）。
  assetChangeRequest.setFavorite(true);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setFavorite successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setFavorite failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setOrientation

```TypeScript
setOrientation(orientation: number): void
```

设置图片的显示旋转角度。本接口通过修改exif元数据实现对图片旋转角度的调整。

**起始版本：** 15

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | number | 是 | 待修改的图片旋转角度，且只能为0、90、180、270。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setOrientationDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
  // 修改图片的旋转角度为90°（参数只能为0°、90°、180°、270°）。
  assetChangeRequest.setOrientation(90);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setOrientation successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setOrientation failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setTitle

```TypeScript
setTitle(title: string): void
```

修改媒体资产的标题。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| title | string | 是 | 待修改的资产标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The asset parameter is not a valid PhotoAsset object; <br>2. System memory insufficient, please retry; <br>3. IPC timeout, please retry. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setTitleDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
  let newTitle: string = 'newTitle';
  assetChangeRequest.setTitle(newTitle);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setTitle successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setTitle failed with error: ${err.code}, ${err.message}`);
  });
}
```

## comment

```TypeScript
readonly comment: string
```

用于MediaChangeRequest类型校验。

如果类（如[MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md)或[MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md)）对象可以访问，就说明该类是MediaChangeRequest的实现类。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
