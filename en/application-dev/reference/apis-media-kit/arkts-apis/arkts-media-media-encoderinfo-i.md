# EncoderInfo

```TypeScript
interface EncoderInfo
```

Describes the information about an encoder.

**Since:** 11

<!--Device-media-interface EncoderInfo--><!--Device-media-interface EncoderInfo-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## bitRate

```TypeScript
bitRate?: Range
```

Bit rate range of the encoder, with the minimum and maximum bit rates specified, in bit/s.

**Type:** [Range](arkts-media-media-range-i.md)

**Since:** 11

<!--Device-EncoderInfo-bitRate?: Range--><!--Device-EncoderInfo-bitRate?: Range-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## channels

```TypeScript
channels?: Range
```

Number of audio channels for the audio capturer, with the minimum and maximum numbers of audio channels specified. This parameter is available only for audio encoders.

**Type:** [Range](arkts-media-media-range-i.md)

**Since:** 11

<!--Device-EncoderInfo-channels?: Range--><!--Device-EncoderInfo-channels?: Range-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## frameRate

```TypeScript
frameRate?: Range
```

Video frame rate range, with the minimum and maximum frame rates specified, in fps. This parameter is available only for video encoders.

**Type:** [Range](arkts-media-media-range-i.md)

**Since:** 11

<!--Device-EncoderInfo-frameRate?: Range--><!--Device-EncoderInfo-frameRate?: Range-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## height

```TypeScript
height?: Range
```

Video frame height range, with the minimum and maximum heights specified, in px. This parameter is available only for video encoders.

**Type:** [Range](arkts-media-media-range-i.md)

**Since:** 11

<!--Device-EncoderInfo-height?: Range--><!--Device-EncoderInfo-height?: Range-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## mimeType

```TypeScript
mimeType: CodecMimeType
```

MIME type of the encoder.

**Type:** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**Since:** 11

<!--Device-EncoderInfo-mimeType: CodecMimeType--><!--Device-EncoderInfo-mimeType: CodecMimeType-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## sampleRate

```TypeScript
sampleRate?: Array<number>
```

Audio sampling rate, including all available audio sampling rates, in Hz. The value depends on the encoder type, and this parameter is available only for audio encoders.

**Type:** Array&lt;number&gt;

**Since:** 11

<!--Device-EncoderInfo-sampleRate?: Array<int>--><!--Device-EncoderInfo-sampleRate?: Array<int>-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## type

```TypeScript
type: string
```

Encoder type. The value **audio** means an audio encoder, and **video** means a video encoder.

**Type:** string

**Since:** 11

<!--Device-EncoderInfo-type: string--><!--Device-EncoderInfo-type: string-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## width

```TypeScript
width?: Range
```

Video frame width range, with the minimum and maximum widths specified, in px. This parameter is available only for video encoders.

**Type:** [Range](arkts-media-media-range-i.md)

**Since:** 11

<!--Device-EncoderInfo-width?: Range--><!--Device-EncoderInfo-width?: Range-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder
