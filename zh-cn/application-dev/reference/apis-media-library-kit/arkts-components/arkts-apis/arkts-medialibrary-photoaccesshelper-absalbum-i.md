# AbsAlbum

定义相册的抽象接口。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
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
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | 是 | 回调函数。当获取相册中的文件成功，err为undefined，data为获取到的图片和视频数据结果集[FetchResult](arkts-medialibrary-file-photoaccesshelper.md)；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 - 11 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getAssets

```TypeScript
getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>
```

获取相册中的文件。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | Promise对象，返回图片和视频数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied<br>**适用版本：** 20+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**适用版本：** 10 - 19 |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## albumName

```TypeScript
albumName: string
```

相册名称。预置相册不可写，用户相册可写。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumSubtype

```TypeScript
readonly albumSubtype: AlbumSubtype
```

相册子类型。

**类型：** [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumType

```TypeScript
readonly albumType: AlbumType
```

相册类型。

**类型：** [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumUri

```TypeScript
readonly albumUri: string
```

相册uri。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## changeTime

```TypeScript
readonly changeTime?: number
```

相册的更改时间，单位：秒。单位为： second，取值应≥0。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## count

```TypeScript
readonly count: number
```

相册中文件数量。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## coverUri

```TypeScript
readonly coverUri: string
```

封面文件uri。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## lpath

```TypeScript
readonly lpath?: string
```

相册的虚拟路径。

支持的相册及对应的lpath值：

- 相机应用相册：'/DCIM/Camera'  
- 截图应用相册：'/Pictures/Screenshots'  
- 屏幕录制应用相册：'/Pictures/Screenrecords'  
- 用户创建的相册：'/Pictures/Users/{用户自定义相册名称}'

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
