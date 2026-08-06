# AudioTimestampInfo

音频流时间戳和当前数据帧位置信息。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-audio-interface AudioTimestampInfo--><!--Device-audio-interface AudioTimestampInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## framePos

```TypeScript
readonly framePos: long
```

当前播放或者录制的数据帧位置。

**类型：** long

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-AudioTimestampInfo-readonly framePos: long--><!--Device-AudioTimestampInfo-readonly framePos: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## timestamp

```TypeScript
readonly timestamp: long
```

播放或者录制到当前数据帧位置时对应的时间戳，单位为纳秒。

**类型：** long

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-AudioTimestampInfo-readonly timestamp: long--><!--Device-AudioTimestampInfo-readonly timestamp: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

