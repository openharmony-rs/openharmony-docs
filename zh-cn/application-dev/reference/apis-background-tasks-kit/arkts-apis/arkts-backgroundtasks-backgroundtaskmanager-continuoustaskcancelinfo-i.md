# ContinuousTaskCancelInfo

长时任务取消信息。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-backgroundTaskManager-interface ContinuousTaskCancelInfo--><!--Device-backgroundTaskManager-interface ContinuousTaskCancelInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## detailedReason

```TypeScript
detailedReason?: ContinuousTaskDetailedCancelReason
```

长时任务取消详细原因。

**类型：** ContinuousTaskDetailedCancelReason

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskCancelInfo-detailedReason?: ContinuousTaskDetailedCancelReason--><!--Device-ContinuousTaskCancelInfo-detailedReason?: ContinuousTaskDetailedCancelReason-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## id

```TypeScript
id: int
```

被取消的长时任务 Id。

**类型：** int

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelInfo-id: int--><!--Device-ContinuousTaskCancelInfo-id: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## reason

```TypeScript
reason: ContinuousTaskCancelReason
```

长时任务取消原因。

**类型：** ContinuousTaskCancelReason

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelInfo-reason: ContinuousTaskCancelReason--><!--Device-ContinuousTaskCancelInfo-reason: ContinuousTaskCancelReason-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

