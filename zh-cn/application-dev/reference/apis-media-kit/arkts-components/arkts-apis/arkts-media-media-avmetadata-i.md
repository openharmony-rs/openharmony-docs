# AVMetadata

```TypeScript
interface AVMetadata
```

音视频元数据，包含各个元数据字段。

**起始版本：** 11

<!--Device-media-interface AVMetadata--><!--Device-media-interface AVMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## album

```TypeScript
album?: string
```

专辑的标题。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-album?: string--><!--Device-AVMetadata-album?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## albumArtist

```TypeScript
albumArtist?: string
```

专辑的艺术家。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-albumArtist?: string--><!--Device-AVMetadata-albumArtist?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## artist

```TypeScript
artist?: string
```

媒体资源的艺术家。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-artist?: string--><!--Device-AVMetadata-artist?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## author

```TypeScript
author?: string
```

媒体资源的作者。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-author?: string--><!--Device-AVMetadata-author?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## composer

```TypeScript
composer?: string
```

媒体资源的作曲家。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-composer?: string--><!--Device-AVMetadata-composer?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## customInfo

```TypeScript
customInfo?: Record<string, string>
```

从moov.meta.list 获取的自定义参数键值映射。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

<!--Device-AVMetadata-customInfo?: Record<string, string>--><!--Device-AVMetadata-customInfo?: Record<string, string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## dateTime

```TypeScript
dateTime?: string
```

媒体资源的创建时间。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-dateTime?: string--><!--Device-AVMetadata-dateTime?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## dateTimeFormat

```TypeScript
dateTimeFormat?: string
```

媒体资源的创建时间，按YYYY-MM-DD HH:mm:ss格式输出。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-dateTimeFormat?: string--><!--Device-AVMetadata-dateTimeFormat?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## description

```TypeScript
description?: string
```

媒体资源的描述信息。当前版本为只读参数。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 23

<!--Device-AVMetadata-description?: string--><!--Device-AVMetadata-description?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## duration

```TypeScript
duration?: string
```

媒体资源的时长。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-duration?: string--><!--Device-AVMetadata-duration?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## encoder

```TypeScript
encoder?: string
```

用于编码的软件、硬件及其设置的标识符。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMetadata-encoder?: string--><!--Device-AVMetadata-encoder?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## genre

```TypeScript
genre?: string
```

媒体资源的类型或体裁。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-genre?: string--><!--Device-AVMetadata-genre?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hasAudio

```TypeScript
hasAudio?: string
```

媒体资源是否包含音频。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-hasAudio?: string--><!--Device-AVMetadata-hasAudio?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hasVideo

```TypeScript
hasVideo?: string
```

媒体资源是否包含视频。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-hasVideo?: string--><!--Device-AVMetadata-hasVideo?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hdrType

```TypeScript
hdrType?: HdrType
```

媒体资源的HDR类型。不支持AVRecorder设置该属性。

**类型：** [HdrType](arkts-media-media-hdrtype-e.md)

**起始版本：** 12

<!--Device-AVMetadata-hdrType?: HdrType--><!--Device-AVMetadata-hdrType?: HdrType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## location

```TypeScript
location?: Location
```

视频的地理位置信息。

**类型：** [Location](arkts-media-media-location-i.md)

**起始版本：** 12

<!--Device-AVMetadata-location?: Location--><!--Device-AVMetadata-location?: Location-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## mimeType

```TypeScript
mimeType?: string
```

媒体资源的mime类型。不支持AVRecorder设置该属性。一些示例的mimeType类型包括: "video/mp4", "audio/mp4", "audio/amr-wb"

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-mimeType?: string--><!--Device-AVMetadata-mimeType?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## sampleRate

```TypeScript
sampleRate?: string
```

音频的采样率，单位为赫兹（Hz）。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-sampleRate?: string--><!--Device-AVMetadata-sampleRate?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## title

```TypeScript
title?: string
```

媒体资源的标题。当前版本为只读参数。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-title?: string--><!--Device-AVMetadata-title?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## trackCount

```TypeScript
trackCount?: string
```

媒体资源的轨道数量。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-trackCount?: string--><!--Device-AVMetadata-trackCount?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## tracks

```TypeScript
tracks?: Array<MediaDescription>
```

媒体资源的轨道信息。不支持AVRecorder设置该属性。

**类型：** Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;

**起始版本：** 20

<!--Device-AVMetadata-tracks?: Array<MediaDescription>--><!--Device-AVMetadata-tracks?: Array<MediaDescription>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoHeight

```TypeScript
videoHeight?: string
```

视频的高度，单位为像素（px）。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-videoHeight?: string--><!--Device-AVMetadata-videoHeight?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoOrientation

```TypeScript
videoOrientation?: string
```

视频的旋转方向，单位为度（°）。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-videoOrientation?: string--><!--Device-AVMetadata-videoOrientation?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoWidth

```TypeScript
videoWidth?: string
```

视频的宽度，单位为像素（px）。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-videoWidth?: string--><!--Device-AVMetadata-videoWidth?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor
