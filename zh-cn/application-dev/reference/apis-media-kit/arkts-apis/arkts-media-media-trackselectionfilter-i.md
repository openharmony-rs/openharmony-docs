# TrackSelectionFilter

Describes the filter conditions for track selection.

**起始版本：** 26.0.0

<!--Device-media-interface TrackSelectionFilter--><!--Device-media-interface TrackSelectionFilter-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## maxAudioBitrate

```TypeScript
maxAudioBitrate?: number
```

Maximum allowed audio bitrate.The value should be an integer.Value constraint:The value must be a positive integer (greater than 0).<br>Unit:bit/s.Default value:If this parameter is not set, the maximum audio bitrate is not limited.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-maxAudioBitrate?: int--><!--Device-TrackSelectionFilter-maxAudioBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## maxAudioChannels

```TypeScript
maxAudioChannels?: number
```

Maximum allowed audio channel count.The value should be an integer.Value constraint:The value must be a positive integer.<br>Default value:If this parameter is not specified, the number of audio channels is not limited.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-maxAudioChannels?: int--><!--Device-TrackSelectionFilter-maxAudioChannels?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## maxVideoBitrate

```TypeScript
maxVideoBitrate?: number
```

Maximum allowed video bitrate.The value should be an integer.Value constraint:The value must be a positive integer.<br>Unit:Bits/sec.Default value:If this parameter is not specified, the maximum video bitrate is not limited.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-maxVideoBitrate?: int--><!--Device-TrackSelectionFilter-maxVideoBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## maxVideoFrameRate

```TypeScript
maxVideoFrameRate?: number
```

Maximum allowed video frame rate.The value should be an integer.Value constraint:The value must be a positive integer.<br>Unit:frame/sec.Default value:If not specified, the maximum video frame rate is not limited.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-maxVideoFrameRate?: int--><!--Device-TrackSelectionFilter-maxVideoFrameRate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## maxVideoResolution

```TypeScript
maxVideoResolution?: VideoSize
```

Maximum allowed video resolution.<br>Default value:If not specified, the maximum video resolution is not limited.

**类型：** VideoSize

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-maxVideoResolution?: VideoSize--><!--Device-TrackSelectionFilter-maxVideoResolution?: VideoSize-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## minAudioBitrate

```TypeScript
minAudioBitrate?: number
```

Minimum allowed audio bitrate.The value should be an integer.Value constraint:The value must be a positive integer.<br>Unit:Bits/sec.Default value:If this parameter is not set, the minimum audio bitrate is not limited.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-minAudioBitrate?: int--><!--Device-TrackSelectionFilter-minAudioBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## minVideoBitrate

```TypeScript
minVideoBitrate?: number
```

Minimum allowed video bitrate.The value should be an integer.Value constraint:The value must be a positive integer.<br>Unit:Bits/sec.Default value:If no value is assigned, the minimum video bitrate is not limited.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-minVideoBitrate?: int--><!--Device-TrackSelectionFilter-minVideoBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## minVideoFrameRate

```TypeScript
minVideoFrameRate?: number
```

Minimum allowed video frame rate.The value should be an integer.Value constraint:The value must be a positive integer.<br>Unit:frame/sec.Default value:If not specified, the minimum frame rate is not specified.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-minVideoFrameRate?: int--><!--Device-TrackSelectionFilter-minVideoFrameRate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## minVideoResolution

```TypeScript
minVideoResolution?: VideoSize
```

Minimum allowed video resolution.<br>Default value:If not specified, the minimum video resolution is not limited.

**类型：** VideoSize

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-minVideoResolution?: VideoSize--><!--Device-TrackSelectionFilter-minVideoResolution?: VideoSize-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredAudioLanguages

```TypeScript
preferredAudioLanguages?: Array<string>
```

The preferred languages for audio tracks.Multiple languages are arranged in the order of the array, with priorities in descending order.Value constraint:Language strings comply with the IETF BCP 47 definition.<br>Default value:If this parameter is not specified or the array is empty, the audio language is not restricted.

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-preferredAudioLanguages?: Array<string>--><!--Device-TrackSelectionFilter-preferredAudioLanguages?: Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredAudioMimeTypes

```TypeScript
preferredAudioMimeTypes?: Array<string>
```

Indicates the preferred encoding MIME type of the audio track.Multiple MIMEs are arranged in the order of the array, with priorities in descending order.Value constraint:Format as a MIME string or a codec string in HLS or DASH.<br>Default value:If not specified or an empty array is set, the MIME type of the audio is not restricted.

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-preferredAudioMimeTypes?: Array<string>--><!--Device-TrackSelectionFilter-preferredAudioMimeTypes?: Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredSubtitleLanguages

```TypeScript
preferredSubtitleLanguages?: Array<string>
```

Preferred language set for subtitles.Multiple languages are arranged in the order of the array, with priorities in descending order.Value constraint:The language string complies with the IETF BCP 47 definition.<br>Default value:If this parameter is not specified or the array is empty, the subtitle language is not restricted.

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-preferredSubtitleLanguages?: Array<string>--><!--Device-TrackSelectionFilter-preferredSubtitleLanguages?: Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredVideoMimeTypes

```TypeScript
preferredVideoMimeTypes?: Array<string>
```

The preferred sample MIME types for video tracks in order of preference,Multiple MIMEs are arranged in the order of the array, with priorities in descending order.Value constraint:Format as a MIME string or a codec string in HLS or DASH.<br>Default value:If not specified or an empty array is set, the Mime type is not limited.

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrackSelectionFilter-preferredVideoMimeTypes?: Array<string>--><!--Device-TrackSelectionFilter-preferredVideoMimeTypes?: Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

