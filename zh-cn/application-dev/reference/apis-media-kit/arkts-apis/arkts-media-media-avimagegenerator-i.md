# AVImageGenerator

视频缩略图获取类，用于从视频资源中获取缩略图。在调用AVImageGenerator的方法前，需要先通过 [createAVImageGenerator()](arkts-media-media-createavimagegenerator-f.md) 构建一个AVImageGenerator实例。 获取视频缩略图的demo可参考：[获取视频缩略图开发指导](../../../media/media/avimagegenerator.md)。 > **说明：** > > - 本Interface首批接口从API version 12开始支持。

**起始版本：** 23

<!--Device-media-interface AVImageGenerator--><!--Device-media-interface AVImageGenerator-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## fetchFrameByTime

```TypeScript
fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams,
      callback: AsyncCallback<image.PixelMap>): void
```

获取视频缩略图。使用callback异步回调。

**起始版本：** 12

<!--Device-AVImageGenerator-fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams,      callback: AsyncCallback<image.PixelMap>): void--><!--Device-AVImageGenerator-fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams,      callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | number | 是 | 需要获取的缩略图在视频中的时间点，单位为微秒（μs）。 |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | 需要获取的缩略图的格式参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | 回调函数。获取缩略图成功时，err为undefined，data为PixelMap实例，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |

## fetchFrameByTime

```TypeScript
fetchFrameByTime(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams,
      callback: AsyncCallback<image.PixelMap | undefined>): void
```

Obtains a video thumbnail. This API uses an asynchronous callback to return the result.

**起始版本：** 23

<!--Device-AVImageGenerator-fetchFrameByTime(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams,      callback: AsyncCallback<image.PixelMap | undefined>): void--><!--Device-AVImageGenerator-fetchFrameByTime(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams,      callback: AsyncCallback<image.PixelMap | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | long | 是 | Time of the video for which a thumbnail is to be obtained, in μs. |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | Relationship between the time passed in and the video frame. |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | Format parameters of the thumbnail to be obtained. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap \| undefined&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **PixelMap** instance obtained; otherwise, **err** is an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by callback. |

## fetchFrameByTime

```TypeScript
fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>
```

获取视频缩略图。使用Promise异步回调。

**起始版本：** 12

<!--Device-AVImageGenerator-fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>--><!--Device-AVImageGenerator-fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | number | 是 | 需要获取的缩略图在视频中的时间点，单位为微秒（μs）。 |
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

## fetchFrameByTime

```TypeScript
fetchFrameByTime(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap | undefined>
```

Obtains a video thumbnail. This API uses a promise to return the result.

**起始版本：** 23

<!--Device-AVImageGenerator-fetchFrameByTime(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap | undefined>--><!--Device-AVImageGenerator-fetchFrameByTime(timeUs: long, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | long | 是 | Time of the video for which a thumbnail is to be obtained, in μs. |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | Relationship between the time passed in and the video frame. |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | 是 | Format parameters of the thumbnail to be obtained. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap \| undefined&gt; | Promise used to return the video thumbnail. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |

## fetchScaledFrameByTime

```TypeScript
fetchScaledFrameByTime(timeUs: number, queryMode: AVImageQueryOptions, outputSize?: OutputSize):
      Promise<image.PixelMap>
```

支持按比例缩放提取视频缩略图。使用Promise异步回调。

**起始版本：** 20

<!--Device-AVImageGenerator-fetchScaledFrameByTime(timeUs: number, queryMode: AVImageQueryOptions, outputSize?: OutputSize):      Promise<image.PixelMap>--><!--Device-AVImageGenerator-fetchScaledFrameByTime(timeUs: number, queryMode: AVImageQueryOptions, outputSize?: OutputSize):      Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | number | 是 | 在视频中需要获取的缩略图的时间点，单位为微秒（μs）。 |
| queryMode | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | 需要获取的缩略图时间点与视频帧的对应关系。 |
| outputSize | [OutputSize](arkts-media-media-outputsize-i.md) | 否 | 定义帧的输出大小。默认按原图大小显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise对象。返回视频缩略图对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) |  |
| [5400106](../errorcode-media.md#5400106-不支持的规格) |  |

## fetchScaledFrameByTime

```TypeScript
fetchScaledFrameByTime(timeUs: long, queryMode: AVImageQueryOptions, outputSize?: OutputSize):
      Promise<image.PixelMap | undefined>
```

Supports extracting video thumbnails by proportional scaling

**起始版本：** 23

<!--Device-AVImageGenerator-fetchScaledFrameByTime(timeUs: long, queryMode: AVImageQueryOptions, outputSize?: OutputSize):      Promise<image.PixelMap | undefined>--><!--Device-AVImageGenerator-fetchScaledFrameByTime(timeUs: long, queryMode: AVImageQueryOptions, outputSize?: OutputSize):      Promise<image.PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeUs | long | 是 | The time expected to fetch picture from the video resource. The unit is microsecond(us). |
| queryMode | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | 是 | Specify how to position the video frame |
| outputSize | [OutputSize](arkts-media-media-outputsize-i.md) | 否 | This field is used to define the output size of frame. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap \| undefined&gt; | Returns the output image object |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) |  |
| [5400106](../errorcode-media.md#5400106-不支持的规格) |  |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放资源。使用callback异步回调。

**起始版本：** 23

<!--Device-AVImageGenerator-release(callback: AsyncCallback<void>): void--><!--Device-AVImageGenerator-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当释放资源成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by callback. |

## release

```TypeScript
release(): Promise<void>
```

释放资源。使用Promise异步回调。

**起始版本：** 23

<!--Device-AVImageGenerator-release(): Promise<void>--><!--Device-AVImageGenerator-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异步方式释放资源release方法的Promise返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Returned by promise. |

## fdSrc

```TypeScript
fdSrc ?: AVFileDescriptor
```

媒体文件描述，通过该属性设置数据源。 **使用示例**： 假设一个连续存储的媒体文件，地址偏移：0，字节长度：100。其文件描述为AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }。 **说明：** 将资源句柄（fd）传递给AVImageGenerator实例之后，不允许通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer/AVMetadataExtractor/ AVImageGenerator/AVTranscoder。同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致视频缩略图数据获取异常。

**类型：** [AVFileDescriptor](arkts-media-multimedia-media-avfiledescriptor-i.md)

**起始版本：** 23

<!--Device-AVImageGenerator-fdSrc ?: AVFileDescriptor--><!--Device-AVImageGenerator-fdSrc ?: AVFileDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

