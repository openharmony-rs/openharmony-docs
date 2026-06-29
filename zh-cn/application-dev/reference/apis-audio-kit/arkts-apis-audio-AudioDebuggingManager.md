# AudioDebuggingManager
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

音频调试管理器，用于音频运行时调试，包括获取快照信息等功能，用于定位音频播放、录音、耳返、会话等场景中的异常问题。

**起始版本：** 26.0.0

## 导入模块

```ts
import { audio } from '@kit.AudioKit';
```

## printAppInfo

printAppInfo(fd: number): void

打印当前进程中所有音频模块的快照信息。快照包含所有播放流、录音流和音频会话信息。快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志。
debugManager.printAppInfo(-1);
```

## printRendererInfo

printRendererInfo(renderer: AudioRenderer, fd: number): void

打印指定音频播放实例的快照信息。快照包含流信息、通路信息、音量和设备信息。快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| renderer | [AudioRenderer](arkts-apis-audio-AudioRenderer.md) | 是 | 目标音频播放实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志。
debugManager.printRendererInfo(renderer, -1);
```

## printCapturerInfo

printCapturerInfo(capturer: AudioCapturer, fd: number): void

打印指定录音实例的快照信息。快照包含流信息、通路信息、音量和设备信息。快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| capturer | [AudioCapturer](arkts-apis-audio-AudioCapturer.md) | 是 | 目标录音实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志。
debugManager.printCapturerInfo(capturer, -1);
```

## printLoopbackInfo

printLoopbackInfo(loopback: AudioLoopback, fd: number): void

打印指定耳返实例的快照信息。快照包含耳返状态、设备和音效信息。快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| loopback | [AudioLoopback](arkts-apis-audio-AudioLoopback.md) | 是 | 目标耳返实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志。
debugManager.printLoopbackInfo(loopback, -1);
```

## printSessionInfo

printSessionInfo(session: AudioSessionManager, fd: number): void

打印指定会话管理器实例的快照信息。快照包含会话状态、场景、策略和设备信息。快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| session | [AudioSessionManager](arkts-apis-audio-AudioSessionManager.md) | 是 | 目标会话管理器实例。 |
| fd | number | 是 | 文件描述符，指定快照信息的写入位置。小于0或不可写时，快照信息将输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志。
debugManager.printSessionInfo(session, -1);
```
