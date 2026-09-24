# Album

```TypeScript
interface Album extends AbsAlbum
```

实体相册。

**继承/实现关系：** Album extends [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## commitModify

```TypeScript
commitModify(callback: AsyncCallback<void>): void
```

更新相册属性修改到数据库中。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当相册属性修改成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album is not a user album, only user albums support this operation; <br>3.The album name exceeds the length limit or contains invalid characters; <br>4.The number of parameters is invalid; <br>5.The callback parameter must be of type AsyncCallback&lt;void&gt;. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2.The server returned an error during commitModify, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  if (albumList === undefined) {
    console.error('albumList is undefined');
    return;
  }
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  if (album === undefined) {
    console.error('album is undefined');
    return;
  }
  album.albumName = 'hello';
  album.commitModify((err) => {
    if (err) {
      console.error(`commitModify failed with error: ${err.code}, ${err.message}`);
    } else {
      console.info('commitModify successfully');
    }
  });
}
```

<a id="commitmodify-1"></a>

## commitModify

```TypeScript
commitModify(): Promise<void>
```

更新相册属性修改到数据库中。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.System out of memory, please retry; <br>2.The object is not a valid instance; <br>3.The album is not a user album, only user albums support this operation; <br>4.The album name exceeds the length limit or contains invalid characters; <br>5.The number of parameters is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2.The server returned an error during commitModify, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  if (albumList === undefined) {
    console.error('albumList is undefined');
    return;
  }
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  if (album === undefined) {
    console.error('album is undefined');
    return;
  }
  album.albumName = 'hello';
  // 提交相册名称修改到数据库。
  album.commitModify().then(() => {
    console.info('commitModify successfully');
  }).catch((err: BusinessError) => {
    console.error(`commitModify failed with error: ${err.code}, ${err.message}`);
  });
}
```

## addAssets

```TypeScript
addAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

向用户相册中添加图片或视频，需预置相册和文件资源。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [addAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 待添加到相册中的图片或视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当添加图片或视频成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.System out of memory, please retry; <br>2.The object is not a valid instance; <br>3.The album is not a user album, only user albums support this operation; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The number of parameters is invalid; <br>8.The array element is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.System memory insufficient, please retry; <br>2.The assets array contains elements with invalid file type, each element must be IMAGE or VIDEO type; <br>3.IPC call failed, please retry and check logs; <br>4.The assets array contains elements that are not valid PhotoAsset objects; <br>5.Server returned a non-permission error code; <br>6.Failed to update album count, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>7.The assets parameter must be an array; <br>8.The assets array is empty; <br>9.The array element must be a valid PhotoAsset object. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('addAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('addAssetsDemoCallback asset is undefined');
      return;
    }
    album.addAssets([asset], (err) => {
      if (!err) {
        console.info('album addAssets successfully');
      } else {
        console.error(`album addAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`addAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

<a id="addassets-1"></a>

## addAssets

```TypeScript
addAssets(assets: Array<PhotoAsset>): Promise<void>
```

向用户相册添加图片或视频，需预置相册和文件资源。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [addAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 待添加到相册中的图片或视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album instance is invalid; <br>3.The album is not a user album, only user albums support addAssets; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The number of parameters is invalid, expected at least 1 parameter; <br>8.The array element is not a valid PhotoAsset object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The assets array contains no valid photo or video resources; <br>2.IPC call returned a non-permission error code; <br>3.Batch insert failed, database operation error, please retry; <br>4.Failed to update album count, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>6.The assets parameter must be an array; <br>7.The assets array is empty; <br>8.The array element must be a valid PhotoAsset object. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('addAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('addAssetsDemoPromise asset is undefined');
      return;
    }
    // 向相册添加资源。
    album.addAssets([asset]).then(() => {
      console.info('album addAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album addAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`addAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

## removeAssets

```TypeScript
removeAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

从用户相册移除图片或视频，需预置相册和文件资源。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [removeAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 相册中待移除的图片或视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当移除图片或视频成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album instance is invalid; <br>3.The album is not a user album, only user albums support removeAssets; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The object is not a valid instance; <br>8.The array element is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The assets array is empty or contains no valid PhotoAsset elements; <br>2.IPC call returned a non-permission error code; <br>3.The assets array contains elements that are not valid PhotoAsset objects; <br>4.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.The assets parameter must be an array; <br>6.The assets array is empty; <br>7.The array element must be a valid PhotoAsset object. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('removeAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('removeAssetsDemoCallback asset is undefined');
      return;
    }
    album.removeAssets([asset], (err) => {
      if (!err) {
        console.info('album removeAssets successfully');
      } else {
        console.error(`album removeAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`removeAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

<a id="removeassets-1"></a>

## removeAssets

```TypeScript
removeAssets(assets: Array<PhotoAsset>): Promise<void>
```

从用户相册中移除图片或视频，需预置相册和文件资源。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [removeAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 相册中待移除的图片或视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album instance is invalid; <br>3.The album is not a user album, only user albums support removeAssets; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The object is not a valid instance; <br>8.The array element is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The assets array is empty or contains no valid PhotoAsset elements; <br>2.IPC call returned a non-permission error code; <br>3.The assets array contains elements that are not valid PhotoAsset objects; <br>4.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.The assets parameter must be an array; <br>6.The assets array is empty; <br>7.The array element must be a valid PhotoAsset object. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('removeAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    if (album === undefined) {
      console.error('removeAssetsPromise albums is undefined');
      return;
    }
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('removeAssetsPromise asset is undefined');
      return;
    }
    // 从相册移除资源。
    album.removeAssets([asset]).then(() => {
      console.info('album removeAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album removeAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`removeAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

## imageCount

```TypeScript
readonly imageCount?: number
```

相册中图片数量。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoCount

```TypeScript
readonly videoCount?: number
```

相册中视频数量。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
