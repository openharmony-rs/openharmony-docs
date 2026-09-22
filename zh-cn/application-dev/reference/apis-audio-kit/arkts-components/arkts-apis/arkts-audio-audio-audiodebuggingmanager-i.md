# AudioDebuggingManager

```TypeScript
interface AudioDebuggingManager
```

AudioDebuggingManager（音频快照）提供音频运行时调试功能，用于获取音频快照信息，帮助开发者定位音频播放、录音、耳返、会话等场景中的异常问题。AudioDebuggingManager是对当前进程中音频各模块运行状态的瞬时记录，涵盖音频流参数、通路状态、音量信息、焦点状态、错误记录等关键数据。开发者可通过快照在不影响业务逻辑的前提下，快速了解音频系统的内部运行情况，用于排查无声、音量异常、焦点丢失、录音卡顿等问题。使用调试接口时，需先通过[getDebuggingManager](arkts-audio-audio-audiomanager-i.md#getdebuggingmanager)获取AudioDebuggingManager实例（单例），再通过该实例调用应用快照、播放快照、录音快照、耳返快照、会话快照等接口，将快照信息输出到指定文件描述符或运行日志。

> **说明：** 
> 
> 快照信息的内容和格式后续会根据开发者使用情况和反馈建议优化调整，随版本迭代可能发生变化，所以仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## printAppInfo

```TypeScript
printAppInfo(fd: number): void
```

打印当前应用进程的完整音频运行时快照。快照包含所有播放流、录音流和音频会话信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

## printCapturerInfo

```TypeScript
printCapturerInfo(capturer: AudioCapturer, fd: number): void
```

打印指定录音实例的完整音频运行时快照。快照包含流信息、通路信息、音量和设备信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturer | [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) | 是 | 目标录音实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

## printLoopbackInfo

```TypeScript
printLoopbackInfo(loopback: AudioLoopback, fd: number): void
```

打印指定耳返实例的完整音频运行时快照。快照包含耳返状态、设备和音效信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loopback | [AudioLoopback](arkts-audio-audio-audioloopback-i.md) | 是 | 目标耳返实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

## printRendererInfo

```TypeScript
printRendererInfo(renderer: AudioRenderer, fd: number): void
```

打印指定音频播放实例的完整音频运行时快照。快照包含流信息、通路信息、音量和设备信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| renderer | [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) | 是 | 目标音频播放实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

## printSessionInfo

```TypeScript
printSessionInfo(session: AudioSessionManager, fd: number): void
```

打印指定会话管理器实例的完整音频运行时快照。快照包含会话状态、场景、策略和设备信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [AudioSessionManager](arkts-audio-audio-audiosessionmanager-i.md) | 是 | 目标会话管理器实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |
