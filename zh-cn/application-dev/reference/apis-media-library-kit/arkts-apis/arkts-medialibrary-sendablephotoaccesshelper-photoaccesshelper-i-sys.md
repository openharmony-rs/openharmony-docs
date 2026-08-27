# PhotoAccessHelper

提供操作系统媒体资源能力的接口。

**继承/实现关系：** PhotoAccessHelper extends lang.ISendable

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## createAsset

```TypeScript
createAsset(displayName: string): Promise<PhotoAsset>
```

指定待创建的图片或者视频的文件名，创建图片或视频资源。使用Promise异步回调。待创建的文件名参数规格为：  
- 应包含有效文件主名和图片或视频扩展名。  
- 文件名字符串长度为1~255。  
- 文件主名中不允许出现的非法英文字符。  
API18开始，非法字符包括：\ / : * ? " &lt; &gt; |API10-17，非法字符包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayName | string | 是 | 创建的图片或者视频文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PhotoAsset & gt; | Promise对象，返回创建的图片和视频结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900020 | Invalid argument. |
| 14000001 | Invalid display name. |
| 14000011 | Internal system error. |

**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-file-sendablephotoaccesshelper.md)的示例使用。

```TypeScript
async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName);
    console.info('createAsset file displayName' + photoAsset.displayName);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createAsset

```TypeScript
createAsset(displayName: string, options: photoAccessHelper.PhotoCreateOptions): Promise<PhotoAsset>
```

指定待创建的图片或者视频的文件名和创建选项，创建图片或视频资源。使用Promise异步回调。待创建的文件名参数规格为：  
- 应包含有效文件主名和图片或视频扩展名。  
- 文件名字符串长度为1~255。  
- 文件主名中不允许出现的非法英文字符。  
API18开始，非法字符包括： \ / : * ? " &lt; &gt; |API10-17，非法字符包括： . .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayName | string | 是 | 创建的图片或者视频文件名。 |
| options | photoAccessHelper.PhotoCreateOptions | 是 | 图片或视频的创建选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PhotoAsset & gt; | Promise used to return the created asset. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 13900020 | Invalid argument. |
| 14000001 | Invalid display name. |
| 14000011 | Internal system error. |

**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-file-sendablephotoaccesshelper.md)的示例使用。

```TypeScript
async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let testFileName:string = 'testFile' + Date.now() + '.jpg';
    let createOption: photoAccessHelper.PhotoCreateOptions = {
      subtype: photoAccessHelper.PhotoSubtype.DEFAULT
    }
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName, createOption);
    console.info('createAsset file displayName' + photoAsset.displayName);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getHiddenAlbums

```TypeScript
getHiddenAlbums(
      mode: photoAccessHelper.HiddenPhotosDisplayMode,
      options?: photoAccessHelper.FetchOptions
    ): Promise<FetchResult<Album>>
```

根据隐藏文件显示模式和检索选项获取系统中的隐藏相册。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | photoAccessHelper.HiddenPhotosDisplayMode | 是 | 隐藏文件显示模式。 |
| options | photoAccessHelper.FetchOptions | 否 | 检索选项，不填时默认根据隐藏文件显示模式检索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;FetchResult & lt;Album & gt; & gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-file-sendablephotoaccesshelper.md)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取系统预置的隐藏相册。
async function getSysHiddenAlbum(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('getSysHiddenAlbumDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ASSETS_MODE)
    .then( async (fetchResult) => {
      if (fetchResult === undefined) {
        console.error('getSysHiddenAlbumPromise fetchResult is undefined');
        return;
      }
      let hiddenAlbum: sendablePhotoAccessHelper.Album = await fetchResult.getFirstObject();
      console.info('getAlbumsPromise successfully, albumUri: ' + hiddenAlbum.albumUri);
      fetchResult.close();
    }).catch((err: BusinessError) => {
      console.error(`getSysHiddenAlbumPromise failed with err: ${err.code}, ${err.message}`);
    });
}

// 获取隐藏相册-相册视图，即系统中包含隐藏文件的相册（不包含系统预置的隐藏相册本身和回收站相册）。
async function getHiddenAlbumsView(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('getHiddenAlbumsViewDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ALBUMS_MODE).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getHiddenAlbumsViewPromise fetchResult is undefined');
      return;
    }
    let albums: Array<sendablePhotoAccessHelper.Album> = await fetchResult.getAllObjects();
    console.info('getHiddenAlbumsViewPromise successfully, albums size: ' + albums.length);

    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    for (let i = 0; i < albums.length; i++) {
      // 获取相册中的隐藏文件。
      albums[i].getAssets(fetchOption).then((assetFetchResult) => {
        console.info('album get hidden assets successfully, getCount: ' + assetFetchResult.getCount());
      }).catch((err: BusinessError) => {
        console.error(`album get hidden assets failed with error: ${err.code}, ${err.message}`);
      });
    }
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getHiddenAlbumsViewPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getPhotoAssets

```TypeScript
getPhotoAssets(assetsData: photoAccessHelper.ValuesBucket[]): Promise<PhotoAsset[]>
```

将ValuesBucket记录转换为PhotoAsset对象。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetsData | photoAccessHelper.ValuesBucket[] | 是 | 资产记录的数组。 数组中的每个元素包含资产的列名称及其对应的值。 数组的大小不能超过500个。 数组中的每个元素必须包含以下资产列信息：file_id、data、display_name、media_type、subtype。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PhotoAsset[] & gt; | Promise对象，返回PhotoAsset对象的数组（数组可能为空）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:  1. Invalid value type in ValuesBucket;  2. Missing required column in ValuesBucket;  3. Array size exceeds 500. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-file-sendablephotoaccesshelper.md)的示例使用。

```TypeScript
async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('getPhotoAssets demo');
  let valuesArr: photoAccessHelper.ValuesBucket[] = [];
  let resultSet: photoAccessHelper.ResultSet | undefined = undefined;
  let photoAssetArr: sendablePhotoAccessHelper.PhotoAsset[] = [];
  let QUERY_SQL = 'SELECT file_id,data,display_name,media_type,subtype from Photos limit 100';
  try {
    resultSet = await photoAccessHelper.getPhotoAccessHelper(context).query(QUERY_SQL);
    let index: number = 0;
    while(resultSet && index < resultSet.rowCount){
      resultSet.goToRow(index);
      valuesArr.push(resultSet.getRow());
      index++;
    }
    photoAssetArr = await phAccessHelper.getPhotoAssets(valuesArr);
    console.info('getPhotoAssets successfully');
  } catch (err) {
    console.error(`valuesArr failed: ${err.code}, ${err.message}`);
  }
}
```

## getSharedPhotoAssets

```TypeScript
getSharedPhotoAssets(options: photoAccessHelper.FetchOptions): Array<SharedPhotoAsset>
```

Fetch shared photo assets.

**起始版本：** 14

**需要权限：** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | photoAccessHelper.FetchOptions | 是 | Fetch options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;SharedPhotoAsset & gt; | Returns the shared photo assets |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error |
