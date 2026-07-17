# BackgroundMode

长时任务类型。

**起始版本：** 9

<!--Device-backgroundTaskManager-export enum BackgroundMode--><!--Device-backgroundTaskManager-export enum BackgroundMode-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## DATA_TRANSFER

```TypeScript
DATA_TRANSFER = 1
```

数据传输。

使用场景举例：非托管形式的上传、下载，如在浏览器后台上传或下载数据。

**说明：** 在数据传输时，应用需要更新进度，如果进度长时间（超过10分钟）未更新，数据传输的长时任务会被取消。

更新进度的通知类型必须为实况窗，具体实现可参考[startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-3)中的示例。

**起始版本：** 9

<!--Device-BackgroundMode-DATA_TRANSFER = 1--><!--Device-BackgroundMode-DATA_TRANSFER = 1-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## AUDIO_PLAYBACK

```TypeScript
AUDIO_PLAYBACK = 2
```

音视频播放。

使用场景举例：音频、视频在后台播放，音视频投播。

**说明：** 从API version 20开始，申请/更新AUDIO_PLAYBACK类型长时任务但不接入AVSession，申请/更新长时任务成功后会在通知栏显示通知。

接入AVSession后，后台任务模块不会发送通知栏通知，由AVSession发送通知。

对于API version 19及之前的版本，后台任务模块不会在通知栏显示通知。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundMode-AUDIO_PLAYBACK = 2--><!--Device-BackgroundMode-AUDIO_PLAYBACK = 2-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## AUDIO_RECORDING

```TypeScript
AUDIO_RECORDING = 3
```

录制。

使用场景举例：录音、录屏退后台。<!--Del-->

**说明：** 系统应用申请/更新该类型的长时任务，没有通知栏消息。<!--DelEnd-->

**起始版本：** 9

<!--Device-BackgroundMode-AUDIO_RECORDING = 3--><!--Device-BackgroundMode-AUDIO_RECORDING = 3-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## LOCATION

```TypeScript
LOCATION = 4
```

定位导航。

**起始版本：** 9

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundMode-LOCATION = 4--><!--Device-BackgroundMode-LOCATION = 4-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## BLUETOOTH_INTERACTION

```TypeScript
BLUETOOTH_INTERACTION = 5
```

蓝牙相关业务。

使用场景举例：通过蓝牙传输文件时退后台。

**起始版本：** 9

<!--Device-BackgroundMode-BLUETOOTH_INTERACTION = 5--><!--Device-BackgroundMode-BLUETOOTH_INTERACTION = 5-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MULTI_DEVICE_CONNECTION

```TypeScript
MULTI_DEVICE_CONNECTION = 6
```

多设备互联。

使用场景举例：分布式业务连接、投播。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundMode-MULTI_DEVICE_CONNECTION = 6--><!--Device-BackgroundMode-MULTI_DEVICE_CONNECTION = 6-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## VOIP

```TypeScript
VOIP = 8
```

音视频通话。

使用场景举例：某些聊天类应用（具有音视频业务）音频、视频通话时退后台。<!--Del-->

**说明：** 系统应用申请/更新该类型的长时任务，没有通知栏消息。<!--DelEnd-->

**起始版本：** 13

<!--Device-BackgroundMode-VOIP = 8--><!--Device-BackgroundMode-VOIP = 8-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## TASK_KEEPING

```TypeScript
TASK_KEEPING = 9
```

计算任务。

使用场景举例：杀毒软件

**说明：** 从API version 21开始，对PC/2in1设备、非PC/2in1设备但申请了ACL权限为[ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system)的应用开放。 API version 20及之前版本，仅对PC/2in1设备开放。

**起始版本：** 9

<!--Device-BackgroundMode-TASK_KEEPING = 9--><!--Device-BackgroundMode-TASK_KEEPING = 9-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

