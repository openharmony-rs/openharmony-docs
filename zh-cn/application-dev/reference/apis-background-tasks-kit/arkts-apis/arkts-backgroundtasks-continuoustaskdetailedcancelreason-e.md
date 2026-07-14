# ContinuousTaskDetailedCancelReason

长时任务取消详细原因。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## USER_CANCEL_REMOVE_NOTIFICATION

```TypeScript
USER_CANCEL_REMOVE_NOTIFICATION = 3
```

用户移除通知。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED

```TypeScript
SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4
```

申请DATA_TRANSFER类型长时任务，但是数据传输速率低。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION

```TypeScript
SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5
```

申请AUDIO_PLAYBACK类型长时任务，但是未接入[AVSession](../../../../media/avsession/avsession-overview.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6
```

申请AUDIO_PLAYBACK类型长时任务，但是未播放音视频。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7
```

申请AUDIO_RECORDING类型长时任务，但是未录制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_LOCATION

```TypeScript
SYSTEM_CANCEL_NOT_USE_LOCATION = 8
```

申请LOCATION类型长时任务，但是未使用定位导航。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_BLUETOOTH

```TypeScript
SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9
```

申请BLUETOOTH_INTERACTION类型长时任务，但是未使用蓝牙相关业务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE

```TypeScript
SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10
```

申请MULTI_DEVICE_CONNECTION类型长时任务，但是未使用多设备互联。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_USE_ILLEGALLY

```TypeScript
SYSTEM_CANCEL_USE_ILLEGALLY = 11
```

使用非法类型的长时任务，如申请AUDIO_PLAYBACK类型长时任务，但是使用音视频播放及定位导航业务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_DATA_TRANSFER_NOT_UPDATE

```TypeScript
SYSTEM_CANCEL_DATA_TRANSFER_NOT_UPDATE = 12
```

申请DATA_TRANSFER类型长时任务，但是进度长时间（首次更新超过10分钟）未更新。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_VOIP_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_VOIP_NOT_RUNNING = 13
```

申请VOIP类型长时任务，但是未检测到音频流或者录音流。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_USER_UNAUTHORIZED

```TypeScript
SYSTEM_CANCEL_USER_UNAUTHORIZED = 14
```

申请特殊场景类型长时任务，但是用户未授权。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

