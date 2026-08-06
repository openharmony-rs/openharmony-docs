# IntervalInfo

开发者可以从订阅函数中获取帧绘制的时间戳信息，包含当前帧到达的时间timestamp和下一帧预期到达的时间targetTimestamp。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-displaySync-interface IntervalInfo--><!--Device-displaySync-interface IntervalInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetTimestamp

```TypeScript
targetTimestamp: long
```

下一帧预期到达的时间（单位：纳秒）。

**类型：** long

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-IntervalInfo-targetTimestamp: long--><!--Device-IntervalInfo-targetTimestamp: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: long
```

当前帧到达的时间（单位：纳秒）。

**类型：** long

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-IntervalInfo-timestamp: long--><!--Device-IntervalInfo-timestamp: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

