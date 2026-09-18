# AVMetadataExtractor

AVMetadataExtractor is a class for metadata retrieval. It provides APIs to obtain metadata and thumbnails from media assets. Before calling any API of AVMetadataExtractor, you must use [media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md) to create an AVMetadataExtractor instance.

For details about the demo of obtaining audio or video metadata and video thumbnails, see [Using AVMetadataExtractor to Extract Audio and Video Metadata (ArkTS)](../../../media/media/avmetadataextractor.md).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## cancelAllFetchFrames

```TypeScript
cancelAllFetchFrames(): void
```

Cancels the ongoing task of obtaining thumbnails in batches. (The thumbnails that have been obtained are not affected.)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## fetchAlbumCover

```TypeScript
fetchAlbumCover(callback: AsyncCallback<image.PixelMap>): void
```

Obtains the cover of the audio album. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the album cover. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by callback. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by callback. |

## fetchAlbumCover

```TypeScript
fetchAlbumCover(): Promise<image.PixelMap>
```

Obtains the cover of the audio album. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the album cover. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by promise. |

## fetchFrameByTime

```TypeScript
fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise<image.PixelMap>
```

Obtains a video thumbnail. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeUs | number | Yes | Time of the video for which a thumbnail is to be obtained, in us. |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | Yes | Relationship between the time passed in and the video frame. |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | Yes | Format parameters of the thumbnail to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the video thumbnail. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext traffic is not permitted.<br>**Applicable version:** 23 and later |

## fetchFrameByTimeWithTimeout

```TypeScript
fetchFrameByTimeWithTimeout(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams,
      timeoutMs: number): Promise<image.PixelMap | undefined>
```

Obtains a video thumbnail. You can set the maximum timeout interval (**timeoutMs**) for obtaining the thumbnail. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeUs | number | Yes | Time of the video for which a thumbnail is to be obtained, in μs. |
| options | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | Yes | Relationship between the time passed in and the video frame. |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | Yes | Format parameters of the thumbnail to be obtained. |
| timeoutMs | number | Yes | Timeout interval for obtaining the thumbnail. The value range is (0, 20000], in milliseconds.<br>If the thumbnail is not obtained within the specified timeout interval, error code 5400104 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; undefined&gt; | Promise used to return the video thumbnail. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |
| [5400104](../errorcode-media.md#5400104-operation-timeout) | Operation timeout. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext traffic is not permitted. |

## fetchFramesByTimes

```TypeScript
fetchFramesByTimes(timesUs: number[], queryOption: AVImageQueryOptions, param: PixelMapParams,
        callback: OnFrameFetched): void
```

Obtains video thumbnails in batches. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - The given video resource is decoded first, and then image frames are extracted from each time point in the
> **timesUs** array based on the provided **options** and **param**.
> 
> - When each image extraction is complete, the system calls the callback function and passes the extraction result. Note that the execution order of the callback function may be inconsistent with the time points in the
> **timesUs** array.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timesUs | number[] | Yes | Set of time points of all thumbnails to be obtained in the video.<br>The unit is microsecond (μs), and the value range of the array length is (0, 4096]. |
| queryOption | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | Yes | Relationship between the time passed in and the video frame. |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | Yes | Format parameters of the thumbnail to be obtained. |
| callback | [OnFrameFetched](arkts-media-media-onframefetched-t.md) | Yes | Thumbnail information to be returned and possible exception types.<br>For details about the exception types, see the returned error code information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by callback. |
| [5400104](../errorcode-media.md#5400104-operation-timeout) | Fetch timeout, Returned by callback. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. e.g. The size of timesUs is larger than 4096. |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext not permitted. |

## fetchFramesByTimesWithTimeout

```TypeScript
fetchFramesByTimesWithTimeout(timesUs: number[], queryOption: AVImageQueryOptions, param: PixelMapParams,
      timeoutMs: number, callback: OnFrameFetched): void
```

Obtains video thumbnails in batches. You can set the maximum timeout interval (**timeoutMs**) for obtaining each thumbnail. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - The given video resource is decoded first, and then image frames are extracted from each time point in the
> **timesUs** array based on the provided **options** and **param**.
> 
> - When each image extraction is complete, the system calls the callback function and passes the extraction result. Note that the execution order of the callback function may be inconsistent with the time points in the
> **timesUs** array.
> 
> - The **timeoutMs** parameter indicates the maximum timeout interval for obtaining each thumbnail frame, not the entire batch thumbnail extraction process.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timesUs | number[] | Yes | Set of time points of all thumbnails to be obtained in the video.<br>The unit is microsecond (μs), and the value range of the array length is (0, 4096]. |
| queryOption | [AVImageQueryOptions](arkts-media-media-avimagequeryoptions-e.md) | Yes | Relationship between the time passed in and the video frame. |
| param | [PixelMapParams](arkts-media-media-pixelmapparams-i.md) | Yes | Format parameters of the thumbnail to be obtained. |
| timeoutMs | number | Yes | Timeout interval for obtaining each thumbnail. The value range is (0, 20000], in milliseconds.<br>If a thumbnail is not obtained within the specified timeout interval, error code 5400104 is returned. |
| callback | [OnFrameFetched](arkts-media-media-onframefetched-t.md) | Yes | Thumbnail information to be returned and possible exception types.<br>For details about the exception types, see the returned error code information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by callback. |
| [5400104](../errorcode-media.md#5400104-operation-timeout) | Fetch timeout, Returned by callback. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. e.g. The size of timesUs is larger than 4096. |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext not permitted. |

## fetchMetadata

```TypeScript
fetchMetadata(callback: AsyncCallback<AVMetadata>): void
```

Obtains the media metadata. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVMetadata](arkts-media-media-avmetadata-i.md)&gt; | Yes | Callback used to return the result, which is an AVMetadata instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by callback. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by callback. |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext traffic is not permitted.<br>**Applicable version:** 23 and later |

## fetchMetadata

```TypeScript
fetchMetadata(): Promise<AVMetadata>
```

Obtains the media metadata. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVMetadata](arkts-media-media-avmetadata-i.md)&gt; | Promise used to return the result, which is an AVMetadata instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext traffic is not permitted.<br>**Applicable version:** 23 and later |

## fetchMetadataWithTimeout

```TypeScript
fetchMetadataWithTimeout(timeoutMs: number): Promise<AVMetadata | undefined>
```

Obtains the media metadata. You can set the maximum timeout interval (**timeoutMs**) for obtaining the metadata. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeoutMs | number | Yes | Timeout interval for obtaining media metadata. The value range is (0, 20000], in milliseconds.<br>If no metadata is returned within the specified timeout interval, error code 5400104 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVMetadata](arkts-media-media-avmetadata-i.md) &#124; undefined&gt; | Promise used to return the audio and video metadata object (**AVMetadata**) asynchronously. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |
| [5400104](../errorcode-media.md#5400104-operation-timeout) | Operation timeout. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. Returned by promise. |
| [5411012](../errorcode-media.md#5411012-request-not-supported-due-to-http-plaintext-interception) | Http cleartext traffic is not permitted. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this AVMetadataExtractor instance. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by callback. |

## release

```TypeScript
release(): Promise<void>
```

Releases this AVMetadataExtractor instance. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |

## setUrlSource

```TypeScript
setUrlSource(url: string, headers?: Record<string, string>): void
```

Sets the data source for a network on-demand resource. Only network metadata ([fetchMetadata](#fetchmetadata)) and thumbnails ([fetchFrameByTime](#fetchframebytime)) can be obtained. The media resource URL must be set before the retrieval.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the media resource.<br>1. The video formats MP4, MPEG-TS, and MKV are supported.<br>2. The audio formats M4A, AAC, MP3, OGG, WAV, FLAC, and AMR are supported.<br> **Example of supported URLs**:<br>1. HTTP: http://xx<br>2. HTTPS: https://xx<br>Note: HLS/DASH and live streaming resources are not supported. |
| headers | Record&lt;string, string&gt; | No | Custom HTTP headers for accessing the network resource. The default value is empty. |

## dataSrc

```TypeScript
dataSrc ?: AVDataSrcDescriptor
```

Streaming media resource descriptor, which specifies the data source. Before obtaining metadata, you must set the data source through either **fdSrc** or **dataSrc**.

When an application obtains a media file from the remote, you can set **dataSrc** to obtain the metadata before the application finishes the downloading.

**Type:** [AVDataSrcDescriptor](arkts-media-media-avdatasrcdescriptor-i.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## fdSrc

```TypeScript
fdSrc ?: AVFileDescriptor
```

Media file descriptor, which specifies the data source. Before obtaining metadata, you must set the data source through either **fdSrc** or **dataSrc**.

There is a media file that stores continuous assets, the address offset is 0, and the byte length is 100. Its file descriptor is **AVFileDescriptor { fd = resourceHandle; offset = 0; length = 100; }**.

**NOTE:** 

After the resource handle (FD) is transferred to an AVMetadataExtractor instance, do not use the resource handle to perform other read and write operations, including but not limited to transferring this handle to other AVPlayer, AVMetadataExtractor, AVImageGenerator, or AVTranscoder instance. Competition occurs when multiple AVMetadataExtractor use the same resource handle to read and write files at the same time, resulting in errors in obtaining data.

**Type:** [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor
