# ContinuousTaskSuspendReason

Describes the reason why a continuous task is suspended.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED

```TypeScript
SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED = 4
```

A continuous task of the **DATA_TRANSFER** type is requested, but the data transmission rate is low.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION

```TypeScript
SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION = 5
```

A continuous task of the **AUDIO_PLAYBACK** type is requested, but [AVSession](../../../media/avsession/avsession-overview.md) is not accessed.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING

```TypeScript
SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING = 6
```

A continuous task of the **AUDIO_PLAYBACK** type is requested, but audio playback is not in progress.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING

```TypeScript
SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING = 7
```

A continuous task of the **AUDIO_RECORDING** type is requested, but audio recording is not in progress.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_LOCATION_NOT_USED

```TypeScript
SYSTEM_SUSPEND_LOCATION_NOT_USED = 8
```

A continuous task of the **LOCATION** type is requested, but the location service is not in use.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_BLUETOOTH_NOT_USED

```TypeScript
SYSTEM_SUSPEND_BLUETOOTH_NOT_USED = 9
```

A continuous task of the **BLUETOOTH_INTERACTION** type is requested, but Bluetooth is not in use.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED

```TypeScript
SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED = 10
```

A continuous task of the **MULTI_DEVICE_CONNECTION** type is requested, but the multi-device connection service is not in use.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_USED_ILLEGALLY

```TypeScript
SYSTEM_SUSPEND_USED_ILLEGALLY = 11
```

A continuous task of an invalid type is used. For example, a continuous task of the **AUDIO_PLAYBACK** type is requested, but the audio playback and location services are in use. This value is reserved.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING

```TypeScript
SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING = 12
```

A continuous task is suspended due to high system load. This value is reserved.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_VOIP_NOT_USED

```TypeScript
SYSTEM_SUSPEND_VOIP_NOT_USED = 13
```

A continuous task of the **VOIP** type is requested, but no audio stream or recording stream is in progress.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_BLUETOOTH_DATA_NOT_EXIST

```TypeScript
SYSTEM_SUSPEND_BLUETOOTH_DATA_NOT_EXIST = 14
```

A continuous task of the **BLUETOOTH_INTERACTION** type is requested, but there is no Bluetooth data flow for a period of time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_POSITION_NOT_MOVED

```TypeScript
SYSTEM_SUSPEND_POSITION_NOT_MOVED = 15
```

A continuous task of the **LOCATION** type is requested, but the device is absolutely still for a period of time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_AUDIO_PLAYBACK_MUTE

```TypeScript
SYSTEM_SUSPEND_AUDIO_PLAYBACK_MUTE = 16
```

A continuous task of the **AUDIO_PLAYBACK** type is requested, but the device is muted for a period of time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_NEARLINK_NOT_USED

```TypeScript
SYSTEM_SUSPEND_NEARLINK_NOT_USED = 17
```

No nearlink connection for a period of time when request nearlink mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_NEARLINK_DATA_NOT_EXIST

```TypeScript
SYSTEM_SUSPEND_NEARLINK_DATA_NOT_EXIST = 18
```

No nearlink data for a period of time when request nearlink mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_USER_UNAUTHORIZED

```TypeScript
SYSTEM_SUSPEND_USER_UNAUTHORIZED = 19
```

A continuous task of the special scenario type is requested, but the user is not authorized.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_SUSPEND_USB_NOT_USED

```TypeScript
SYSTEM_SUSPEND_USB_NOT_USED = 20
```

A continuous task of the **USB_CONNECTION** type is requested, but USB device is not in use.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
