# AVMetadataExtractor

AVMetadataExtractor is a class for metadata retrieval. It provides APIs to obtain metadata and thumbnails from media assets. Before calling any API of AVMetadataExtractor, you must use [media.createAVMetadataExtractor](arkts-media-media-createavmetadataextractor-f.md) to create an AVMetadataExtractor instance.

For details about the demo of obtaining audio or video metadata and video thumbnails, see [Using AVMetadataExtractor to Extract Audio and Video Metadata (ArkTS)](../../../media/media/avmetadataextractor.md).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## getFrameIndexByTime

```TypeScript
getFrameIndexByTime(timeUs: number): Promise<number>
```

Obtains the video frame number corresponding to a video timestamp. Only MP4 video files are supported.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeUs | number | Yes | Video timestamp, in microseconds. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the video frame number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by promise. |

**Examples**

```TypeScript
import { media } from '@kit.MediaKit';
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.getFrameIndexByTime(0).then((index: number) => {
  console.info(`Succeeded getFrameIndexByTime index: ${index}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getFrameIndexByTime ${err.message}`);
})
```

## getTimeByFrameIndex

```TypeScript
getTimeByFrameIndex(index: number): Promise<number>
```

Obtains the video timestamp corresponding to a video frame number. Only MP4 video files are supported.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Video frame number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the timestamp, in microseconds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Returned by promise. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. Returned by promise. |

**Examples**

```TypeScript
import { media } from '@kit.MediaKit';
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.getTimeByFrameIndex(0).then((timeUs: number) => {
  console.info(`Succeeded getTimeByFrameIndex timeUs: ${timeUs}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getTimeByFrameIndex ${err.message}`);
})
```
