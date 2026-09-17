# PhotoAsset

提供封装文件属性的方法。

**继承/实现关系：** PhotoAsset extends lang.ISendable

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## commitModify

```TypeScript
commitModify(): Promise<void>
```

修改文件的元数据。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

## convertToPhotoAsset

```TypeScript
convertToPhotoAsset(): photoAccessHelper.PhotoAsset
```

将Sendable类型PhotoAsset转换为非Sendable类型PhotoAsset。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [photoAccessHelper.PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 返回非Sendable类型的[PhotoAsset](arkts-medialibrary-file-photoaccesshelper.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```

## get

```TypeScript
get(member: string): photoAccessHelper.MemberType
```

获取PhotoAsset成员参数的值。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| member | string | 是 | 成员参数名称，在get时，除了'uri'、'media_type'、'subtype'和'display_name'四个属性之外，其他的属性都需要在fetchColumns中填入需要get的[PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)，例如：get title属性fetchColumns: ['title']。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [photoAccessHelper.MemberType](arkts-medialibrary-photoaccesshelper-membertype-t.md) | 获取PhotoAsset成员参数的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```

## getThumbnail

```TypeScript
getThumbnail(size?: image.Size): Promise<image.PixelMap>
```

获取文件的缩略图，传入缩略图尺寸。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md) | 否 | 缩略图尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise对象，返回缩略图的PixelMap。 |

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

## set

```TypeScript
set(member: string, value: string): void
```

设置PhotoAsset成员参数。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| member | string | 是 | 成员参数名称例如：[PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md).TITLE。字符串长度的取值范围为[1, 255]。 |
| value | string | 是 | 设置成员参数名称，只能修改[PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md).TITLE的值。title的参数规格为：<br>- 不应包含扩展名。<br>- 文件名字符串长度的取值范围为[1, 255]（资产文件名为标题+扩展名）。<br>- 不允许出现的非法英文字符，包括：. \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**示例**

```TypeScript
phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。
```

## displayName

```TypeScript
readonly displayName: string
```

显示文件名，包含后缀名。字符串长度的取值范围为[1, 255]。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoType

```TypeScript
readonly photoType: PhotoType
```

媒体文件类型。

**类型：** [PhotoType](arkts-medialibrary-sendablephotoaccesshelper-phototype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uri

```TypeScript
readonly uri: string
```

媒体文件资源URI（如：file://media/Photo/1/IMG_datetime_0001/displayName.jpg），详情参见用户文件URI介绍中的[媒体文件URI](../../../file-management/user-file-uri-intro.md#媒体文件uri)。服务中使用。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
