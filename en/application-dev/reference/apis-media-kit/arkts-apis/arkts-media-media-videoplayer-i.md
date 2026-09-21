# VideoPlayer

```TypeScript
interface VideoPlayer
```

VideoPlayer is a class for video playback management. It provides APIs to manage and play videos. Before calling any API in VideoPlayer, you must use [createVideoPlayer()](arkts-media-media-createvideoplayer-f.md) to create a VideoPlayer instance.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [media](arkts-media-multimedia-media.md)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## getTrackDescription

```TypeScript
getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void
```

Obtains the video track information. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription)(callback: AsyncCallback&lt;Array&lt;MediaDescription&gt;&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the MediaDescription array obtained; otherwise, **err** is an error object. |

<a id="gettrackdescription-1"></a>

## getTrackDescription

```TypeScript
getTrackDescription(): Promise<Array<MediaDescription>>
```

Obtains the video track information. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;&gt; | Promise used to return the MediaDescription array that holds the video track information. |

## on('playbackCompleted')

```TypeScript
on(type: 'playbackCompleted', callback: Callback<void>): void
```

Subscribes to the video playback completion event.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstatechange)(type: 'stateChange', callback: OnAVPlayerStateChangeHandle)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playbackCompleted' | Yes | Event type, which is **'playbackCompleted'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the event is triggered. |

## on('bufferingUpdate')

```TypeScript
on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void
```

Subscribes to the video buffering update event. This API works only under online playback.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onbufferingupdate)(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | Yes | Event type, which is **'bufferingUpdate'** in this case. |
| callback | (infoType: BufferingInfoType, value: number) =&gt; void | Yes | Callback invoked when the event is triggered.<br>The value of [BufferingInfoType](arkts-media-media-bufferinginfotype-e.md) is fixed at **0**. |

## on('startRenderFrame')

```TypeScript
on(type: 'startRenderFrame', callback: Callback<void>): void
```

Subscribes to the frame rendering start event.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onstartrenderframe)(type: 'startRenderFrame', callback: Callback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'startRenderFrame' | Yes | Event type, which is **'startRenderFrame'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the event is triggered. |

## on('videoSizeChanged')

```TypeScript
on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void
```

Subscribes to the video width and height change event.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onvideosizechange)(type: 'videoSizeChange', callback: OnVideoSizeChangeHandler)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'videoSizeChanged' | Yes | Event type, which is **'videoSizeChanged'** in this case. |
| callback | (width: number, height: number) =&gt; void | Yes | Callback invoked when the event is triggered. **width** indicates the video width, and **height** indicates the video height. |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void
```

Subscribes to the audio interruption event. For details, see [audio.InterruptEvent](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptevent-i.md).

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onaudiointerrupt)(type: 'audioInterrupt', callback: Callback&lt;audio.InterruptEvent&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type, which is **'audioInterrupt'** in this case. |
| callback | (info: audio.InterruptEvent) =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to video playback error events. After an error event is reported, you must handle the event and exit the playback.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avplayer-i.md#onerror)(type: 'error', callback: ErrorCallback)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which is **'error'** in this case.<br>This event is triggered when an error occurs during video playback. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback invoked when the event is triggered. |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

Pauses video playback. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [pause](arkts-media-media-avplayer-i.md#pause)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

<a id="pause-1"></a>

## pause

```TypeScript
pause(): Promise<void>
```

Pauses video playback. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [pause](arkts-media-media-avplayer-i.md#pause)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## play

```TypeScript
play(callback: AsyncCallback<void>): void
```

Starts video playback. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [play](arkts-media-media-avplayer-i.md#play)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

<a id="play-1"></a>

## play

```TypeScript
play(): Promise<void>
```

Starts video playback. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [play](arkts-media-media-avplayer-i.md#play)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## prepare

```TypeScript
prepare(callback: AsyncCallback<void>): void
```

Prepares for video playback. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [prepare](arkts-media-media-avplayer-i.md#prepare)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

<a id="prepare-1"></a>

## prepare

```TypeScript
prepare(): Promise<void>
```

Prepares for video playback. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [prepare](arkts-media-media-avplayer-i.md#prepare)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases the video playback resources. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [release](arkts-media-media-avplayer-i.md#release)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases the video playback resources. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [release](arkts-media-media-avplayer-i.md#release)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

Resets video playback. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [reset](arkts-media-media-avplayer-i.md#reset)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

<a id="reset-1"></a>

## reset

```TypeScript
reset(): Promise<void>
```

Resets video playback. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [reset](arkts-media-media-avplayer-i.md#reset)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## seek

```TypeScript
seek(timeMs: number, callback: AsyncCallback<number>): void
```

Seeks to the specified playback position. The previous key frame at the specified position is played. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [seek](arkts-media-media-avplayer-i.md#seek)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeMs | number | Yes | Position to seek to, in ms. The value range is [0, duration]. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the new playback position; otherwise, **err** is an error object. |

<a id="seek-1"></a>

## seek

```TypeScript
seek(timeMs: number, mode: SeekMode, callback: AsyncCallback<number>): void
```

Seeks to the specified playback position. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [seek](arkts-media-media-avplayer-i.md#seek)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeMs | number | Yes | Position to seek to, in ms. The value range is [0, duration]. |
| mode | [SeekMode](arkts-media-media-seekmode-e.md) | Yes | Seek mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the new playback position; otherwise, **err** is an error object. |

<a id="seek-2"></a>

## seek

```TypeScript
seek(timeMs: number, mode?: SeekMode): Promise<number>
```

Seeks to the specified playback position. If **mode** is not specified, the previous key frame at the specified position is played. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [seek](arkts-media-media-avplayer-i.md#seek)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeMs | number | Yes | Position to seek to, in ms. The value range is [0, duration]. |
| mode | [SeekMode](arkts-media-media-seekmode-e.md) | No | Seek mode based on the video I frame. The default value is **SEEK_PREV_SYNC**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the playback position, in ms. |

## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void
```

Sets a surface ID. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - **SetDisplaySurface** must be called between the URL setting and the calling of **prepare**. A surface must be set for video streams without audio. Otherwise, the calling of **prepare** fails.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | Surface ID, which is obtained from the **XComponent**. For details about how to obtain it, see [XComponent](../../apis-arkui/arkts-components/arkts-arkui-xcomponent-comp.md#xcomponent). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the setting is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

<a id="setdisplaysurface-1"></a>

## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string): Promise<void>
```

Sets a surface ID. This API uses a promise to return the result.

> **NOTE:** 
> 
> - **SetDisplaySurface** must be called between the URL setting and the calling of **prepare**. A surface must be set for video streams without audio. Otherwise, the calling of **prepare** fails.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | Surface ID, which is obtained from the **XComponent**. For details about how to obtain it, see [XComponent](../../apis-arkui/arkts-components/arkts-arkui-xcomponent-comp.md#xcomponent). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## setSpeed

```TypeScript
setSpeed(speed: number, callback: AsyncCallback<number>): void
```

Sets the playback speed. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setSpeed](arkts-media-media-avplayer-i.md#setspeed)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | number | Yes | Video playback speed. For details, see [PlaybackSpeed](arkts-media-media-playbackspeed-e.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the playback speed; otherwise, **err** is an error object. |

<a id="setspeed-1"></a>

## setSpeed

```TypeScript
setSpeed(speed: number): Promise<number>
```

Sets the playback speed. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setSpeed](arkts-media-media-avplayer-i.md#setspeed)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | number | Yes | Video playback speed. For details, see [PlaybackSpeed](arkts-media-media-playbackspeed-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the playback speed. For details, see [PlaybackSpeed](arkts-media-media-playbackspeed-e.md). |

## setVolume

```TypeScript
setVolume(vol: number, callback: AsyncCallback<void>): void
```

Sets the volume. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setVolume](arkts-media-media-avplayer-i.md#setvolume)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| vol | number | Yes | Relative volume. The value ranges from 0.00 to 1.00. The value **1.00** indicates the maximum volume (100%). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the setting is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

<a id="setvolume-1"></a>

## setVolume

```TypeScript
setVolume(vol: number): Promise<void>
```

Sets the volume. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setVolume](arkts-media-media-avplayer-i.md#setvolume)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| vol | number | Yes | Relative volume. The value ranges from 0.00 to 1.00. The value **1.00** indicates the maximum volume (100%). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops video playback. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [stop](arkts-media-media-avplayer-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

<a id="stop-1"></a>

## stop

```TypeScript
stop(): Promise<void>
```

Stops video playback. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [stop](arkts-media-media-avplayer-i.md#stop)()

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## audioInterruptMode

```TypeScript
audioInterruptMode?: audio.InterruptMode
```

Audio interruption mode.

**Type:** [audio.InterruptMode](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptmode-e.md)

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [audioInterruptMode](arkts-media-media-avplayer-i.md#audiointerruptmode)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## currentTime

```TypeScript
readonly currentTime: number
```

Current video playback position, in ms.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [currentTime](arkts-media-media-avplayer-i.md#currenttime)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## duration

```TypeScript
readonly duration: number
```

Video duration, in ms. The value **-1** indicates the live mode.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [duration](arkts-media-media-avplayer-i.md#duration)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## fdSrc

```TypeScript
fdSrc: AVFileDescriptor
```

Description of a video file. This property is required when video assets of an application are continuously stored in a file.

Assume that a music file that stores continuous music assets consists of the following:

Video 1 (address offset: 0, byte length: 100)

Video 2 (address offset: 101; byte length: 50)

Video 3 (address offset: 151, byte length: 150)

1. To play video 1: AVFileDescriptor { fd = resource handle; offset = 0; length = 100; }
2. To play video 2: AVFileDescriptor { fd = resource handle; offset = 101; length = 50; }
3. To play video 3: AVFileDescriptor { fd = resource handle; offset = 151; length = 150; }

To play an independent video file, use **src=fd://xx**.

**Type:** [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md)

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [fdSrc](arkts-media-media-avplayer-i.md#fdsrc)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## height

```TypeScript
readonly height: number
```

Video height, in px.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [height](arkts-media-media-avplayer-i.md#height)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## loop

```TypeScript
loop: boolean
```

Whether to loop video playback. **true** to loop, **false** otherwise.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [loop](arkts-media-media-avplayer-i.md#loop)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## state

```TypeScript
readonly state: VideoPlayState
```

Video playback state.

**Type:** [VideoPlayState](arkts-media-media-videoplaystate-t.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [state](arkts-media-media-avplayer-i.md#state)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## url

```TypeScript
url: string
```

Video URL. The video formats MP4, MPEG-TS, and MKV are supported.

**Example of supported URLs**:

1. FD: fd://xx

![](../../../reference/apis-media-kit/figures/en-us_image_url.png)

2. HTTP: http://xx
3. HTTPS: https://xx
4. HLS: http://xx or https://xx
5. File type: file://xx

**NOTE:** 

WebM is no longer supported since API version 11.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [url](arkts-media-media-avplayer-i.md#url)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## videoScaleType

```TypeScript
videoScaleType?: VideoScaleType
```

Video scale type. The default value is **VIDEO_SCALE_TYPE_FIT**.

**Type:** [VideoScaleType](arkts-media-media-videoscaletype-e.md)

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [videoScaleType](arkts-media-media-avplayer-i.md#videoscaletype)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## width

```TypeScript
readonly width: number
```

Video width, in px.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [width](arkts-media-media-avplayer-i.md#width)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer
