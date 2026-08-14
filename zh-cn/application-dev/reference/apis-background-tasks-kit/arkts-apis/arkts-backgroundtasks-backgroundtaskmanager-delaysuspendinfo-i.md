# DelaySuspendInfo

短时任务信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-backgroundTaskManager-interface DelaySuspendInfo--><!--Device-backgroundTaskManager-interface DelaySuspendInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## actualDelayTime

```TypeScript
actualDelayTime: int
```

Actual duration of the transient task requested by the application, in milliseconds. &lt;br&gt;Unit:ms **说明：** 申请时间最长为3分钟，低电量（[BatteryCapacityLevel](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-batteryinfo-batterycapacitylevel-e.md#BatteryCapacityLevel)为LEVEL_LOW） 时最长为1分钟。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DelaySuspendInfo-actualDelayTime: int--><!--Device-DelaySuspendInfo-actualDelayTime: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## requestId

```TypeScript
requestId: int
```

应用实际申请的短时任务时间，单位：ms。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DelaySuspendInfo-requestId: int--><!--Device-DelaySuspendInfo-requestId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

