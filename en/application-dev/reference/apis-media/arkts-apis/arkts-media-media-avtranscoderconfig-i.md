# AVTranscoderConfig

```TypeScript
interface AVTranscoderConfig
```

Describes the video transcoding parameters.

**Since:** 12

<!--Device-media-interface AVTranscoderConfig--><!--Device-media-interface AVTranscoderConfig-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## Modules to Import

```TypeScript
```

## audioBitrate

```TypeScript
audioBitrate?: number
```

Bitrate of the output audio, in bit/s. The value range is [1-500000]. The default value is 48 kbit/s.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-audioBitrate?: int--><!--Device-AVTranscoderConfig-audioBitrate?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## audioCodec

```TypeScript
audioCodec?: CodecMimeType
```

Encoding format of the output audio. Currently, only AAC is supported. The default value is **AAC**.

**Type:** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-audioCodec?: CodecMimeType--><!--Device-AVTranscoderConfig-audioCodec?: CodecMimeType-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## audioCodecV2

```TypeScript
audioCodecV2?: CodecMimeType
```

Encoding format of the output audio. If the specified format is not supported, prepare will fail. Default value: AUDIO_AAC.

**Type:** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-AVTranscoderConfig-audioCodecV2?: CodecMimeType--><!--Device-AVTranscoderConfig-audioCodecV2?: CodecMimeType-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## destHDRMode

```TypeScript
destHDRMode?:DestHDRMode
```

Specifies the HDR format of the target file. Default value: SDR.

**Type:** [DestHDRMode](arkts-media-media-desthdrmode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AVTranscoderConfig-destHDRMode?:DestHDRMode--><!--Device-AVTranscoderConfig-destHDRMode?:DestHDRMode-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

Indicates whether to enable B Frame Encoding for reduce file size.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-enableBFrame?: boolean--><!--Device-AVTranscoderConfig-enableBFrame?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## enableStableQualityMode

```TypeScript
enableStableQualityMode?: boolean
```

Whether to enable video encoding policy to quality stable encoding.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AVTranscoderConfig-enableStableQualityMode?: boolean--><!--Device-AVTranscoderConfig-enableStableQualityMode?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## endTime

```TypeScript
endTime?: number
```

Specifies the time when the transcoding ends in the source file. The unit is millisecond. Default value: Default to end of source file.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AVTranscoderConfig-endTime?: int--><!--Device-AVTranscoderConfig-endTime?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## fileFormat

```TypeScript
fileFormat: ContainerFormatType
```

Container format of the output video file. Currently, only MP4 is supported.

**Type:** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-fileFormat: ContainerFormatType--><!--Device-AVTranscoderConfig-fileFormat: ContainerFormatType-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## sqrFactor

```TypeScript
sqrFactor?: number
```

Set the quality parameter in StableQualityMode. The value range is [0, 51]. A smaller value indicates a higher output bit rate and better quality. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AVTranscoderConfig-sqrFactor?: int--><!--Device-AVTranscoderConfig-sqrFactor?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## startTime

```TypeScript
startTime?: number
```

Time point from which the source file is transcoded. The unit is millisecond. Default value: The default value is the beginning of the source file.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AVTranscoderConfig-startTime?: int--><!--Device-AVTranscoderConfig-startTime?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## videoBitrate

```TypeScript
videoBitrate?: number
```

Bitrate of the output video, in bit/s. The default bitrate depends on the resolution of the output video. The default bitrate is 1 Mbit/s for the resolution in the range [240p, 480P], 2 Mbit/s for the range (480P,720P], 4 Mbit/s for the range (720P,1080P], and 8 Mbit/s for 1080p or higher.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-videoBitrate?: int--><!--Device-AVTranscoderConfig-videoBitrate?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## videoCodec

```TypeScript
videoCodec?: CodecMimeType
```

Encoding format of the output video. Currently, only AVC and HEVC are supported. If the source video is in HEVC format, the default value is **HEVC**. Otherwise, the default value is **AVC**.

**Type:** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-videoCodec?: CodecMimeType--><!--Device-AVTranscoderConfig-videoCodec?: CodecMimeType-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## videoFrameHeight

```TypeScript
videoFrameHeight?: number
```

Height of the output video frame, in px. The value range is [240 - 2160]. The default value is the height of the source video frame.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-videoFrameHeight?: int--><!--Device-AVTranscoderConfig-videoFrameHeight?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## videoFrameWidth

```TypeScript
videoFrameWidth?: number
```

Width of the output video frame, in px. The value range is [240 - 3840]. The default value is the width of the source video frame.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-AVTranscoderConfig-videoFrameWidth?: int--><!--Device-AVTranscoderConfig-videoFrameWidth?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder
