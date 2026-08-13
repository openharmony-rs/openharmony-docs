# AudioTimestampInfo

音频流时间戳和当前数据帧位置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-audio-interface AudioTimestampInfo--><!--Device-audio-interface AudioTimestampInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## framePos

```TypeScript
readonly framePos: long
```

当前播放或者录制的数据帧位置。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioTimestampInfo-readonly framePos: long--><!--Device-AudioTimestampInfo-readonly framePos: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## timestamp

```TypeScript
readonly timestamp: long
```

播放或者录制到当前数据帧位置时对应的时间戳，单位为纳秒。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioTimestampInfo-readonly timestamp: long--><!--Device-AudioTimestampInfo-readonly timestamp: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

