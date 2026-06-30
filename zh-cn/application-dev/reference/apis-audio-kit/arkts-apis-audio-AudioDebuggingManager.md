# Interface (AudioDebuggingManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

音频调试管理器，用于音频运行时调试，包括获取快照信息等功能，用于定位音频播放、录音、耳返、会话等场景中的异常问题。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - **ArkTS-Dyn起始版本：** 26.0.0
> - **ArkTS-Sta起始版本：** 26.0.0

## 导入模块

```ts
import { audio } from '@kit.AudioKit';
```

## printAppInfo

ArkTS-Dyn: printAppInfo(fd: number): void

ArkTS-Sta: printAppInfo(fd: int): void

打印当前进程中所有音频模块的快照信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| fd | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志
debugManager.printAppInfo(-1);
```

## printRendererInfo

ArkTS-Dyn: printRendererInfo(renderer: AudioRenderer, fd: number): void

ArkTS-Sta: printRendererInfo(renderer: AudioRenderer, fd: int): void

打印指定音频播放实例的快照信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| renderer | [AudioRenderer](arkts-apis-audio-AudioRenderer.md) | 是 | 目标音频播放实例。 |
| fd | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志
debugManager.printRendererInfo(renderer, -1);
```

## printCapturerInfo

ArkTS-Dyn: printCapturerInfo(capturer: AudioCapturer, fd: number): void

ArkTS-Sta: printCapturerInfo(capturer: AudioCapturer, fd: int): void

打印指定录音实例的快照信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| capturer | [AudioCapturer](arkts-apis-audio-AudioCapturer.md) | 是 | 目标录音实例。 |
| fd | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志
debugManager.printCapturerInfo(capturer, -1);
```

## printLoopbackInfo

ArkTS-Dyn: printLoopbackInfo(loopback: AudioLoopback, fd: number): void

ArkTS-Sta: printLoopbackInfo(loopback: AudioLoopback, fd: int): void

打印指定耳返实例的快照信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| loopback | [AudioLoopback](arkts-apis-audio-AudioLoopback.md) | 是 | 目标耳返实例。 |
| fd | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志
debugManager.printLoopbackInfo(loopback, -1);
```

## printSessionInfo

ArkTS-Dyn: printSessionInfo(session: AudioSessionManager, fd: number): void

ArkTS-Sta: printSessionInfo(session: AudioSessionManager, fd: int): void

打印指定会话管理器实例的快照信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | ---- |
| session | [AudioSessionManager](arkts-apis-audio-AudioSessionManager.md) | 是 | 目标会话管理器实例。 |
| fd | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

const audioManager = audio.getAudioManager();
const debugManager = audioManager.getDebuggingManager();

// 输出到日志
debugManager.printSessionInfo(session, -1);
```
