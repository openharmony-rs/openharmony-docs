# AudioCapturerOptions

Describes audio capturer configurations.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## playbackCaptureUid

```TypeScript
playbackCaptureUid?: number
```

The target application uid for voice/video communication playback capture. This parameter takes effect only when [MODE_ONLY_VOIP](arkts-audio-audio-audioplaybackcapturemode-e-sys.md#mode_only_voip) is set in [playbackCaptureMode](arkts-audio-audio-audiocaptureroptions-i.md#playbackcapturemode). In other playback capture modes, this parameter is ignored. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

**System API:** This is a system API.

## preferredInputDevice

```TypeScript
preferredInputDevice?: AudioDeviceDescriptor
```

Perfered input device for this audio capturer. The preferredInputDevice must be an input device, and the source type in captureInfo must be SOURCE_TYPE_RECONGITION or [SOURCE_TYPE_VOICE_TRANSCRIPTION](arkts-audio-audio-sourcetype-e-sys.md#source_type_voice_transcription), otherwise this parameter will be ignored. If the user does not specify a device, the system automatically selects the recording device for the audio capturer. When the user specifies a prefer device to create a recongition or transcription recording,

1) If the prefer device is online, the current audiocapturer may use the preferred device for recording; if the prefer device goes offline during operation, the system automatically selects a recording device. 2) If the prefer device is offline, the system automatically selects a recording device; if the prefer device comes online during operation, it may switch to the prefer device for recording. Users can query the device which is in use by [getCurrentAudioCapturerChangeInfo](arkts-audio-audio-audiocapturer-i.md#getcurrentaudiocapturerchangeinfo).

**Type:** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**Since:** 22

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.
