# Interface (AVImageGenerator)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zengyawen-->

> **说明：**
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 12开始支持。

视频缩略图获取类，用于从视频资源中获取缩略图。在调用AVImageGenerator的方法前，需要先通过[createAVImageGenerator()](arkts-apis-media-f.md#mediacreateavimagegenerator12)构建一个AVImageGenerator实例。

获取视频缩略图的demo可参考：[获取视频缩略图开发指导](../../media/media/avimagegenerator.md)。

## 导入模块

```ts
import { media } from '@kit.MediaKit';
```

## 属性

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

| 名称                                                | 类型                                                         | 可读 | 可写 | 说明                                                         |
| --------------------------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| fdSrc<sup>12+</sup>                                  | [AVFileDescriptor](arkts-apis-media-i.md#avfiledescriptor9)                       | 是   | 是   | 媒体文件描述，通过该属性设置数据源。<br/> **使用示例**：<br/>假设一个连续存储的媒体文件，地址偏移:0，字节长度:100。其文件描述为 AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }。<br>**说明：** <br> - 将资源句柄（fd）传递给 AVImageGenerator 实例之后，请不要通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个 AVPlayer / AVMetadataExtractor / AVImageGenerator / AVTranscoder。同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致视频缩略图数据获取异常。 |

## fetchFrameByTime<sup>12+</sup>

fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams, callback: AsyncCallback\<image.PixelMap>): void

异步方式获取视频缩略图。通过注册回调函数获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| timeUs | number                   | 是   | 需要获取的缩略图在视频中的时间点，单位为微秒（μs）。 |
| options | [AVImageQueryOptions](arkts-apis-media-e.md#avimagequeryoptions12)     | 是   | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-apis-media-i.md#pixelmapparams12)     | 是   | 需要获取的缩略图的格式参数。 |
| callback | AsyncCallback\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)>   | 是   | 回调函数。获取缩略图成功时，err为undefined，data为PixelMap实例，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Returned by callback. |
| 5400106  | Unsupported format. Returned by callback.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;
let pixel_map : image.PixelMap | undefined = undefined;

// 初始化入参。
let timeUs: number = 0;

let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_NEXT_SYNC;

let param: media.PixelMapParams = {
  width : 300,
  height : 300,
};

// 获取缩略图。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if(generator != null){
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.fetchFrameByTime(timeUs, queryOption, param, (error: BusinessError, pixelMap) => {
      if (error) {
        console.error(`Failed to fetch FrameByTime, err = ${JSON.stringify(error)}`);
        return;
      }
      pixel_map = pixelMap;
    });
  } else {
    console.error(`Failed to creat AVImageGenerator, error message:${err.message}`);
  };
});
```

## fetchFrameByTime<sup>12+</sup>

fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>

异步方式获取视频缩略图。通过Promise获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| timeUs | number                   | 是   | 需要获取的缩略图在视频中的时间点，单位为微秒（μs）。 |
| options | [AVImageQueryOptions](arkts-apis-media-e.md#avimagequeryoptions12)     | 是   | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-apis-media-i.md#pixelmapparams12)    | 是   | 需要获取的缩略图的格式参数。 |

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| Promise\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)> | Promise对象，返回视频缩略图对象。 |

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
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;
let pixel_map : image.PixelMap | undefined = undefined;

// 初始化入参。
let timeUs: number = 0;

let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_NEXT_SYNC;

let param: media.PixelMapParams = {
  width : 300,
  height : 300,
};

// 获取缩略图。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if(generator != null){
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.fetchFrameByTime(timeUs, queryOption, param).then((pixelMap: image.PixelMap) => {
      pixel_map = pixelMap;
    }).catch((error: BusinessError) => {
      console.error(`Failed to fetch FrameByTime, error message:${error.message}`);
    });
  } else {
    console.error(`Failed to creat AVImageGenerator, error message:${err.message}`);
  };
});
```

## fetchScaledFrameByTime<sup>20+</sup>

fetchScaledFrameByTime(timeUs: number, queryMode: AVImageQueryOptions, outputSize?: OutputSize):Promise\<image.PixelMap\>

支持按比例缩放提取视频缩略图。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名     | 类型                                          | 必填 | 说明                                                 |
| ---------- | --------------------------------------------- | ---- | ---------------------------------------------------- |
| timeUs     | number                                        | 是   | 在视频中需要获取的缩略图的时间点，单位为微秒（μs）。 |
| queryMode  | [AVImageQueryOptions](arkts-apis-media-e.md#avimagequeryoptions12) | 是   | 需要获取的缩略图时间点与视频帧的对应关系。           |
| outputSize | [OutputSize ](arkts-apis-media-i.md#outputsize20)                  | 否   | 定义帧的输出大小。默认按原图大小显示。               |

**返回值：**

| 类型                                                         | 说明                              |
| ------------------------------------------------------------ | --------------------------------- |
| Promise\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)> | Promise对象。返回视频缩略图对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 5400102  | Operation not allowed. Returned by promise. |
| 5400106  | Unsupported format. Returned by promise.    |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';
let avImageGenerator: media.AVImageGenerator | undefined = undefined;
let pixel_map : image.PixelMap | undefined = undefined;
// 初始化入参。
let timeUs: number = 0;
let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_NEXT_SYNC;
let outputSize: media.OutputSize = {
  width : 300,
  height : 300,
};
// 获取缩略图。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if(generator != null){
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.fetchScaledFrameByTime(timeUs, queryOption, outputSize).then((pixelMap: image.PixelMap) => {
      pixel_map = pixelMap;
    }).catch((error: BusinessError) => {
      console.error(`Failed to fetch ScaledFrameByTime, error message:${error.message}`);
    });
  } else {
    console.error(`Failed to creat AVImageGenerator, error message:${err.message}`);
  };
});
```

## release<sup>12+</sup>

release(callback: AsyncCallback\<void>): void

异步方式释放资源。通过注册回调函数获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| callback | AsyncCallback\<void>                   | 是   | 回调函数。当释放资源成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Returned by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

//释放资源。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if(generator != null){
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release((error: BusinessError) => {
      if (error) {
        console.error(`Failed to release, err = ${JSON.stringify(error)}`);
        return;
      }
      console.info(`Succeeded in releasing`);
    });
  } else {
    console.error(`Failed to creat AVImageGenerator, error message:${err.message}`);
  };
});
```

## release<sup>12+</sup>

release(): Promise\<void>

异步方式释放资源。通过Promise获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

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
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

//释放资源
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if(generator != null){
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release().then(() => {
      console.info(`Succeeded in releasing.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to release, error message:${error.message}`);
    });
  } else {
    console.error(`Failed to creat AVImageGenerator, error message:${err.message}`);
  };
});
```
