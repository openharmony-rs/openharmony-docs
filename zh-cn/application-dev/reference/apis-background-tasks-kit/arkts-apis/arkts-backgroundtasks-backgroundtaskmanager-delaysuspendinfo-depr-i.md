# DelaySuspendInfo

延迟挂起信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [DelaySuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-delaysuspendinfo-depr-i.md)

<!--Device-backgroundTaskManager-interface DelaySuspendInfo--><!--Device-backgroundTaskManager-interface DelaySuspendInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## actualDelayTime

```TypeScript
actualDelayTime: number
```

应用的实际挂起延迟时间，单位：ms。

一般情况下默认值为180000，低电量（依据系统低电量广播）时默认值为60000。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** DelaySuspendInfo

<!--Device-DelaySuspendInfo-actualDelayTime: number--><!--Device-DelaySuspendInfo-actualDelayTime: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## requestId

```TypeScript
requestId: number
```

延迟挂起的请求ID。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** DelaySuspendInfo

<!--Device-DelaySuspendInfo-requestId: number--><!--Device-DelaySuspendInfo-requestId: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

