# BackgroundMode

Defines the type of a continuous task.

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## DATA_TRANSFER

```TypeScript
DATA_TRANSFER = 1
```

Data transfer.

Use scenario: upload and download in non-hosting mode, for example, uploading or downloading data in the background of a browser.

Note: During data transfer, the application needs to update the progress. If the progress is not updated for more than 10 minutes, the continuous task of the **DATA_TRANSFER** type will be canceled.

The notification type of the progress update must be live view. For details, see the example in [startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md).

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## AUDIO_PLAYBACK

```TypeScript
AUDIO_PLAYBACK = 2
```

Audio and video playback.

Use scenario: audio/video playback in the background and audio/video casting.

Note: Since API version 20, if an application requests or updates a continuous task of the **AUDIO_PLAYBACK** type without connecting to AVSession, a notification will appear in the notification panel once the task is successfully requested or updated.

Once AVSession is connected, notifications will be sent by AVSession instead of the background task module.

For API version 19 and earlier versions, the background task module does not display notifications in the notification panel.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## AUDIO_RECORDING

```TypeScript
AUDIO_RECORDING = 3
```

Audio recording.

Use scenario: recording and screen capture in the background.<!--Del-->

Note: No notification is displayed if a system application requests or updates a continuous task.<!--DelEnd-->

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## LOCATION

```TypeScript
LOCATION = 4
```

Positioning and navigation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## BLUETOOTH_INTERACTION

```TypeScript
BLUETOOTH_INTERACTION = 5
```

Bluetooth-related services.

Use scenario: An application moves to the background while transferring files via Bluetooth.

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MULTI_DEVICE_CONNECTION

```TypeScript
MULTI_DEVICE_CONNECTION = 6
```

Multi-device connection.

Use scenario: distributed service connection and casting.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## VOIP

```TypeScript
VOIP = 8
```

Audio and video calls.

Use scenario: Chat applications (with audio and video services) transition into the background during audio and video calls.<!--Del-->

Note: No notification is displayed if a system application requests or updates a continuous task.<!--DelEnd-->

**Since:** 13

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## TASK_KEEPING

```TypeScript
TASK_KEEPING = 9
```

Computing tasks.

Use scenario: antivirus software.

**NOTE:**  Starting from API version 21, this capability is available for PCs/2-in-1 devices, and non-PCs/2-in-1 devices that have obtained the ACL permission [ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system). In API version 20 and earlier versions, this task type is limited to PCs/2-in-1 devices only.

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
