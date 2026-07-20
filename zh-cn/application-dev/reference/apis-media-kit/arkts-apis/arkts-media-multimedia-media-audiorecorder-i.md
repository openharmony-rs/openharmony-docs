# AudioRecorder

> **说明：**  
>  
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVRecorder](arkts-media-media-n.md)替代。

音频录制管理类，用于录制音频媒体。在调用AudioRecorder的方法前，需要先通过[createAudioRecorder()](arkts-media-media-createaudiorecorder-f.md#createaudiorecorder-1) 构建一个AudioRecorder实例。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [media:media](arkts-media-media-n.md)

<!--Device-unnamed-interface AudioRecorder--><!--Device-unnamed-interface AudioRecorder-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

<a id="on"></a>
## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('stateChange')](@ohos.multimedia.media:media.AVRecorder.on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| ’resume‘ \| 'stop' \| 'release' \| 'reset'。<br/>- 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。<br/>- 'start' ：完成start调用，音频录制开始，触发该事件。<br/>- 'pause': 完成pause调用，音频暂停录制，触发该事件。<br/>- 'resume': 完成resume调用，音频恢复录制，触发该事件。<br/>- 'stop' ：完成stop调用，音频停止录制，触发该事件。<br/>- 'release' ：完成release调用，音频释放录制资源，触发该事件。<br/>   - 'reset'：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () =&gt; void | 是 | 录制事件回调方法。 |

<a id="on-1"></a>
## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('stateChange')](@ohos.multimedia.media:media.AVRecorder.on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| ’resume‘ \| 'stop' \| 'release' \| 'reset'。<br/>- 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。<br/>- 'start' ：完成start调用，音频录制开始，触发该事件。<br/>- 'pause': 完成pause调用，音频暂停录制，触发该事件。<br/>- 'resume': 完成resume调用，音频恢复录制，触发该事件。<br/>- 'stop' ：完成stop调用，音频停止录制，触发该事件。<br/>- 'release' ：完成release调用，音频释放录制资源，触发该事件。<br/>   - 'reset'：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () =&gt; void | 是 | 录制事件回调方法。 |

<a id="on-2"></a>
## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('stateChange')](@ohos.multimedia.media:media.AVRecorder.on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| ’resume‘ \| 'stop' \| 'release' \| 'reset'。<br/>- 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。<br/>- 'start' ：完成start调用，音频录制开始，触发该事件。<br/>- 'pause': 完成pause调用，音频暂停录制，触发该事件。<br/>- 'resume': 完成resume调用，音频恢复录制，触发该事件。<br/>- 'stop' ：完成stop调用，音频停止录制，触发该事件。<br/>- 'release' ：完成release调用，音频释放录制资源，触发该事件。<br/>   - 'reset'：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () =&gt; void | 是 | 录制事件回调方法。 |

<a id="on-3"></a>
## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('stateChange')](@ohos.multimedia.media:media.AVRecorder.on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| ’resume‘ \| 'stop' \| 'release' \| 'reset'。<br/>- 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。<br/>- 'start' ：完成start调用，音频录制开始，触发该事件。<br/>- 'pause': 完成pause调用，音频暂停录制，触发该事件。<br/>- 'resume': 完成resume调用，音频恢复录制，触发该事件。<br/>- 'stop' ：完成stop调用，音频停止录制，触发该事件。<br/>- 'release' ：完成release调用，音频释放录制资源，触发该事件。<br/>   - 'reset'：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () =&gt; void | 是 | 录制事件回调方法。 |

<a id="on-4"></a>
## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('stateChange')](@ohos.multimedia.media:media.AVRecorder.on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| ’resume‘ \| 'stop' \| 'release' \| 'reset'。<br/>- 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。<br/>- 'start' ：完成start调用，音频录制开始，触发该事件。<br/>- 'pause': 完成pause调用，音频暂停录制，触发该事件。<br/>- 'resume': 完成resume调用，音频恢复录制，触发该事件。<br/>- 'stop' ：完成stop调用，音频停止录制，触发该事件。<br/>- 'release' ：完成release调用，音频释放录制资源，触发该事件。<br/>   - 'reset'：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () =&gt; void | 是 | 录制事件回调方法。 |

<a id="on-5"></a>
## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('stateChange')](@ohos.multimedia.media:media.AVRecorder.on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| ’resume‘ \| 'stop' \| 'release' \| 'reset'。<br/>- 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。<br/>- 'start' ：完成start调用，音频录制开始，触发该事件。<br/>- 'pause': 完成pause调用，音频暂停录制，触发该事件。<br/>- 'resume': 完成resume调用，音频恢复录制，触发该事件。<br/>- 'stop' ：完成stop调用，音频停止录制，触发该事件。<br/>- 'release' ：完成release调用，音频释放录制资源，触发该事件。<br/>   - 'reset'：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () =&gt; void | 是 | 录制事件回调方法。 |

<a id="on-6"></a>
## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('stateChange')](@ohos.multimedia.media:media.AVRecorder.on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| ’resume‘ \| 'stop' \| 'release' \| 'reset'。<br/>- 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。<br/>- 'start' ：完成start调用，音频录制开始，触发该事件。<br/>- 'pause': 完成pause调用，音频暂停录制，触发该事件。<br/>- 'resume': 完成resume调用，音频恢复录制，触发该事件。<br/>- 'stop' ：完成stop调用，音频停止录制，触发该事件。<br/>- 'release' ：完成release调用，音频释放录制资源，触发该事件。<br/>   - 'reset'：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () =&gt; void | 是 | 录制事件回调方法。 |

<a id="on-7"></a>
## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

开始订阅音频录制错误事件，当上报error错误事件后，用户需处理error事件，退出录制操作。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.on('error')](@ohos.multimedia.media:media.AVRecorder.on(type: 'error', callback: ErrorCallback))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on(type:

<!--Device-AudioRecorder-on(type: 'error', callback: ErrorCallback): void--><!--Device-AudioRecorder-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 录制错误事件回调类型'error'。<br/>- 'error'：音频录制过程中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 录制错误事件回调方法。 |

<a id="pause"></a>
## pause

```TypeScript
pause(): void
```

暂停录制，需要在'start'事件成功触发后，才能调用pause方法。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.pause](@ohos.multimedia.media:media.AVRecorder.pause(callback: AsyncCallback<void>))替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** pause(callback:

<!--Device-AudioRecorder-pause(): void--><!--Device-AudioRecorder-pause(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

<a id="prepare"></a>
## prepare

```TypeScript
prepare(config: AudioRecorderConfig): void
```

录音准备。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.prepare](@ohos.multimedia.media:media.AVRecorder.prepare(config: AVRecorderConfig, callback: AsyncCallback<void>))  
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** prepare(config:

**需要权限：** ohos.permission.MICROPHONE

<!--Device-AudioRecorder-prepare(config: AudioRecorderConfig): void--><!--Device-AudioRecorder-prepare(config: AudioRecorderConfig): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AudioRecorderConfig](arkts-media-multimedia-media-audiorecorderconfig-i.md) | 是 | 配置录音的相关参数，包括音频输出URI、编码格式、采样率、声道数、输出格式等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied.<br>**适用版本：** 12+ |

<a id="release"></a>
## release

```TypeScript
release(): void
```

释放录音资源。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.release](@ohos.multimedia.media:media.AVRecorder.release(callback: AsyncCallback<void>))替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** release(callback:

<!--Device-AudioRecorder-release(): void--><!--Device-AudioRecorder-release(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

<a id="reset"></a>
## reset

```TypeScript
reset(): void
```

重置录音。

进行重置录音之前，需要先调用stop()停止录音。重置录音之后，需要调用prepare()设置录音参数项，才能再次进行录音。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.reset](@ohos.multimedia.media:media.AVRecorder.reset(callback: AsyncCallback<void>))替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** reset(callback:

<!--Device-AudioRecorder-reset(): void--><!--Device-AudioRecorder-reset(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

<a id="resume"></a>
## resume

```TypeScript
resume(): void
```

恢复录制，需要在'pause'事件成功触发后，才能调用resume方法。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.resume](@ohos.multimedia.media:media.AVRecorder.resume(callback: AsyncCallback<void>))替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** resume(callback:

<!--Device-AudioRecorder-resume(): void--><!--Device-AudioRecorder-resume(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

<a id="start"></a>
## start

```TypeScript
start(): void
```

开始录制，需在'prepare'事件成功触发后，才能调用start方法。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.start](@ohos.multimedia.media:media.AVRecorder.start(callback: AsyncCallback<void>))替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** start(callback:

<!--Device-AudioRecorder-start(): void--><!--Device-AudioRecorder-start(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

<a id="stop"></a>
## stop

```TypeScript
stop(): void
```

停止录音。

> **说明：**  
> > 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [AVRecorder.stop](@ohos.multimedia.media:media.AVRecorder.stop(callback: AsyncCallback<void>))替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** stop(callback:

<!--Device-AudioRecorder-stop(): void--><!--Device-AudioRecorder-stop(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

