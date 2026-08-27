# AVMetadata

音视频元数据，包含各个元数据字段。

**起始版本：** 11

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

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## albumArtist

```TypeScript
albumArtist?: string
```

专辑的艺术家。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## artist

```TypeScript
artist?: string
```

媒体资源的艺术家。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## author

```TypeScript
author?: string
```

媒体资源的作者。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## composer

```TypeScript
composer?: string
```

媒体资源的作曲家。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## customInfo

```TypeScript
customInfo?: Record<string, string>
```

从moov.meta.list 获取的自定义参数键值映射。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## dateTime

```TypeScript
dateTime?: string
```

媒体资源的创建时间。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## dateTimeFormat

```TypeScript
dateTimeFormat?: string
```

媒体资源的创建时间，按YYYY-MM-DD HH:mm:ss格式输出。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## description

```TypeScript
description?: string
```

媒体资源的描述信息。当前版本为只读参数。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## duration

```TypeScript
duration?: string
```

媒体资源的时长。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## encoder

```TypeScript
encoder?: string
```

用于编码的软件、硬件及其设置的标识符。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## genre

```TypeScript
genre?: string
```

媒体资源的类型或体裁。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hasAudio

```TypeScript
hasAudio?: string
```

媒体资源是否包含音频。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hasVideo

```TypeScript
hasVideo?: string
```

媒体资源是否包含视频。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hdrType

```TypeScript
hdrType?: HdrType
```

媒体资源的HDR类型。不支持AVRecorder设置该属性。

**类型：** HdrType

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## location

```TypeScript
location?: Location
```

视频的地理位置信息。

**类型：** Location

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## mimeType

```TypeScript
mimeType?: string
```

媒体资源的mime类型。不支持AVRecorder设置该属性。 一些示例的mimeType类型包括: "video/mp4", "audio/mp4", "audio/amr-wb"

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## sampleRate

```TypeScript
sampleRate?: string
```

音频的采样率，单位为赫兹（Hz）。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## title

```TypeScript
title?: string
```

媒体资源的标题。当前版本为只读参数。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## trackCount

```TypeScript
trackCount?: string
```

媒体资源的轨道数量。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## tracks

```TypeScript
tracks?: Array<MediaDescription>
```

媒体资源的轨道信息。不支持AVRecorder设置该属性。

**类型：** Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoHeight

```TypeScript
videoHeight?: string
```

视频的高度，单位为像素（px）。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoOrientation

```TypeScript
videoOrientation?: string
```

视频的旋转方向，单位为度（°）。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoWidth

```TypeScript
videoWidth?: string
```

视频的宽度，单位为像素（px）。不支持AVRecorder设置该属性。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor
