# IntervalInfo

开发者可以从回调函数中获取帧绘制的时间戳信息，包含当前帧到达的时间timestamp和下一帧预期到达的时间targetTimestamp。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-displaySync-interface IntervalInfo--><!--Device-displaySync-interface IntervalInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetTimestamp

```TypeScript
targetTimestamp: long
```

下一帧预期到达的时间（单位：纳秒）。系统启动以来的单调递增时间，值应大于timestamp。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-IntervalInfo-targetTimestamp: long--><!--Device-IntervalInfo-targetTimestamp: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: long
```

当前帧到达的时间（单位：纳秒）。系统启动以来的单调递增时间。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-IntervalInfo-timestamp: long--><!--Device-IntervalInfo-timestamp: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

