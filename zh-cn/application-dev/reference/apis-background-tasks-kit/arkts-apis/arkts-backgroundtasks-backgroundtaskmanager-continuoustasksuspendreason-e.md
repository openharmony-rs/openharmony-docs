# ContinuousTaskSuspendReason

长时任务暂停原因。

**起始版本：** 20

<!--Device-backgroundTaskManager-export enum ContinuousTaskSuspendReason--><!--Device-backgroundTaskManager-export enum ContinuousTaskSuspendReason-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED

```TypeScript
SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4
```

申请DATA_TRANSFER类型长时任务，但是数据传输速率低。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION

```TypeScript
SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5
```

申请AUDIO_PLAYBACK类型长时任务，但是未接入[AVSession](../../../../media/avsession/avsession-overview.md)。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING

```TypeScript
SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6
```

申请AUDIO_PLAYBACK类型长时任务，但是未播放音视频。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING

```TypeScript
SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7
```

申请AUDIO_RECORDING类型长时任务，但是未录制。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_LOCATION_NOT_USED

```TypeScript
SYSTEM_SUSPEND_LOCATION_NOT_USED = 8
```

申请LOCATION类型长时任务，但是未使用定位导航。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_LOCATION_NOT_USED = 8--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_LOCATION_NOT_USED = 8-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_BLUETOOTH_NOT_USED

```TypeScript
SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9
```

申请BLUETOOTH_INTERACTION类型长时任务，但是未使用蓝牙相关业务。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED

```TypeScript
SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10
```

申请MULTI_DEVICE_CONNECTION类型长时任务，但是未使用多设备互联。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_USED_ILLEGALLY

```TypeScript
SYSTEM_SUSPEND_USED_ILLEGALLY = 11
```

使用非法类型的长时任务，如申请AUDIO_PLAYBACK类型长时任务，但是使用音视频播放及定位导航业务。预留接口，暂未启用。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_USED_ILLEGALLY = 11--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_USED_ILLEGALLY = 11-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING

```TypeScript
SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12
```

系统高负载暂停长时任务。预留接口，暂未启用。

**起始版本：** 20

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_VOIP_NOT_USED

```TypeScript
SYSTEM_SUSPEND_VOIP_NOT_USED = 13
```

申请VOIP类型长时任务，但是未检测到音频流或者录音流。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_VOIP_NOT_USED = 13--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_VOIP_NOT_USED = 13-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_BLUETOOTH_DATA_NOT_EXIST

```TypeScript
SYSTEM_SUSPEND_BLUETOOTH_DATA_NOT_EXIST = 14
```

申请BLUETOOTH_INTERACTION类型长时任务，但是一段时间没有蓝牙数据流。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_BLUETOOTH_DATA_NOT_EXIST = 14--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_BLUETOOTH_DATA_NOT_EXIST = 14-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_POSITION_NOT_MOVED

```TypeScript
SYSTEM_SUSPEND_POSITION_NOT_MOVED = 15
```

申请LOCATION类型长时任务，但是一段时间内设备处于绝对静止状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_POSITION_NOT_MOVED = 15--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_POSITION_NOT_MOVED = 15-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_PLAYBACK_MUTE

```TypeScript
SYSTEM_SUSPEND_AUDIO_PLAYBACK_MUTE = 16
```

申请AUDIO_PLAYBACK类型长时任务，但是一段时间内处于整机静音状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_PLAYBACK_MUTE = 16--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_AUDIO_PLAYBACK_MUTE = 16-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_NEARLINK_NOT_USED

```TypeScript
SYSTEM_SUSPEND_NEARLINK_NOT_USED = 17
```

申请星闪类型长时任务，但是一段时间没有星闪配对连接。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_NEARLINK_NOT_USED = 17--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_NEARLINK_NOT_USED = 17-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_NEARLINK_DATA_NOT_EXIST

```TypeScript
SYSTEM_SUSPEND_NEARLINK_DATA_NOT_EXIST = 18
```

申请星闪类型长时任务，但是一段时间没有星闪数据流。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_NEARLINK_DATA_NOT_EXIST = 18--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_NEARLINK_DATA_NOT_EXIST = 18-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_USER_UNAUTHORIZED

```TypeScript
SYSTEM_SUSPEND_USER_UNAUTHORIZED = 19
```

申请特殊场景类型长时任务，但是用户未授权。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_USER_UNAUTHORIZED = 19--><!--Device-ContinuousTaskSuspendReason-SYSTEM_SUSPEND_USER_UNAUTHORIZED = 19-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

