# AudioTimestampInfo

音频流时间戳和当前数据帧位置信息。

**起始版本：** 19

<!--Device-audio-interface AudioTimestampInfo--><!--Device-audio-interface AudioTimestampInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## framePos

```TypeScript
readonly framePos: number
```

当前播放或者录制的数据帧位置。

**类型：** number

**起始版本：** 19

<!--Device-AudioTimestampInfo-readonly framePos: long--><!--Device-AudioTimestampInfo-readonly framePos: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## timestamp

```TypeScript
readonly timestamp: number
```

播放或者录制到当前数据帧位置时对应的时间戳，单位为纳秒。

**类型：** number

**起始版本：** 19

<!--Device-AudioTimestampInfo-readonly timestamp: long--><!--Device-AudioTimestampInfo-readonly timestamp: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

