# Album

实体相册。

**继承/实现关系：** Album extends [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i.md)

**起始版本：** 23

<!--Device-photoAccessHelper-interface Album--><!--Device-photoAccessHelper-interface Album-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## deleteAssets

```TypeScript
deleteAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

从回收站中彻底删除图片或者视频，需要先在回收站中预置文件资源。使用callback异步回调。 > **说明：** > > 此操作不可逆，执行此操作后文件资源将彻底删除，请谨慎操作。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-deleteAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void--><!--Device-Album-deleteAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 回收站中待彻底删除图片或者视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('deleteAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.TRASH);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    album.deleteAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album deleteAssets successfully');
      } else {
        console.error(`album deleteAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`deleteAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## deleteAssets

```TypeScript
deleteAssets(assets: Array<PhotoAsset>): Promise<void>
```

从回收站中彻底删除图片或者视频，需要先在回收站中预置文件资源，建议删除数量不超过1000张。使用Promise异步回调。 > **说明：** > > 此操作不可逆，执行此操作后文件资源将彻底删除，请谨慎操作。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-deleteAssets(assets: Array<PhotoAsset>): Promise<void>--><!--Device-Album-deleteAssets(assets: Array<PhotoAsset>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 回收站中待彻底删除图片或者视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('deleteAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.TRASH);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    album.deleteAssets([asset]).then(() => {
      console.info('album deleteAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album deleteAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`deleteAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getAttribute

```TypeScript
getAttribute(attrs: AlbumAttribute[]): Promise<Record<AlbumAttribute, AlbumAttributeInfo>>
```

获取相册属性信息。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Album-getAttribute(attrs: AlbumAttribute[]): Promise<Record<AlbumAttribute, AlbumAttributeInfo>>--><!--Device-Album-getAttribute(attrs: AlbumAttribute[]): Promise<Record<AlbumAttribute, AlbumAttributeInfo>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attrs | [AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md)[] | 是 | 相册获取的属性。 最大长度为20且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;[AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md), [AlbumAttributeInfo](arkts-medialibrary-photoaccesshelper-albumattributeinfo-i-sys.md)&gt;&gt; | Returns a record of attributes and their values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Unsupported attribute; <br>2. The attrs size exceed 20; <br>3. Empty or duplicate attribute; |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getAttributeDemo');
    // 创建查询条件。
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    // 设置查询选项。
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    // 获取智能相册（人像相册）。
    let albumFetchResult = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SMART, 
      photoAccessHelper.AlbumSubtype.PORTRAIT, fetchOptions);
    // 获取第一个相册对象。
    let album = await albumFetchResult.getFirstObject();
    if (album === undefined) {
      console.error('album is undefined');
      return;
    }
    // 定义要获取的属性列表。
    let attrs: [photoAccessHelper.AlbumAttribute] = [
      photoAccessHelper.AlbumAttribute.EXTRA_INFO_ATTR
    ];
    // 获取相册属性信息。
    let attrInfo = await album.getAttribute(attrs);
    console.info(`getAttribute successfully, attrInfo: ${JSON.stringify(attrInfo)}`);
  } catch (err) {
    console.error(`getAttribute failed with err: ${err.code}, ${err.message}`);
  }
}
```

## getFaceId

```TypeScript
getFaceId(): Promise<string>
```

获取人像相册或合影相册的封面人脸标识。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-Album-getFaceId(): Promise<string>--><!--Device-Album-getFaceId(): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，人像相册返回tag_id，合影相册返回group_tag，未找到返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getFaceIdDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.equalTo("user_display_level", 1);
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult =
      await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.PORTRAIT,
        fetchOptions);
    if (fetchResult === undefined) {
      console.error('getFaceId fetchResult is undefined');
      return;
    }
    let album = await fetchResult?.getFirstObject();
    if (album === undefined) {
      console.error('album is undefined');
      return;
    }
    let faceId = await album?.getFaceId();
    if (faceId === undefined) {
      console.error('faceId is undefined');
      return;
    }
    console.info(`getFaceId successfully, faceId: ${faceId}`);
    fetchResult.close();
  } catch (err) {
    console.error(`getFaceId failed with err: ${err.code}, ${err.message}`);
  }
}
```

## getFusionAssetsInfo

```TypeScript
getFusionAssetsInfo(): Promise<FusionAssetsInfo[]>
```

获取融合资产信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-Album-getFusionAssetsInfo(): Promise<FusionAssetsInfo[]>--><!--Device-Album-getFusionAssetsInfo(): Promise<FusionAssetsInfo[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FusionAssetsInfo](arkts-medialibrary-photoaccesshelper-fusionassetsinfo-i-sys.md)[]&gt; | Returns fusion assets information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. <br>Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

## getSelectedAssets

```TypeScript
getSelectedAssets(optionCheck: FetchOptions, filter?: string): Promise<FetchResult<PhotoAsset>>
```

获取符合系统预设筛选条件的人像相册资产。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-Album-getSelectedAssets(optionCheck: FetchOptions, filter?: string): Promise<FetchResult<PhotoAsset>>--><!--Device-Album-getSelectedAssets(optionCheck: FetchOptions, filter?: string): Promise<FetchResult<PhotoAsset>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optionCheck | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项，限制返回资产数量。 |
| filter | string | 否 | 过滤选项，必须是一个Json字符串 <br>过滤选项，必须是一个Json字符串。<br>当前仅支持传递currentFileId，表示当前精选人像卡片展示图片的file_id。例如:'{" currentFileId":"123"}'。 <br>>如果不填写，则从头开始返回资产。 <br>如果填写了currentFileId，则根据该currentFileId内部计算评分，返回评分小于或等于该评分的资产。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;PhotoAsset&gt;&gt; | Promise对象，返回获取的图片结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: 1. The input parameter is not within the valid range. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example1(phAccessHelper: photoAccessHelper.PhotoAccessHelper) : Promise<void> {
  try {
    console.info('getSelectedAssetsDemo');
    let predicatesHomePage: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicatesHomePage.equalTo('user_display_level', 1);
    let optionHome: photoAccessHelper.FetchOptions = {
      predicates: predicatesHomePage,
      fetchColumns: [],
    };
    let albumFetchResult = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SMART,
      photoAccessHelper.AlbumSubtype.PORTRAIT, optionHome);

    if (albumFetchResult === undefined) {
      console.error('getSelected fetchResult is undefined');
      return;
    }
    let album = await albumFetchResult?.getFirstObject();
    if (album === undefined) {
      console.error('album is undefined');
      return;
    }

    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult = await album.getSelectedAssets(fetchOption);
    let photoAsset = await fetchResult.getFirstObject();
    if (!fetchResult||fetchResult.getCount() <= 0) {
      console.error('get selected assets in album with empty dataList');
      return;
    }

    let uriParts = photoAsset.uri.split('/');
    let fileId = uriParts[uriParts.length - 3];
    let filter = `{"currentFileId":"${fileId}"}`;
    let fetchResult1 = await album.getSelectedAssets(fetchOption, filter);
    if (!fetchResult1||fetchResult1.getCount() <= 0) {
      console.error('get selected assets in album with empty dataList');
      return;
    }
    let photoAssetList = fetchResult.getAllObjects();
    console.info('get selected assets in album success');
  } catch (err) {
    console.error(`get selected assets in album fail, error: ${err?.code}, ${err?.message}`);
  }
}
```

## recoverAssets

```TypeScript
recoverAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

从回收站中恢复图片或者视频，需要先在回收站中预置文件资源。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [recoverAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#recoverassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-recoverAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void--><!--Device-Album-recoverAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 回收站中待恢复图片或者视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('recoverAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.TRASH);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    album.recoverAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album recoverAssets successfully');
      } else {
        console.error(`album recoverAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`recoverAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## recoverAssets

```TypeScript
recoverAssets(assets: Array<PhotoAsset>): Promise<void>
```

从回收站中恢复图片或者视频，需要先在回收站中预置文件资源。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [recoverAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#recoverassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-recoverAssets(assets: Array<PhotoAsset>): Promise<void>--><!--Device-Album-recoverAssets(assets: Array<PhotoAsset>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 回收站中待恢复图片或者视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('recoverAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.TRASH);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    album.recoverAssets([asset]).then(() => {
      console.info('album recoverAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album recoverAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`recoverAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setCoverUri

```TypeScript
setCoverUri(uri: string, callback: AsyncCallback<void>): void
```

设置用户相册封面。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [setCoverUri](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#setcoveruri)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-setCoverUri(uri: string, callback: AsyncCallback<void>): void--><!--Device-Album-setCoverUri(uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待设置为相册封面文件的uri。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('setCoverUriDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    album.setCoverUri(asset.uri, (err) => {
      if (err === undefined) {
        console.info('album setCoverUri successfully');
      } else {
        console.error(`album setCoverUri failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`setCoverUriDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setCoverUri

```TypeScript
setCoverUri(uri: string): Promise<void>
```

设置用户相册封面。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [setCoverUri](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#setcoveruri)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-setCoverUri(uri: string): Promise<void>--><!--Device-Album-setCoverUri(uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待设置为相册封面文件的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## dateAdded

```TypeScript
readonly dateAdded?: long
```

相册添加时间，单位：秒。

**类型：** long

**起始版本：** 23

<!--Device-Album-readonly dateAdded?: long--><!--Device-Album-readonly dateAdded?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateModified

```TypeScript
readonly dateModified?: long
```

相册修改时间，单位：秒。

**类型：** long

**起始版本：** 23

<!--Device-Album-readonly dateModified?: long--><!--Device-Album-readonly dateModified?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

