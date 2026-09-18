# AudioCapturerMicInConfig (System API)

Describes audio capturer configuration that can capture microphone input (mic-in) audio data before any processing.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
capturerInfo: AudioCapturerInfo
```

Capturer attribute information.

**Type:** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## ecStreamInfo

```TypeScript
ecStreamInfo?: AudioStreamInfo
```

Stream information that describes echo reference signal. If not set this attribute, the capturer will only record Mic-In audio stream.

**Type:** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## micInStreamInfo

```TypeScript
micInStreamInfo: AudioStreamInfo
```

Stream information that describes Mic-In audio stream.

**Type:** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## preferredInputDevice

```TypeScript
preferredInputDevice?: AudioDeviceDescriptor
```

Prefered input device for this audio capturer. The preferred device must be an input device, and the source type in captureInfo must be [SOURCE_TYPE_VOICE_RECOGNITION](arkts-audio-audio-sourcetype-e.md#source_type_voice_recognition), [SOURCE_TYPE_VOICE_TRANSCRIPTION](arkts-audio-audio-sourcetype-e-sys.md#source_type_voice_transcription) or [SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT](arkts-audio-audio-sourcetype-e-sys.md#source_type_unprocessed_voice_assistant), otherwise this parameter will be ignored. If the user does not specify a device, the system will automatically select the recording device for the audio capturer. When the user specifies a preferred device: 1) If the preferred device is online, the current audio capturer may use the preferred device for recording. If the preferred device becomes offline during recording, the system will select another device. 2) If the preferred device is offline, the system will select a recording device. If the preferred device becomes online during recording, it may switch to the preferred device. The user can query the selected device by [getCurrentAudioCapturerChangeInfo](arkts-audio-audio-audiocapturer-i.md#getcurrentaudiocapturerchangeinfo).

**Type:** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## processedStreamInfo

```TypeScript
processedStreamInfo?: AudioStreamInfo
```

Stream information that describes the processed audio stream.

**Type:** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.
