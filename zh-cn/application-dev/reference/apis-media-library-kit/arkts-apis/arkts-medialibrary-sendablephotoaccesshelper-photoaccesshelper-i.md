# PhotoAccessHelper

提供操作系统媒体资源能力的接口。

**继承/实现关系：** PhotoAccessHelper extends lang.ISendable

**起始版本：** 12

<!--Device-sendablePhotoAccessHelper-interface PhotoAccessHelper--><!--Device-sendablePhotoAccessHelper-interface PhotoAccessHelper-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, options?: photoAccessHelper.CreateOptions): Promise<string>
```

指定文件类型、后缀和创建选项，创建图片或视频资源。使用Promise异步回调。 此接口在未申请相册管理模块权限'ohos.permission.WRITE_IMAGEVIDEO'时，可以使用安全控件创建媒体资源，详情请参考 [保存媒体库资源](../../../media/medialibrary/photoAccessHelper-savebutton.md).

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, options?: photoAccessHelper.CreateOptions): Promise<string>--><!--Device-PhotoAccessHelper-createAsset(photoType: PhotoType, extension: string, options?: photoAccessHelper.CreateOptions): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoType | PhotoType | 是 | 创建的文件类型，IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件名后缀参数，例如：'jpg'。字符串长度的取值范围为[1, 255]。 . |
| options | photoAccessHelper.CreateOptions | 否 | 创建选项，例如{title: 'testPhoto'}。 <br>文件名中不允许出现非法英文字符。 <br>API18开始，非法字符包括： \ / : ? " &lt; &gt; \| <br>API10-17，非法字符包括： . .. \ / : ? " ' ` &lt; &gt; \| { } [ ] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回创建的图片和视频的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let photoType: sendablePhotoAccessHelper.PhotoType = sendablePhotoAccessHelper.PhotoType.IMAGE;
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

## getAlbums

```TypeScript
getAlbums(options: photoAccessHelper.FetchOptions): Promise<FetchResult<Album>>
```

根据检索选项获取相册。使用Promise异步回调。 获取相册前需先保证相册存在。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAlbums(options: photoAccessHelper.FetchOptions): Promise<FetchResult<Album>>--><!--Device-PhotoAccessHelper-getAlbums(options: photoAccessHelper.FetchOptions): Promise<FetchResult<Album>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | photoAccessHelper.FetchOptions | 是 | 检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;Album&gt;&gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  // 示例代码中为获取相册名为newAlbumName的相册。
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getAlbumsPromise fetchResult is undefined');
      return;
    }
    let album: sendablePhotoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsPromise successfully, albumName: ' + album.albumName);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getAlbumsPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getAlbums

```TypeScript
getAlbums(
      type: AlbumType,
      subtype: AlbumSubtype,
      options?: photoAccessHelper.FetchOptions
    ): Promise<FetchResult<Album>>
```

根据检索选项和相册类型获取相册。使用Promise异步回调。 获取相册前需先保证相册存在。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAlbums(      type: AlbumType,      subtype: AlbumSubtype,      options?: photoAccessHelper.FetchOptions    ): Promise<FetchResult<Album>>--><!--Device-PhotoAccessHelper-getAlbums(      type: AlbumType,      subtype: AlbumSubtype,      options?: photoAccessHelper.FetchOptions    ): Promise<FetchResult<Album>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | AlbumType | 是 | 相册类型。 |
| subtype | AlbumSubtype | 是 | 相册子类型。 |
| options | photoAccessHelper.FetchOptions | 否 | 检索选项，不填时默认根据相册类型检索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;Album&gt;&gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  // 示例代码中为获取相册名为newAlbumName的相册。
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(sendablePhotoAccessHelper.AlbumType.USER, sendablePhotoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getAlbumsPromise fetchResult is undefined');
      return;
    }
    let album: sendablePhotoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsPromise successfully, albumName: ' + album.albumName);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getAlbumsPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getAssets

```TypeScript
getAssets(options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>
```

获取图片和视频资源。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAssets(options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>--><!--Device-PhotoAccessHelper-getAssets(options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | photoAccessHelper.FetchOptions | 是 | 图片和视频检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;PhotoAsset&gt;&gt; | Promise对象，返回图片和视频数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('getAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
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
getBurstAssets(burstKey: string, options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>
```

获取连拍照片资源。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getBurstAssets(burstKey: string, options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>--><!--Device-PhotoAccessHelper-getBurstAssets(burstKey: string, options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| burstKey | string | 是 | 一组连拍照片的唯一标识：uuid（可传入 [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)的BURST_KEY）。 字符串长度为36字节。 |
| options | photoAccessHelper.FetchOptions | 是 | 连拍照片检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;PhotoAsset&gt;&gt; | Promise对象，返回连拍照片数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('getBurstAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAssetList: Array<sendablePhotoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
  let photoAsset: sendablePhotoAccessHelper.PhotoAsset;
  // burstKey为36位的uuid，可以根据photoAccessHelper.PhotoKeys获取。
  for(photoAsset of photoAssetList){
    let burstKey: string = photoAccessHelper.PhotoKeys.BURST_KEY.toString();
    let photoAccessBurstKey: photoAccessHelper.MemberType = photoAsset.get(burstKey).toString();
    try {
      let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await
      phAccessHelper.getBurstAssets(photoAccessBurstKey, fetchOption);
      if (fetchResult !== undefined) {
        console.info('fetchResult success');
        let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
        if (photoAsset !== undefined) {
          console.info('photoAsset.displayName :' + photoAsset.displayName);
        }
      }
    } catch (err) {
      console.error(`getBurstAssets failed, error: ${err.code}, ${err.message}`);
    }
  }
}
```

## release

```TypeScript
release(): Promise<void>
```

释放PhotoAccessHelper实例，当后续不需要使用PhotoAccessHelper实例中的方法时调用。使用Promise异步回调。

**起始版本：** 12

<!--Device-PhotoAccessHelper-release(): Promise<void>--><!--Device-PhotoAccessHelper-release(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('releaseDemo');
  try {
    console.info('use function...');
  } catch (err) {
    console.error(`function error ...`);
  }finally{
      try{
          phAccessHelper?.release();
          console.info(`release success`);
      } catch(e){
          console.error(`release error :${e}`);
      }
  }
}
```

