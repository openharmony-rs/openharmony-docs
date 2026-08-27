# AudioRecorder


> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVRecorder](arkts-media-media-avrecorder-i.md)替代。
音频录制管理类，用于录制音频媒体。在调用AudioRecorder的方法前，需要先通过 [createAudioRecorder()](arkts-media-media-createaudiorecorder-f.md) 构建一个AudioRecorder实例。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [media](arkts-multimedia-media.md)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('stateChange')](arkts-media-media-avrecorder-i.md#onstatechange)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset'。  - 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。  - 'start' ：完成start调用，音频录制开始，触发该事件。  - 'pause' ：完成pause调用，音频暂停录制，触发该事件。  - 'resume' ：完成resume调用，音频恢复录制，触发该事件。  - 'stop' ：完成stop调用，音频停止录制，触发该事件。  - 'release' ：完成release调用，音频释放录制资源，触发该事件。  - 'reset' ：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () = & gt; void | 是 | 录制事件回调方法。 |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('stateChange')](arkts-media-media-avrecorder-i.md#onstatechange)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset'。  - 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。  - 'start' ：完成start调用，音频录制开始，触发该事件。  - 'pause' ：完成pause调用，音频暂停录制，触发该事件。  - 'resume' ：完成resume调用，音频恢复录制，触发该事件。  - 'stop' ：完成stop调用，音频停止录制，触发该事件。  - 'release' ：完成release调用，音频释放录制资源，触发该事件。  - 'reset' ：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () = & gt; void | 是 | 录制事件回调方法。 |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('stateChange')](arkts-media-media-avrecorder-i.md#onstatechange)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset'。  - 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。  - 'start' ：完成start调用，音频录制开始，触发该事件。  - 'pause' ：完成pause调用，音频暂停录制，触发该事件。  - 'resume' ：完成resume调用，音频恢复录制，触发该事件。  - 'stop' ：完成stop调用，音频停止录制，触发该事件。  - 'release' ：完成release调用，音频释放录制资源，触发该事件。  - 'reset' ：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () = & gt; void | 是 | 录制事件回调方法。 |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('stateChange')](arkts-media-media-avrecorder-i.md#onstatechange)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset'。  - 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。  - 'start' ：完成start调用，音频录制开始，触发该事件。  - 'pause' ：完成pause调用，音频暂停录制，触发该事件。  - 'resume' ：完成resume调用，音频恢复录制，触发该事件。  - 'stop' ：完成stop调用，音频停止录制，触发该事件。  - 'release' ：完成release调用，音频释放录制资源，触发该事件。  - 'reset' ：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () = & gt; void | 是 | 录制事件回调方法。 |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('stateChange')](arkts-media-media-avrecorder-i.md#onstatechange)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset'。  - 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。  - 'start' ：完成start调用，音频录制开始，触发该事件。  - 'pause' ：完成pause调用，音频暂停录制，触发该事件。  - 'resume' ：完成resume调用，音频恢复录制，触发该事件。  - 'stop' ：完成stop调用，音频停止录制，触发该事件。  - 'release' ：完成release调用，音频释放录制资源，触发该事件。  - 'reset' ：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () = & gt; void | 是 | 录制事件回调方法。 |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('stateChange')](arkts-media-media-avrecorder-i.md#onstatechange)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset'。  - 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。  - 'start' ：完成start调用，音频录制开始，触发该事件。  - 'pause' ：完成pause调用，音频暂停录制，触发该事件。  - 'resume' ：完成resume调用，音频恢复录制，触发该事件。  - 'stop' ：完成stop调用，音频停止录制，触发该事件。  - 'release' ：完成release调用，音频释放录制资源，触发该事件。  - 'reset' ：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () = & gt; void | 是 | 录制事件回调方法。 |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

开始订阅音频录制事件。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('stateChange')](arkts-media-media-avrecorder-i.md#onstatechange)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset' | 是 | 录制事件回调类型，支持的事件包括：'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset'。  - 'prepare' ：完成prepare调用，音频录制参数设置完成，触发该事件。  - 'start' ：完成start调用，音频录制开始，触发该事件。  - 'pause' ：完成pause调用，音频暂停录制，触发该事件。  - 'resume' ：完成resume调用，音频恢复录制，触发该事件。  - 'stop' ：完成stop调用，音频停止录制，触发该事件。  - 'release' ：完成release调用，音频释放录制资源，触发该事件。  - 'reset' ：完成reset调用，音频重置为初始状态，触发该事件。 |
| callback | () = & gt; void | 是 | 录制事件回调方法。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

开始订阅音频录制错误事件，当上报error错误事件后，用户需处理error事件，退出录制操作。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.on('error')](arkts-media-media-avrecorder-i.md#onerror)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [on](arkts-media-media-avrecorder-i.md#onerror)(type: 'error', callback: ErrorCallback)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 录制错误事件回调类型'error'。   - 'error'：音频录制过程中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 录制错误事件回调方法。 |

## pause

```TypeScript
pause(): void
```

暂停录制，需要在'start'事件成功触发后，才能调用pause方法。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.pause](arkts-media-media-avrecorder-i.md#pause)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [pause](arkts-media-media-avrecorder-i.md#pause)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**示例**

```TypeScript
audioPlayer.on('pause', () => {    // 设置'pause'事件回调。
  console.info('audio pause called');
});
audioPlayer.pause();
```

```TypeScript
audioRecorder.on('pause', () => {    // 设置'pause'事件回调。
  console.info('audio recorder pause called');
});
audioRecorder.pause();
```

## prepare

```TypeScript
prepare(config: AudioRecorderConfig): void
```

录音准备。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.prepare](arkts-media-media-avrecorder-i.md#prepare)
> 替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [prepare](arkts-media-media-avrecorder-i.md#prepare)(config: AVRecorderConfig, callback: AsyncCallback&lt;void&gt;)

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AudioRecorderConfig](arkts-media-media-audiorecorderconfig-i.md) | 是 | 配置录音的相关参数，包括音频输出URI、编码格式、采样率、声道数、输出格式等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let audioRecorderConfig: media.AudioRecorderConfig = {
  audioEncoder : media.AudioEncoder.AAC_LC,
  audioEncodeBitRate : 64000,
  audioSampleRate : 44100,
  numberOfChannels : 2,
  format : media.AudioOutputFormat.AAC_ADTS,
  uri : 'fd://1',       // fd通过fs.open()获取。文件需先由调用者创建，并给予适当的权限。
  location : { latitude : 30, longitude : 130},
};
audioRecorder.on('prepare', () => {    // 设置'prepare'事件回调。
  console.info('prepare called');
});
audioRecorder.prepare(audioRecorderConfig);
```

## release

```TypeScript
release(): void
```

释放录音资源。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.release](arkts-media-media-avrecorder-i.md#release)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [release](arkts-media-media-avrecorder-i.md#release)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**示例**

```TypeScript
audioPlayer.release();
audioPlayer = undefined;
```

```TypeScript
audioRecorder.on('release', () => {    // 设置'release'事件回调。
  console.info('audio recorder release called');
});
audioRecorder.release();
audioRecorder = undefined;
```

## reset

```TypeScript
reset(): void
```

重置录音。进行重置录音之前，需要先调用stop()停止录音。重置录音之后，需要调用prepare()设置录音参数项，才能再次进行录音。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.reset](arkts-media-media-avrecorder-i.md#reset)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [reset](arkts-media-media-avrecorder-i.md#reset)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**示例**

```TypeScript
audioPlayer.on('reset', () => {    // 设置'reset'事件回调。
  console.info('audio reset called');
});
audioPlayer.reset();
```

```TypeScript
audioRecorder.on('reset', () => {    // 设置'reset'事件回调。
  console.info('audio recorder reset called');
});
audioRecorder.reset();
```

## resume

```TypeScript
resume(): void
```

恢复录制，需要在'pause'事件成功触发后，才能调用resume方法。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.resume](arkts-media-media-avrecorder-i.md#resume)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [resume](arkts-media-media-avrecorder-i.md#resume)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**示例**

```TypeScript
audioRecorder.on('resume', () => {    // 设置'resume'事件回调。
  console.info('audio recorder resume called');
});
audioRecorder.resume();
```

## start

```TypeScript
start(): void
```

开始录制，需在'prepare'事件成功触发后，才能调用start方法。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.start](arkts-media-media-avrecorder-i.md#start)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [start](arkts-media-media-avrecorder-i.md#start)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**示例**

```TypeScript
audioRecorder.on('start', () => {    // 设置'start'事件回调。
  console.info('audio recorder start called');
});
audioRecorder.start();
```

## stop

```TypeScript
stop(): void
```

停止录音。

> **说明：**
> 
> 从API version 6开始支持，从API version 9开始废弃，建议使用
> [AVRecorder.stop](arkts-media-media-avrecorder-i.md#stop)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [stop](arkts-media-media-avrecorder-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**示例**

```TypeScript
audioPlayer.on('stop', () => {    // 设置'stop'事件回调。
  console.info('audio stop called');
});
audioPlayer.stop();
```

```TypeScript
audioRecorder.on('stop', () => {    // 设置'stop'事件回调。
  console.info('audio recorder stop called');
});
audioRecorder.stop();
```
