# AudioPlayer

> **说明：**  
>  
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer](arkts-media-media-n.md)替代。

音频播放管理类，用于管理和播放音频媒体。在调用AudioPlayer的方法前，需要先通过[createAudioPlayer()](arkts-media-media-createaudioplayer-f.md#createaudioplayer)构建一个AudioPlayer实例。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [media:media](arkts-media-media-n.md)

<!--Device-unnamed-interface AudioPlayer--><!--Device-unnamed-interface AudioPlayer-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## getTrackDescription

```TypeScript
getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void
```

获取音频轨道信息。需在'dataLoad'事件成功触发后，才能调用。通过回调函数获取返回值。
> **说明：**  
> > 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getTrackDescription(callback:](arkts-media-media-avplayer-i.md#gettrackdescription)

<!--Device-AudioPlayer-getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void--><!--Device-AudioPlayer-getTrackDescription(callback: AsyncCallback<Array<MediaDescription>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;MediaDescription&gt;&gt; | 是 | 回调函数。获取音频轨道信息成功时，err为undefined，data为获取到的MediaDescription数组，否则为错误对象。 |

## getTrackDescription

```TypeScript
getTrackDescription(): Promise<Array<MediaDescription>>
```

获取音频轨道信息。需在'dataLoad'事件成功触发后，才能调用。通过Promise获取返回值。
> **说明：**  
> > 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.getTrackDescription](arkts-media-media-avplayer-i.md#gettrackdescription)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getTrackDescription()](arkts-media-media-avplayer-i.md#gettrackdescription)

<!--Device-AudioPlayer-getTrackDescription(): Promise<Array<MediaDescription>>--><!--Device-AudioPlayer-getTrackDescription(): Promise<Array<MediaDescription>>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;MediaDescription&gt;&gt; | 音频轨道信息MediaDescription数组Promise返回值。 |

## on('bufferingUpdate')

```TypeScript
on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void
```

开始订阅音频缓存更新事件。仅网络播放支持该订阅事件。
> **说明：**  
> > 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('bufferingUpdate')](@ohos.multimedia.media:media.AVPlayer.on(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler))  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void--><!--Device-AudioPlayer-on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bufferingUpdate' | 是 | 音频缓存事件回调类型，支持的事件：'bufferingUpdate'。 |
| callback | (infoType: BufferingInfoType, value: number) =&gt; void | 是 | 音频缓存事件回调方法。<br>[BufferingInfoType](@ohos.multimedia.media:media.BufferingInfoType)value值固定为0。 |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

开始订阅音频播放事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void--><!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange' | 是 | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](media.AudioPlayer.play)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](media.AudioPlayer.pause)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](media.AudioPlayer.stop)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](media.AudioPlayer.reset)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](media.AudioPlayer.setVolume)调用，播放音量改变后触发该事件。 |
| callback | () =&gt; void | 是 | 播放事件回调方法。 |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

开始订阅音频播放事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void--><!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange' | 是 | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](media.AudioPlayer.play)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](media.AudioPlayer.pause)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](media.AudioPlayer.stop)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](media.AudioPlayer.reset)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](media.AudioPlayer.setVolume)调用，播放音量改变后触发该事件。 |
| callback | () =&gt; void | 是 | 播放事件回调方法。 |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

开始订阅音频播放事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void--><!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange' | 是 | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](media.AudioPlayer.play)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](media.AudioPlayer.pause)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](media.AudioPlayer.stop)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](media.AudioPlayer.reset)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](media.AudioPlayer.setVolume)调用，播放音量改变后触发该事件。 |
| callback | () =&gt; void | 是 | 播放事件回调方法。 |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

开始订阅音频播放事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void--><!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange' | 是 | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](media.AudioPlayer.play)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](media.AudioPlayer.pause)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](media.AudioPlayer.stop)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](media.AudioPlayer.reset)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](media.AudioPlayer.setVolume)调用，播放音量改变后触发该事件。 |
| callback | () =&gt; void | 是 | 播放事件回调方法。 |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

开始订阅音频播放事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void--><!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange' | 是 | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](media.AudioPlayer.play)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](media.AudioPlayer.pause)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](media.AudioPlayer.stop)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](media.AudioPlayer.reset)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](media.AudioPlayer.setVolume)调用，播放音量改变后触发该事件。 |
| callback | () =&gt; void | 是 | 播放事件回调方法。 |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

开始订阅音频播放事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void--><!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange' | 是 | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](media.AudioPlayer.play)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](media.AudioPlayer.pause)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](media.AudioPlayer.stop)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](media.AudioPlayer.reset)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](media.AudioPlayer.setVolume)调用，播放音量改变后触发该事件。 |
| callback | () =&gt; void | 是 | 播放事件回调方法。 |

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')

```TypeScript
on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void
```

开始订阅音频播放事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('stateChange')](@ohos.multimedia.media:media.AVPlayer.on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void--><!--Device-AudioPlayer-on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange' | 是 | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](media.AudioPlayer.play)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](media.AudioPlayer.pause)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](media.AudioPlayer.stop)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](media.AudioPlayer.reset)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](media.AudioPlayer.setVolume)调用，播放音量改变后触发该事件。 |
| callback | () =&gt; void | 是 | 播放事件回调方法。 |

## on('timeUpdate')

```TypeScript
on(type: 'timeUpdate', callback: Callback<number>): void
```

开始订阅音频播放时间更新事件。处于播放状态时，每隔1s上报一次该事件。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('timeUpdate')](@ohos.multimedia.media:media.AVPlayer.on(type: 'timeUpdate', callback: Callback<int>))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'timeUpdate', callback: Callback<number>): void--><!--Device-AudioPlayer-on(type: 'timeUpdate', callback: Callback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'timeUpdate' | 是 | 播放事件回调类型，支持的事件包括：'timeUpdate'。<br>- 'timeUpdate'：音频播放时间戳更新，开始播放后自动触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 是 | 播放事件回调方法。回调方法入参为更新后的时间戳。 |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void
```

监听音频焦点变化事件，参考[audio.InterruptEvent](../../apis-audio-kit/arkts-apis/arkts-audio-audio-interruptevent-i.md)。
> **说明：**  
> > 从API version 9开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('audioInterrupt')](@ohos.multimedia.media:media.AVPlayer.on(type: 'audioInterrupt', callback: Callback&lt;audio.InterruptEvent&gt;))  
> 替代。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void--><!--Device-AudioPlayer-on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 音频焦点变化事件回调类型，支持的事件：'audioInterrupt'。 |
| callback | (info: audio.InterruptEvent) =&gt; void | 是 | 音频焦点变化事件回调方法。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

开始订阅音频播放错误事件，当上报error错误事件后，用户需处理error事件，退出播放操作。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.on('error')](@ohos.multimedia.media:media.AVPlayer.on(type: 'error', callback: ErrorCallback))替  
> 代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioPlayer-on(type: 'error', callback: ErrorCallback): void--><!--Device-AudioPlayer-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 播放错误事件回调类型，支持的事件包括：'error'。<br>- 'error'：音频播放中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 播放错误事件回调方法。 |

## pause

```TypeScript
pause(): void
```

暂停播放音频资源。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.pause](arkts-media-media-avplayer-i.md#pause)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [pause(callback:](arkts-media-media-avplayer-i.md#pause)

<!--Device-AudioPlayer-pause(): void--><!--Device-AudioPlayer-pause(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## play

```TypeScript
play(): void
```

开始播放音频资源，需在'dataLoad'事件成功触发后，才能调用。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.play](arkts-media-media-avplayer-i.md#play)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [play(callback:](arkts-media-media-avplayer-i.md#play)

<!--Device-AudioPlayer-play(): void--><!--Device-AudioPlayer-play(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## release

```TypeScript
release(): void
```

释放音频资源。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.release](arkts-media-media-avplayer-i.md#release)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [release(callback:](arkts-media-media-avplayer-i.md#release)

<!--Device-AudioPlayer-release(): void--><!--Device-AudioPlayer-release(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## reset

```TypeScript
reset(): void
```

重置播放音频资源。
> **说明：**  
> > 从API version 7开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.reset](arkts-media-media-avplayer-i.md#reset)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [reset(callback:](arkts-media-media-avplayer-i.md#reset)

<!--Device-AudioPlayer-reset(): void--><!--Device-AudioPlayer-reset(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## seek

```TypeScript
seek(timeMs: number): void
```

跳转到指定播放位置。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.seek](arkts-media-media-avplayer-i.md#seek)替代  
> 。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [seek](arkts-media-media-avplayer-i.md#seek)

<!--Device-AudioPlayer-seek(timeMs: number): void--><!--Device-AudioPlayer-seek(timeMs: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeMs | number | 是 | 指定的跳转时间节点，单位毫秒（ms），取值范围[0, duration]。 |

## setVolume

```TypeScript
setVolume(vol: number): void
```

设置音量。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.setVolume](arkts-media-media-avplayer-i.md#setvolume)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [setVolume](arkts-media-media-avplayer-i.md#setvolume)

<!--Device-AudioPlayer-setVolume(vol: number): void--><!--Device-AudioPlayer-setVolume(vol: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vol | number | 是 | 指定的相对音量大小，取值范围为[0.00-1.00]，1表示最大音量，即100%。 |

## stop

```TypeScript
stop(): void
```

停止播放音频资源。
> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVPlayer.stop](arkts-media-media-avplayer-i.md#stop)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [stop(callback:](arkts-media-media-avplayer-i.md#stop)

<!--Device-AudioPlayer-stop(): void--><!--Device-AudioPlayer-stop(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## audioInterruptMode

```TypeScript
audioInterruptMode?: audio.InterruptMode
```

音频焦点模型。

**类型：** audio.InterruptMode

**起始版本：** 9

**废弃版本：** 9

**替代接口：** audioInterruptMode

<!--Device-AudioPlayer-audioInterruptMode?: audio.InterruptMode--><!--Device-AudioPlayer-audioInterruptMode?: audio.InterruptMode-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## currentTime

```TypeScript
readonly currentTime: number
```

音频的当前播放位置，单位为毫秒（ms）。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** currentTime

<!--Device-AudioPlayer-readonly currentTime: number--><!--Device-AudioPlayer-readonly currentTime: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## duration

```TypeScript
readonly duration: number
```

音频时长，单位为毫秒（ms）。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** duration

<!--Device-AudioPlayer-readonly duration: number--><!--Device-AudioPlayer-readonly duration: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## fdSrc

```TypeScript
fdSrc: AVFileDescriptor
```

音频媒体文件描述，使用场景：应用中的音频资源被连续存储在同一个文件中。

**使用示例**：

假设一个连续存储的音乐文件:

音乐1(地址偏移:0，字节长度:100)

音乐2(地址偏移:101，字节长度:50)

音乐3(地址偏移:151，字节长度:150)

1. 播放音乐1：AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }2. 播放音乐2：AVFileDescriptor { fd = 资源句柄; offset = 101; length = 50; }3. 播放音乐3：AVFileDescriptor { fd = 资源句柄; offset = 151; length = 150; }

假设是一个独立的音乐文件: 请使用src=fd://xx

**类型：** AVFileDescriptor

**起始版本：** 9

**废弃版本：** 9

**替代接口：** fdSrc

<!--Device-AudioPlayer-fdSrc: AVFileDescriptor--><!--Device-AudioPlayer-fdSrc: AVFileDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## loop

```TypeScript
loop: boolean
```

音频循环播放属性，设置为'true'表示循环播放。

**类型：** boolean

**起始版本：** 6

**废弃版本：** 9

**替代接口：** loop

<!--Device-AudioPlayer-loop: boolean--><!--Device-AudioPlayer-loop: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## src

```TypeScript
src: string
```

音频媒体URI，支持当前主流的音频格式(m4a、aac、mp3、ogg、wav、amr)。

**支持路径示例**：

1. fd类型播放：fd://xx

![](../../../reference/apis-media-kit/figures/zh-cn_image_url.png)

2. http网络播放: http://xx3. https网络播放: https://xx4. hls网络播放路径：http://xx或者https://xx

ohos.permission.READ_MEDIA 或 ohos.permission.INTERNET。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** url

**需要权限：** ohos.permission.READ_MEDIA or ohos.permission.INTERNET

<!--Device-AudioPlayer-src: string--><!--Device-AudioPlayer-src: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

## state

```TypeScript
readonly state: AudioState
```

可以查询音频播放的状态，该状态不可作为调用play/pause/stop等状态切换的触发条件。

**类型：** AudioState

**起始版本：** 6

**废弃版本：** 9

**替代接口：** state

<!--Device-AudioPlayer-readonly state: AudioState--><!--Device-AudioPlayer-readonly state: AudioState-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

