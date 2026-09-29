# AudioLoopback

```TypeScript
interface AudioLoopback
```

This interface provides APIs for audio monitoring.

Before calling any API in AudioLoopback, you must use [audio.createAudioLoopback](arkts-audio-audio-createaudioloopback-f.md) to create an AudioLoopback instance.

When audio loopback is enabled, the system creates a low-latency renderer and capturer to implement low-latency in- ear monitoring. The audio captured is routed back to the renderer through an internal path. The renderer follows the audio focus strategy for [STREAM_USAGE_MUSIC](arkts-audio-audio-streamusage-e.md), whereas the capturer follows the strategy for [SOURCE_TYPE_MIC](arkts-audio-audio-sourcetype-e.md).

The system automatically chooses the input and output devices. If these devices do not support low latency, audio loopback does not work. If another audio stream takes over the audio focus or if the input or output device changes to the one that does not support low latency, the system disables audio loopback automatically.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 20.

**Since:** 20

<!--Device-audio-interface AudioLoopback--><!--Device-audio-interface AudioLoopback-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## enable

```TypeScript
enable(enable: boolean): Promise<boolean>
```

Enable or disable audio loopback. When audio loopback is enabled, the system automatically creates fast playback and recording streams to implement low-latency in-ear monitoring. When audio loopback is disabled, the audio stream is destroyed. If enabling audio loopback fails, you can use [getStatus](#getstatus) to query the cause. After audio loopback is enabled, you can subscribe to the statusChange event to listen for audio loopback status changes.

**Since:** 20

**Required permissions:** ohos.permission.MICROPHONE

<!--Device-AudioLoopback-enable(enable: boolean): Promise<boolean>--><!--Device-AudioLoopback-enable(enable: boolean): Promise<boolean>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable or disable audio loopback. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the API call is successful. **true** is successful, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## getEqualizerPreset

```TypeScript
getEqualizerPreset(): AudioLoopbackEqualizerPreset
```

Gets the current equalizer preset. The default equalizer preset of audio loopback is [FULL](arkts-audio-audio-audioloopbackequalizerpreset-e.md#full) if users do not modify the preset.

**Since:** 21

<!--Device-AudioLoopback-getEqualizerPreset(): AudioLoopbackEqualizerPreset--><!--Device-AudioLoopback-getEqualizerPreset(): AudioLoopbackEqualizerPreset-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioLoopbackEqualizerPreset](arkts-audio-audio-audioloopbackequalizerpreset-e.md) | Equalizer type.<br>If no equalizer type has been set, the default equalizer type is **FULL**. |

## getPreferredDevicePair

```TypeScript
getPreferredDevicePair(): AudioDevicePair | null
```

Gets the preferred audio device pair in current device connection situation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopback-getPreferredDevicePair(): AudioDevicePair | null--><!--Device-AudioLoopback-getPreferredDevicePair(): AudioDevicePair | null-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDevicePair](arkts-audio-audio-audiodevicepair-i.md) &#124; null | The preferred audio device pair in audio system, or null if there is no supported device pair. |

## getReverbPreset

```TypeScript
getReverbPreset(): AudioLoopbackReverbPreset
```

Get the current reverberation. The default reverberation preset of audio loopback is [THEATER](arkts-audio-audio-audioloopbackreverbpreset-e.md#theater) if users do not modify the preset.

**Since:** 21

<!--Device-AudioLoopback-getReverbPreset(): AudioLoopbackReverbPreset--><!--Device-AudioLoopback-getReverbPreset(): AudioLoopbackReverbPreset-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioLoopbackReverbPreset](arkts-audio-audio-audioloopbackreverbpreset-e.md) | Reverb mode.<br>If no reverb mode has been set, the default reverb mode is **THEATER**. |

## getStatus

```TypeScript
getStatus(): Promise<AudioLoopbackStatus>
```

Obtains the audio loopback status. This API uses a promise to return the result.

**Since:** 20

<!--Device-AudioLoopback-getStatus(): Promise<AudioLoopbackStatus>--><!--Device-AudioLoopback-getStatus(): Promise<AudioLoopbackStatus>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioLoopbackStatus](arkts-audio-audio-audioloopbackstatus-e.md)&gt; | Promise used to return the audio loopback status. |

## getSupportedDevicePairs

```TypeScript
getSupportedDevicePairs(): Array<AudioDevicePair>
```

Gets supported audio device pairs in current device connection situation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopback-getSupportedDevicePairs(): Array<AudioDevicePair>--><!--Device-AudioLoopback-getSupportedDevicePairs(): Array<AudioDevicePair>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AudioDevicePair](arkts-audio-audio-audiodevicepair-i.md)&gt; | Audio device pairs that support loopback, if there is no supported device pair, empty array will be returned. |

## getVolume

```TypeScript
getVolume(): number
```

Gets the output volume for audio loopback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopback-getVolume(): double--><!--Device-AudioLoopback-getVolume(): double-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| number | Current audio loopback output volume value. |

## off('statusChange')

```TypeScript
off(type: 'statusChange', callback?: Callback<AudioLoopbackStatus>): void
```

Unsubscribes from the audio loopback status event. This API uses an asynchronous callback to return the result.

**Since:** 20

<!--Device-AudioLoopback-off(type: 'statusChange', callback?: Callback<AudioLoopbackStatus>): void--><!--Device-AudioLoopback-off(type: 'statusChange', callback?: Callback<AudioLoopbackStatus>): void-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'statusChange' | Yes | Event type. The event **'statusChange'** is triggered when the status of the audio loopback is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioLoopbackStatus](arkts-audio-audio-audioloopbackstatus-e.md)&gt; | No | Callback used to return the audio loopback status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## on('statusChange')

```TypeScript
on(type: 'statusChange', callback: Callback<AudioLoopbackStatus>): void
```

Subscribes to the audio loopback status change event, which is triggered when the status of the audio loopback is changed. This API uses an asynchronous callback to return the result.

**Since:** 20

<!--Device-AudioLoopback-on(type: 'statusChange', callback: Callback<AudioLoopbackStatus>): void--><!--Device-AudioLoopback-on(type: 'statusChange', callback: Callback<AudioLoopbackStatus>): void-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'statusChange' | Yes | Event type. The event **'statusChange'** is triggered when the status of the audio loopback is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioLoopbackStatus](arkts-audio-audio-audioloopbackstatus-e.md)&gt; | Yes | Callback used to return the audio loopback status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## setEqualizerPreset

```TypeScript
setEqualizerPreset(preset: AudioLoopbackEqualizerPreset): boolean
```

Sets the equalizer preset of the audio loopback.

**Since:** 21

<!--Device-AudioLoopback-setEqualizerPreset(preset: AudioLoopbackEqualizerPreset): boolean--><!--Device-AudioLoopback-setEqualizerPreset(preset: AudioLoopbackEqualizerPreset): boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| preset | [AudioLoopbackEqualizerPreset](arkts-audio-audio-audioloopbackequalizerpreset-e.md) | Yes | Equalizer type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Setting result. **true** if successful, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## setReverbPreset

```TypeScript
setReverbPreset(preset: AudioLoopbackReverbPreset): boolean
```

Sets the reverberation of the audio loopback.

**Since:** 21

<!--Device-AudioLoopback-setReverbPreset(preset: AudioLoopbackReverbPreset): boolean--><!--Device-AudioLoopback-setReverbPreset(preset: AudioLoopbackReverbPreset): boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| preset | [AudioLoopbackReverbPreset](arkts-audio-audio-audioloopbackreverbpreset-e.md) | Yes | Reverb mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Setting result. **true** if successful, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## setVolume

```TypeScript
setVolume(volume: number): Promise<void>
```

Sets the volume for audio loopback. This volume does not affect other audio streams or the system volume.

**Since:** 20

<!--Device-AudioLoopback-setVolume(volume: double): Promise<void>--><!--Device-AudioLoopback-setVolume(volume: double): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volume | number | Yes | Volume to set. The value type is float, ranging from 0.0 to 1.0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, from 0.0 to 1.0. |
