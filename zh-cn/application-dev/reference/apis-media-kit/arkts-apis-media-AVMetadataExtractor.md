# Interface (AVMetadataExtractor)

> **说明：**
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 11开始支持。

元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过[media.createAVMetadataExtractor](arkts-apis-media-f.md#mediacreateavmetadataextractor11)构建一个AVMetadataExtractor实例。

获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../media/media/avmetadataextractor.md)。

## 导入模块

```ts
import { media } from '@kit.MediaKit';
```

## 属性

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

| 名称                                                | 类型                                                         | 可读 | 可写 | 说明                                                         |
| --------------------------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| fdSrc<sup>11+</sup>                                  | [AVFileDescriptor](arkts-apis-media-i.md#avfiledescriptor9)                       | 是   | 是   | 媒体文件描述，通过该属性设置数据源。在获取元数据之前，必须设置数据源属性，只能设置fdSrc和dataSrc的其中一个。<br/> **使用示例**：<br/>假设一个连续存储的媒体文件，地址偏移:0，字节长度:100。其文件描述为 AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }。<br>**说明：** <br> - 将资源句柄（fd）传递给 AVMetadataExtractor 实例之后，请不要通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个 AVPlayer / AVMetadataExtractor / AVImageGenerator / AVTranscoder。同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致音视频元数据获取异常。 |
| dataSrc<sup>11+</sup>                               | [AVDataSrcDescriptor](arkts-apis-media-i.md#avdatasrcdescriptor10)                | 是   | 是   | 流式媒体资源描述，通过该属性设置数据源。在获取元数据之前，必须设置数据源属性，只能设置fdSrc和dataSrc的其中一个。<br/> 当应用从远端获取音视频媒体文件，在应用未下载完整音视频资源时，可以设置dataSrc提前获取该资源的元数据。|

### setUrlSource<sup>20+</sup>

setUrlSource(url: string, headers?: Record\<string, string>): Promise\<void>

网络点播资源地址描述，通过该接口设置数据源。使用Promise异步回调。只支持获取网络[fetchMetadata](#fetchmetadata11)（元数据）、[fetchFrameByTime](#fetchframebytime20)（缩略图），在获取之前，必须设置媒体资源URL。

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| url | string       | 是   | 媒体资源URL。<br/>1. 支持的视频格式包括：mp4、mpeg-ts、mkv。<br/>2. 支持的音频格式包括：m4a、aac、mp3、ogg、wav、flac、amr。<br/>**支持路径示例**：<br/>1. http网络播放：http\://xx。<br/>2. https网络播放：https\://xx。<br/>**说明：**<br>- 不支持设置hls/dash、直播资源。<br/>- 设置网络资源路径，需[声明权限](../../security/AccessToken/declare-permissions.md)：[ohos.permission.INTERNET](../../security/AccessToken/permissions-for-all.md#ohospermissioninternet)，相关错误码: [201](../errorcode-universal.md)。|
| headers | Record\<string, string> | 否   | 支持访问网络资源HttpHeader自定义。默认为空。|

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 201      | Permission denied, requires internet access permission. Returned by promise.  |
| 5400102  | Operation not allowed, the URL source has already been set and cannot be modified. Returned by promise. |
| 5400108  | Parameter check failed. Returned by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avMetadataExtractor: media.AVMetadataExtractor | undefined = undefined;

media.createAVMetadataExtractor(async (error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor != null) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
    let url = "http://xx";
    let headers: Record<string, string> = {
      "User-Agent" : "User-Agent-Value"
    };
    await avMetadataExtractor.setUrlSource(url, headers).then(() => {
    }).catch((error: BusinessError) => {
      console.error(`Failed to setUrlSource, code: ${error.code} message: ${error.message}`);
    });
  } else {
    console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
  }
});
```

### fetchFrameByTime<sup>20+</sup>

fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise\<image.PixelMap>

获取视频缩略图。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| timeUs | number                   | 是   | 需要获取的缩略图在视频中的时间点，单位为微秒（us）。 |
| options | [AVImageQueryOptions](arkts-apis-media-e.md#avimagequeryoptions12)     | 是   | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-apis-media-i.md#pixelmapparams12)    | 是   | 需要获取的缩略图的格式参数。 |

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| Promise\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)> | Promise对象，返回视频缩略图对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Returned by promise. |
| 5400106  | Unsupported format. Returned by promise.  |
| 5400108  | Parameter check failed. Returned by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let avMetadataExtractor: media.AVMetadataExtractor | undefined = undefined;
let pixel_map : image.PixelMap | undefined = undefined;

// 初始化入参。
let timeUs: number = 0;
let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_PREVIOUS_SYNC;
let param: media.PixelMapParams = {
  width : 300,
  height : 300
};
// 获取缩略图。
media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor != null) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
    avMetadataExtractor.fetchFrameByTime(timeUs, queryOption, param).then((pixelMap: image.PixelMap) => {
      pixel_map = pixelMap;
    }).catch((error: BusinessError) => {
      console.error(`Failed to fetch FrameByTime, error message:${error.message}`);
    });
  } else {
    console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
  }
});
```

## fetchMetadata<sup>11+</sup>

fetchMetadata(callback: AsyncCallback\<AVMetadata>): void

异步方式获取媒体元数据。通过注册回调函数获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| callback | AsyncCallback\<[AVMetadata](arkts-apis-media-i.md#avmetadata11)>       | 是   | 回调函数。异步返回音视频元数据对象（AVMetadata）。|

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Returned by callback. |
| 5400106  | Unsupported format. Returned by callback.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.fetchMetadata((error: BusinessError, metadata: media.AVMetadata) => {
  if (error) {
    console.error(`Failed to fetch Metadata, err = ${JSON.stringify(error)}`);
    return;
  }
  console.info(`Succeeded in fetching Metadata, genre: ${metadata.genre}`);
});
```

## fetchMetadata<sup>11+</sup>

fetchMetadata(): Promise\<AVMetadata>

异步方式获取媒体元数据。通过Promise获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| Promise\<[AVMetadata](arkts-apis-media-i.md#avmetadata11)>  | Promise对象。异步返回音视频元数据对象（AVMetadata）。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Returned by promise. |
| 5400106  | Unsupported format. Returned by promise.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.fetchMetadata().then((metadata: media.AVMetadata) => {
  console.info(`Succeeded in fetching Metadata, genre: ${metadata.genre}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to fetch Metadata, error message:${error.message}`);
});
```

## fetchAlbumCover<sup>11+</sup>

fetchAlbumCover(callback: AsyncCallback\<image.PixelMap>): void

异步方式获取音频专辑封面。通过注册回调函数获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| callback | AsyncCallback\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)>    | 是   | 回调函数。异步返回专辑封面。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Return by callback. |
| 5400106  | Unsupported format. Returned by callback.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let pixel_map : image.PixelMap | undefined = undefined;

avMetadataExtractor.fetchAlbumCover((error: BusinessError, pixelMap: image.PixelMap) => {
  if (error) {
    console.error(`Failed to fetch AlbumCover, error = ${JSON.stringify(error)}`);
    return;
  }
  pixel_map = pixelMap;
});
```

## fetchAlbumCover<sup>11+</sup>

fetchAlbumCover(): Promise\<image.PixelMap>

异步方式获取专辑封面。通过Promise获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| Promise\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)> |  Promise对象。异步返回专辑封面。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Returned by promise. |
| 5400106  | Unsupported format. Returned by promise.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let pixel_map : image.PixelMap | undefined = undefined;

avMetadataExtractor.fetchAlbumCover().then((pixelMap: image.PixelMap) => {
  pixel_map = pixelMap;
}).catch((error: BusinessError) => {
  console.error(`Failed to fetch AlbumCover, error message:${error.message}`);
});
```

## release<sup>11+</sup>

release(callback: AsyncCallback\<void>): void

异步方式释放资源。通过注册回调函数获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| callback | AsyncCallback\<void>                   | 是   |回调函数。当释放资源成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Returned by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.release((error: BusinessError) => {
  if (error) {
    console.error(`Failed to release, err = ${JSON.stringify(error)}`);
    return;
  }
  console.info(`Succeeded in releasing.`);
});
```

## release<sup>11+</sup>

release(): Promise\<void>

异步方式释放资源。通过Promise获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| Promise\<void> | 异步方式释放资源release方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Returned by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.release().then(() => {
  console.info(`Succeeded in releasing.`);
}).catch((error: BusinessError) => {
  console.error(`Failed to release, error message:${error.message}`);
});
```
