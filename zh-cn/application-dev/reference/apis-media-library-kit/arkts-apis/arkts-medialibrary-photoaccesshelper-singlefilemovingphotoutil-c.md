# SingleFileMovingPhotoUtil

```TypeScript
class SingleFileMovingPhotoUtil
```

合一动态照片管理类

**起始版本：** 26.1.0

<!--Device-photoAccessHelper-class SingleFileMovingPhotoUtil--><!--Device-photoAccessHelper-class SingleFileMovingPhotoUtil-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getVideoOffset

```TypeScript
static getVideoOffset(singleFileMovingPhotoUri: string): number
```

获取视频在合一动态照片中的偏移量

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SingleFileMovingPhotoUtil-static getVideoOffset(singleFileMovingPhotoUri: string): int--><!--Device-SingleFileMovingPhotoUtil-static getVideoOffset(singleFileMovingPhotoUri: string): int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| singleFileMovingPhotoUri | string | 是 | 合一动态照片uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 视频在合一动态照片中的偏移量 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The singleFileMovingPhotoUri is empty or can not open. <br>2. The singleFileMovingPhotoUri is belonging to MediaLibrary. |
| 23800109 | Incorrect file format. |

## isSingleFileMovingPhoto

```TypeScript
static isSingleFileMovingPhoto(uri: string): boolean
```

判断一个文件是否是合一动态照片

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SingleFileMovingPhotoUtil-static isSingleFileMovingPhoto(uri: string): boolean--><!--Device-SingleFileMovingPhotoUtil-static isSingleFileMovingPhoto(uri: string): boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Input uri. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是合一动态返回true,否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The uri is invalid. <br>2. The uri can not be opened. |

## packingSingleFileMovingPhoto

```TypeScript
static packingSingleFileMovingPhoto(imageUri: string, videoUri: string, outParentFolder: string): string
```

将一张图片和一段视频合并为合一动态照片

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SingleFileMovingPhotoUtil-static packingSingleFileMovingPhoto(imageUri: string, videoUri: string, outParentFolder: string): string--><!--Device-SingleFileMovingPhotoUtil-static packingSingleFileMovingPhoto(imageUri: string, videoUri: string, outParentFolder: string): string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageUri | string | 是 | 输入图片的uri。 |
| videoUri | string | 是 | 输入视频的uri。 |
| outParentFolder | string | 是 | 输出合一动态照片的父目录。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回合一动态照片的路径 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. ImageUri、videoUri and outParentFolder are empty or can not open. <br>2. The image and video formats do not satisfy jpeg/jpg/heic/heif+mp4. <br>3. When saving generated files, a naming conflict occurs after more than 10 attempts. |

## unpackingSingleFileMovingPhoto

```TypeScript
static unpackingSingleFileMovingPhoto(
        singleFileMovingPhotoUri: string, 
        outImageParentFolder: string, 
        outVideoParentFolder: string): string[]
```

拆分合一动态照片为一张图片和一张视频

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SingleFileMovingPhotoUtil-static unpackingSingleFileMovingPhoto(        singleFileMovingPhotoUri: string,         outImageParentFolder: string,         outVideoParentFolder: string): string[]--><!--Device-SingleFileMovingPhotoUtil-static unpackingSingleFileMovingPhoto(        singleFileMovingPhotoUri: string,         outImageParentFolder: string,         outVideoParentFolder: string): string[]-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| singleFileMovingPhotoUri | string | 是 | 合一动态照片。 |
| outImageParentFolder | string | 是 | 图片保存父目录。 |
| outVideoParentFolder | string | 是 | 视频保存父目录。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回图片和视频的路径 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. SingleFileMovingPhotoUri、outImageParentFolder、outVideoParentFolder are empty or can not open. <br>2. When saving generated files, a naming conflict occurs after more than 10 attempts. |
| 23800109 | Incorrect file format. |
