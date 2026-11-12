# 长时任务主类型与子类型对照表

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

长时任务主类型[BackgroundTaskMode](js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmode21)是指后台运行长时任务的业务类型；长时任务子类型[BackgroundTaskSubmode](js-apis-resourceschedule-backgroundTaskManager.md#backgroundtasksubmode21)用于在同一主类型下进一步区分通知呈现形式或细分场景。申请或更新长时任务时，主类型与子类型需要配合使用。

| 长时任务主类型 | 长时任务子类型  |
| --------------------------------- | ----------------------------------- |
| MODE_DATA_TRANSFER                | SUBMODE_LIVE_VIEW_NOTIFICATION      |
| MODE_AUDIO_PLAYBACK               | SUBMODE_NORMAL_NOTIFICATION         |
| MODE_AUDIO_RECORDING              | SUBMODE_NORMAL_NOTIFICATION         |
| MODE_LOCATION                     | SUBMODE_NORMAL_NOTIFICATION         |
| MODE_BLUETOOTH_INTERACTION        | SUBMODE_NORMAL_NOTIFICATION <br/>SUBMODE_CAR_KEY_NORMAL_NOTIFICATION         |
| MODE_MULTI_DEVICE_CONNECTION      | SUBMODE_NORMAL_NOTIFICATION         |
| MODE_VOIP                         | SUBMODE_NORMAL_NOTIFICATION         |
| MODE_TASK_KEEPING                 | SUBMODE_NORMAL_NOTIFICATION         |
| MODE_AV_PLAYBACK_AND_RECORD  | SUBMODE_AUDIO_PLAYBACK_NORMAL_NOTIFICATION<br/>SUBMODE_AVSESSION_AUDIO_PLAYBACK<br/>SUBMODE_AUDIO_RECORD_NORMAL_NOTIFICATION<br/>SUBMODE_SCREEN_RECORD_NORMAL_NOTIFICATION<br/>SUBMODE_VOICE_CHAT_NORMAL_NOTIFICATION  |
| MODE_SPECIAL_SCENARIO_PROCESSING  | SUBMODE_MEDIA_PROCESS_NORMAL_NOTIFICATION <br/>SUBMODE_VIDEO_BROADCAST_NORMAL_NOTIFICATION  <br/>SUBMODE_WORK_OUT_NORMAL_NOTIFICATION |
| MODE_NEARLINK                   | SUBMODE_NORMAL_NOTIFICATION         |
| MODE_USB_CONNECTION             | SUBMODE_NORMAL_NOTIFICATION         |
