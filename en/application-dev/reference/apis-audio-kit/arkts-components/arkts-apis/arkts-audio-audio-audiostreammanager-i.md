# AudioStreamManager

```TypeScript
interface AudioStreamManager
```

This interface implements audio stream management.

Before calling any API in AudioStreamManager, you must use [getStreamManager](arkts-audio-audio-audiomanager-i.md#getstreammanager) to obtain an AudioStreamManager instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 9.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAudioEffectInfoArray

```TypeScript
getAudioEffectInfoArray(usage: StreamUsage, callback: AsyncCallback<AudioEffectInfoArray>): void
```

Obtains information about the audio effect mode in use. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream usage. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the information about the audio effect mode obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getAudioEffectInfoArray(audio.StreamUsage.STREAM_USAGE_MUSIC, (err: BusinessError, audioEffectInfoArray: audio.AudioEffectInfoArray) => {
  if (err) {
    console.error(`Failed to get audio effect info array. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting effect info array, AudioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
  }
});
```

<a id="getaudioeffectinfoarray-1"></a>

## getAudioEffectInfoArray

```TypeScript
getAudioEffectInfoArray(usage: StreamUsage): Promise<AudioEffectInfoArray>
```

Obtains information about the audio effect mode in use. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream usage. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md)&gt; | Promise used to return the information about the audio effect mode obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getAudioEffectInfoArray(audio.StreamUsage.STREAM_USAGE_MUSIC).then((audioEffectInfoArray: audio.AudioEffectInfoArray) => {
  console.info(`Succeeded in getting effect info array, AudioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get audio effect info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getAudioEffectInfoArraySync

```TypeScript
getAudioEffectInfoArraySync(usage: StreamUsage): AudioEffectInfoArray
```

Obtains information about the audio effect mode in use. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream usage. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md) | Information about the audio effect mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioEffectInfoArray = audioStreamManager.getAudioEffectInfoArraySync(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in getting effect info array, AudioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get audio effect info array. Code: ${error.code}, message: ${error.message}`);
}
```

## getCurrentAudioCapturerInfoArray

```TypeScript
getCurrentAudioCapturerInfoArray(callback: AsyncCallback<AudioCapturerChangeInfoArray>): void
```

Obtains the information about this audio capturer. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The audio capturer information returned by this API may include internal audio recording streams, such as voice
> wakeup and cellular calls.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the audio capturer information obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioCapturerInfoArray((err: BusinessError, audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  if (err) {
    console.error(`Failed to get current audio capturer info array. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting current audio capturer info array, AudioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
  }
});
```

<a id="getcurrentaudiocapturerinfoarray-1"></a>

## getCurrentAudioCapturerInfoArray

```TypeScript
getCurrentAudioCapturerInfoArray(): Promise<AudioCapturerChangeInfoArray>
```

Obtains the information about this audio capturer. This API uses a promise to return the result.

> **NOTE:** 
> 
> The audio capturer information returned by this API may include internal audio recording streams, such as voice
> wakeup and cellular calls.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | Promise used to return the audio capturer information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioCapturerInfoArray().then((audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  console.info(`Succeeded in getting current audio capturer info array, AudioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get current audio capturer info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getCurrentAudioCapturerInfoArraySync

```TypeScript
getCurrentAudioCapturerInfoArraySync(): AudioCapturerChangeInfoArray
```

Obtains the information about this audio capturer. This API returns the result synchronously.

> **NOTE:** 
> 
> The audio capturer information returned by this API may include internal audio recording streams, such as voice
> wakeup and cellular calls.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md) | Audio capturer information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioCapturerChangeInfoArray = audioStreamManager.getCurrentAudioCapturerInfoArraySync();
  console.info(`Succeeded in getting current audio capturer info array, AudioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get current audio capturer info array. Code: ${error.code}, message: ${error.message}`);
}
```

## getCurrentAudioRendererInfoArray

```TypeScript
getCurrentAudioRendererInfoArray(callback: AsyncCallback<AudioRendererChangeInfoArray>): void
```

Obtains the information about this audio renderer. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The audio renderer information returned by this API may include internal audio playback streams, such as
> cellular calls and ultrasonic streams.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the audio renderer information obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioRendererInfoArray((err: BusinessError, audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  if (err) {
    console.error(`Failed to get current audio renderer info array. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting current audio renderer info array, AudioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
  }
});
```

<a id="getcurrentaudiorendererinfoarray-1"></a>

## getCurrentAudioRendererInfoArray

```TypeScript
getCurrentAudioRendererInfoArray(): Promise<AudioRendererChangeInfoArray>
```

Obtains the information about this audio renderer. This API uses a promise to return the result.

> **NOTE:** 
> 
> The audio renderer information returned by this API may include internal audio playback streams, such as
> cellular calls and ultrasonic streams.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | Promise used to return the audio renderer information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioRendererInfoArray().then((audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  console.info(`Succeeded in getting current audio renderer info array, AudioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get current audio renderer info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getCurrentAudioRendererInfoArraySync

```TypeScript
getCurrentAudioRendererInfoArraySync(): AudioRendererChangeInfoArray
```

Obtains the information about this audio renderer. This API returns the result synchronously.

> **NOTE:** 
> 
> The audio renderer information returned by this API may include internal audio playback streams, such as
> cellular calls and ultrasonic streams.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md) | Audio renderer information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray = audioStreamManager.getCurrentAudioRendererInfoArraySync();
  console.info(`Succeeded in getting current audio renderer info array, AudioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get current audio renderer info array. Code: ${error.code}, message: ${error.message}`);
}
```

## isAcousticEchoCancelerSupported

```TypeScript
isAcousticEchoCancelerSupported(sourceType: SourceType): boolean
```

Checks whether the specified audio source type supports echo cancellation.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceType | [SourceType](arkts-audio-audio-sourcetype-e.md) | Yes | Audio source type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether echo cancellation is supported. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isAcousticEchoCancelerSupported = audioStreamManager.isAcousticEchoCancelerSupported(audio.SourceType.SOURCE_TYPE_LIVE);
  console.info(`Succeeded in using isAcousticEchoCancelerSupported function, IsAcousticEchoCancelerSupported: ${isAcousticEchoCancelerSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isAcousticEchoCancelerSupported function. code: ${error.code}, message: ${error.message}`);
}
```

## isActive

```TypeScript
isActive(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void
```

Checks whether a stream is active. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [isStreamActive](#isstreamactive)

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream types. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true** if the stream is active or **false** if not active; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.isActive(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: boolean) => {
if (err) {
  console.error(`Failed to obtain the active status of the stream. ${err}`);
  return;
}
  console.info(`Callback invoked to indicate that the active status of the stream is obtained ${value}.`);
});
```

<a id="isactive-1"></a>

## isActive

```TypeScript
isActive(volumeType: AudioVolumeType): Promise<boolean>
```

Checks whether a stream is active. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [isStreamActive](#isstreamactive)

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream types. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the stream is active. **true** if active, **false** otherwise. |

**Examples**

```TypeScript
audioStreamManager.isActive(audio.AudioVolumeType.MEDIA).then((value: boolean) => {
  console.info(`Promise returned to indicate that the active status of the stream is obtained ${value}.`);
});
```

## isActiveSync

```TypeScript
isActiveSync(volumeType: AudioVolumeType): boolean
```

Checks whether a stream is active. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [isStreamActive](#isstreamactive)

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Yes | Audio stream types. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the stream is active. **true** if active, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value: boolean = audioStreamManager.isActiveSync(audio.AudioVolumeType.MEDIA);
  console.info(`Indicate that the active status of the stream is obtained ${value}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the active status of the stream ${error}.`);
}
```

## isAudioLoopbackSupported

```TypeScript
isAudioLoopbackSupported(mode: AudioLoopbackMode): boolean
```

Checks whether the current system supports the specified audio loopback mode.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AudioLoopbackMode](arkts-audio-audio-audioloopbackmode-e.md) | Yes | Audio loopback mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the audio loopback mode is supported. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isAudioLoopbackSupported = audioStreamManager.isAudioLoopbackSupported(audio.AudioLoopbackMode.HARDWARE);
  console.info(`Succeeded in using isAudioLoopbackSupported function, IsAudioLoopbackSupported: ${isAudioLoopbackSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isAudioLoopbackSupported function. code: ${error.code}, message: ${error.message}`);
}
```

## isDirectPlaybackSupported

```TypeScript
isDirectPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

Return if direct playback is supported for the specific audio stream info and usage type in current device situation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | Yes | reference of stream info structure to describe basic audio format. |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | stream usage type used to decide the audio device and pipe type selection result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if direct playback is supported in this situation. |

**Examples**

```TypeScript
let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isDirectPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`isDirectPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isDirectPlaybackSupported function. code: ${error.code}, message: ${error.message}`);
}
```

## isFastPlaybackSupported

```TypeScript
isFastPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

Return if fast playback is supported for the specific audio stream info and usage type in current device situation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | Yes | reference of stream info structure to describe basic audio format. |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | stream usage type used to decide the audio device and pipe type selection result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if fast playback is supported in this situation. |

**Examples**

```TypeScript
let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isFastPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`isFastPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isFastPlaybackSupported function. code: ${error.code}, message: ${error.message}`);
}
```

## isFastRecordingSupported

```TypeScript
isFastRecordingSupported(streamInfo: AudioStreamInfo, source: SourceType): boolean
```

Return if fast recording is supported for the specific audio stream info and usage type in current device situation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | Yes | reference of stream info structure to describe basic audio format. |
| source | [SourceType](arkts-audio-audio-sourcetype-e.md) | Yes | stream source type used to decide the audio device and pipe type selection result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if fast recording is supported in this situation. |

**Examples**

```TypeScript
let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isFastRecordingSupported(streamInfo, audio.SourceType.SOURCE_TYPE_MIC);
  console.info(`isFastRecordingSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isFastRecordingSupported function. code: ${error.code}, message: ${error.message}`);
}
```

## isIntelligentNoiseReductionEnabledForCurrentDevice

```TypeScript
isIntelligentNoiseReductionEnabledForCurrentDevice(sourceType: SourceType): boolean
```

Checks whether the intelligent noise reduction feature is enabled for the audio stream of the specified source type.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceType | [SourceType](arkts-audio-audio-sourcetype-e.md) | Yes | Audio source type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the intelligent noise reduction feature is enabled. **true** if enabled, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isSupport = audioStreamManager.isIntelligentNoiseReductionEnabledForCurrentDevice(audio.SourceType.SOURCE_TYPE_LIVE);
  console.info(`SourceType: ${audio.SourceType.SOURCE_TYPE_LIVE} intelligent noise reduction enabled is: ${isSupport}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`isIntelligentNoiseReductionEnabledForCurrentDevice ERROR: ${error}`);
}
```

## isMultichannelPlaybackSupported

```TypeScript
isMultichannelPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

Return if multichannel playback is supported for the specific audio stream info and usage type in current device situation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | Yes | reference of stream info structure to describe basic audio format. |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | stream usage type used to decide the audio device and pipe type selection result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if multichannel playback is supported in this situation. |

**Examples**

```TypeScript
let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_3,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_2POINT1
};

try {
  let isSupported = audioStreamManager.isMultichannelPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`isMultichannelPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isMultichannelPlaybackSupported function. code: ${error.code}, message: ${error.message}`);
}
```

## isOffloadPlaybackSupported

```TypeScript
isOffloadPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

Return if offload playback is supported for the specific audio stream info and usage type in current device situation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | Yes | reference of stream info structure to describe basic audio format. |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | stream usage type used to decide the audio device and pipe type selection result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if offload playback is supported in this situation. |

**Examples**

```TypeScript
let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isOffloadPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`isOffloadPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isOffloadPlaybackSupported function. code: ${error.code}, message: ${error.message}`);
}
```

## isRecordingAvailable

```TypeScript
isRecordingAvailable(capturerInfo: AudioCapturerInfo): boolean
```

Checks whether recording can be started based on the audio source type in the audio capturer information.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | Yes | Audio capturer information. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether recording can be started. **true** if recording can be started, **false** otherwise.<br>This API checks whether the specified audio source type in the capturer information can acquire focus. It should be called before starting audio recording to avoid conflicts with existing recording streams. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC,
  capturerFlags: 0
};

let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};

audio.createAudioCapturer(audioCapturerOptions, (err: BusinessError, audioCapturer: audio.AudioCapturer) => {
  if (err) {
    console.error(`Failed to create AudioCapturer. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in creating AudioCapturer.');
    try {
      let isRecordingAvailable = audioStreamManager.isRecordingAvailable(audioCapturerInfo);
      console.info(`Succeeded in using isRecordingAvailable function, IsRecordingAvailable: ${isRecordingAvailable}.`);
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to use isRecordingAvailable function. code: ${error.code}, message: ${error.message}`);
    }
  }
});
```

## isStreamActive

```TypeScript
isStreamActive(streamUsage: StreamUsage): boolean
```

Checks whether a stream is active. This API returns the result synchronously.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | Yes | Audio stream usage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the stream is active. **true** if active, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isStreamActive = audioStreamManager.isStreamActive(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in using isStreamActive function, IsStreamActive: ${isStreamActive}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to use isStreamActive function. code: ${error.code}, message: ${error.message}`);
}
```

## off('audioRendererChange')

```TypeScript
off(type: 'audioRendererChange', callback?: Callback<AudioRendererChangeInfoArray>): void
```

Unsubscribes from the audio renderer change event. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The audio renderer information returned by this API may include internal audio playback streams, such as
> cellular calls and ultrasonic streams.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioRendererChange' | Yes | Event type. The event **'audioRendererChange'** is triggered when the audio playback stream status or device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | No | Callback used to return the audio renderer information.<br>**Since:** 18 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// When there are multiple listeners for this event, you can use audioStreamManager.off('audioRendererChange'); to unregister all of them.
let audioRendererChangeCallback = (audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  console.info(`Succeeded in using on or off function, AudioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
};

audioStreamManager.on('audioRendererChange', audioRendererChangeCallback);

audioStreamManager.off('audioRendererChange', audioRendererChangeCallback);
```

## off('audioCapturerChange')

```TypeScript
off(type: 'audioCapturerChange', callback?: Callback<AudioCapturerChangeInfoArray>): void
```

Unsubscribes from the audio capturer change event. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The audio capturer information returned by this API may include internal audio recording streams, such as voice
> wakeup and cellular calls.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | Yes | Event type. The event **'audioCapturerChange'** is triggered when the audio capturer is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | No | Callback used to return the audio capturer information.<br>**Since:** 18 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// When there are multiple listeners for this event, you can use audioStreamManager.off('audioCapturerChange'); to unregister all of them.
let audioCapturerChangeCallback = (audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) =>  {
  console.info(`Succeeded in using on or off function, AudioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
};

audioStreamManager.on('audioCapturerChange', audioCapturerChangeCallback);

audioStreamManager.off('audioCapturerChange', audioCapturerChangeCallback);
```

## on('audioRendererChange')

```TypeScript
on(type: 'audioRendererChange', callback: Callback<AudioRendererChangeInfoArray>): void
```

Subscribes to the audio renderer change event, which is triggered when the audio playback stream status or device is changed. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The audio renderer information returned by this API may include internal audio playback streams, such as
> cellular calls and ultrasonic streams.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioRendererChange' | Yes | Event type. The event **'audioRendererChange'** is triggered when the audio playback stream status or device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | Yes | Callback used to return the audio renderer information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioStreamManager.on('audioRendererChange',  (audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  console.info(`Succeeded in using on function, AudioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
});
```

## on('audioCapturerChange')

```TypeScript
on(type: 'audioCapturerChange', callback: Callback<AudioCapturerChangeInfoArray>): void
```

Subscribes to the audio capturer change event, which is triggered when the audio recording stream status or device is changed. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The audio capturer information returned by this API may include internal audio recording streams, such as voice
> wakeup and cellular calls.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | Yes | Event type. The event **'audioCapturerChange'** is triggered when the audio recording stream status or device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | Yes | Callback used to return the audio capturer information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioStreamManager.on('audioCapturerChange', (audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) =>  {
  console.info(`Succeeded in using on function, AudioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
});
```
