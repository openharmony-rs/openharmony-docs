# Class (SingleFileMovingPhotoUtil)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

合一动态照片是指将图片和视频封装在同一个文件中的动态照片，文件由图片数据和视频数据依次拼接而成，视频数据位于图片数据之后。相比图片和视频分别保存的双文件形式，合一动态照片更便于传输、备份和分享。

本类提供合一动态照片的判断、拆分、合并以及获取视频偏移能力。相关开发指导请参考[使用合一动态照片](../../media/medialibrary/photoAccessHelper-singlefile-movingphoto.md)。

**起始版本：** 26.1.0

## 导入模块

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## isSingleFileMovingPhoto

static isSingleFileMovingPhoto(uri: string): boolean

判断指定URI对应的资产是否为合一动态照片。

**起始版本：** 26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名  | 类型    | 必填 | 说明                       |
| ------- | ------- | ---- | -------------------------- |
| uri | string | 是   | 待判断的资产URI。 |

**返回值：**

| 类型                                    | 说明              |
| --------------------------------------- | ----------------- |
| boolean | 返回判断结果。即uri对应的资产是否为合一动态照片，true表示是，false表示不是。 |

**错误码：**

以下错误码的详细介绍请参见[媒体库错误码](errorcode-medialibrary.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 23800151 | The scenario parameter verification fails. Possible causes:<br>1. The uri is invalid.<br>2. The uri can not be opened. |

**示例：**

```ts
async function example() {
  try {
    let uri: string = 'file://com.example.temptest/data/storage/el2/base/haps/EntryFile.jpg';
    let result: boolean = photoAccessHelper.SingleFileMovingPhotoUtil.isSingleFileMovingPhoto(uri);
    console.info(`isSingleFileMovingPhoto: ${result}`);
  } catch (err) {
    console.error(`isSingleFileMovingPhoto failed, error: ${err.code}, ${err.message}`);
  }
}
```

## unpackingSingleFileMovingPhoto

static unpackingSingleFileMovingPhoto(singleFileMovingPhotoUri: string, outImageParentFolder: string, outVideoParentFolder: string): string[]

将合一动态照片拆分为一个图片和一个视频。

**起始版本：** 26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名   | 类型   | 必填 | 说明                      |
| -------- | ------ | ---- | ------------------------- |
| singleFileMovingPhotoUri | string | 是   | 合一动态照片URI。 |
| outImageParentFolder | string | 是   | 拆分后生成的图片的输出父目录。 |
| outVideoParentFolder | string | 是   | 拆分后生成的视频的输出父目录。 |

**返回值：**

| 类型                                    | 说明              |
| --------------------------------------- | ----------------- |
| string[] | 返回拆分后生成的图片和视频的路径数组。 |

**错误码：**

以下错误码的详细介绍请参见[媒体库错误码](errorcode-medialibrary.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 23800151 | The scenario parameter verification fails. Possible causes:<br>1. SingleFileMovingPhotoUri, outImageParentFolder, outVideoParentFolder are empty or can not open.<br>2. When saving generated files, a naming conflict occurs after more than 10 attempts.|
| 23800109 | Incorrect file format. |

**示例：**

```ts
async function example() {
  try {
    let singleFileMovingPhotoUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/EntryFile.jpg';
    let outImageParentFolder: string = 'file://com.example.temptest/data/storage/el2/base/haps/images'; // 拆分后生成的图片的输出父目录。
    let outVideoParentFolder: string = 'file://com.example.temptest/data/storage/el2/base/haps/videos'; // 拆分后生成的视频的输出父目录。
    let result: string[] = photoAccessHelper.SingleFileMovingPhotoUtil.unpackingSingleFileMovingPhoto(singleFileMovingPhotoUri, outImageParentFolder, outVideoParentFolder);
    console.info(`unpackingSingleFileMovingPhoto result: ${JSON.stringify(result)}`);
  } catch (err) {
    console.error(`unpackingSingleFileMovingPhoto failed, error: ${err.code}, ${err.message}`);
  }
}
```

## packingSingleFileMovingPhoto

static packingSingleFileMovingPhoto(imageUri: string, videoUri: string, outParentFolder: string): string

将一个图片和一个视频合并为合一动态照片。

**起始版本：** 26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名   | 类型   | 必填 | 说明                      |
| -------- | ------ | ---- | ------------------------- |
| imageUri | string | 是   | 输入的图片URI。 |
| videoUri | string | 是   | 输入的视频URI。 |
| outParentFolder | string | 是   | 输出合一动态照片的父目录。 |

**返回值：**

| 类型                                    | 说明              |
| --------------------------------------- | ----------------- |
| string | 返回生成的合一动态照片路径。 |

**错误码：**

以下错误码的详细介绍请参见[媒体库错误码](errorcode-medialibrary.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 23800151 | The scenario parameter verification fails. Possible causes:<br>1. ImageUri, videoUri and outParentFolder are empty or can not open.<br>2. The image and video formats do not satisfy jpeg/jpg/heic/heif+mp4.<br>3. When saving generated files, a naming conflict occurs after more than 10 attempts. |

**示例：**

```ts
async function example() {
  try {
    let imageUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg';
    let videoUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4';
    let outParentFolder: string = 'file://com.example.temptest/data/storage/el2/base/haps/output';
    let result: string = photoAccessHelper.SingleFileMovingPhotoUtil.packingSingleFileMovingPhoto(imageUri, videoUri, outParentFolder);
    console.info(`packingSingleFileMovingPhoto result: ${result}`);
  } catch (err) {
    console.error(`packingSingleFileMovingPhoto failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getVideoOffset

static getVideoOffset(singleFileMovingPhotoUri: string): number

获取视频在合一动态照片中的偏移量。

**起始版本：** 26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名   | 类型   | 必填 | 说明                      |
| -------- | ------ | ---- | ------------------------- |
| singleFileMovingPhotoUri | string | 是   | 合一动态照片URI。 |

**返回值：**

| 类型                                    | 说明              |
| --------------------------------------- | ----------------- |
| number | 视频在合一动态照片中的偏移量。单位为字节（Byte）。 |

**错误码：**

以下错误码的详细介绍请参见[媒体库错误码](errorcode-medialibrary.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 23800151 | The scenario parameter verification fails. Possible causes:<br>1. The singleFileMovingPhotoUri is empty or can not open.<br>2. The singleFileMovingPhotoUri is belonging to MediaLibrary. |
| 23800109 | Incorrect file format. |

**示例：**

```ts
async function example() {
  try {
    let singleFileMovingPhotoUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/EntryFile.jpg';
    let offset: number = photoAccessHelper.SingleFileMovingPhotoUtil.getVideoOffset(singleFileMovingPhotoUri);
    console.info(`getVideoOffset: ${offset}`);
  } catch (err) {
    console.error(`getVideoOffset failed, error: ${err.code}, ${err.message}`);
  }
}
```
