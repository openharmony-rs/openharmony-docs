# BackgroundTaskSubmode

```TypeScript
export enum BackgroundTaskSubmode
```

Defines the subtype of a continuous task. It is usually used together with the main type [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md). For details, see the mapping table. The two types are newly added in API version 21 for requesting and updating continuous tasks.

**Since:** 21

<!--Device-backgroundTaskManager-export enum BackgroundTaskSubmode--><!--Device-backgroundTaskManager-export enum BackgroundTaskSubmode-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_CAR_KEY_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_CAR_KEY_NORMAL_NOTIFICATION = 1
```

**CAR_KEY** type. It is of the normal text notification type.

**Since:** 21

<!--Device-BackgroundTaskSubmode-SUBMODE_CAR_KEY_NORMAL_NOTIFICATION = 1--><!--Device-BackgroundTaskSubmode-SUBMODE_CAR_KEY_NORMAL_NOTIFICATION = 1-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_NORMAL_NOTIFICATION = 2
```

Normal text notification.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-BackgroundTaskSubmode-SUBMODE_NORMAL_NOTIFICATION = 2--><!--Device-BackgroundTaskSubmode-SUBMODE_NORMAL_NOTIFICATION = 2-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_LIVE_VIEW_NOTIFICATION

```TypeScript
SUBMODE_LIVE_VIEW_NOTIFICATION = 3
```

Live view notification.

**Since:** 21

<!--Device-BackgroundTaskSubmode-SUBMODE_LIVE_VIEW_NOTIFICATION = 3--><!--Device-BackgroundTaskSubmode-SUBMODE_LIVE_VIEW_NOTIFICATION = 3-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_AUDIO_PLAYBACK_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_AUDIO_PLAYBACK_NORMAL_NOTIFICATION = 4
```

Audio and video playback. It is of the normal text notification type. You can access [AVSession](../../../media/avsession/avsession-overview.md) as needed.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-BackgroundTaskSubmode-SUBMODE_AUDIO_PLAYBACK_NORMAL_NOTIFICATION = 4--><!--Device-BackgroundTaskSubmode-SUBMODE_AUDIO_PLAYBACK_NORMAL_NOTIFICATION = 4-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_AVSESSION_AUDIO_PLAYBACK

```TypeScript
SUBMODE_AVSESSION_AUDIO_PLAYBACK = 5
```

Audio and video playback scenario where [AVSession](../../../media/avsession/avsession-overview.md) is accessed. It is of the normal text notification type.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-BackgroundTaskSubmode-SUBMODE_AVSESSION_AUDIO_PLAYBACK = 5--><!--Device-BackgroundTaskSubmode-SUBMODE_AVSESSION_AUDIO_PLAYBACK = 5-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_AUDIO_RECORD_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_AUDIO_RECORD_NORMAL_NOTIFICATION = 6
```

Recording. It is of the normal text notification type.

**Since:** 22

<!--Device-BackgroundTaskSubmode-SUBMODE_AUDIO_RECORD_NORMAL_NOTIFICATION = 6--><!--Device-BackgroundTaskSubmode-SUBMODE_AUDIO_RECORD_NORMAL_NOTIFICATION = 6-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_SCREEN_RECORD_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_SCREEN_RECORD_NORMAL_NOTIFICATION = 7
```

Recording. It is of the normal text notification type.

**Since:** 22

<!--Device-BackgroundTaskSubmode-SUBMODE_SCREEN_RECORD_NORMAL_NOTIFICATION = 7--><!--Device-BackgroundTaskSubmode-SUBMODE_SCREEN_RECORD_NORMAL_NOTIFICATION = 7-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_VOICE_CHAT_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_VOICE_CHAT_NORMAL_NOTIFICATION = 8
```

Call. It is of the normal text notification type.

**Since:** 22

<!--Device-BackgroundTaskSubmode-SUBMODE_VOICE_CHAT_NORMAL_NOTIFICATION = 8--><!--Device-BackgroundTaskSubmode-SUBMODE_VOICE_CHAT_NORMAL_NOTIFICATION = 8-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_MEDIA_PROCESS_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_MEDIA_PROCESS_NORMAL_NOTIFICATION = 9
```

Media processing. For example, an application exports media files in the background. It is of the normal text notification type.

**Since:** 22

<!--Device-BackgroundTaskSubmode-SUBMODE_MEDIA_PROCESS_NORMAL_NOTIFICATION = 9--><!--Device-BackgroundTaskSubmode-SUBMODE_MEDIA_PROCESS_NORMAL_NOTIFICATION = 9-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_VIDEO_BROADCAST_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_VIDEO_BROADCAST_NORMAL_NOTIFICATION = 10
```

Video casting. For example, an application uses a third-party casting component to cast a video in the background, and the notification type is common text notification.

**Since:** 22

<!--Device-BackgroundTaskSubmode-SUBMODE_VIDEO_BROADCAST_NORMAL_NOTIFICATION = 10--><!--Device-BackgroundTaskSubmode-SUBMODE_VIDEO_BROADCAST_NORMAL_NOTIFICATION = 10-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## SUBMODE_WORK_OUT_NORMAL_NOTIFICATION

```TypeScript
SUBMODE_WORK_OUT_NORMAL_NOTIFICATION = 11
```

Exercise. For example, an application has an indoor running scenario in the background, and the notification type is common text notification.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundTaskSubmode-SUBMODE_WORK_OUT_NORMAL_NOTIFICATION = 11--><!--Device-BackgroundTaskSubmode-SUBMODE_WORK_OUT_NORMAL_NOTIFICATION = 11-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
