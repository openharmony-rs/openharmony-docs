# ContinuousTaskDetailedCancelReason

Describes the detailed reason for canceling a continuous task.

**Since:** 26.0.0

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## USER_CANCEL_REMOVE_NOTIFICATION

```TypeScript
USER_CANCEL_REMOVE_NOTIFICATION = 3
```

User removal notification.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED

```TypeScript
SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED = 4
```

A continuous task of the **DATA_TRANSFER** type is requested, but the data transmission rate is low.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING = 6
```

A continuous task of the **AUDIO_PLAYBACK** type is requested, but the audio and video are not played.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING = 7
```

A continuous task of the **AUDIO_RECORDING** type is requested, but audio recording is not in progress.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_LOCATION

```TypeScript
SYSTEM_CANCEL_NOT_USE_LOCATION = 8
```

A continuous task of the **LOCATION** type is requested, but the location service is not in use.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_BLUETOOTH

```TypeScript
SYSTEM_CANCEL_NOT_USE_BLUETOOTH = 9
```

A continuous task of the **BLUETOOTH_INTERACTION** type is requested, but Bluetooth is not in use.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE

```TypeScript
SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE = 10
```

A continuous task of the **MULTI_DEVICE_CONNECTION** type is requested, but the multi-device connection service is not in use.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_USE_ILLEGALLY

```TypeScript
SYSTEM_CANCEL_USE_ILLEGALLY = 11
```

A continuous task of an invalid type is used. For example, a continuous task of the **AUDIO_PLAYBACK** type is requested, but the audio playback and location services are in use.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_DATA_TRANSFER_NOT_UPDATE

```TypeScript
SYSTEM_CANCEL_DATA_TRANSFER_NOT_UPDATE = 12
```

A continuous task of the **DATA_TRANSFER** type is requested, but the progress is not updated for a long time (the first update takes more than 10 minutes).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_VOIP_NOT_RUNNING

```TypeScript
SYSTEM_CANCEL_VOIP_NOT_RUNNING = 13
```

A continuous task of the **VOIP** type is requested, but no audio stream or recording stream is in progress.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_USER_UNAUTHORIZED

```TypeScript
SYSTEM_CANCEL_USER_UNAUTHORIZED = 14
```

A continuous task of the special scenario type is requested, but the user is not authorized.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_NEARLINK

```TypeScript
SYSTEM_CANCEL_NOT_USE_NEARLINK = 15
```

A continuous task of the **NEARLINK** type is requested, but nearlink is not in use.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SYSTEM_CANCEL_NOT_USE_USB

```TypeScript
SYSTEM_CANCEL_NOT_USE_USB = 16
```

A continuous task of the **USB_CONNECTION** type is requested, but USB device is not in use.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
