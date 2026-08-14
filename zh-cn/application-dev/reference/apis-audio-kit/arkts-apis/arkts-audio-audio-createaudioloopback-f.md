# createAudioLoopback

## createAudioLoopback

```TypeScript
function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback>
```

创建音频返听器。使用Promise异步回调。 在使用createAudioLoopback接口之前，需先通过[isAudioLoopbackSupported](arkts-audio-audio-audiostreammanager-i.md#isAudioLoopbackSupported)查 询系统返听能力。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-audio-function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback>--><!--Device-audio-function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioLoopbackMode](arkts-audio-audio-audioloopbackmode-e.md) | 是 | 音频返听模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioLoopback](arkts-audio-audio-audioloopback-i.md)&gt; | Promise对象，成功将返回音频返听器对象，异常将返回error对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Loopback mode is unsupported. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioLoopback: audio.AudioLoopback;

audio.createAudioLoopback(audio.AudioLoopbackMode.HARDWARE).then((data) => {
  audioLoopback = data;
  console.info('AudioLoopback Created : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`AudioLoopback Created : ERROR : ${err}`);
});
```


## createAudioLoopback

```TypeScript
function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback | null>
```

Creates an &lt;b&gt;AudioLoopback&lt;/b&gt; instance, which provides low-latency in-ear monitoring using a fast capturer and renderer.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-audio-function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback | null>--><!--Device-audio-function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback | null>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioLoopbackMode](arkts-audio-audio-audioloopbackmode-e.md) | 是 | Audio loopback mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioLoopback](arkts-audio-audio-audioloopback-i.md) \| null&gt; | Promise used to return the &lt;b&gt;AudioLoopback&lt;/b&gt; instance, or null when an error happens. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Loopback mode is unsupported. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioLoopback: audio.AudioLoopback;

audio.createAudioLoopback(audio.AudioLoopbackMode.HARDWARE).then((data) => {
  if (data != null) {
    audioLoopback = data;
    console.info('AudioLoopback Created : SUCCESS');
  }
}).catch((err: BusinessError) => {
  console.error(`AudioLoopback Created : ERROR : ${err}`);
});
```

