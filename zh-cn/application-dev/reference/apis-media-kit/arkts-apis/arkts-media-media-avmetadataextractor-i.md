# AVMetadataExtractor

元数据获取类，用于从媒体资源中获取元数据、缩略图。在调用AVMetadataExtractor的方法前，需要先通过[media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md#createavmetadataextractor)构建一个AVMetadataExtractor实例。

获取音频或视频元数据、视频缩略图的demo可参考：[使用AVMetadataExtractor提取音视频元数据信息(ArkTS)](../../../media/media/avmetadataextractor.md)。
> **说明：**  
>  
> - 本Interface首批接口从API version 11开始支持。

**起始版本：** 11

<!--Device-media-interface AVMetadataExtractor--><!--Device-media-interface AVMetadataExtractor-End-->

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

<!--Device-AVMetadataExtractor-cancelAllFetchFrames(): void--><!--Device-AVMetadataExtractor-cancelAllFetchFrames(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## fetchAlbumCover

```TypeScript
fetchAlbumCover(callback: AsyncCallback<image.PixelMap>): void
```

获取音频专辑封面。使用callback异步回调。

**起始版本：** 11

<!--Device-AVMetadataExtractor-fetchAlbumCover(callback: AsyncCallback<image.PixelMap>): void--><!--Device-AVMetadataExtractor-fetchAlbumCover(callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;image.PixelMap&gt; | 是 | 回调函数。异步返回专辑封面。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |

## fetchAlbumCover

```TypeScript
fetchAlbumCover(): Promise<image.PixelMap>
```

获取专辑封面。使用Promise异步回调。

**起始版本：** 11

<!--Device-AVMetadataExtractor-fetchAlbumCover(): Promise<image.PixelMap>--><!--Device-AVMetadataExtractor-fetchAlbumCover(): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise对象。异步返回专辑封面。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |

## fetchFrameByTime

```TypeScript
fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>
```

获取视频缩略图。使用Promise异步回调。

**起始版本：** 20

<!--Device-AVMetadataExtractor-fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>--><!--Device-AVMetadataExtractor-fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>-End-->

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
| Promise&lt;image.PixelMap&gt; | Promise对象，返回视频缩略图对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted.<br>**适用版本：** 23+ |

## fetchFrameByTimeWithTimeout

```TypeScript
fetchFrameByTimeWithTimeout(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams,
      timeoutMs: number): Promise<image.PixelMap | undefined>
```

获取视频缩略图，支持设置缩略图获取最大耗时timeoutMs。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMetadataExtractor-fetchFrameByTimeWithTimeout(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams,      timeoutMs: long): Promise<image.PixelMap | undefined>--><!--Device-AVMetadataExtractor-fetchFrameByTimeWithTimeout(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams,      timeoutMs: long): Promise<image.PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | number | 是 | 需要获取的缩略图在视频中的时间点，单位为微秒（μs）。 |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |
| timeoutMs | number | 是 | 获取缩略图的最大等待时间，时间范围为(0, 20000]，单位为毫秒（ms）。<br>在指定的超时时间内未获取缩略图则返回错误码5400104。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap \| undefined&gt; | Promise对象，返回视频缩略图对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Operation timeout. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted. |

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

<!--Device-AVMetadataExtractor-fetchFramesByTimes(timesUs: long[], queryOption: AVImageQueryOptions, param: PixelMapParams,        callback: OnFrameFetched): void--><!--Device-AVMetadataExtractor-fetchFramesByTimes(timesUs: long[], queryOption: AVImageQueryOptions, param: PixelMapParams,        callback: OnFrameFetched): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timesUs | number[] | 是 | 需要获取的所有缩略图在视频中的时间点集合。<br>时间单位为微秒（μs），数组长度取值范围为(0, 4096]。 |
| queryOption | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |
| callback | [OnFrameFetched](arkts-media-media-onframefetched-t.md) | 是 | 需要返回的缩略图信息及可能的异常类型。<br>异常类型请参考具体返回的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Fetch timeout, Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. e.g. The size of timesUs is larger than 4096. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext not permitted. |

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

<!--Device-AVMetadataExtractor-fetchFramesByTimesWithTimeout(timesUs: long[], queryOption: AVImageQueryOptions, param: PixelMapParams,      timeoutMs: long, callback: OnFrameFetched): void--><!--Device-AVMetadataExtractor-fetchFramesByTimesWithTimeout(timesUs: long[], queryOption: AVImageQueryOptions, param: PixelMapParams,      timeoutMs: long, callback: OnFrameFetched): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timesUs | number[] | 是 | 需要获取的所有缩略图在视频中的时间点集合。<br>时间单位为微秒（μs），数组长度取值范围为(0, 4096]。 |
| queryOption | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |
| timeoutMs | number | 是 | 获取每一帧缩略图的最大等待时间，时间范围为(0, 20000]，单位为毫秒（ms）。<br>对于每一帧缩略图，在指定的超时时间内未获取缩略图则返回错误码5400104。 |
| callback | [OnFrameFetched](arkts-media-media-onframefetched-t.md) | 是 | 需要返回的缩略图信息及可能的异常类型。<br>异常类型请参考具体返回的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Fetch timeout, Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. e.g. The size of timesUs is larger than 4096. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext not permitted. |

## fetchMetadata

```TypeScript
fetchMetadata(callback: AsyncCallback<AVMetadata>): void
```

获取媒体元数据。使用callback异步回调。

**起始版本：** 11

<!--Device-AVMetadataExtractor-fetchMetadata(callback: AsyncCallback<AVMetadata>): void--><!--Device-AVMetadataExtractor-fetchMetadata(callback: AsyncCallback<AVMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AVMetadata&gt; | 是 | 回调函数。异步返回音视频元数据对象（AVMetadata）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted.<br>**适用版本：** 23+ |

## fetchMetadata

```TypeScript
fetchMetadata(): Promise<AVMetadata>
```

获取媒体元数据。使用Promise异步回调。

**起始版本：** 11

<!--Device-AVMetadataExtractor-fetchMetadata(): Promise<AVMetadata>--><!--Device-AVMetadataExtractor-fetchMetadata(): Promise<AVMetadata>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVMetadata&gt; | Promise对象。异步返回音视频元数据对象（AVMetadata）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted.<br>**适用版本：** 23+ |

## fetchMetadataWithTimeout

```TypeScript
fetchMetadataWithTimeout(timeoutMs: number): Promise<AVMetadata | undefined>
```

获取媒体元数据，支持设置获取最大耗时timeoutMs。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMetadataExtractor-fetchMetadataWithTimeout(timeoutMs: long): Promise<AVMetadata | undefined>--><!--Device-AVMetadataExtractor-fetchMetadataWithTimeout(timeoutMs: long): Promise<AVMetadata | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeoutMs | number | 是 | 获取媒体元数据的最大等待时间，时间范围为(0, 20000]，单位为毫秒（ms）。<br>在给定的超时时间内未返回元数据则返回错误码5400104。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVMetadata \| undefined&gt; | Promise对象，异步返回音视频元数据对象（AVMetadata）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Operation timeout. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-http明文拦截导致请求不受支持) | Http cleartext traffic is not permitted. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放资源。使用callback异步回调。

**起始版本：** 11

<!--Device-AVMetadataExtractor-release(callback: AsyncCallback<void>): void--><!--Device-AVMetadataExtractor-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当释放资源成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |

## release

```TypeScript
release(): Promise<void>
```

释放资源。使用Promise异步回调。

**起始版本：** 11

<!--Device-AVMetadataExtractor-release(): Promise<void>--><!--Device-AVMetadataExtractor-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异步方式释放资源release方法的Promise返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |

## setUrlSource

```TypeScript
setUrlSource(url: string, headers?: Record<string, string>): void
```

网络点播资源地址描述，通过该接口设置数据源。只支持获取网络[fetchMetadata](arkts-media-media-avmetadataextractor-i.md#fetchmetadata)（元数据）和[fetchFrameByTime](arkts-media-media-avmetadataextractor-i.md#fetchframebytime)（缩略图），在获取之前，必须设置媒体资源URL。

**起始版本：** 20

<!--Device-AVMetadataExtractor-setUrlSource(url: string, headers?: Record<string, string>): void--><!--Device-AVMetadataExtractor-setUrlSource(url: string, headers?: Record<string, string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 媒体资源URL。<br/>1. 支持的视频格式包括：mp4、mpeg-ts、mkv。<br/>2. 支持的音频格式包括：m4a、aac、mp3、ogg、wav、flac、amr。<br/>**支持路径示例**：<br/>1. http网络播放：`http://xx`。<br/>2. https网络播放：`https://xx`。<br/>**说明：** 不支持设置HLS/Dash、直播资源。 |
| headers | Record&lt;string, string&gt; | 否 | 支持访问网络资源HttpHeader自定义。默认为空。 |

## dataSrc

```TypeScript
dataSrc ?: AVDataSrcDescriptor
```

流式媒体资源描述，通过该属性设置数据源。在获取元数据之前，必须设置数据源属性，只能设置fdSrc和dataSrc的其中一个。

当应用从远端获取音视频媒体文件，在应用未下载完整音视频资源时，可以设置dataSrc提前获取该资源的元数据。

**类型：** AVDataSrcDescriptor

**起始版本：** 11

<!--Device-AVMetadataExtractor-dataSrc ?: AVDataSrcDescriptor--><!--Device-AVMetadataExtractor-dataSrc ?: AVDataSrcDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## fdSrc

```TypeScript
fdSrc ?: AVFileDescriptor
```

媒体文件描述，通过该属性设置数据源。在获取元数据之前，必须设置数据源属性，只能设置fdSrc和dataSrc的其中一个。

**使用示例**：

假设一个连续存储的媒体文件，地址偏移：0，字节长度：100。其文件描述为AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }。

**说明：**

将资源句柄（fd）传递给AVMetadataExtractor实例之后，不允许通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer/AVMetadataExtractor/AVImageGenerator/AVTranscoder。同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致音视频元数据获取异常。

**类型：** AVFileDescriptor

**起始版本：** 11

<!--Device-AVMetadataExtractor-fdSrc ?: AVFileDescriptor--><!--Device-AVMetadataExtractor-fdSrc ?: AVFileDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

