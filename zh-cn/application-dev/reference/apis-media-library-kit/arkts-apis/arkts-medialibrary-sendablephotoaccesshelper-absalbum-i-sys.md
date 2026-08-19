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

## getSharedPhotoAssets

```TypeScript
getSharedPhotoAssets(options: photoAccessHelper.FetchOptions): Array<SharedPhotoAsset>
```

Fetch shared photo assets in an album.

**起始版本：** 14

**需要权限：** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

<!--Device-AbsAlbum-getSharedPhotoAssets(options: photoAccessHelper.FetchOptions): Array<SharedPhotoAsset>--><!--Device-AbsAlbum-getSharedPhotoAssets(options: photoAccessHelper.FetchOptions): Array<SharedPhotoAsset>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | photoAccessHelper.FetchOptions | 是 | Fetch options. |

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

