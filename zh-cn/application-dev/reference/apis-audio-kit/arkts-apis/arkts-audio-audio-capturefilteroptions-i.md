# CaptureFilterOptions

待录制的播放音频流的筛选信息。

**起始版本：** 10

**废弃版本：** 12

**替代接口：** OH_AVScreenCapture in native interface.

<!--Device-audio-interface CaptureFilterOptions--><!--Device-audio-interface CaptureFilterOptions-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
import { audioHaptic } from '@kit.AudioKit';
```

## usages

```TypeScript
usages: Array<StreamUsage>
```

Filter by stream usages. But not allow to capture voice streams.

**类型：** Array&lt;[StreamUsage](arkts-audio-audio-streamusage-e.md)&gt;

**起始版本：** 11

**废弃版本：** 12

**替代接口：** OH_AVScreenCapture in native interface.

<!--Device-CaptureFilterOptions-usages: Array<StreamUsage>--><!--Device-CaptureFilterOptions-usages: Array<StreamUsage>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

