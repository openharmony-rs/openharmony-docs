# TransientTaskInfo

所有短时任务信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-backgroundTaskManager-interface TransientTaskInfo--><!--Device-backgroundTaskManager-interface TransientTaskInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## remainingQuota

```TypeScript
remainingQuota: int
```

应用当日所剩余总配额，单位：ms。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TransientTaskInfo-remainingQuota: int--><!--Device-TransientTaskInfo-remainingQuota: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## transientTasks

```TypeScript
transientTasks: DelaySuspendInfo[]
```

当前已申请的所有短时任务信息。

**类型：** DelaySuspendInfo[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TransientTaskInfo-transientTasks: DelaySuspendInfo[]--><!--Device-TransientTaskInfo-transientTasks: DelaySuspendInfo[]-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

