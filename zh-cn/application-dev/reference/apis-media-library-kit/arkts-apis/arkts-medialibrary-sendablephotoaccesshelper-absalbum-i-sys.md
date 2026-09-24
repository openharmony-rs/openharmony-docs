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

## getSharedPhotoAssets

```TypeScript
getSharedPhotoAssets(options: photoAccessHelper.FetchOptions): Array<SharedPhotoAsset>
```

Fetch shared photo assets in an album.

**起始版本：** 14

**需要权限：** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [photoAccessHelper.FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | Fetch options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[SharedPhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-sharedphotoasset-i-sys.md)&gt; | Returns the shared photo assets |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |
