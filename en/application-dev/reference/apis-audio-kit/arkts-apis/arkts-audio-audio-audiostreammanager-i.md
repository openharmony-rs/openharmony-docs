# AudioStreamManager

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
