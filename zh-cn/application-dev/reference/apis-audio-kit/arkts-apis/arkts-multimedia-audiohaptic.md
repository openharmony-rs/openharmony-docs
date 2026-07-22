# @ohos.multimedia.audioHaptic

音振协同，表示在播放声音时，可同步发起振动。可用于来电通知、消息提醒等场景。

**设备行为差异：** 若设备无振动器件，将不会产生振动效果。

**起始版本：** 11

<!--Device-unnamed-declare namespace audioHaptic--><!--Device-unnamed-declare namespace audioHaptic-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## 导入模块

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md#getaudiohapticmanager) | 获取音振管理器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AudioHapticFileDescriptor](arkts-audio-audiohaptic-audiohapticfiledescriptor-i.md) | 描述音振文件描述符。 > **注意：**  >  > 开发者需要确保fd是可用的文件描述符，且offset和length的值都是正确的。 |
| [AudioHapticManager](arkts-audio-audiohaptic-audiohapticmanager-i.md) | 管理音振协同功能。在调用AudioHapticManager的接口前，需要先通过[getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md#getaudiohapticmanager)创建实例。 |
| [AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i.md) | 音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过[createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer)创建实例。 |
| [AudioHapticPlayerOptions](arkts-audio-audiohaptic-audiohapticplayeroptions-i.md) | 音振播放器选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i-sys.md) | 音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过[createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer)创建实例。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AudioHapticType](arkts-audio-audiohaptic-audiohaptictype-e.md) | 枚举，音振类型。 |
| [AudioLatencyMode](arkts-audio-audiohaptic-audiolatencymode-e.md) | 枚举，音频时延模式。 |

