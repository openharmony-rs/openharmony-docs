# @ohos.multimedia.audioHaptic

音振协同


**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## 导入模块

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md) | 获取音振管理器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AudioHapticFileDescriptor](arkts-audio-audiohaptic-audiohapticfiledescriptor-i.md) | 描述音振文件描述符。 |
| [AudioHapticManager](arkts-audio-audiohaptic-audiohapticmanager-i.md) | 管理音振协同功能。在调用AudioHapticManager的接口前，需要先通过[getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md)创建实例。 |
| [AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i.md) | 音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过 [createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer)创建 实例。 |
| [AudioHapticPlayerOptions](arkts-audio-audiohaptic-audiohapticplayeroptions-i.md) | 音振播放器选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i-sys.md) | 音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过 [createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer)创建 实例。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AudioHapticType](arkts-audio-audiohaptic-audiohaptictype-e.md) | 枚举，音振类型。@enum { number } |
| [AudioLatencyMode](arkts-audio-audiohaptic-audiolatencymode-e.md) | 枚举，音频时延模式。@enum {number} |
