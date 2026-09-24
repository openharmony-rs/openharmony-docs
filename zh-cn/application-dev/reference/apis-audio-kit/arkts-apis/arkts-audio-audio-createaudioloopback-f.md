# createAudioLoopback

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## createAudioLoopback

```TypeScript
function createAudioLoopback(mode: AudioLoopbackMode): Promise<AudioLoopback>
```

创建音频返听器。使用Promise异步回调。

在使用createAudioLoopback接口之前，需先通过[isAudioLoopbackSupported](arkts-audio-audio-audiostreammanager-i.md#isaudioloopbacksupported)查询系统返听能力。

**起始版本：** 20

**需要权限：** 
- API版本27+：N/A
- API版本20-26：ohos.permission.MICROPHONE

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
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied.<br>**适用版本：** 20 - 26.0.0 |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Unsupported API.<br>**适用版本：** 20 - 26.0.0 |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Loopback mode is unsupported. |

**示例**
