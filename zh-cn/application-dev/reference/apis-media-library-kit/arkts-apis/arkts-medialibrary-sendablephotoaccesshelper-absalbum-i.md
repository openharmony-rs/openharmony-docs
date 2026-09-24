# AbsAlbum

```TypeScript
interface AbsAlbum  extends lang.ISendable
```

定义相册的抽象接口。

**继承/实现关系：** AbsAlbum extends [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-lang-isendable-i.md)

**起始版本：** 12

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

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [photoAccessHelper.FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)&gt;&gt; | Promise对象，返回图片和视频数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Failed to parse FetchOptions, please check if the parameter is valid; <br>2. System internal error, failed to create boolean value, possible causes: 1. Memory insufficient; 2. IPC timeout. Please retry; <br>3. System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

## albumName

```TypeScript
albumName: string
```

相册名称。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumSubtype

```TypeScript
readonly albumSubtype: AlbumSubtype
```

相册子类型。

**类型：** [AlbumSubtype](arkts-medialibrary-sendablephotoaccesshelper-albumsubtype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumType

```TypeScript
readonly albumType: AlbumType
```

相册类型。

**类型：** [AlbumType](arkts-medialibrary-sendablephotoaccesshelper-albumtype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumUri

```TypeScript
readonly albumUri: string
```

相册Uri。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## count

```TypeScript
readonly count: number
```

相册中文件数量。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## coverUri

```TypeScript
readonly coverUri: string
```

封面文件Uri。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
