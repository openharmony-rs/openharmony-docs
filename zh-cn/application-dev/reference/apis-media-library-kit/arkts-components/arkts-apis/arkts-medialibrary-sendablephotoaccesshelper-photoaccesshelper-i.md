# PhotoAccessHelper

提供操作系统媒体资源能力的接口。

**继承/实现关系：** PhotoAccessHelper extends lang.ISendable

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## createAsset

```TypeScript
createAsset(photoType: PhotoType, extension: string, options?: photoAccessHelper.CreateOptions): Promise<string>
```

指定文件类型、后缀和创建选项，创建图片或视频资源。使用Promise异步回调。

此接口在未申请相册管理模块权限'ohos.permission.WRITE_IMAGEVIDEO'时，可以使用安全控件创建媒体资源，详情请参考[保存媒体库资源](../../../media/medialibrary/photoAccessHelper-savebutton.md).

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoType | [PhotoType](arkts-medialibrary-sendablephotoaccesshelper-phototype-e.md) | 是 | 创建的文件类型，IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件名后缀参数，例如：'jpg'。字符串长度的取值范围为[1, 255]。. |
| options | [photoAccessHelper.CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | 否 | 创建选项，例如{title: 'testPhoto'}。<br>文件名中不允许出现非法英文字符。<br>API18开始，非法字符包括： \ / : * ? " &lt; &gt; &#124; <br>API10-17，非法字符包括： . .. \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回创建的图片和视频的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```

```TypeScript
phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-medialibrary-file-sendablephotoaccesshelper.md)的示例使用。
```

## getAlbums

```TypeScript
getAlbums(options: photoAccessHelper.FetchOptions): Promise<FetchResult<Album>>
```

根据检索选项获取相册。使用Promise异步回调。

获取相册前需先保证相册存在。

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
| Promise&lt;[FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md)&lt;[Album](arkts-medialibrary-sendablephotoaccesshelper-album-i.md)&gt;&gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```

## getAlbums

```TypeScript
getAlbums(
      type: AlbumType,
      subtype: AlbumSubtype,
      options?: photoAccessHelper.FetchOptions
    ): Promise<FetchResult<Album>>
```

根据检索选项和相册类型获取相册。使用Promise异步回调。

获取相册前需先保证相册存在。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AlbumType](arkts-medialibrary-sendablephotoaccesshelper-albumtype-e.md) | 是 | 相册类型。 |
| subtype | [AlbumSubtype](arkts-medialibrary-sendablephotoaccesshelper-albumsubtype-e.md) | 是 | 相册子类型。 |
| options | [photoAccessHelper.FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 否 | 检索选项，不填时默认根据相册类型检索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md)&lt;[Album](arkts-medialibrary-sendablephotoaccesshelper-album-i.md)&gt;&gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

参见 [getAlbums](#getalbums)

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
| options | [photoAccessHelper.FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 图片和视频检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)&gt;&gt; | Promise对象，返回图片和视频数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```

## getBurstAssets

```TypeScript
getBurstAssets(burstKey: string, options: photoAccessHelper.FetchOptions): Promise<FetchResult<PhotoAsset>>
```

获取连拍照片资源。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| burstKey | string | 是 | 一组连拍照片的唯一标识：uuid（可传入[PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)的BURST_KEY）。字符串长度为36字节。 |
| options | [photoAccessHelper.FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 连拍照片检索选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)&gt;&gt; | Promise对象，返回连拍照片数据结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```

## release

```TypeScript
release(): Promise<void>
```

释放PhotoAccessHelper实例，当后续不需要使用PhotoAccessHelper实例中的方法时调用。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```
