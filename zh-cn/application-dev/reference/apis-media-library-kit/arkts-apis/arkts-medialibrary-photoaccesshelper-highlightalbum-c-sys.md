# HighlightAlbum（系统接口）

时刻相册。

**起始版本：** 23

<!--Device-photoAccessHelper-class HighlightAlbum--><!--Device-photoAccessHelper-class HighlightAlbum-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## constructor

```TypeScript
constructor(album: Album)
```

构造函数。

**起始版本：** 23

<!--Device-HighlightAlbum-constructor(album: Album)--><!--Device-HighlightAlbum-constructor(album: Album)-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| album | Album | 是 | 智慧相册。 |

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
  console.info('HighlightAlbum constructorDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(
    photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.HIGHLIGHT, fetchOption);
  let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
  let highlightAlbum: photoAccessHelper.HighlightAlbum = new photoAccessHelper.HighlightAlbum(album);
  albumFetchResult.close();
}
```

## deleteHighlightAlbums

```TypeScript
static deleteHighlightAlbums(context: Context, albums: Array<Album>): Promise<int>
```

删除指定时刻相册。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-HighlightAlbum-static deleteHighlightAlbums(context: Context, albums: Array<Album>): Promise<int>--><!--Device-HighlightAlbum-static deleteHighlightAlbums(context: Context, albums: Array<Album>): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| albums | Array&lt;Album&gt; | 是 | 需要删除的时刻相册。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 是否成功删除相册。成功返回0，失败返回1。 |

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

async function example(context: Context) {
  try {
    console.info('deleteHighlightAlbums');
    let helper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let albumFetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> =
      await helper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.HIGHLIGHT, albumFetchOption);
    if (albumFetchResult.getCount() === 0) {
      console.error('No album');
      return;
    }
    let highlightAlbum: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    albumFetchResult.close();
    let result = await photoAccessHelper.HighlightAlbum.deleteHighlightAlbums(context, [highlightAlbum]);
    console.info('deleteHighlightAlbums success');
  } catch (err) {
    console.error(`deleteHighlightAlbums with error: ${err}`);
  }
}
```

## getHighlightAlbumInfo

```TypeScript
getHighlightAlbumInfo(type: HighlightAlbumInfoType): Promise<string>
```

获取指定时刻相册的特定信息。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-HighlightAlbum-getHighlightAlbumInfo(type: HighlightAlbumInfoType): Promise<string>--><!--Device-HighlightAlbum-getHighlightAlbumInfo(type: HighlightAlbumInfoType): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [HighlightAlbumInfoType](arkts-medialibrary-photoaccesshelper-highlightalbuminfotype-e-sys.md) | 是 | 需要获取的时刻相册信息类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回指定的时刻相册信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getHighlightAlbumInfoDemo')
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(
      photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.HIGHLIGHT, fetchOptions);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    if (album != undefined) {
      let highlightAlbum: photoAccessHelper.HighlightAlbum = new photoAccessHelper.HighlightAlbum(album);
      let coverInfo: string = await highlightAlbum.getHighlightAlbumInfo(
        photoAccessHelper.HighlightAlbumInfoType.COVER_INFO);
      console.info('get cover info result: ' + JSON.stringify(coverInfo));
    }

    albumFetchResult.close();
  } catch (err) {
    console.error(`getHighlightAlbumInfoDemofailed with error: ${err.code}, ${err.message}`);
  }
}
```

## getHighlightResource

```TypeScript
getHighlightResource(resourceUri: string): Promise<ArrayBuffer>
```

获取指定时刻缓存资源的ArrayBuffer。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-HighlightAlbum-getHighlightResource(resourceUri: string): Promise<ArrayBuffer>--><!--Device-HighlightAlbum-getHighlightResource(resourceUri: string): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceUri | string | 是 | 指定时刻缓存资源uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回资源的ArrayBuffer。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getHighlightResourceDemo')
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(
      photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.HIGHLIGHT, fetchOptions);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    if (album != undefined) {
      let highlightAlbum: photoAccessHelper.HighlightAlbum = new photoAccessHelper.HighlightAlbum(album);
      let uri: string = 'file://media/highlight/cover/10/1_1/background.png?oper=highlight'
      let arrayBuffer: ArrayBuffer = await highlightAlbum.getHighlightResource(uri);
    }
    albumFetchResult.close();
  } catch (err) {
    console.error(`getHighlightResourceDemofailed with error: ${err.code}, ${err.message}`);
  }
}
```

## setHighlightUserActionData

```TypeScript
setHighlightUserActionData(type: HighlightUserActionType, actionData: int): Promise<void>
```

设置指定时刻用户行为数据。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-HighlightAlbum-setHighlightUserActionData(type: HighlightUserActionType, actionData: int): Promise<void>--><!--Device-HighlightAlbum-setHighlightUserActionData(type: HighlightUserActionType, actionData: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [HighlightUserActionType](arkts-medialibrary-photoaccesshelper-highlightuseractiontype-e-sys.md) | 是 | 需要设置的用户行为数据类型。 |
| actionData | int | 是 | 行为数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('setHighlightUserActionDataDemo')
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(
      photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.HIGHLIGHT, fetchOptions);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    if (album != undefined) {
      let highlightAlbum: photoAccessHelper.HighlightAlbum = new photoAccessHelper.HighlightAlbum(album);
      highlightAlbum.setHighlightUserActionData(photoAccessHelper.HighlightUserActionType.INSERTED_PIC_COUNT, 1);
    }
    albumFetchResult.close();
  } catch (err) {
    console.error(`setHighlightUserActionDataDemofailed with error: ${err.code}, ${err.message}`);
  }
}
```

## setSubTitle

```TypeScript
setSubTitle(subTitle: string): Promise<void>
```

设置时刻副标题内容。 副标题参数规格为： - 副标题字符串长度为0~255。 - 不允许出现的非法英文字符，包括： . \ / : * ? " ' ` &lt; &gt; | { } [ ] - 英文字符大小写不敏感。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-HighlightAlbum-setSubTitle(subTitle: string): Promise<void>--><!--Device-HighlightAlbum-setSubTitle(subTitle: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subTitle | string | 是 | 需要设置的时刻副标题内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Returns void |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

