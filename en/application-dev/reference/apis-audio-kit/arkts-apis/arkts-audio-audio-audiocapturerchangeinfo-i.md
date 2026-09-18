# AudioCapturerChangeInfo

Describes the audio capturer change event.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
readonly capturerInfo: AudioCapturerInfo
```

Audio capturer information.

**Type:** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## deviceDescriptors

```TypeScript
readonly deviceDescriptors: AudioDeviceDescriptors
```

Audio device information.

**Type:** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## muted

```TypeScript
readonly muted?: boolean
```

Whether the audio capturer is muted. **true** if muted, **false** otherwise.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## streamId

```TypeScript
readonly streamId: number
```

Unique ID of an audio stream.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer
