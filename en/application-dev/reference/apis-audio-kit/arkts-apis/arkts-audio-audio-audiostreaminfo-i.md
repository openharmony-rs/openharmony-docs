# AudioStreamInfo

Describes audio stream information.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## channelLayout

```TypeScript
channelLayout?: AudioChannelLayout
```

Audio channel layout. The default value is **0x0**.

**Type:** [AudioChannelLayout](arkts-audio-audio-audiochannellayout-e.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## channels

```TypeScript
channels: AudioChannel
```

Number of audio channels.

**Type:** [AudioChannel](arkts-audio-audio-audiochannel-e.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## encodingType

```TypeScript
encodingType: AudioEncodingType
```

Audio encoding type.

**Type:** [AudioEncodingType](arkts-audio-audio-audioencodingtype-e.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## sampleFormat

```TypeScript
sampleFormat: AudioSampleFormat
```

Audio sample format.

**Type:** [AudioSampleFormat](arkts-audio-audio-audiosampleformat-e.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## samplingRate

```TypeScript
samplingRate: AudioSamplingRate | number
```

Audio sampling rate.

**Type:** [AudioSamplingRate](arkts-audio-audio-audiosamplingrate-e.md) &#124; number

**Since:** 8

**Model restriction:** 
- API version 26.0.0 and later: This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Multimedia.Audio.Core
