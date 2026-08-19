# MediaAnalysisAlbumChangeRequest（系统接口）

智慧相册变更请求。

**继承/实现关系：** MediaAnalysisAlbumChangeRequest extends [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md)

**起始版本：** 23

<!--Device-photoAccessHelper-class MediaAnalysisAlbumChangeRequest--><!--Device-photoAccessHelper-class MediaAnalysisAlbumChangeRequest-End-->

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

<!--Device-MediaAnalysisAlbumChangeRequest-constructor(album: Album)--><!--Device-MediaAnalysisAlbumChangeRequest-constructor(album: Album)-End-->

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

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  console.info('MediaAnalysisAlbumChangeRequest constructorDemo');
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
  let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
    new photoAccessHelper.MediaAnalysisAlbumChangeRequest(highlightAlbum);
}
```

## createAnalysisAlbumRequest

```TypeScript
static createAnalysisAlbumRequest(
      context: Context, 
      name: string, 
      subtype: AlbumSubtype
    ): MediaAnalysisAlbumChangeRequest | null
```

创建一个 MediaAnalysisAlbumChangeRequest 实例

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAnalysisAlbumChangeRequest-static createAnalysisAlbumRequest(      context: Context,       name: string,       subtype: AlbumSubtype    ): MediaAnalysisAlbumChangeRequest | null--><!--Device-MediaAnalysisAlbumChangeRequest-static createAnalysisAlbumRequest(      context: Context,       name: string,       subtype: AlbumSubtype    ): MediaAnalysisAlbumChangeRequest | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 实例的上下文 |
| name | string | 是 | 相册名称 |
| subtype | AlbumSubtype | 是 | 相册子类 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAnalysisAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaanalysisalbumchangerequest-c-sys.md) | 返回一个智慧相册变更句柄 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: <br>1. The input parameter is not within the valid range. |

## createAnalysisAlbumRequest

```TypeScript
static createAnalysisAlbumRequest(
      context: Context, 
      name: string, 
      subtype: AlbumSubtype
    ): MediaAnalysisAlbumChangeRequest
```

创建智慧相册的变更请求。 > **说明：**> > 相册名的参数规格如下： > > - 相册名字符串长度的取值范围为[1, 255]。 > > - 不允许出现非法英文字符，包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAnalysisAlbumChangeRequest-static createAnalysisAlbumRequest(      context: Context,       name: string,       subtype: AlbumSubtype    ): MediaAnalysisAlbumChangeRequest--><!--Device-MediaAnalysisAlbumChangeRequest-static createAnalysisAlbumRequest(      context: Context,       name: string,       subtype: AlbumSubtype    ): MediaAnalysisAlbumChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| name | string | 是 | 待创建相册的名称。 |
| subtype | AlbumSubtype | 是 | 待创建智慧相册的子类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAnalysisAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaanalysisalbumchangerequest-c-sys.md) | 返回创建智慧相册的变更请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: <br>1. The input parameter is not within the valid range. |

**示例**

photoAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('createAlbumRequestDemo');
  try {
    let albumName: string = 'newAlbumName' + new Date().getTime();
    let albumChangeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest = photoAccessHelper.MediaAnalysisAlbumChangeRequest.createAnalysisAlbumRequest(context, albumName, photoAccessHelper.AlbumSubtype.PORTRAIT);
    await phAccessHelper.applyChanges(albumChangeRequest);
    console.info('apply createAlbumRequest successfully');
  } catch (err) {
    console.error(`createAlbumRequestDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setDefaultCoverUri

```TypeScript
setDefaultCoverUri(coverUri: string): void
```

设置智慧相册的默认封面。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAnalysisAlbumChangeRequest-setDefaultCoverUri(coverUri: string): void--><!--Device-MediaAnalysisAlbumChangeRequest-setDefaultCoverUri(coverUri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| coverUri | string | 是 | 待设置为智慧相册默认封面的文件URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: <br>1. The input parameter is not within the valid range. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  console.info('setDefaultCoverUri');
  try {
    let helper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let albumFetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> =
      await helper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.PORTRAIT, albumFetchOption);
    if (albumFetchResult.getCount() === 0) {
      console.error('No album');
      return;
    }
    let portraitAlbum: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    albumFetchResult.close();
    // 获取相册中的资源。
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
      await portraitAlbum.getAssets(fetchOption);
    if (fetchResult.getCount() === 0) {
      console.error('No asset in album');
      fetchResult.close();
      return;
    }
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let coverUri: string = asset.uri;
    fetchResult.close();
    // 设置默认封面。
    let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
      new photoAccessHelper.MediaAnalysisAlbumChangeRequest(portraitAlbum);
    changeRequest.setDefaultCoverUri(coverUri);
    await helper.applyChanges(changeRequest);
    console.info('setDefaultCoverUri success');
  } catch (err) {
    console.error(`setDefaultCoverUri error: ${err}`);
  }
}
```

## setOrderPosition

```TypeScript
setOrderPosition(assets: Array<PhotoAsset>, position: Array<int>): void
```

设置智慧相册中资产的顺序位置。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAnalysisAlbumChangeRequest-setOrderPosition(assets: Array<PhotoAsset>, position: Array<int>): void--><!--Device-MediaAnalysisAlbumChangeRequest-setOrderPosition(assets: Array<PhotoAsset>, position: Array<int>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 需要设置顺序位置的相册中资产。 |
| position | Array&lt;int&gt; | 是 | 相册中资产的顺序位置。 |

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
    console.info('setOrderPosition');
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
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    const fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
      await highlightAlbum.getAssets(fetchOption);
    let assets: photoAccessHelper.PhotoAsset[] = await fetchResult.getAllObjects();
    let indexes: number[] = [];
    for (let i = 0; i < assets.length; i++) {
      indexes.push(i);
    }
    let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
      new photoAccessHelper.MediaAnalysisAlbumChangeRequest(highlightAlbum);
    changeRequest.setOrderPosition(assets, indexes);
    await helper.applyChanges(changeRequest);
    console.info(`setOrderPosition ${indexes}`);
  } catch (err) {
    console.error(`setOrderPosition error: ${err}`);
  }
}
```

## setRelationship

```TypeScript
setRelationship(relationship: string): Promise<void>
```

设置人像相册中的人物关系。 支持的人物关系名称范围： | 唯一标识 | 含义 | | ---------- | ------- | | me | 我 | | son | 儿子 | | daughter | 女儿 | | wife | 妻子 | | husband | 丈夫 | | father | 爸爸 | | mother | 妈妈 | | colleague | 同事 | | friend | 朋友 | | classmate | 同学 | | best_friend_female | 闺蜜 | | boyfriend | 男朋友 | | girlfriend | 女朋友 | | family | 家人 | | maternal_grandfather | 外公 | | maternal_grandmother | 外婆 | | paternal_grandfather | 爷爷 | | paternal_grandmother | 奶奶 | | older_brother | 哥哥 | | older_sister | 姐姐 | | younger_brother | 弟弟 | | younger_sister | 妹妹 | | relative | 亲戚 | | other | 其他 |

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAnalysisAlbumChangeRequest-setRelationship(relationship: string): Promise<void>--><!--Device-MediaAnalysisAlbumChangeRequest-setRelationship(relationship: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relationship | string | 是 | 需要设置的人物关系名称。 <br>支持设置为空字符串，功能为取消当前设置的人物关系。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: <br>1. The input parameter is not within the valid range. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function SetRelationshipExample(context: Context, relationship: string) {
  try {
    console.info('setRelationship');
    let helper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let albumFetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> =
      await helper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.PORTRAIT, albumFetchOption);
    if (albumFetchResult.getCount() === 0) {
      console.error('No album');
      return;
    }
    let portraitAlbum: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    albumFetchResult.close();
    let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
      new photoAccessHelper.MediaAnalysisAlbumChangeRequest(portraitAlbum);
    changeRequest.setRelationship(relationship);
    await helper.applyChanges(changeRequest);
    console.info(`setRelationship ${relationship}`);
  } catch (err) {
    console.error(`setRelationship error: ${err}`);
  }
}
```

