# createMicInAudioCapturer (System API)

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## createMicInAudioCapturer

```TypeScript
function createMicInAudioCapturer(config: AudioCapturerMicInConfig): Promise<AudioCapturer | null>
```

Obtains a special [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) instance. This method uses a promise to return the capturer instance. This capture can be used to record both Mic-In audio data and echo reference signal, for application to process algorithm. Mic-In audio data and echo reference signal will be put in one buffer or multiple buffers according to configuration set by application. Capturer is also not allowed to be created when application is in background.

**Since:** 23

**Required permissions:** ohos.permission.MICROPHONE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md) | Yes | Capturer configuration, see [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md) for details. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md) &#124; null&gt; | Promise used to return the audio capturer instance, or null if any error occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied, including background recording. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Capturer creation is not supported, may caused by following problems: <br> 1. Source type is unsupported for this capturer, only [SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT](arkts-audio-audio-sourcetype-e-sys.md#source_type_unprocessed_voice_assistant) is supported currently. <br> 2. Echo reference signal's config is unsupported, echo reference's sampling rate and format must be the same as MicIn audio data currently. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio system internal error, such as system process crash. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioEcStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
  channels: audio.AudioChannel.CHANNEL_2, // Channel.
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT, // Audio source type: microphone. The value of SourceType must be SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT.
  capturerFlags: 0 // AudioCapturer flag.
};

let audioMicInStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
  channels: audio.AudioChannel.CHANNEL_2, // Channel.
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
};

let audioCapturerMicInConfig: audio.AudioCapturerMicInConfig = {
  ecStreamInfo: audioEcStreamInfo,
  capturerInfo: audioCapturerInfo,
  micInStreamInfo: audioMicInStreamInfo
};

let audioCapturer: audio.AudioCapturer | null = null;

audio.createMicInAudioCapturer(audioCapturerMicInConfig).then((data) => {
  audioCapturer = data;
  console.info('AudioCapturer Created : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`AudioCapturer Created : ERROR : ${err}`);
});
```
