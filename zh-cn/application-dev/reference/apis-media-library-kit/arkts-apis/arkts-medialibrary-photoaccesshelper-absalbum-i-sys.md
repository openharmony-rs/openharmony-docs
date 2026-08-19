# AbsAlbum

定义相册的抽象接口。

**起始版本：** 23

<!--Device-photoAccessHelper-interface AbsAlbum--><!--Device-photoAccessHelper-interface AbsAlbum-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getSharedPhotoAssets

```TypeScript
getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>
```

获取共享的照片资产。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

<!--Device-AbsAlbum-getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>--><!--Device-AbsAlbum-getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | Fetch options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;SharedPhotoAsset&gt; | Returns the shared photo assets |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

## coverUriSource

```TypeScript
readonly coverUriSource?: CoverUriSource
```

相册封面来源。

**类型：** [CoverUriSource](arkts-medialibrary-photoaccesshelper-coverurisource-e-sys.md)

**起始版本：** 23

<!--Device-AbsAlbum-readonly coverUriSource?: CoverUriSource--><!--Device-AbsAlbum-readonly coverUriSource?: CoverUriSource-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hidden

```TypeScript
readonly hidden?: boolean
```

相册是否为隐藏状态。true表示相册为隐藏状态，false表示相册不为隐藏状态。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbsAlbum-readonly hidden?: boolean--><!--Device-AbsAlbum-readonly hidden?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## lpath

```TypeScript
readonly lpath?: string
```

相册的虚拟路径。 支持的相册及对应的lpath值： - 相机应用相册：'/DCIM/Camera' - 截图应用相册：'/Pictures/Screenshots' - 屏幕录制应用相册：'/Pictures/Screenrecords' - 用户创建的相册：'/Pictures/Users/{用户自定义相册名称}'

**类型：** string

**起始版本：** 23

<!--Device-AbsAlbum-readonly lpath?: string--><!--Device-AbsAlbum-readonly lpath?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## uploadStatus

```TypeScript
readonly uploadStatus: boolean
```

表示是否允许相册同步到云空间或家庭存储。true表示允许，false表示不允许。

**类型：** boolean

**起始版本：** 26.0.0

<!--Device-AbsAlbum-readonly uploadStatus: boolean--><!--Device-AbsAlbum-readonly uploadStatus: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

