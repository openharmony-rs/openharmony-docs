# 使用合一动态照片
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

从API版本26.1.0开始，支持合一动态照片能力，包括合一动态照片的判断、加载、拆分、合并以及视频偏移量获取。

动态照片是一种结合了图片和视频的照片形式，可以显示一小段时间的动态画面和声音。媒体库中的动态照片以图片和视频两个文件的形式保存，通过资产URI关联二者，称为双文件动态照片。

合一动态照片（Single File Moving Photo）是将图片和视频封装在同一个文件中形成的动态照片文件。文件由图片数据和视频数据依次拼接而成，视频数据位于图片数据之后，因此只要知道图片数据的长度（即视频数据的起始偏移量），就可以从文件中分别解析出图片和视频。

与双文件动态照片相比，合一动态照片有以下特点：

- **单文件存储**：一次读写即可完成图片和视频的搬运，不会出现图片和视频分离或错配的情况。
- **便于传输与分享**：可直接通过文件通道、网络请求等通用文件能力上传、下载和转发，无需额外维护图片与视频的对应关系。
- **可拆分与合并**：既能拆分为图片和视频分别处理，也能将图片和视频重新封装为合一动态照片。
- **可播放**：可加载为[MovingPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MovingPhoto.md)对象，用于播放和读取图片、视频内容。

合一动态照片支持的图片格式为JPEG（jpg/jpeg）或HEIF（heic/heif），视频格式为MP4。

## 场景介绍

- **动态照片分享与传输**：社交、即时通信类应用需要将动态照片上传到服务端或转发给其他用户时，使用合一动态照片可以按普通文件上传，避免分别传输图片和视频带来的同步问题。
- **动态照片备份与迁移**：将动态照片导出为单个文件保存到应用沙箱或外部存储，便于用户备份、迁移和恢复。
- **动态照片播放**：将本地合一动态照片加载为MovingPhoto对象，配合[MovingPhotoView](movingphotoview-guidelines.md)播放动态效果。
- **动态照片编辑与合成**：拆分合一动态照片，对图片或视频单独进行处理（如裁剪、转码、添加水印）后，再合并为新的合一动态照片。
- **自定义文件解析**：需要读取合一动态照片文件中视频数据时，通过视频偏移量定位视频数据的起始位置。

## 接口说明

| 接口 | 说明 |
| ---- | ---- |
| [isSingleFileMovingPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-SingleFileMovingPhotoUtil.md#issinglefilemovingphoto) | 判断指定URI对应的资产是否为合一动态照片。 |
| [loadSingleFileMovingPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetManager.md#loadsinglefilemovingphoto) | 加载合一动态照片，将其转换为MovingPhoto对象。 |
| [unpackingSingleFileMovingPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-SingleFileMovingPhotoUtil.md#unpackingsinglefilemovingphoto) | 将合一动态照片拆分为一个图片和一个视频。 |
| [packingSingleFileMovingPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-SingleFileMovingPhotoUtil.md#packingsinglefilemovingphoto) | 将一个图片和一个视频合并为合一动态照片。 |
| [getVideoOffset](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-SingleFileMovingPhotoUtil.md#getvideooffset) | 获取视频在合一动态照片中的偏移量。 |

## 开发步骤

对于来源不确定的文件（如从网络下载或从其他应用接收的文件），加载、拆分合一动态照片以及获取视频偏移量前，必须先调用isSingleFileMovingPhoto判断其是否为合一动态照片；返回false时按普通图片处理，不应调用上述三个接口，否则会触发23800109（Incorrect file format）等错误码。

各步骤的前置关系如下：

| 步骤 | 前置步骤 |
| ---- | -------- |
| 判断是否为合一动态照片 | 无 |
| 加载合一动态照片 | 判断是否为合一动态照片 |
| 拆分合一动态照片 | 判断是否为合一动态照片 |
| 合并生成合一动态照片 | 无，输入为独立的图片与视频 |
| 获取视频偏移量 | 判断是否为合一动态照片 |

下文的加载、拆分与获取视频偏移量示例，均在函数入口处调用isSingleFileMovingPhoto完成该前置校验。

### 判断是否为合一动态照片

对于来源不确定的文件（如从网络下载或从其他应用接收的文件），可先调用isSingleFileMovingPhoto判断指定URI对应的资产是否为合一动态照片，再决定后续处理方式。加载、拆分合一动态照片以及获取视频偏移量前，均需先执行本步骤。

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

function checkSingleFileMovingPhoto(uri: string): boolean {
  try {
    let isSingleFileMovingPhoto: boolean =
      photoAccessHelper.SingleFileMovingPhotoUtil.isSingleFileMovingPhoto(uri);
    console.info(`isSingleFileMovingPhoto: ${isSingleFileMovingPhoto}`);
    return isSingleFileMovingPhoto;
  } catch (err) {
    console.error(`Failed to judge single file moving photo. Code: ${err.code}, message: ${err.message}`);
    return false;
  }
}
```

### 加载合一动态照片

前置步骤：调用isSingleFileMovingPhoto确认uri对应的资产为合一动态照片（返回true），再调用loadSingleFileMovingPhoto加载，将其转换为MovingPhoto对象。

获取到MovingPhoto对象后，可用于播放，或通过MovingPhoto.requestContent读取图片和视频内容，具体请参考[读取动态照片资源](photoAccessHelper-movingphoto.md#读取动态照片资源)；播放方式请参考[使用MovingPhotoView播放动态照片](movingphotoview-guidelines.md)。

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

function loadSingleFileMovingPhoto(uri: string): photoAccessHelper.MovingPhoto | undefined {
  try {
    // 前置步骤：加载前判断uri对应的资产是否为合一动态照片。
    if (!photoAccessHelper.SingleFileMovingPhotoUtil.isSingleFileMovingPhoto(uri)) {
      console.error('The uri is not a single file moving photo, skip loading.');
      return undefined;
    }
    let movingPhoto: photoAccessHelper.MovingPhoto =
      photoAccessHelper.MediaAssetManager.loadSingleFileMovingPhoto(uri);
    console.info(`Succeeded in loading single file moving photo, uri: ${movingPhoto.getUri()}`);
    return movingPhoto;
  } catch (err) {
    console.error(`Failed to load single file moving photo. Code: ${err.code}, message: ${err.message}`);
    return undefined;
  }
}
```

### 拆分合一动态照片

前置步骤：调用isSingleFileMovingPhoto确认uri对应的资产为合一动态照片（返回true），再调用unpackingSingleFileMovingPhoto将其拆分为一个图片和一个视频，返回包含拆分后生成的图片路径和视频路径的数组，适用于需要对图片或视频单独处理的场景。

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';
import { fileUri } from '@kit.CoreFileKit';

function unpackingSingleFileMovingPhoto(context: common.UIAbilityContext, uri: string): string[] {
  try {
    // 前置步骤：拆分前判断uri对应的资产是否为合一动态照片。
    if (!photoAccessHelper.SingleFileMovingPhotoUtil.isSingleFileMovingPhoto(uri)) {
      console.error('The uri is not a single file moving photo, skip unpacking.');
      return [];
    }
    // 输出目录需提前创建，并有可写权限。
    let imageFolder: string = fileUri.getUriFromPath(context.filesDir + '/unpack/images');
    let videoFolder: string = fileUri.getUriFromPath(context.filesDir + '/unpack/videos');
    let result: string[] =
      photoAccessHelper.SingleFileMovingPhotoUtil.unpackingSingleFileMovingPhoto(uri, imageFolder, videoFolder);
    console.info(`Succeeded in unpacking single file moving photo: ${JSON.stringify(result)}`);
    return result;
  } catch (err) {
    console.error(`Failed to unpack single file moving photo. Code: ${err.code}, message: ${err.message}`);
    return [];
  }
}
```

### 合并生成合一动态照片

调用packingSingleFileMovingPhoto将一个图片和一个视频合并为合一动态照片，返回生成的合一动态照片路径，可用于将编辑后的内容重新封装，或生成用于分享的单文件动态照片。该步骤的输入为独立的图片与视频，不需要执行isSingleFileMovingPhoto前置判断。

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';
import { fileUri } from '@kit.CoreFileKit';

function packingSingleFileMovingPhoto(context: common.UIAbilityContext, imageUri: string, videoUri: string): string {
  try {
    // 输出目录需提前创建，并有可写权限。
    let outParentFolder: string = fileUri.getUriFromPath(context.filesDir + '/pack');
    let result: string =
      photoAccessHelper.SingleFileMovingPhotoUtil.packingSingleFileMovingPhoto(imageUri, videoUri, outParentFolder);
    console.info(`Succeeded in packing single file moving photo, path: ${result}`);
    return result;
  } catch (err) {
    console.error(`Failed to pack single file moving photo. Code: ${err.code}, message: ${err.message}`);
    return '';
  }
}
```

### 获取视频偏移量

前置步骤：调用isSingleFileMovingPhoto确认uri对应的资产为合一动态照片（返回true），再调用getVideoOffset获取视频在合一动态照片中的偏移量，单位为字节（Byte）。当应用需要自行解析文件、直接读取视频数据时，可从该偏移量开始读取。

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { fileIo as fs, fileUri } from '@kit.CoreFileKit';

function readVideoData(uri: string): ArrayBuffer | undefined {
  try {
    // 前置步骤：读取视频数据前判断uri对应的资产是否为合一动态照片。
    if (!photoAccessHelper.SingleFileMovingPhotoUtil.isSingleFileMovingPhoto(uri)) {
      console.error('The uri is not a single file moving photo, skip reading video data.');
      return undefined;
    }
    let offset: number = photoAccessHelper.SingleFileMovingPhotoUtil.getVideoOffset(uri);
    let path: string = fileUri.getPathFromUri(uri);
    let file: fs.File = fs.openSync(path, fs.OpenMode.READ_ONLY);
    let fileSize: number = fs.statSync(file.fd).size;
    let videoData: ArrayBuffer = new ArrayBuffer(fileSize - offset);
    fs.readSync(file.fd, videoData, { offset: offset });
    fs.closeSync(file);
    console.info(`Succeeded in reading video data, offset: ${offset}, size: ${videoData.byteLength}`);
    return videoData;
  } catch (err) {
    console.error(`Failed to read video data. Code: ${err.code}, message: ${err.message}`);
    return undefined;
  }
}
```
