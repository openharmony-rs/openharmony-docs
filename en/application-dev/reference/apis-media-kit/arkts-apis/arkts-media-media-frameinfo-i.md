# FrameInfo

Defines the frame info when fetch picture form a video.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## actualTimeUs

```TypeScript
actualTimeUs?: number
```

The actual frame time.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## image

```TypeScript
image?: image.PixelMap
```

The image extracted from video.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## requestedTimeUs

```TypeScript
requestedTimeUs: number
```

The requested frame time.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## result

```TypeScript
result: FetchResult
```

The fetch result code - succeed, failed or cancelled.

**Type:** [FetchResult](arkts-media-media-fetchresult-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor
