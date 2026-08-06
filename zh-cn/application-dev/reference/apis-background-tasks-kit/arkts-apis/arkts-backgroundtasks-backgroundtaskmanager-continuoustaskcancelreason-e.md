# ContinuousTaskCancelReason

长时任务取消原因。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-backgroundTaskManager-export enum ContinuousTaskCancelReason--><!--Device-backgroundTaskManager-export enum ContinuousTaskCancelReason-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## USER_CANCEL

```TypeScript
USER_CANCEL = 1
```

用户取消。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-USER_CANCEL = 1--><!--Device-ContinuousTaskCancelReason-USER_CANCEL = 1-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL

```TypeScript
SYSTEM_CANCEL = 2
```

系统取消。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL = 2--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL = 2-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## USER_CANCEL_REMOVE_NOTIFICATION

```TypeScript
USER_CANCEL_REMOVE_NOTIFICATION = 3
```

用户移除通知。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-USER_CANCEL_REMOVE_NOTIFICATION = 3--><!--Device-ContinuousTaskCancelReason-USER_CANCEL_REMOVE_NOTIFICATION = 3-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED

```TypeScript
SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4
```

申请DATA\_TRANSFER类型长时任务，但是数据传输速率低。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION

```TypeScript
SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5
```

申请AUDIO\_PLAYBACK类型长时任务，但是未接入\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6
```

申请AUDIO\_PLAYBACK类型长时任务，但是未播放音视频。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7
```

申请AUDIO\_RECORDING类型长时任务，但是未录制。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_LOCATION

```TypeScript
SYSTEM_CANCEL_NOT_USE_LOCATION = 8
```

申请LOCATION类型长时任务，但是未使用定位导航。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_NOT_USE_LOCATION = 8--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_NOT_USE_LOCATION = 8-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_BLUETOOTH

```TypeScript
SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9
```

申请BLUETOOTH\_INTERACTION类型长时任务，但是未使用蓝牙相关业务。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE

```TypeScript
SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10
```

申请MULTI\_DEVICE\_CONNECTION类型长时任务，但是未使用多设备互联。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_USE_ILLEGALLY

```TypeScript
SYSTEM_CANCEL_USE_ILLEGALLY = 11
```

使用非法类型的长时任务，如申请AUDIO\_PLAYBACK类型长时任务，但是使用音视频播放及定位导航业务。预留接口，暂未启用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_USE_ILLEGALLY = 11--><!--Device-ContinuousTaskCancelReason-SYSTEM_CANCEL_USE_ILLEGALLY = 11-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

