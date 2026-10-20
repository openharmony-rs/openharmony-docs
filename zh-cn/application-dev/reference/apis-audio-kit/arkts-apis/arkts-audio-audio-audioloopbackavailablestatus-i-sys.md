# AudioLoopbackAvailableStatus（系统接口）

```TypeScript
interface AudioLoopbackAvailableStatus
```

定义全局音频返听的可用状态。

**起始版本：** 26.0.1

<!--Device-audio-interface AudioLoopbackAvailableStatus--><!--Device-audio-interface AudioLoopbackAvailableStatus-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## available

```TypeScript
available: boolean
```

可用状态。播控应用基于该状态确定用户开关音频返听的反馈。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopbackAvailableStatus-available: boolean--><!--Device-AudioLoopbackAvailableStatus-available: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## unavailableReason

```TypeScript
unavailableReason?: AudioLoopbackUnavailableReason
```

不可用原因。播控应用根据这些信息决定提示信息。<br>该参数仅在状态为不可用时存在。

**类型：** [AudioLoopbackUnavailableReason](arkts-audio-audio-audioloopbackunavailablereason-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopbackAvailableStatus-unavailableReason?: AudioLoopbackUnavailableReason--><!--Device-AudioLoopbackAvailableStatus-unavailableReason?: AudioLoopbackUnavailableReason-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
