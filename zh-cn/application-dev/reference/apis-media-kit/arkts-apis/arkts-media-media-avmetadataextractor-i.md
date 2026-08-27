# AVMetadataExtractor

元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过 [media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md) 构建一个AVMetadataExtractor实例。获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../media/media/avmetadataextractor.md)。

> **说明：**
> 
> - 本Interface首批接口从API version 11开始支持。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## cancelAllFetchFrames

```TypeScript
cancelAllFetchFrames(): void
```

取消正在进行的批量获取缩略图任务（已完成部分不受影响）。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avMetadataExtractor: media.AVMetadataExtractor | undefined = undefined;

media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
    avMetadataExtractor.cancelAllFetchFrames();
  } else {
    console.error(`Failed to create AVMetadataExtractor, code: ${error.code} message: ${error.message}`);
  }
});
```

## fetchAlbumCover

```TypeScript
fetchAlbumCover(callback: AsyncCallback<image.PixelMap>): void
```

获取音频专辑封面。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;image.PixelMap&gt; | 是 | 回调函数。异步返回专辑封面。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  let pixel_map: image.PixelMap | undefined = undefined;

  avMetadataExtractor.fetchAlbumCover((error: BusinessError, pixelMap: image.PixelMap) => {
    if (error) {
      console.error(`Failed to fetch AlbumCover, code: ${error.code} message: ${error.message}`);
      return;
    }
    pixel_map = pixelMap;
  });
}
```

## fetchAlbumCover

```TypeScript
fetchAlbumCover(): Promise<image.PixelMap>
```

获取专辑封面。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;image.PixelMap & gt; | Promise对象。异步返回专辑封面。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  let pixel_map: image.PixelMap | undefined = undefined;

  avMetadataExtractor.fetchAlbumCover().then((pixelMap: image.PixelMap) => {
    pixel_map = pixelMap;
  }).catch((error: BusinessError) => {
    console.error(`Failed to fetch AlbumCover, code:${error.code} message:${error.message}`);
  });
}
```

## fetchFrameByTime

```TypeScript
fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>
```

获取视频缩略图。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | number | 是 | 需要获取的缩略图在视频中的时间点，单位为微秒（us）。 |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;image.PixelMap & gt; | Promise对象，返回视频缩略图对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted.<br>**适用版本：** 23+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;
let pixel_map: image.PixelMap | undefined = undefined;

// 初始化入参。
let timeUs: number = 0;

let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_NEXT_SYNC;

let param: media.PixelMapParams = {
  width: 300,
  height: 300,
};

// 获取缩略图。
media.createAVImageGenerator(async (err: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    generator.fdSrc = await context.resourceManager.getRawFd('H264_AAC.mp4');
    avImageGenerator.fetchFrameByTime(timeUs, queryOption, param).then((pixelMap: image.PixelMap) => {
      pixel_map = pixelMap;
    }).catch((error: BusinessError) => {
      console.error(`Failed to fetch FrameByTime, code: ${error.code}, message: ${error.message}`);
    });
  } else {
    console.error(`Failed to create AVImageGenerator, code: ${err.code}, message: ${err.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let avMetadataExtractor: media.AVMetadataExtractor | undefined = undefined;
let pixelMap: image.PixelMap | undefined = undefined;

// 初始化入参。
let timeUs: number = 0;
let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_PREVIOUS_SYNC;
let param: media.PixelMapParams = {
  width: 300,
  height: 300
};
// 获取缩略图。
media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
    avMetadataExtractor.fetchFrameByTime(timeUs, queryOption, param).then((fetchedPixelMap: image.PixelMap) => {
      pixelMap = fetchedPixelMap;
    }).catch((error: BusinessError) => {
      console.error(`Failed to fetch FrameByTime, code:${error.code} message:${error.message}`);
    });
  } else {
    console.error(`Failed to create AVMetadataExtractor, code: ${error.code} message: ${error.message}`);
  }
});
```

## fetchFrameByTimeWithTimeout

```TypeScript
fetchFrameByTimeWithTimeout(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams,
      timeoutMs: number): Promise<image.PixelMap | undefined>
```

获取视频缩略图，支持设置缩略图获取最大耗时timeoutMs。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | number | 是 | 需要获取的缩略图在视频中的时间点，单位为微秒（μs）。 |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |
| timeoutMs | number | 是 | 获取缩略图的最大等待时间，时间范围为(0, 20000]，单位为毫秒（ms）。在指定的超时时间内未获取缩略图则返回错误码5400104。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;image.PixelMap \ | undefined & gt; | Promise对象，返回视频缩略图对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Operation timeout. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let avMetadataExtractor: media.AVMetadataExtractor | undefined = undefined;
let pixelMap: image.PixelMap | undefined = undefined;

// 初始化入参。
let timeUs: number = 0;
let timeoutMs: number = 3000;
let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_PREVIOUS_SYNC;
let param: media.PixelMapParams = {
  width: 300,
  height: 300
};
// 获取缩略图。
media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
    avMetadataExtractor.fetchFrameByTimeWithTimeout(timeUs, queryOption, param, timeoutMs).then((fetchedPixelMap: image.PixelMap | undefined) => {
      pixelMap = fetchedPixelMap;
    }).catch((error: BusinessError) => {
      console.error(`Failed to fetch FrameByTime, code: ${error.code}, message: ${error.message}`);
    });
  } else {
    console.error(`Failed to create AVMetadataExtractor, code: ${error.code}, message: ${error.message}`);
  }
});
```

## fetchFramesByTimes

```TypeScript
fetchFramesByTimes(timesUs: number[], queryOption: AVImageQueryOptions, param: PixelMapParams,
        callback: OnFrameFetched): void
```

批量获取视频缩略图。使用Callback异步回调。

> **说明：**
> 
> - 先对给定的视频资源进行解码，随后依据提供的参数options和param，从timesUs数组中的每个时间点提取图像帧。
> 
> - 当每一次图像提取完成时，系统将调用回调函数并传递提取结果。请注意，回调函数的执行顺序会与timesUs数组中时间点的先后顺序不一致。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timesUs | number[] | 是 | 需要获取的所有缩略图在视频中的时间点集合。时间单位为微秒（μs），数组长度取值范围为(0, 4096]。 |
| queryOption | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |
| callback | [OnFrameFetched](arkts-media-media-onframefetched-t.md) | 是 | 需要返回的缩略图信息及可能的异常类型。异常类型请参考具体返回的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Fetch timeout, Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. e.g. The size of timesUs is larger than 4096. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext not permitted. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

async function fetchFramesByTimesDemo() {
  // 初始化入参。
  let timesUs: number[] = [0];
  let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_PREVIOUS_SYNC;
  let param: media.PixelMapParams = {
    width: 300,
    height: 300
  };
  // 获取缩略图。
  let avMetadataExtractor = await media.createAVMetadataExtractor();
  if (avMetadataExtractor) {
    console.info('Succeeded in creating AVMetadataExtractor');
    avMetadataExtractor.fetchFramesByTimes(timesUs, queryOption, param, (frameInfo: media.FrameInfo, err: BusinessError) => {
      if (err) {
        console.info(`fetchFramesByTimes callback failed, code: ${err.code} message: ${err.message}`);
        return;
      }
      if (frameInfo != undefined && frameInfo.image != undefined) {
        this.pixelMap = frameInfo.image;
      }});
  }
}
```

## fetchFramesByTimesWithTimeout

```TypeScript
fetchFramesByTimesWithTimeout(timesUs: number[], queryOption: AVImageQueryOptions, param: PixelMapParams,
      timeoutMs: number, callback: OnFrameFetched): void
```

批量获取视频缩略图，支持设置每一帧缩略图获取最大耗时timeoutMs。使用Callback异步回调。

> **说明：**
> 
> - 先对给定的视频资源进行解码，随后依据提供的参数options和param，从timesUs数组中的每个时间点提取图像帧。
> 
> - 当每一次图像提取完成时，系统将调用回调函数并传递提取结果。请注意，回调函数的执行顺序会与timesUs数组中时间点的先后顺序不一致。
> 
> - 超时时间timeoutMs是针对每一帧的获取时间，而非整个批量抽帧流程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timesUs | number[] | 是 | 需要获取的所有缩略图在视频中的时间点集合。时间单位为微秒（μs），数组长度取值范围为(0, 4096]。 |
| queryOption | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |
| timeoutMs | number | 是 | 获取每一帧缩略图的最大等待时间，时间范围为(0, 20000]，单位为毫秒（ms）。对于每一帧缩略图，在指定的超时时间内未获取缩略图则返回错误码5400104。 |
| callback | [OnFrameFetched](arkts-media-media-onframefetched-t.md) | 是 | 需要返回的缩略图信息及可能的异常类型。异常类型请参考具体返回的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Fetch timeout, Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. e.g. The size of timesUs is larger than 4096. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext not permitted. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

async function fetchFramesByTimesDemo() {
  // 初始化入参。
  let timesUs: number[] = [0];
  let timeoutMs: number = 3000;
  let queryOption: media.AVImageQueryOptions = media.AVImageQueryOptions.AV_IMAGE_QUERY_PREVIOUS_SYNC;
  let param: media.PixelMapParams = {
    width: 300,
    height: 300
  };
  // 获取缩略图。
  let avMetadataExtractor = await media.createAVMetadataExtractor();
  if (avMetadataExtractor) {
    console.info('Succeeded in creating AVMetadataExtractor');
    avMetadataExtractor.fetchFramesByTimesWithTimeout(timesUs, queryOption, param, timeoutMs, (frameInfo: media.FrameInfo, err: BusinessError) => {
      if (err) {
        console.error(`fetchFramesByTimes callback failed, code: ${err.code}, message: ${err.message}`);
        return;
      }
      if (frameInfo != undefined && frameInfo.image != undefined) {
        this.pixelMap = frameInfo.image;
      }});
  }
}
```

## fetchMetadata

```TypeScript
fetchMetadata(callback: AsyncCallback<AVMetadata>): void
```

获取媒体元数据。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AVMetadata&gt; | 是 | 回调函数。异步返回音视频元数据对象（AVMetadata）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted.<br>**适用版本：** 23+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  avMetadataExtractor.fetchMetadata((error: BusinessError, metadata: media.AVMetadata) => {
    if (error) {
      console.error(`Failed to fetch Metadata, code: ${error.code} message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in fetching Metadata, genre: ${metadata.genre}`);
  });
}
```

## fetchMetadata

```TypeScript
fetchMetadata(): Promise<AVMetadata>
```

获取媒体元数据。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;AVMetadata & gt; | Promise对象。异步返回音视频元数据对象（AVMetadata）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted.<br>**适用版本：** 23+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  avMetadataExtractor.fetchMetadata().then((metadata: media.AVMetadata) => {
    console.info(`Succeeded in fetching Metadata, genre: ${metadata.genre}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to fetch Metadata, code: ${error.code} message: ${error.message}`);
  });
}
```

## fetchMetadataWithTimeout

```TypeScript
fetchMetadataWithTimeout(timeoutMs: number): Promise<AVMetadata | undefined>
```

获取媒体元数据，支持设置获取最大耗时timeoutMs。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeoutMs | number | 是 | 获取媒体元数据的最大等待时间，时间范围为(0, 20000]，单位为毫秒（ms）。在给定的超时时间内未返回元数据则返回错误码5400104。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;AVMetadata \ | undefined & gt; | Promise对象，异步返回音视频元数据对象（AVMetadata）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Operation timeout. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  let timeoutMs = 3000;
  avMetadataExtractor.fetchMetadataWithTimeout(timeoutMs).then((metadata: media.AVMetadata | undefined) => {
    if (metadata) {
      console.info(`Succeeded in fetching Metadata, genre: ${metadata.genre}`);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to fetch Metadata, code: ${error.code}, message: ${error.message}`);
  });
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放资源。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当释放资源成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.release((err: BusinessError) => {
  if (err == null) {
    console.info('release videorecorder success');
  } else {
    console.error('release videorecorder failed and error is ' + err.message);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

// 释放资源。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release((error: BusinessError) => {
      if (error) {
        console.error(`Failed to release, code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info(`Succeeded in releasing`);
    });
  } else {
    console.error(`Failed to create AVImageGenerator, code: ${err.code}, message: ${err.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  avMetadataExtractor.release((error: BusinessError) => {
    if (error) {
      console.error(`Failed to release, code: ${error.code} message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in releasing.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发除released以外的状态才能调用。
  avPlayer.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in releasing');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in releasing AVRecorder');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.release((err: BusinessError) => {
  if (err) {
    console.error('Failed to release!');
  } else {
    console.info('Succeeded in releasing!');
  }
});
```

## release

```TypeScript
release(): Promise<void>
```

释放资源。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 异步方式释放资源release方法的Promise返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.release().then(() => {
  console.info('release videorecorder success');
}).catch((err: BusinessError) => {
  console.error('release videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

// 释放资源。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release().then(() => {
      console.info(`Succeeded in releasing.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to release, code: ${error.code}, message: ${error.message}`);
    });
  } else {
    console.error(`Failed to create AVImageGenerator, code: ${err.code}, message: ${err.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  if (avMetadataExtractor) {
    avMetadataExtractor.release().then(() => {
      console.info(`Succeeded in releasing.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to release, code: ${error.code} message: ${error.message}`);
    });
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发除released以外的状态才能调用。
  avPlayer.release().then(() => {
    console.info('Succeeded in releasing');
  }, (err: BusinessError) => {
    console.error(`Failed to release. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release().then(() => {
  console.info('Succeeded in releasing AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to release AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testRelease() {
  // 创建录屏实例。
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // 其余流程。

  // 调用release方法。
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.release().then(() => {
      console.info('Succeeded in releasing avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to release avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.release().then(() => {
    console.info('release AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('release AVTranscoder failed and catch error is ' + err.message);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.release().then(() => {
  console.info('Succeeded in releasing');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## setUrlSource

```TypeScript
setUrlSource(url: string, headers?: Record<string, string>): void
```

网络点播资源地址描述，通过该接口设置数据源。只支持获取网络 [fetchMetadata](#fetchmetadata)（元数据）和 [fetchFrameByTime](#fetchframebytime) （缩略图），在获取之前，必须设置媒体资源URL。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 媒体资源URL。 1. 支持的视频格式包括：mp4、mpeg-ts、mkv。 2. 支持的音频格式包括：m4a、aac、mp3、ogg、wav、flac、amr。    **支持路径示例**： 1. http网络播放：`http://xx`。 2. https网络播放：`https://xx`。   **说明：** 不支持设置HLS/Dash、直播资源。 |
| headers | Record & lt;string, string & gt; | 否 | 支持访问网络资源HttpHeader自定义。默认为空。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avMetadataExtractor: media.AVMetadataExtractor | undefined = undefined;

media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
    let url = "http://xx";
    let headers: Record<string, string> = {
      "User-Agent": "User-Agent-Value"
    };
    avMetadataExtractor.setUrlSource(url, headers);
  } else {
    console.error(`Failed to create AVMetadataExtractor, code: ${error.code} message: ${error.message}`);
  }
});
```

## dataSrc

```TypeScript
dataSrc ?: AVDataSrcDescriptor
```

流式媒体资源描述，通过该属性设置数据源。在获取元数据之前，必须设置数据源属性，只能设置fdSrc和dataSrc的其中一个。当应用从远端获取音视频媒体文件，在应用未下载完整音视频资源时，可以设置dataSrc提前获取该资源的元数据。

**类型：** [AVDataSrcDescriptor](arkts-media-media-avdatasrcdescriptor-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## fdSrc

```TypeScript
fdSrc ?: AVFileDescriptor
```

媒体文件描述，通过该属性设置数据源。在获取元数据之前，必须设置数据源属性，只能设置fdSrc和dataSrc的其中一个。  
**使用示例**：假设一个连续存储的媒体文件，地址偏移：0，字节长度：100。其文件描述为AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }。  
**说明：**将资源句柄（fd）传递给AVMetadataExtractor实例之后，不允许通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer/AVMetadataExtractor/ AVImageGenerator/AVTranscoder。同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致音视频元数据获取异常。

**类型：** [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor
