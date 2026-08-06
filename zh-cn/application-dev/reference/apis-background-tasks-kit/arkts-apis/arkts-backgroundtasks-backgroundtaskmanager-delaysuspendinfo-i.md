# DelaySuspendInfo

短时任务信息。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-backgroundTaskManager-interface DelaySuspendInfo--><!--Device-backgroundTaskManager-interface DelaySuspendInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## actualDelayTime

```TypeScript
actualDelayTime: int
```

Actual duration of the transient task requested by the application, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_Unit:ms **说明：** 申请时间最长为3分钟，低电量（[BatteryCapacityLevel]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_为LEVEL\_LOW） 时最长为1分钟。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-DelaySuspendInfo-actualDelayTime: int--><!--Device-DelaySuspendInfo-actualDelayTime: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## requestId

```TypeScript
requestId: int
```

应用实际申请的短时任务时间，单位：ms。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-DelaySuspendInfo-requestId: int--><!--Device-DelaySuspendInfo-requestId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

