# PhotoAccessHelper

提供访问照片和相册的功能。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## applyChanges

```TypeScript
applyChanges(mediaChangeRequest: MediaChangeRequest): Promise<void>
```

提交媒体变更请求，使用Promise方式返回结果。

**起始版本：** 11

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaChangeRequest | [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md) | 是 | 媒体变更请求，支持资产变更请求和相册变更请求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | System inner fail |

**示例**

该接口依赖于MediaChangeRequest对象，详细代码示例请参见MediaAssetChangeRequest和MediaAlbumChangeRequest中的接口示例。

## checkPhotoUrisReadPermission

```TypeScript
checkPhotoUrisReadPermission(uris: string[]): Promise<Map<string, MediaAssetPermissionState>>
```

查询URI对应资产的读权限，以及资产是否存在。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | string[] | 是 | 待查询的URI数组，单次最多查询500条。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;string, [MediaAssetPermissionState](arkts-medialibrary-photoaccesshelper-mediaassetpermissionstate-e.md)&gt;&gt; | Promise对象，返回URI与MediaAssetPermissionState的键值对集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario-specific parameters are incorrect. Possible causes are as follows:  1. The length of the input parameter queue is greater than 500.  2. The input parameter is null or undefined. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('checkPhotoUrisReadPermissionDemo');

  try {
    let uris: string[] = [
      'file://fileUriDemo1', // 实际场景请使用真实的URI。
      'file://fileUriDemo2'
    ];
    let permissionMap: Map<string, photoAccessHelper.MediaAssetPermissionState> =
      await phAccessHelper.checkPhotoUrisReadPermission(uris);
  } catch (err) {
    const error = err as BusinessError;
    console.error(`checkPhotoUrisReadPermission failed, error: ${error.code}, ${error.message}`);
  }
}
```

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback<string>): void
```

指定文件类型、后缀和创建选项，创建图片或视频资源。使用callback方式返回结果。在未申请相册管理模块权限'ohos.permission.WRITE_IMAGEVIDEO'时，可以使用安全控件或授权弹窗的方式创建媒体资源，详情请参考 [保存媒体库资源](../../../media/medialibrary/photoAccessHelper-savebutton.md)。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoType | PhotoType | 是 | 创建的文件类型，IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件名后缀参数，例如：'jpg'。 |
| options | [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | 是 | 创建选项，当前仅支持'title'，例如{title: 'testPhoto'}。    **注意：** 传入'subtype'选项，配置不生效，仅支持保存DEFAULT类型图片。 文件名中不允许出现非法英文字符，包括： . .. \ / : * ? " ' ` &lt;&gt; \| { } [ ] |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | callback返回创建的图片和视频的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 11+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
  let extension:string = 'jpg';
  let options: photoAccessHelper.CreateOptions = {
    title: 'testPhoto'
  }
  phAccessHelper.createAsset(photoType, extension, options, (err, uri) => {
    if (uri !== undefined) {
      console.info('createAsset uri' + uri);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback<string>): void
```

指定文件类型和后缀，创建图片或视频资源，使用callback方式返回结果。在未申请相册管理模块权限'ohos.permission.WRITE_IMAGEVIDEO'时，可以使用安全控件或授权弹窗的方式创建媒体资源，详情请参考 [保存媒体库资源](../../../media/medialibrary/photoAccessHelper-savebutton.md)。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoType | PhotoType | 是 | 创建的文件类型，IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件名后缀参数，例如：'jpg'。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | callback返回创建的图片和视频的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 11+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
  let extension: string = 'jpg';
  phAccessHelper.createAsset(photoType, extension, (err, uri) => {
    if (uri !== undefined) {
      console.info('createAsset uri' + uri);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise<string>
```

指定文件类型、后缀和创建选项，创建图片或视频资源，以Promise方式返回结果。在未申请相册管理模块权限'ohos.permission.WRITE_IMAGEVIDEO'时，可以使用安全控件或授权弹窗的方式创建媒体资源，详情请参考 [保存媒体库资源](../../../media/medialibrary/photoAccessHelper-savebutton.md)。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoType | PhotoType | 是 | 创建的文件类型，IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件名后缀参数，例如：'jpg'。 |
| options | [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | 否 | 创建选项，当前仅支持'title'，例如{title: 'testPhoto'}。    **注意：** 传入'subtype'选项，配置不生效，仅支持保存DEFAULT类型图片。 文件名中不允许出现非法英文字符，包括： . .. \ / : * ? " ' ` &lt;&gt; \| { } [ ] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回创建的图片和视频的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 11+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let options: photoAccessHelper.CreateOptions = {
      title: 'testPhoto'
    }
    let uri: string = await phAccessHelper.createAsset(photoType, extension, options);
    console.info('createAsset uri' + uri);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createAssetWithShortTermPermission

```TypeScript
createAssetWithShortTermPermission(photoCreationConfig: PhotoCreationConfig): Promise<string>
```

接口提供给应用调用，支持首次调用后拉起保存确认弹框。在用户同意保存后返回已创建并授予保存权限的uri，支持应用使用uri写入图片/视频。在用户"同意"后的5分钟之内，同一个应用再次调用接口，支持无需弹框确认自动返回已授权的uri给应用，支持应用保存图片/视频。退出应用会结束授权，再次进入需要重新弹出弹框进行确认授权。

**起始版本：** 12

**需要权限：** ohos.permission.SHORT_TERM_WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoCreationConfig | [PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md) | 是 | 保存图片/视频到媒体库的配置，包括保存的文件名等。    **注意：** 传入'subtype'选项，配置项不生效，仅支持保存DEFAULT类型图片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回给应用的媒体库文件uri。uri已对应用授权，支持应用写入数据。如果生成uri异常，则返回批量创建错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
    console.info('createAssetWithShortTermPermissionDemo.');
    
    try {
        let photoCreationConfig: photoAccessHelper.PhotoCreationConfig = {
            title: '123456', 
            fileNameExtension: 'jpg',
            photoType: photoAccessHelper.PhotoType.IMAGE,
            subtype: photoAccessHelper.PhotoSubtype.DEFAULT, 
        };

        let resultUri: string = await phAccessHelper.createAssetWithShortTermPermission(photoCreationConfig);
        let resultFile: fileIo.File = fileIo.openSync(resultUri, fileIo.OpenMode.READ_WRITE);
        // 实际场景请使用真实的URI和文件大小。
        let srcFile:  fileIo.File = fileIo.openSync("file://test.jpg", fileIo.OpenMode.READ_ONLY);
        let bufSize: number = 2000000;
        let readSize: number = 0;
        let buf = new ArrayBuffer(bufSize);
        let readLen = fileIo.readSync(srcFile.fd, buf, {
            offset: readSize,
            length: bufSize
        });
        if (readLen > 0) {
            readSize += readLen;
            fileIo.writeSync(resultFile.fd, buf, { length: readLen });
        }
        fileIo.closeSync(srcFile);
        fileIo.closeSync(resultFile);
    } catch (err) {
        console.error('createAssetWithShortTermPermission failed, errCode is ' + err.code + ', errMsg is ' + err.message);
    }
    
}
```

## createAssetWithShortTermPermissionEx

```TypeScript
createAssetWithShortTermPermissionEx(creationSetting: CreationSetting): Promise<string>
```

应用调用该接口后，系统会首次拉起保存确认弹框。使用Promise异步回调。

> **说明：**
> 
> - 用户同意保存后，接口将返回已创建并授予保存权限的URI，应用可使用该URI写入图片/视频。
> 
> - 在用户同意后的5分钟内，若同一应用再次调用此接口，系统将无需弹框确认，直接返回已授权的URI，供应用保存图片/视频。退出应用会结束授权，再次进入需要重新弹出弹框进行确认授权。

**起始版本：** 23

**需要权限：** ohos.permission.SHORT_TERM_WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| creationSetting | [CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md) | 是 | 保存图片或视频到媒体库时的配置项，包括保存的文件名等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回给应用的媒体库文件URI。支持应用使用返回的URI写入数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

## createDeleteRequest

```TypeScript
createDeleteRequest(uriList: Array<string>, callback: AsyncCallback<void>): void
```

创建一个弹出框来删除照片，删除的文件进入到回收站，使用callback方式返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uriList | Array &lt;string&gt; | 是 | 待删除的媒体文件uri数组，最大删除数量300。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createDeleteRequestDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    phAccessHelper.createDeleteRequest([asset.uri], (err) => {
      if (err === undefined) {
        console.info('createDeleteRequest successfully');
      } else {
        console.error(`createDeleteRequest failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`fetch failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createDeleteRequest

```TypeScript
createDeleteRequest(uriList: Array<string>): Promise<void>
```

创建一个弹出框来删除照片，删除的文件进入到回收站，使用Promise方式返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uriList | Array &lt;string&gt; | 是 | 待删除的媒体文件uri数组，最大删除数量300。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createDeleteRequestDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    await phAccessHelper.createDeleteRequest([asset.uri]);
    console.info('createDeleteRequest successfully');
  } catch (err) {
    console.error(`createDeleteRequest failed with error: ${err.code}, ${err.message}`);
  }
}
```

## createPhotoAsset

```TypeScript
createPhotoAsset(photoType: PhotoType, extension: string, title?: string): Promise<string>
```

指定文件类型、后缀和标题，创建图片或视频资源。使用Promise异步回调。在未申请相册管理模块权限'ohos.permission.WRITE_IMAGEVIDEO'时，可以使用安全控件或授权弹窗的方式创建媒体资源，详情请参考 [开发指南](../../../media/medialibrary/photoAccessHelper-savebutton.md)。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoType | PhotoType | 是 | 创建的文件类型。例如：IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件名后缀参数。例如：'jpg'。 |
| title | string | 否 | 图片或视频资产的标题。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回创建的图片或视频的URL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:  1. The extension format is unsupported  2. Title contains unsupported character, such as . .. \ / : * ? " ' ` &lt;&gt; \| { } [ ]  3. The title is an empty string  4. The total length of title and extension is more than 255 |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createPhotoAssetDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let title: string = 'testPhoto';
    let uri: string = await phAccessHelper.createPhotoAsset(photoType, extension, title);
    console.info('createPhotoAsset uri' + uri);
    console.info('createPhotoAsset successfully');
  } catch (err) {
    console.error(`createPhotoAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getAlbumIdByLpath

```TypeScript
getAlbumIdByLpath(lpath: string): Promise<number>
```

根据相册的虚拟路径获取媒体库相册的ID。使用Promise异步回调。该接口仅支持以下相册：相机相册（'/DCIM/Camera'）、截图相册（'/Pictures/Screenshots'）和屏幕录制相册（'/Pictures/Screenrecords'）。​**模型约束**： 此接口仅可在Stage模型下使用。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lpath | string | 是 | 相册的虚拟路径，lpath长度不能超过255个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象，返回相册lpath对应的媒体库相册的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The lpath is invalid, such as null, undefined and empty. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAlbumIdByLpath');

  try {
      let albumId: number = await phAccessHelper.getAlbumIdByLpath('testLpath');
      console.info('requestFile:: albumId: ', albumId);

      console.info('getAlbumIdByLpath completed.');
      console.info(`albumId : ${albumId}`);
    } catch (err) {
      console.error(`getAlbumIdByLpath failed: ${err.code}, ${err.message}`);
    }
}
```

## getAlbums

```TypeScript
getAlbums(
      type: AlbumType,
      subtype: AlbumSubtype,
      options: FetchOptions,
      callback: AsyncCallback<FetchResult<Album>>
    ): void
```

根据检索选项和相册类型获取相册，使用callback方式返回结果。获取相册前，确保相册已存在。

**起始版本：** 10

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | AlbumType | 是 | 相册类型。 |
| subtype | AlbumSubtype | 是 | 相册子类型。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;FetchResult&lt;Album&gt;&gt; | 是 | callback返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 - 11 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // 示例代码中为获取相册名为newAlbumName的相册。
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions, async (err, fetchResult) => {
    if (err) {
      console.error(`getAlbumsCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    if (fetchResult === undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumName: ' + album.albumName);
    fetchResult.close();
  });
}
```

## getAlbums

```TypeScript
getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback<FetchResult<Album>>): void
```

根据相册类型获取相册，使用callback方式返回结果。获取相册前需先保证相册存在。

**起始版本：** 10

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | AlbumType | 是 | 相册类型。 |
| subtype | AlbumSubtype | 是 | 相册子类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;FetchResult&lt;Album&gt;&gt; | 是 | callback返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 - 11 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // 示例代码中为获取系统相册VIDEO，默认已预置。
  console.info('getAlbumsDemo');
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.VIDEO, async (err, fetchResult) => {
    if (err) {
      console.error(`getAlbumsCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    if (fetchResult === undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumUri: ' + album.albumUri);
    fetchResult.close();
  });
}
```

## getAlbums

```TypeScript
getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise<FetchResult<Album>>
```

根据检索选项和相册类型获取相册，使用Promise方式返回结果。在获取相册之前，确保相册已存在。

**起始版本：** 10

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | AlbumType | 是 | 相册类型。 |
| subtype | AlbumSubtype | 是 | 相册子类型。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 否 | 检索选项，不填时默认根据相册类型检索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;FetchResult &lt;Album&gt;&gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 - 11 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // 示例代码中为获取相册名为newAlbumName的相册。
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getAlbumsPromise fetchResult is undefined');
      return;
    }
    let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsPromise successfully, albumName: ' + album.albumName);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getAlbumsPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getAssets

```TypeScript
getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void
```

获取相册中的文件。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;FetchResult&lt;PhotoAsset&gt;&gt; | 是 | 回调函数。当获取相册中的文件成功，err为undefined，data为获取到的图片和视频数据结果集 [FetchResult](arkts-file-photoaccesshelper.md)；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 - 11 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumGetAssetsDemoCallback');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  album.getAssets(fetchOption, (err, albumFetchResult) => {
    if (albumFetchResult !== undefined) {
      console.info('album getAssets successfully, getCount: ' + albumFetchResult.getCount());
    } else {
      console.error(`album getAssets failed with error: ${err.code}, ${err.message}`);
    }
  });
}
```

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };

  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName : ' + photoAsset.displayName);
      }
    } else {
      console.error(`fetchResult fail with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## getAssets

```TypeScript
getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>
```

获取图片和视频资源，使用Promise方式返回结果。

**起始版本：** 10

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 图片和视频检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;FetchResult &lt;PhotoAsset&gt;&gt; | Promise对象，返回图片和视频数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 20+ |
| 13900012 | Permission denied<br>**适用版本：** 10 - 19 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumGetAssetsDemoPromise');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  album.getAssets(fetchOption).then((albumFetchResult) => {
    console.info('album getAssets successfully, getCount: ' + albumFetchResult.getCount());
  }).catch((err: BusinessError) => {
    console.error(`album getAssets failed with error: ${err.code}, ${err.message}`);
  });
}
```

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName :' + photoAsset.displayName);
      }
    }
  } catch (err) {
    console.error(`getAssets failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getBurstAssets

```TypeScript
getBurstAssets(burstKey: string, options: FetchOptions): Promise<FetchResult<PhotoAsset>>
```

获取连拍照片资源，使用Promise方式返回结果。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| burstKey | string | 是 | 一组连拍照片的唯一标识：uuid（可传入[PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)的BURST_KEY）。字符串长度为 36字节。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 连拍照片检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;FetchResult &lt;PhotoAsset&gt;&gt; | Promise对象，返回连拍照片数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getBurstAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  // burstKey为36位的uuid，可以根据photoAccessHelper.PhotoKeys获取。
  let burstKey: string = "e719d696-09fa-44f8-8e9e-ec3f215aa62a";
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await 
      phAccessHelper.getBurstAssets(burstKey, fetchOptions);
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName :' + photoAsset.displayName);
      }
    }
  } catch (err) {
    console.error(`getBurstAssets failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getPhotoPickerComponentDefaultAlbumName

```TypeScript
getPhotoPickerComponentDefaultAlbumName(): Promise<string>
```

应用使用PhotoPickerComponent组件选择照片时，支持调用API获取组件默认显示相册的相册名字符串。跟随当前系统语言，支持返回当前语言的相册名。使用Promise异步回调。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回默认相册的相册名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. The IPC request timed out.  2. system running error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import {photoAccessHelper} from '@kit.MediaLibraryKit';

async function example(context: Context) {
  console.info('getPhotoPickerComponentDefaultAlbumNameDemo');
  let phAccessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  phAccessHelper.getPhotoPickerComponentDefaultAlbumName().then((defaultAlbumName) => {
    console.info('getPhotoPickerComponentDefaultAlbumName success, defaultAlbumName is ' + defaultAlbumName);
  }).catch((err: BusinessError) => {
    console.error(`getPhotoPickerComponentDefaultAlbumName failed with error: ${err.code}, ${err.message}`);
  });
}
```

## getRecentPhotoInfo

```TypeScript
getRecentPhotoInfo(options?: RecentPhotoOptions): Promise<RecentPhotoInfo>
```

应用使用RecentPhotoComponent组件查看最近图片时，支持调用API获取最近图片信息。使用Promise异步回调。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RecentPhotoOptions](arkts-medialibrary-photoaccesshelper-recentphotooptions-c.md) | 否 | 最近图片配置选项参数。若无此参数，则取按照创建时间排序的最新一张图片。 该参数在配置的情况下，需与RecentPhotoComponent组件中的options配置相同才可以查到一样的图片，否则可能存在接口能查到最近图片，组件没查到最近图片的情况。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RecentPhotoInfo](arkts-medialibrary-photoaccesshelper-recentphotoinfo-c.md)&gt; | Promise对象，返回最近图片信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper, PhotoSource, RecentPhotoOptions} from '@kit.MediaLibraryKit';

async function example(context: Context) {
  console.info('getRecentPhotoInfoDemo');
  let phAccessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  let recentPhotoOptions: RecentPhotoOptions = {
    period: 60 * 60,
    MIMEType: photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE,
    photoSource: PhotoSource.ALL
  }

  phAccessHelper.getRecentPhotoInfo(recentPhotoOptions).then((recentPhotoInfo) => {
    console.info('getRecentPhotoInfo success, recentPhotoInfo is ' + JSON.stringify(recentPhotoInfo));
  }).catch((err: BusinessError) => {
    console.error(`getRecentPhotoInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

## getSupportedPhotoFormats

```TypeScript
getSupportedPhotoFormats(photoType: PhotoType): Promise<Array<string>>
```

接口提供给应用调用，获取媒体库支持的图片或者视频后缀列表。

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoType | PhotoType | 是 | 媒体文件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;string&gt;&gt; | Promise对象，返回支持的图片或者视频后缀列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error. It is recommended to retry and check the logs. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, photoTypeNumber: number){
  console.info('getSupportedPhotoFormatsDemo.');

  try {
    let outputText: string;
    if (photoTypeNumber !== photoAccessHelper.PhotoType.IMAGE && photoTypeNumber !== photoAccessHelper.PhotoType.VIDEO) {
      outputText = 'Does not support querying formats other than images or videos';
      return;
    }
    outputText = 'The supported types are:\n';
    let imageFormat  = await phAccessHelper.getSupportedPhotoFormats(photoAccessHelper.PhotoType.IMAGE);
    let result = "";
    for (let i = 0; i < imageFormat.length; i++) {
      result += imageFormat[i];
      if (i !== imageFormat.length - 1) {
        result += ', ';
      }
    }
    outputText += result;
    console.info('getSupportedPhotoFormats success, data is ' + outputText);
  } catch (error) {
    console.error('getSupportedPhotoFormats failed, errCode is', error);
  }
}
```

## off('photoChange')

```TypeScript
off(type: 'photoChange', callback?: Callback<PhotoAssetChangeInfos>): void
```

取消对'photoChange'媒体资产的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoChange' | 是 | 取消监听媒体资产，取值为'photoChange'。取消监听后，有资产发生变化时，不再通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | 取消 on('photoChange') 注册时指定的callback监听；不填时，则取消对'photoChange'的所有监听。    **注意：** 取消注册的callback后，有资产发生变化时，不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## off('photoAlbumChange')

```TypeScript
off(type: 'photoAlbumChange', callback?: Callback<AlbumChangeInfos>): void
```

取消对'photoAlbumChange'相册的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAlbumChange' | 是 | 取消监听相册，取值为'photoAlbumChange'。取消监听后，有相册发生变化时，不再通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | 取消 on('photoAlbumChange') 注册时指定的callback监听；不填时，则取消对'photoAlbumChange'的所有监听。    **注意：** 取消注册的callback后，有相册发生变化时，不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## offMediaLibraryAvailability

```TypeScript
offMediaLibraryAvailability(callback? : Callback<MediaLibraryAvailability>):void
```

取消注册媒体库可用性状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MediaLibraryAvailability](arkts-medialibrary-photoaccesshelper-medialibraryavailability-i.md)&gt; | 否 | 回调函数，返回取消 [onMediaLibraryAvailability](#onmedialibraryavailability) 注册时指定的callback监听。不填时，则取消对媒体库可用性变化的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
class MediaLibraryExample {
  private helper: photoAccessHelper.PhotoAccessHelper;
  private handleMediaLibraryChange?: (changeData: photoAccessHelper.MediaLibraryAvailability) => void;

  constructor(context: common.Context) {
    this.helper = photoAccessHelper.getPhotoAccessHelper(context);
  }

  offMediaLibraryAvailability = async () => {
    try {
      this.helper.onMediaLibraryAvailability(this.handleMediaLibraryChange);
      this.helper.offMediaLibraryAvailability(this.handleMediaLibraryChange);
      console.info('媒体库监听解除成功');
    } catch (err) {
      console.error(`offMediaLibraryAvailability failed::${(err as BusinessError).code}, ${(err as BusinessError).message} !`);
    }
  };
}
```

## offSinglePhotoAlbumChange

```TypeScript
offSinglePhotoAlbumChange(album?: Album, callback?: Callback<AlbumChangeInfos>): void
```

取消对单个相册的监听。具体规则如下：
1. 不携带任何参数时，取消所有单个相册监听。
2. 携带album，不携带callback时，取消该album下所有callback监听。
3. 携带album和callback时，仅取消指定callback监听。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| album | Album | 否 | 取消监听相册。取消监听后,有相册发生变化时,不再通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | 用于取消订阅的回调。不携带时，取消album参数下所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}
let onCallback3 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback3 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // 注册onCallback1监听。
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback2);
    // 注册onCallback3监听。
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback3);

    // 解注册onCallback1监听。
    phAccessHelper.offSinglePhotoAlbumChange(album, onCallback1);
    // 解注册album下所有callback。
    phAccessHelper.offSinglePhotoAlbumChange(album);
    // 解注册所有singlePhotoAlbumChange类型监听。
    phAccessHelper.offSinglePhotoAlbumChange();
  } catch (error) {
    console.error('offSinglePhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## offSinglePhotoChange

```TypeScript
offSinglePhotoChange(asset?: PhotoAsset, callback?: Callback<PhotoAssetChangeInfos>): void
```

取消单个资产的监听。具体规则如下：
1. 不携带参数时，取消所有单个资产监听。
2. 携带asset，不携带callback时，取消该asset下所有callback监听。
3. 携带asset和callback时，仅取消指定callback监听。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| asset | PhotoAsset | 否 | 取消监听资产。取消asset资产监听后,当asset发生变化时,不再通过callback返回变更信息。不携带时，取消注册过的所有单个资产监听。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | 用于取消订阅的回调。不携带时，取消asset参数下所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}
let onCallback3 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback3 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // 注册onCallback1监听。
    phAccessHelper.onSinglePhotoChange(asset, onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.onSinglePhotoChange(asset, onCallback2);
    // 注册onCallback3监听。
    phAccessHelper.onSinglePhotoChange(asset, onCallback3);

    // 解注册onCallback1监听。
    phAccessHelper.offSinglePhotoChange(asset, onCallback1);
    // 解注册asset下所有callback。
    phAccessHelper.offSinglePhotoChange(asset);
    // 解注册所有singlePhotoAssetChange类型监听。
    phAccessHelper.offSinglePhotoChange();
  } catch (error) {
    console.error('offSinglePhotoChangeDemo failed, errCode is', error);
  }
}
```

## on('photoChange')

```TypeScript
on(type: 'photoChange', callback: Callback<PhotoAssetChangeInfos>): void
```

注册'photoChange'监听媒体资产，并通过callback方式返回资产变化结果，可以注册多个callback。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoChange' | 是 | 注册监听媒体资产，取值为'photoChange'。注册完成后，有资产发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | 返回变更的媒体资产信息 [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)。    **注意：** 该接口可以注册多个不同的callback监听， off('photoChange') 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## on('photoAlbumChange')

```TypeScript
on(type: 'photoAlbumChange', callback: Callback<AlbumChangeInfos>): void
```

注册'photoAlbumChange'监听相册，并通过callback方式返回相册变化结果，可以注册多个callback。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAlbumChange' | 是 | 注册监听相册，取值为'photoAlbumChange'。注册完成后，有相册发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | 返回变更的相册信息 [AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)。    **注意：** 该接口可以注册多个不同的callback监听， off('photoAlbumChange') 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## onMediaLibraryAvailability

```TypeScript
onMediaLibraryAvailability(callback: Callback<MediaLibraryAvailability>): void
```

注册媒体库可用性状态，返回媒体库当前可用状态和不可用原因。使用callback异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MediaLibraryAvailability](arkts-medialibrary-photoaccesshelper-medialibraryavailability-i.md)&gt; | 是 | 回调函数，返回媒体库可用性信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario-specific parameters are incorrect. Possible causes are as follows:  1. The input parameter is null or undefined. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
class MediaLibraryExample {
  private helper: photoAccessHelper.PhotoAccessHelper;
  private handleMediaLibraryChange?: (changeData: photoAccessHelper.MediaLibraryAvailability) => void;

  constructor(context: common.Context) {
    this.helper = photoAccessHelper.getPhotoAccessHelper(context);
  }

  onMediaLibraryAvailability = async () => {
    try {
      this.handleMediaLibraryChange = (
        changeData: photoAccessHelper.MediaLibraryAvailability
      ) => {
        const availabilityStatus = changeData.availabilityStatus;
        const unavailabilityReason = changeData.unavailabilityReason;
        console.info(`媒体库状态变化：状态=${availabilityStatus}，原因=${unavailabilityReason}`);
      };
      this.helper.onMediaLibraryAvailability(this.handleMediaLibraryChange);
      console.info('媒体库监听注册成功');
    } catch (err) {
      console.error(`onMediaLibraryAvailability failed::${(err as BusinessError).code}, ${(err as BusinessError).message} !`);
    }
  };
}
```

## onSinglePhotoAlbumChange

```TypeScript
onSinglePhotoAlbumChange(album: Album, callback: Callback<AlbumChangeInfos>): void
```

注册对普通单个相册变化的监听。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| album | Album | 是 | 注册单个监听的媒体相册。注册完成后，当该相册发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | 返回变更的媒体相册信息 [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)。    **注意：** 该接口可以注册多个不同的callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoAlbumChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // 注册onCallback1监听。
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback2);
  } catch (error) {
    console.error('onSinglePhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## onSinglePhotoChange

```TypeScript
onSinglePhotoChange(asset: PhotoAsset, callback: Callback<PhotoAssetChangeInfos>): void
```

注册对普通单个资产变化的监听。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| asset | PhotoAsset | 是 | 注册单个监听的媒体资产。注册完成后，有资产发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | 返回变更的媒体资产信息 PhotoAssetChangeInfos。    **注意：** 该接口可以注册多个不同的callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes:  1. The database is corrupted.  2. The file system is abnormal.  3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // 触发回调时，具体的操作。
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // 注册onCallback1监听。
    phAccessHelper.onSinglePhotoChange(asset, onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.onSinglePhotoChange(asset, onCallback2);
  } catch (error) {
    console.error('onSinglePhotoChangeDemo failed, errCode is', error);
  }
}
```

## registerChange

```TypeScript
registerChange(uri: string, forChildUris: boolean, callback: Callback<ChangeData>): void
```

注册指定uri的监听，并通过callback方式返回异步结果。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | PhotoAsset的uri, Album的uri或[DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e.md)的值。 |
| forChildUris | boolean | 是 | 是否模糊监听。uri为相册uri时：forChildUris为true，能监听到相册中文件的变化。如果是false，只能监听相册本身变化；uri为 photoAsset时：forChildUris为true、false没有区别；uri为DefaultChangeUri时：forChildUris必须为true，如果为false将找不到该uri，收不到任何消息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ChangeData&gt; | 是 | 返回要监听的[ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i.md)。注：uri可以注册多个不同的 callback监听，[unRegisterChange](#unregisterchange)可以关闭该uri所有监听，也可以关闭指定 callback的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('registerChangeDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset !== undefined) {
    console.info('photoAsset.displayName : ' + photoAsset.displayName);
  }
  let onCallback1 = (changeData: photoAccessHelper.ChangeData) => {
      console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
    // file had changed, do something.
  }
  let onCallback2 = (changeData: photoAccessHelper.ChangeData) => {
      console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
    // file had changed, do something.
  }
  // 注册onCallback1监听。
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback1);
  // 注册onCallback2监听。
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback2);

  await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [photoAsset]);
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放PhotoAccessHelper实例。使用callback异步回调。当后续不需要使用PhotoAccessHelper实例中的方法时调用。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调表示成功还是失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('releaseDemo');
  phAccessHelper.release((err) => {
    if (err !== undefined) {
      console.error(`release failed. error: ${err.code}, ${err.message}`);
    } else {
      console.info('release ok.');
    }
  });
}
```

## release

```TypeScript
release(): Promise<void>
```

释放PhotoAccessHelper实例。使用Promise异步回调。当后续不需要使用PhotoAccessHelper实例中的方法时调用。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('releaseDemo');
  try {
    await phAccessHelper.release();
    console.info('release ok.');
  } catch (err) {
    console.error(`release failed. error: ${err.code}, ${err.message}`);
  }
}
```

## requestPhotoUrisReadPermission

```TypeScript
requestPhotoUrisReadPermission(srcFileUris: Array<string>): Promise<Array<string>>
```

<!--RP1--><!--RP1End-->调用接口给未授权的URI进行授权，返回已创建并授予保存权限的URI列表。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcFileUris | Array &lt;string&gt; | 是 | 需进行授权的图片/视频文件对应的 [媒体文件URI](../../../file-management/user-file-uri-intro.md#媒体文件uri)。    **注意：** 仅支持处理图片、视频URI，且最大数量限制为100个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;string&gt;&gt; | Promise对象，返回已授权的URI列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestPhotoUrisReadPermissionDemo.');

  try {
    // 获取需要进行授权的图片/视频URI。
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // 实际场景请使用真实的URI。
    ];
    let desFileUris: Array<string> = await phAccessHelper.requestPhotoUrisReadPermission(srcFileUris);
    console.info('requestPhotoUrisReadPermission success, data is ' + desFileUris);
  } catch (err) {
    console.error('requestPhotoUrisReadPermission failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## requestPhotoUrisReadPermissionEx

```TypeScript
requestPhotoUrisReadPermissionEx(srcFileUris: Array<string>): Promise<RequestReadPermissionResult>
```

应用调用接口为未授权的URI授权。使用promise异步回调。返回授权结果，其中包含已创建并授予保存权限的URI列表以及无效的URI列表。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcFileUris | Array &lt;string&gt; | 是 | 需进行授权的图片/视频文件对应的 [媒体库uri](../../../file-management/user-file-uri-intro.md#媒体文件uri)。    **注意：** 仅支持处理图片、视频uri，且最大数量限制为100个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RequestReadPermissionResult](arkts-medialibrary-photoaccesshelper-requestreadpermissionresult-c.md)&gt; | Promise对象，返回已授权的uri列表和无效的uri列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
console.info('requestPhotoUrisReadPermissionExDemo.');

  try {
    // 获取需要进行授权的图片/视频URI。
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // 实际场景请使用真实的URI。
    ];
    let requestReadPermissionResult: photoAccessHelper.RequestReadPermissionResult = await phAccessHelper.requestPhotoUrisReadPermissionEx(srcFileUris);
    console.info('requestPhotoUrisReadPermissionEx success, data is ' + requestReadPermissionResult);
  } catch (err) {
    console.error('requestPhotoUrisReadPermissionEx failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## setAssetCompatibleCapability

```TypeScript
setAssetCompatibleCapability(capability: AssetCompatibleCapability): Promise<void>
```

配置资产兼容能力。系统会对特殊的资产（如高分辨率资产）进行兼容性处理，如果开发者希望获得原始资产需要向系统注册兼容能力。​

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md) | 是 | 资产兼容能力。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The capability is invalid. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let capability : photoAccessHelper.AssetCompatibleCapability = {
        supportedHighResolution : true,
    };
    await phAccessHelper.setAssetCompatibleCapability(capability);
  } catch (error) {
    console.error('failed to setAssetCompatibleCapability err', error);
  }
}
```

## showAssetsCreationDialog

```TypeScript
showAssetsCreationDialog(srcFileUris: Array<string>, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>
```

调用接口显示保存确认弹窗。如果用户同意保存，将返回一个已创建并授予保存权限的URI列表（此列表永久生效），应用可使用这些URI写入图片或视频。如果用户拒绝保存，将返回一个空列表。弹框需显示应用名称，但无法直接获取。因此，调用此接口时，请确保[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的 `abilities`标签已配置`label`和`icon`项。需要注意的是，图标不受`abilities`标签中的`icon`项影响，不支持修改。

> **说明：**
> 
> 当传入URI为沙箱路径时，可正常保存图片/视频，但无界面预览。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcFileUris | Array &lt;string&gt; | 是 | 需保存到媒体库中的图片/视频文件对应的 [媒体文件URI](../../../file-management/user-file-uri-intro.md#媒体文件uri)。    **注意：**    - 一次弹窗最多保存100张图片。    - 仅支持处理图片、视频URI。    - 不支持手动拼接的URI，需调用接口获取，获取方式参考[媒体文件URI获取方式](../../../file-management/user-file-uri-intro.md#媒体文件uri获取方式)。 |
| photoCreationConfigs | Array&lt;[PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md)&gt; | 是 | 保存图片或视频到媒体库的配置，包括文件名等，与srcFileUris保持一一对应。    **注意：** 传入'subtype'选项，配置项不生效，仅支持保存DEFAULT类型图片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;string&gt;&gt; | Promise对象，返回给应用的媒体库文件URI列表。URI已对应用授权，支持应用写入数据。如果生成URI异常，则返回批量创建错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('ShowAssetsCreationDialogDemo.');

  try {
    // 获取需要保存到媒体库的位于应用沙箱的图片/视频URI。
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // 实际场景请使用真实的URI。
    ];
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: 'test2', // 可选。
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT, // 可选。
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    console.info('showAssetsCreationDialog success, data is ' + desFileUris);
  } catch (err) {
    console.error('showAssetsCreationDialog failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## showAssetsCreationDialogEx

```TypeScript
showAssetsCreationDialogEx(srcFileUris: Array<string>, creationSettings: Array<CreationSetting>): Promise<Array<string>>
```

调用接口显示保存确认弹窗。使用Promise异步回调。

> **说明：**
> 
> - 用户同意后，返回已创建并授予保存权限的URI列表，该列表永久有效，支持写入图片/视频。用户拒绝时，返回空列表。
> 
> - 弹框需显示应用名称，名称和图标需在[module.json5配置文件](../../../quick-start/module-configuration-file.md)的`abilities`标签中配置
> `label`和`icon`项。
> 
> - 当传入URI为沙箱路径时，可正常保存图片或视频，但不显示界面预览。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcFileUris | Array &lt;string&gt; | 是 | 需保存到媒体库中的图片或视频文件对应的 [媒体文件URI](../../../file-management/user-file-uri-intro.md#媒体文件uri)。    **注意：**    - 一次弹窗最多保存100张图片。    - 仅支持处理图片和视频URI。    - 不支持手动拼接URI，需调用接口获取，具体请参考[媒体文件URI获取方式](../../../file-management/user-file-uri-intro.md#媒体文件uri获取方式)。 |
| creationSettings | Array&lt;[CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md)&gt; | 是 | 保存图片或视频到媒体库的配置，包括文件名等，与srcFileUris参数中的URI保持一一对应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;string&gt;&gt; | Promise对象，返回给应用的媒体库文件URI列表。支持应用使用返回的URI写入数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) { 
  console.info('ShowAssetsCreationDialogExDemo.'); 

  try {
    // 获取需要保存到媒体库的位于应用沙箱的图片/视频URI。
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // 实际场景请使用真实的URI。
    ];
    let photoCreationConfigs: Array<photoAccessHelper.CreationSetting> = [
      {
        title: 'test2', // 可选。
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialogEx(srcFileUris, photoCreationConfigs);
    console.info('showAssetsCreationDialogEx success, data is ' + desFileUris);
  } catch (err) {
    console.error('showAssetsCreationDialogEx failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## showSingleAssetCreationDialogEx

```TypeScript
showSingleAssetCreationDialogEx(srcFileUri: string, creationSetting: CreationSetting, isImageFullyDisplayed: boolean): Promise<string>
```

针对单个图片/视频调用接口显示保存确认弹窗。使用Promise异步回调。

> **说明：**
> 
> - 如果用户同意保存，将返回一个已创建并授予保存权限的URI（此URI永久生效），应用可使用这个URI写入图片或视频。如果用户拒绝保存，将返回一个空字符串。
> 
> - 弹框需显示应用名称，但无法直接获取。因此，调用此接口时，请确保[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的
> `abilities`标签已配置`label`和`icon`项。需要注意的是，图标不受`abilities`标签中的`icon`项影响，不支持修改。
> 
> - 当传入URI为沙箱路径时，可正常保存图片/视频，但无界面预览。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcFileUri | string | 是 | 需要保存到媒体库中的图片/视频文件所对应的 [媒体文件URI](../../../file-management/user-file-uri-intro.md#媒体文件uri)。    **注意：**    - 一次弹窗最多保存1张图片。    - 仅支持处理图片、视频URI。    - 不支持手动拼接的URI，需调用接口获取，具体请参考[媒体文件URI获取方式](../../../file-management/user-file-uri-intro.md#媒体文件uri获取方式)。 |
| creationSetting | [CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md) | 是 | 保存图片或视频到媒体库的配置（包括文件名等），与srcFileUri保持对应。 |
| isImageFullyDisplayed | boolean | 是 | 表示是否完整显示图片。true表示完整显示，false表示不完整显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回给应用的媒体库文件URI。URI已对应用授权，支持应用写入数据。如果生成URI异常，则返回批量创建错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('ShowSingleAssetCreationDialogExDemo.');

  try {
    // 获取需要保存到媒体库的位于应用沙箱的图片/视频URI。
    let srcFileUri: string = 'file://fileUriDemo1'; // 实际场景请使用真实的URI。
    let photoCreationConfig: photoAccessHelper.CreationSetting = {
      title: 'test2', // 可选。
      fileNameExtension: 'jpg',
      photoType: photoAccessHelper.PhotoType.IMAGE
    }
    let isImageFullyDisplayed: boolean = true
    let desFileUri: string = await phAccessHelper.showSingleAssetCreationDialogEx(srcFileUri, photoCreationConfig, isImageFullyDisplayed);
    console.info('showSingleAssetCreationDialogEx success, data is ' + desFileUri);
  } catch (err) {
    console.error('showSingleAssetCreationDialogEx failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## unRegisterChange

```TypeScript
unRegisterChange(uri: string, callback?: Callback<ChangeData>): void
```

取消指定uri的监听，一个uri可以注册多个监听，存在多个callback监听时，可以取消指定注册的callback的监听；不指定callback时取消该uri的所有监听。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | PhotoAsset的uri, Album的uri或[DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e.md)的值。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ChangeData&gt; | 否 | 取消 [registerChange](#registerchange)注册时的callback的监听，不填时，取消该uri的所有监听。注： off指定注册的callback后不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |

**示例**

phAccessHelper的创建请参考photoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('offDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset !== undefined) {
    console.info('photoAsset.displayName : ' + photoAsset.displayName);
  }
  let onCallback1 = (changeData: photoAccessHelper.ChangeData) => {
    console.info('onCallback1 on');
  }
  let onCallback2 = (changeData: photoAccessHelper.ChangeData) => {
    console.info('onCallback2 on');
  }
  // 注册onCallback1监听。
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback1);
  // 注册onCallback2监听。
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback2);
  // 关闭onCallback1监听，onCallback2 继续监听。
  phAccessHelper.unRegisterChange(photoAsset.uri, onCallback1);
  await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [photoAsset]);
}
```
