# ContinuousTaskCancelReason

Describes the reason for canceling a continuous task.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## USER_CANCEL

```TypeScript
USER_CANCEL = 1
```

The task is canceled by the user.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL

```TypeScript
SYSTEM_CANCEL = 2
```

The task is canceled by the system.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## USER_CANCEL_REMOVE_NOTIFICATION

```TypeScript
USER_CANCEL_REMOVE_NOTIFICATION = 3
```

User removal notification. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED

```TypeScript
SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4
```

A continuous task of the DATA_TRANSFER type is requested, but the data transmission rate is low. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION

```TypeScript
SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5
```

A continuous task of the AUDIO_PLAYBACK type is requested, but the [AVSession](../../../media/avsession/avsession-overview.md) is not accessed. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6
```

A continuous task of the AUDIO_PLAYBACK type is requested, but the audio and video are not played. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7
```

A continuous task of the AUDIO_RECORDING type is requested, but audio recording is not in progress. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_LOCATION

```TypeScript
SYSTEM_CANCEL_NOT_USE_LOCATION = 8
```

A continuous task of the **LOCATION** type is requested, but the location service is not in use. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_BLUETOOTH

```TypeScript
SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9
```

A continuous task of the BLUETOOTH_INTERACTION type is requested, but Bluetooth-related services are not used. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE

```TypeScript
SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10
```

A continuous task of the MULTI_DEVICE_CONNECTION type is requested, but multi-device connection is not used. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_USE_ILLEGALLY

```TypeScript
SYSTEM_CANCEL_USE_ILLEGALLY = 11
```

A continuous task of an invalid type is used. For example, a continuous task of the **AUDIO_PLAYBACK** type is requested, but the audio playback and location services are in use. This value is reserved.

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
