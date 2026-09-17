# AudioPlayer

AudioPlayer is a class for audio playback management. It provides APIs to manage and play audio. Before calling any API in AudioPlayer, you must use [createAudioPlayer()](arkts-media-media-createaudioplayer-f.md) to create an AudioPlayer instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [media](arkts-media-multimedia-media.md)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## getTrackDescription

```TypeScript
getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void
```

Obtains the audio track information. It can be called only after the **'dataLoad'** event is triggered. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription)(callback: AsyncCallback&lt;Array&lt;MediaDescription&gt;&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the MediaDescription array obtained; otherwise, **err** is an error object. |

## getTrackDescription

```TypeScript
getTrackDescription(): Promise<Array<MediaDescription>>
```

Obtains the audio track information. It can be called only after the **'dataLoad'** event is triggered. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription)()

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Promise used to return a **MediaDescription** array, which records the audio track information. |

## on('bufferingUpdate')

```TypeScript
on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void
```

Subscribes to the audio buffering update event. This API works only under online playback.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onbufferingupdate)(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | Yes | Event type, which is **'bufferingUpdate'** in this case. |
| callback | (infoType: BufferingInfoType, value: number) =&gt; void | Yes | Callback invoked when the event is triggered.<br>The value of [BufferingInfoType](arkts-media-media-bufferinginfotype-e.md) is fixed at **0**. |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

Subscribes to the audio playback events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'play' &#124; 'pause' &#124; 'stop' &#124; 'reset' &#124; 'dataLoad' &#124; 'finish' &#124; 'volumeChange' | Yes | Event type. The following events are supported:<br>- 'play': triggered when the [play()](#play) API is called and audio playback starts.<br>- 'pause': triggered when the [pause()](#pause) API is called and audio playback is paused.<br>- 'stop': triggered when the [stop()](#stop) API is called and audio playback stops.<br>- 'reset': triggered when the [reset()](#reset) API is called and audio playback is reset.<br>- 'dataLoad': triggered when the audio data is loaded, that is, when the **src** property is configured.<br>- 'finish': triggered when the audio playback is finished.<br>- 'volumeChange': triggered when the [setVolume()](#setvolume) API is called and the playback volume is changed. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

Subscribes to the audio playback events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'play' &#124; 'pause' &#124; 'stop' &#124; 'reset' &#124; 'dataLoad' &#124; 'finish' &#124; 'volumeChange' | Yes | Event type. The following events are supported:<br>- 'play': triggered when the [play()](#play) API is called and audio playback starts.<br>- 'pause': triggered when the [pause()](#pause) API is called and audio playback is paused.<br>- 'stop': triggered when the [stop()](#stop) API is called and audio playback stops.<br>- 'reset': triggered when the [reset()](#reset) API is called and audio playback is reset.<br>- 'dataLoad': triggered when the audio data is loaded, that is, when the **src** property is configured.<br>- 'finish': triggered when the audio playback is finished.<br>- 'volumeChange': triggered when the [setVolume()](#setvolume) API is called and the playback volume is changed. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

Subscribes to the audio playback events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'play' &#124; 'pause' &#124; 'stop' &#124; 'reset' &#124; 'dataLoad' &#124; 'finish' &#124; 'volumeChange' | Yes | Event type. The following events are supported:<br>- 'play': triggered when the [play()](#play) API is called and audio playback starts.<br>- 'pause': triggered when the [pause()](#pause) API is called and audio playback is paused.<br>- 'stop': triggered when the [stop()](#stop) API is called and audio playback stops.<br>- 'reset': triggered when the [reset()](#reset) API is called and audio playback is reset.<br>- 'dataLoad': triggered when the audio data is loaded, that is, when the **src** property is configured.<br>- 'finish': triggered when the audio playback is finished.<br>- 'volumeChange': triggered when the [setVolume()](#setvolume) API is called and the playback volume is changed. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

Subscribes to the audio playback events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'play' &#124; 'pause' &#124; 'stop' &#124; 'reset' &#124; 'dataLoad' &#124; 'finish' &#124; 'volumeChange' | Yes | Event type. The following events are supported:<br>- 'play': triggered when the [play()](#play) API is called and audio playback starts.<br>- 'pause': triggered when the [pause()](#pause) API is called and audio playback is paused.<br>- 'stop': triggered when the [stop()](#stop) API is called and audio playback stops.<br>- 'reset': triggered when the [reset()](#reset) API is called and audio playback is reset.<br>- 'dataLoad': triggered when the audio data is loaded, that is, when the **src** property is configured.<br>- 'finish': triggered when the audio playback is finished.<br>- 'volumeChange': triggered when the [setVolume()](#setvolume) API is called and the playback volume is changed. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

Subscribes to the audio playback events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'play' &#124; 'pause' &#124; 'stop' &#124; 'reset' &#124; 'dataLoad' &#124; 'finish' &#124; 'volumeChange' | Yes | Event type. The following events are supported:<br>- 'play': triggered when the [play()](#play) API is called and audio playback starts.<br>- 'pause': triggered when the [pause()](#pause) API is called and audio playback is paused.<br>- 'stop': triggered when the [stop()](#stop) API is called and audio playback stops.<br>- 'reset': triggered when the [reset()](#reset) API is called and audio playback is reset.<br>- 'dataLoad': triggered when the audio data is loaded, that is, when the **src** property is configured.<br>- 'finish': triggered when the audio playback is finished.<br>- 'volumeChange': triggered when the [setVolume()](#setvolume) API is called and the playback volume is changed. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

Subscribes to the audio playback events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'play' &#124; 'pause' &#124; 'stop' &#124; 'reset' &#124; 'dataLoad' &#124; 'finish' &#124; 'volumeChange' | Yes | Event type. The following events are supported:<br>- 'play': triggered when the [play()](#play) API is called and audio playback starts.<br>- 'pause': triggered when the [pause()](#pause) API is called and audio playback is paused.<br>- 'stop': triggered when the [stop()](#stop) API is called and audio playback stops.<br>- 'reset': triggered when the [reset()](#reset) API is called and audio playback is reset.<br>- 'dataLoad': triggered when the audio data is loaded, that is, when the **src** property is configured.<br>- 'finish': triggered when the audio playback is finished.<br>- 'volumeChange': triggered when the [setVolume()](#setvolume) API is called and the playback volume is changed. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

Subscribes to the audio playback events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'play' &#124; 'pause' &#124; 'stop' &#124; 'reset' &#124; 'dataLoad' &#124; 'finish' &#124; 'volumeChange' | Yes | Event type. The following events are supported:<br>- 'play': triggered when the [play()](#play) API is called and audio playback starts.<br>- 'pause': triggered when the [pause()](#pause) API is called and audio playback is paused.<br>- 'stop': triggered when the [stop()](#stop) API is called and audio playback stops.<br>- 'reset': triggered when the [reset()](#reset) API is called and audio playback is reset.<br>- 'dataLoad': triggered when the audio data is loaded, that is, when the **src** property is configured.<br>- 'finish': triggered when the audio playback is finished.<br>- 'volumeChange': triggered when the [setVolume()](#setvolume) API is called and the playback volume is changed. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('timeUpdate')

```TypeScript
on(type: 'timeUpdate', callback: Callback<number>): void
```

Subscribes to the **'timeUpdate'** event. This event is reported every second when the audio playback is in progress.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** on(type: 'timeUpdate', callback: Callback&lt;number&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'timeUpdate' | Yes | Event type, which is **'timeUpdate'** in this case.<br>The **'timeUpdate'** event is triggered when the audio playback starts after an audio playback timestamp update. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback invoked when the event is triggered. The input parameter is the updated timestamp. |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void
```

Subscribes to the audio interruption event. For details, see [audio.InterruptEvent](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptevent-i.md).

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onaudiointerrupt)(type: 'audioInterrupt', callback: Callback&lt;audio.InterruptEvent&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type, which is **'audioInterrupt'** in this case. |
| callback | (info: audio.InterruptEvent) =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to audio playback error events. After an error event is reported, you must handle the event and exit the playback.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onerror)(type: 'error', callback: ErrorCallback)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which is **'error'** in this case.<br>This event is triggered when an error occurs during audio playback. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback invoked when the event is triggered. |

## pause

```TypeScript
pause(): void
```

Pauses audio playback.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [pause](arkts-media-media-avplayer-i.md#pause)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## play

```TypeScript
play(): void
```

Starts to play an audio asset. This API can be called only after the **'dataLoad'** event is triggered.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [play](arkts-media-media-avplayer-i.md#play)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## release

```TypeScript
release(): void
```

Releases the audio playback resources.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [release](arkts-media-media-avplayer-i.md#release)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## reset

```TypeScript
reset(): void
```

Resets the audio asset to be played.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [reset](arkts-media-media-avplayer-i.md#reset)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## seek

```TypeScript
seek(timeMs: number): void
```

Seeks to the specified playback position.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [seek](arkts-media-media-avplayer-i.md#seek)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeMs | number | Yes | Position to seek to, in ms. The value range is [0, duration]. |

## setVolume

```TypeScript
setVolume(vol: number): void
```

Sets the volume.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setVolume](arkts-media-media-avplayer-i.md#setvolume)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| vol | number | Yes | Relative volume. The value ranges from 0.00 to 1.00. The value **1.00** indicates the maximum volume (100%). |

## stop

```TypeScript
stop(): void
```

Stops audio playback.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [stop](arkts-media-media-avplayer-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## audioInterruptMode

```TypeScript
audioInterruptMode?: audio.InterruptMode
```

Audio interruption mode.

**Type:** [audio.InterruptMode](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptmode-e.md)

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [audioInterruptMode](arkts-media-media-avplayer-i.md#audiointerruptmode)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## currentTime

```TypeScript
readonly currentTime: number
```

Current audio playback position, in ms.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [currentTime](arkts-media-media-avplayer-i.md#currenttime)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## duration

```TypeScript
readonly duration: number
```

Audio duration, in ms.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [duration](arkts-media-media-avplayer-i.md#duration)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## fdSrc

```TypeScript
fdSrc: AVFileDescriptor
```

Description of the audio file. This property is required when audio assets of an application are continuously stored in a file.

Assume that a music file that stores continuous music assets consists of the following:

Music 1 (address offset: 0, byte length: 100)

Music 2 (address offset: 101; byte length: 50)

Music 3 (address offset: 151, byte length: 150)

1. To play music 1: AVFileDescriptor { fd = resource handle; offset = 0; length = 100; }
2. To play music 2: AVFileDescriptor { fd = resource handle; offset = 101; length = 50; }
3. To play music 3: AVFileDescriptor { fd = resource handle; offset = 151; length = 150; }

To play an independent music file, use **src=fd://xx**.

**Type:** [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md)

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [fdSrc](arkts-media-media-avplayer-i.md#fdsrc)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## loop

```TypeScript
loop: boolean
```

Whether to loop audio playback. **true** to loop, **false** otherwise.

**Type:** boolean

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [loop](arkts-media-media-avplayer-i.md#loop)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## src

```TypeScript
src: string
```

Audio file URI. The mainstream audio formats (M4A, AAC, MP3, OGG, WAV, and AMR) are supported.

**Example of supported URLs**:

1. FD: fd://xx

![](../../../reference/apis-media-kit/figures/en-us_image_url.png)

2. HTTP: http://xx
3. HTTPS: https://xx
4. HLS: http://xx or https://xx

ohos.permission.READ_MEDIA or ohos.permission.INTERNET

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [url](arkts-media-media-avplayer-i.md#url)

**Required permissions:** ohos.permission.READ_MEDIA or ohos.permission.INTERNET

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

## state

```TypeScript
readonly state: AudioState
```

Audio playback state. This state cannot be used as the condition for triggering the call of **play()**, **pause()**, or **stop()**.

**Type:** [AudioState](arkts-media-media-audiostate-t.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [state](arkts-media-media-avplayer-i.md#state)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer
