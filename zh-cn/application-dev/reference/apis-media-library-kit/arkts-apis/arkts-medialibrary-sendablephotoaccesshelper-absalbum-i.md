# AbsAlbum

定义相册的抽象接口。

**继承/实现关系：** AbsAlbum extends lang.ISendable

**起始版本：** 12

<!--Device-sendablePhotoAccessHelper-interface AbsAlbum--><!--Device-sendablePhotoAccessHelper-interface AbsAlbum-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## getAssets

```TypeScript
getAssets(options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>
```

获取图片和视频资源。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-AbsAlbum-getAssets(options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>--><!--Device-AbsAlbum-getAssets(options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | photoAccessHelper.FetchOptions | 是 | 检索选项。 |

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

## albumName

```TypeScript
albumName: string
```

相册名称。

**类型：** string

**起始版本：** 12

<!--Device-AbsAlbum-albumName: string--><!--Device-AbsAlbum-albumName: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumSubtype

```TypeScript
readonly albumSubtype: AlbumSubtype
```

相册子类型。

**类型：** AlbumSubtype

**起始版本：** 12

<!--Device-AbsAlbum-readonly albumSubtype: AlbumSubtype--><!--Device-AbsAlbum-readonly albumSubtype: AlbumSubtype-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumType

```TypeScript
readonly albumType: AlbumType
```

相册类型。

**类型：** AlbumType

**起始版本：** 12

<!--Device-AbsAlbum-readonly albumType: AlbumType--><!--Device-AbsAlbum-readonly albumType: AlbumType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumUri

```TypeScript
readonly albumUri: string
```

相册Uri。

**类型：** string

**起始版本：** 12

<!--Device-AbsAlbum-readonly albumUri: string--><!--Device-AbsAlbum-readonly albumUri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## count

```TypeScript
readonly count: number
```

相册中文件数量。

**类型：** number

**起始版本：** 12

<!--Device-AbsAlbum-readonly count: number--><!--Device-AbsAlbum-readonly count: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## coverUri

```TypeScript
readonly coverUri: string
```

封面文件Uri。

**类型：** string

**起始版本：** 12

<!--Device-AbsAlbum-readonly coverUri: string--><!--Device-AbsAlbum-readonly coverUri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

