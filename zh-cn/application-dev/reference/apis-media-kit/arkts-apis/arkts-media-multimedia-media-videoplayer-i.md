# VideoPlayer

视频播放管理类，用于管理和播放视频媒体。在调用VideoPlayer的方法前，需要先通过[createVideoPlayer()](arkts-media-media-createvideoplayer-f.md#createvideoplayer-1)构建一个VideoPlayer实例。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer](arkts-media-media-n.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [media:media](arkts-media-media-n.md)

<!--Device-unnamed-interface VideoPlayer--><!--Device-unnamed-interface VideoPlayer-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## getTrackDescription

```TypeScript
getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void
```

获取视频轨道信息。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getTrackDescription(callback:

<!--Device-VideoPlayer-getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void--><!--Device-VideoPlayer-getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<MediaDescription>> | 是 | 回调函数。获取视频轨道信息成功时，err为undefined，data为获取到的视频轨道信息MediaDescription数组，否则为错误对象。 |

## getTrackDescription

```TypeScript
getTrackDescription(): Promise<Array<MediaDescription>>
```

获取视频轨道信息。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getTrackDescription()](arkts-media-media-avplayer-i.md#gettrackdescription-2)

<!--Device-VideoPlayer-getTrackDescription(): Promise<Array<MediaDescription>>--><!--Device-VideoPlayer-getTrackDescription(): Promise<Array<MediaDescription>>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<MediaDescription>> | Promise对象，返回获取的视频轨道信息MediaDescription数组。 |

## on('playbackCompleted')

```TypeScript
on(type: 'playbackCompleted', callback: Callback<void>): void
```

开始监听视频播放完成事件。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-VideoPlayer-on(type: 'playbackCompleted', callback: Callback<void>): void--><!--Device-VideoPlayer-on(type: 'playbackCompleted', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackCompleted' | 是 | 视频播放完成事件回调类型，支持的事件：'playbackCompleted'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<void> | 是 | 视频播放完成事件回调方法。 |

## on('bufferingUpdate')

```TypeScript
on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void
```

开始监听视频缓存更新事件。仅网络播放支持该订阅事件。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('bufferingUpdate')](@ohos.multimedia.media:media.AVPlayer.on(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler))  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-VideoPlayer-on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void--><!--Device-VideoPlayer-on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | 是 | 视频缓存事件回调类型，支持的事件：'bufferingUpdate'。 |
| callback | (infoType: BufferingInfoType, value: number) => void | 是 | 视频缓存事件回调方法。<br>[BufferingInfoType](@ohos.multimedia.media:media.BufferingInfoType)value值固定为0。 |

## on('startRenderFrame')

```TypeScript
on(type: 'startRenderFrame', callback: Callback<void>): void
```

开始监听视频播放首帧送显上报事件。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('startRenderFrame')](@ohos.multimedia.media:media.AVPlayer.on(type: 'startRenderFrame', callback: Callback<void>))  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-VideoPlayer-on(type: 'startRenderFrame', callback: Callback<void>): void--><!--Device-VideoPlayer-on(type: 'startRenderFrame', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'startRenderFrame' | 是 | 视频播放首帧送显上报事件回调类型，支持的事件：'startRenderFrame'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<void> | 是 | 视频播放首帧送显上报事件回调方法。 |

## on('videoSizeChanged')

```TypeScript
on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void
```

开始监听视频播放宽高变化事件。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('videoSizeChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'videoSizeChange', callback: OnVideoSizeChangeHandler))  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-VideoPlayer-on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void--><!--Device-VideoPlayer-on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'videoSizeChanged' | 是 | 视频播放宽高变化事件回调类型，支持的事件：'videoSizeChanged'。 |
| callback | (width: number, height: number) => void | 是 | 视频播放宽高变化事件回调方法，width表示宽，height表示高。 |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void
```

监听音频焦点变化事件，参考[audio.InterruptEvent](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptevent-i.md)。

> **说明：**  
>  
> 从API version 9开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('audioInterrupt')](@ohos.multimedia.media:media.AVPlayer.on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>))  
> 替代。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-VideoPlayer-on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void--><!--Device-VideoPlayer-on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 音频焦点变化事件回调类型，支持的事件：'audioInterrupt'。 |
| callback | (info: audio.InterruptEvent) => void | 是 | 音频焦点变化事件回调方法。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

开始监听视频播放错误事件，当上报error错误事件后，用户需处理error事件，退出播放操作。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('error')](@ohos.multimedia.media:media.AVPlayer.on(type: 'error', callback: ErrorCallback))替  
> 代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-VideoPlayer-on(type: 'error', callback: ErrorCallback): void--><!--Device-VideoPlayer-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 播放错误事件回调类型，支持的事件包括：'error'。<br>- 'error'：视频播放中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 播放错误事件回调方法。 |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

通过回调方式暂停播放视频。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.pause](arkts-media-media-avplayer-i.md#pause-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** pause(callback:

<!--Device-VideoPlayer-pause(callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-pause(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当暂停播放视频成功，err为undefined，否则为错误对象。 |

## pause

```TypeScript
pause(): Promise<void>
```

暂停播放视频。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.pause](arkts-media-media-avplayer-i.md#pause-2)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [pause()](arkts-media-media-avplayer-i.md#pause-2)

<!--Device-VideoPlayer-pause(): Promise<void>--><!--Device-VideoPlayer-pause(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 暂停播放视频的Promise返回值。 |

## play

```TypeScript
play(callback: AsyncCallback<void>): void
```

开始播放视频。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.play](arkts-media-media-avplayer-i.md#play-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** play(callback:

<!--Device-VideoPlayer-play(callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-play(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当开始播放视频成功，err为undefined，否则为错误对象。 |

## play

```TypeScript
play(): Promise<void>
```

开始播放视频。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.play](arkts-media-media-avplayer-i.md#play-2)替代  
> 。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [play()](arkts-media-media-avplayer-i.md#play-2)

<!--Device-VideoPlayer-play(): Promise<void>--><!--Device-VideoPlayer-play(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 开始播放视频的Promise返回值。 |

## prepare

```TypeScript
prepare(callback: AsyncCallback<void>): void
```

准备播放视频。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.prepare](arkts-media-media-avplayer-i.md#prepare-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** prepare(callback:

<!--Device-VideoPlayer-prepare(callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-prepare(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当准备播放视频成功，err为undefined，否则为错误对象。 |

## prepare

```TypeScript
prepare(): Promise<void>
```

准备播放视频。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.prepare](arkts-media-media-avplayer-i.md#prepare-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [prepare()](arkts-media-media-avplayer-i.md#prepare-2)

<!--Device-VideoPlayer-prepare(): Promise<void>--><!--Device-VideoPlayer-prepare(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 准备播放视频的Promise返回值。 |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放视频资源。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.release](arkts-media-media-avplayer-i.md#release-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** release(callback:

<!--Device-VideoPlayer-release(callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当释放视频资源成功，err为undefined，否则为错误对象。 |

## release

```TypeScript
release(): Promise<void>
```

释放视频资源。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.release](arkts-media-media-avplayer-i.md#release-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [release()](arkts-media-media-avplayer-i.md#release-2)

<!--Device-VideoPlayer-release(): Promise<void>--><!--Device-VideoPlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 释放视频资源的Promise返回值。 |

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

重置播放视频。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.reset](arkts-media-media-avplayer-i.md#reset-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** reset(callback:

<!--Device-VideoPlayer-reset(callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-reset(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当重置播放视频成功，err为undefined，否则为错误对象。 |

## reset

```TypeScript
reset(): Promise<void>
```

重置播放视频。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.reset](arkts-media-media-avplayer-i.md#reset-2)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [reset()](arkts-media-media-avplayer-i.md#reset-2)

<!--Device-VideoPlayer-reset(): Promise<void>--><!--Device-VideoPlayer-reset(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## seek

```TypeScript
seek(timeMs: number, callback: AsyncCallback<number>): void
```

跳转到指定播放位置，默认跳转到指定时间点的上一个关键帧。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.seek](arkts-media-media-avplayer-i.md#seek-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [seek](arkts-media-media-avplayer-i.md#seek-1)

<!--Device-VideoPlayer-seek(timeMs: number, callback: AsyncCallback<number>): void--><!--Device-VideoPlayer-seek(timeMs: number, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeMs | number | 是 | 指定的跳转时间节点，单位毫秒（ms），取值范围为[0, duration]。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。跳转到指定播放位置成功时，err为undefined，data为获取到的跳转到的播放位置，否则为错误对象。 |

## seek

```TypeScript
seek(timeMs: number, mode: SeekMode, callback: AsyncCallback<number>): void
```

跳转到指定播放位置。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.seek](arkts-media-media-avplayer-i.md#seek-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [seek](arkts-media-media-avplayer-i.md#seek-1)

<!--Device-VideoPlayer-seek(timeMs: number, mode: SeekMode, callback: AsyncCallback<number>): void--><!--Device-VideoPlayer-seek(timeMs: number, mode: SeekMode, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeMs | number | 是 | 指定的跳转时间节点，单位毫秒（ms），取值范围为[0, duration]。 |
| mode | [SeekMode](arkts-media-multimedia-media-seekmode-e.md) | 是 | 跳转模式。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。跳转到指定播放位置成功时，err为undefined，data为获取到的跳转到的播放位置，否则为错误对象。 |

## seek

```TypeScript
seek(timeMs: number, mode?: SeekMode): Promise<number>
```

跳转到指定播放位置，如果没有设置mode则跳转到指定时间点的上一个关键帧。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.seek](arkts-media-media-avplayer-i.md#seek-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [seek](arkts-media-media-avplayer-i.md#seek-1)

<!--Device-VideoPlayer-seek(timeMs: number, mode?: SeekMode): Promise<number>--><!--Device-VideoPlayer-seek(timeMs: number, mode?: SeekMode): Promise<number>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeMs | number | 是 | 指定的跳转时间节点，单位毫秒（ms），取值范围为[0, duration]。 |
| mode | [SeekMode](arkts-media-multimedia-media-seekmode-e.md) | 否 | 基于视频I帧的跳转模式，默认为SEEK_PREV_SYNC模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | 跳转到指定播放位置的Promise返回值，单位ms。 |

## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void
```

设置SurfaceId。通过回调函数获取返回值。

> **说明：**  
>  
> - SetDisplaySurface需要在设置url和Prepare之间，无音频的视频流必须设置Surface否则Prepare失败。  
>  
> - 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.surfaceId](../../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#属性)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

<!--Device-VideoPlayer-setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 指定SurfaceId，应从XComponent组件获取，获取方式请参考[XComponent](./@internal/component/ets/xcomponent)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置SurfaceId成功，err为undefined，否则为错误对象。 |

## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string): Promise<void>
```

设置SurfaceId。通过Promise获取返回值。

> **说明：**  
>  
> - SetDisplaySurface需要在设置url和Prepare之间，无音频的视频流必须设置Surface否则Prepare失败。  
>  
> - 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.surfaceId](../../../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#属性)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

<!--Device-VideoPlayer-setDisplaySurface(surfaceId: string): Promise<void>--><!--Device-VideoPlayer-setDisplaySurface(surfaceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 指定SurfaceId，应从XComponent组件获取，获取方式请参考[XComponent](./@internal/component/ets/xcomponent)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 设置SurfaceId的Promise返回值。 |

## setSpeed

```TypeScript
setSpeed(speed: number, callback: AsyncCallback<number>): void
```

设置播放速度。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.setSpeed](@ohos.multimedia.media:media.AVPlayer.setSpeed)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSpeed

<!--Device-VideoPlayer-setSpeed(speed: number, callback: AsyncCallback<number>): void--><!--Device-VideoPlayer-setSpeed(speed: number, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | number | 是 | 指定播放视频速度，具体见[PlaybackSpeed](@ohos.multimedia.media:media.PlaybackSpeed)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。设置播放速度成功时，err为undefined，data为设置的播放速度，否则为错误对象。 |

## setSpeed

```TypeScript
setSpeed(speed: number): Promise<number>
```

设置播放速度。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.setSpeed](@ohos.multimedia.media:media.AVPlayer.setSpeed)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSpeed

<!--Device-VideoPlayer-setSpeed(speed: number): Promise<number>--><!--Device-VideoPlayer-setSpeed(speed: number): Promise<number>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | number | 是 | 指定播放视频速度，具体见[PlaybackSpeed](@ohos.multimedia.media:media.PlaybackSpeed)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回设置的播放速度，具体见[PlaybackSpeed](@ohos.multimedia.media:media.PlaybackSpeed)。 |

## setVolume

```TypeScript
setVolume(vol: number, callback: AsyncCallback<void>): void
```

设置音量。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.setVolume](arkts-media-media-avplayer-i.md#setvolume-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setVolume](arkts-media-media-avplayer-i.md#setvolume-1)

<!--Device-VideoPlayer-setVolume(vol: number, callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-setVolume(vol: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vol | number | 是 | 指定的相对音量大小，取值范围为[0.00-1.00]，1表示最大音量，即100%。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置音量成功，err为undefined，否则为错误对象。 |

## setVolume

```TypeScript
setVolume(vol: number): Promise<void>
```

设置音量。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.setVolume](arkts-media-media-avplayer-i.md#setvolume-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setVolume](arkts-media-media-avplayer-i.md#setvolume-1)

<!--Device-VideoPlayer-setVolume(vol: number): Promise<void>--><!--Device-VideoPlayer-setVolume(vol: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vol | number | 是 | 指定的相对音量大小，取值范围为[0.00-1.00]，1表示最大音量，即100%。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 设置音量的Promise返回值。 |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

通过回调方式停止播放视频。通过回调函数获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.stop](arkts-media-media-avplayer-i.md#stop-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** stop(callback:

<!--Device-VideoPlayer-stop(callback: AsyncCallback<void>): void--><!--Device-VideoPlayer-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当停止播放视频成功，err为undefined，否则为错误对象。 |

## stop

```TypeScript
stop(): Promise<void>
```

停止播放视频。通过Promise获取返回值。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.stop](arkts-media-media-avplayer-i.md#stop-2)替代  
> 。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [stop()](arkts-media-media-avplayer-i.md#stop-2)

<!--Device-VideoPlayer-stop(): Promise<void>--><!--Device-VideoPlayer-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 停止播放视频的Promise返回值。 |

## audioInterruptMode

```TypeScript
audioInterruptMode?: audio.InterruptMode
```

音频焦点模式。

**类型：** audio.InterruptMode

**起始版本：** 9

**废弃版本：** 9

**替代接口：** audioInterruptMode

<!--Device-VideoPlayer-audioInterruptMode?: audio.InterruptMode--><!--Device-VideoPlayer-audioInterruptMode?: audio.InterruptMode-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## currentTime

```TypeScript
readonly currentTime: number
```

视频的当前播放位置，单位为毫秒（ms）。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** currentTime

<!--Device-VideoPlayer-readonly currentTime: number--><!--Device-VideoPlayer-readonly currentTime: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## duration

```TypeScript
readonly duration: number
```

视频时长，单位为毫秒（ms），返回-1表示直播模式。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** duration

<!--Device-VideoPlayer-readonly duration: number--><!--Device-VideoPlayer-readonly duration: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## fdSrc

```TypeScript
fdSrc: AVFileDescriptor
```

视频媒体文件描述，使用场景：应用中的视频资源被连续存储在同一个文件中。

**使用示例**：

假设一个连续存储的音乐文件:

视频1(地址偏移:0，字节长度:100)

视频2(地址偏移:101，字节长度:50)

视频3(地址偏移:151，字节长度:150)

1. 播放视频1：AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }2. 播放视频2：AVFileDescriptor { fd = 资源句柄; offset = 101; length = 50; }3. 播放视频3：AVFileDescriptor { fd = 资源句柄; offset = 151; length = 150; }

假设是一个独立的视频文件: 请使用src=fd://xx

**类型：** AVFileDescriptor

**起始版本：** 9

**废弃版本：** 9

**替代接口：** fdSrc

<!--Device-VideoPlayer-fdSrc: AVFileDescriptor--><!--Device-VideoPlayer-fdSrc: AVFileDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## height

```TypeScript
readonly height: number
```

视频高，单位为像素（px）。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** height

<!--Device-VideoPlayer-readonly height: number--><!--Device-VideoPlayer-readonly height: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## loop

```TypeScript
loop: boolean
```

视频循环播放属性，设置为'true'表示循环播放。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** loop

<!--Device-VideoPlayer-loop: boolean--><!--Device-VideoPlayer-loop: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## state

```TypeScript
readonly state: VideoPlayState
```

视频播放的状态。

**类型：** VideoPlayState

**起始版本：** 8

**废弃版本：** 9

**替代接口：** state

<!--Device-VideoPlayer-readonly state: VideoPlayState--><!--Device-VideoPlayer-readonly state: VideoPlayState-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## url

```TypeScript
url: string
```

视频媒体URL，支持当前主流的视频格式(mp4、mpeg-ts、mkv)。

**支持路径示例**：

1. fd类型播放：fd://xx

![](../../../../reference/apis-media-kit/figures/zh-cn_image_url.png)

2. http网络播放: http://xx3. https网络播放: https://xx4. hls网络播放路径：http://xx或者https://xx5. file类型: file://xx

**说明：**

从API version 11开始不支持webm。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** url

<!--Device-VideoPlayer-url: string--><!--Device-VideoPlayer-url: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## videoScaleType

```TypeScript
videoScaleType?: VideoScaleType
```

视频缩放模式。默认值为VIDEO_SCALE_TYPE_FIT。

**类型：** VideoScaleType

**起始版本：** 9

**废弃版本：** 9

**替代接口：** videoScaleType

<!--Device-VideoPlayer-videoScaleType?: VideoScaleType--><!--Device-VideoPlayer-videoScaleType?: VideoScaleType-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

## width

```TypeScript
readonly width: number
```

视频宽，单位为像素（px）。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** width

<!--Device-VideoPlayer-readonly width: number--><!--Device-VideoPlayer-readonly width: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

