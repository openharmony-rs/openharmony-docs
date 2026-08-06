# BackgroundTaskMode

长时任务主类型。通常与长时任务子类型[BackgroundTaskSubmode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_配合使用，对照关系请参考长时任务主类型与子类型 对照表，两者共同作为API version 21新增的 [申请]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [更新]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_长时任务接口入参 ，用于指定长时任务类型。\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_仅当主类型为MODE\_SPECIAL\_SCENARIO\_PROCESSING特殊场景类型，或非PC/2in1设备主类型为MODE\_TASK\_KEEPING计算任务时，调用长时任务相关接口时需同时申 请ACL权限 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ ，其他场景无需申请该权限。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-backgroundTaskManager-export enum BackgroundTaskMode--><!--Device-backgroundTaskManager-export enum BackgroundTaskMode-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_DATA_TRANSFER

```TypeScript
MODE_DATA_TRANSFER = 1
```

数据传输。 使用场景举例：非托管形式的上传、下载，如在浏览器后台上传或下载数据。 **说明：** 1. 在数据传输时，应用需要更新进度，如果进度长时间（超过10分钟）未更新，数据传输的长时任务会被取消。 2. 更新进度的通知类型必须为实况窗，具体实现可参考[startBackgroundRunning()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的示例。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-BackgroundTaskMode-MODE_DATA_TRANSFER = 1--><!--Device-BackgroundTaskMode-MODE_DATA_TRANSFER = 1-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_AUDIO_PLAYBACK

```TypeScript
MODE_AUDIO_PLAYBACK = 2
```

音视频播放。 使用场景举例：音频、视频在后台播放，音视频投播。 **说明：** 申请/更新MODE\_AUDIO\_PLAYBACK类型长时任务但不接入AVSession，申请/更新长时任务成功后会在通知栏显示通知。接入AVSession后，后台任务模块不会发送通知栏通知，由AVSession 发送通知。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundTaskMode-MODE_AUDIO_PLAYBACK = 2--><!--Device-BackgroundTaskMode-MODE_AUDIO_PLAYBACK = 2-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_AUDIO_RECORDING

```TypeScript
MODE_AUDIO_RECORDING = 3
```

录制。 使用场景举例：录音、录屏退后台。\_\_\_MD\_COMMENT\_DESC\_USD\_0\_\_\_ **说明：** 系统应用申请/更新该类型的长时任务，没有通知栏消息。\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-BackgroundTaskMode-MODE_AUDIO_RECORDING = 3--><!--Device-BackgroundTaskMode-MODE_AUDIO_RECORDING = 3-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_LOCATION

```TypeScript
MODE_LOCATION = 4
```

定位导航。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundTaskMode-MODE_LOCATION = 4--><!--Device-BackgroundTaskMode-MODE_LOCATION = 4-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_BLUETOOTH_INTERACTION

```TypeScript
MODE_BLUETOOTH_INTERACTION = 5
```

蓝牙相关业务。 使用场景举例：通过蓝牙传输文件时退后台。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-BackgroundTaskMode-MODE_BLUETOOTH_INTERACTION = 5--><!--Device-BackgroundTaskMode-MODE_BLUETOOTH_INTERACTION = 5-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_MULTI_DEVICE_CONNECTION

```TypeScript
MODE_MULTI_DEVICE_CONNECTION = 6
```

多设备互联。 使用场景举例：分布式业务连接、投播。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundTaskMode-MODE_MULTI_DEVICE_CONNECTION = 6--><!--Device-BackgroundTaskMode-MODE_MULTI_DEVICE_CONNECTION = 6-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_VOIP

```TypeScript
MODE_VOIP = 8
```

音视频通话。 使用场景举例：某些聊天类应用（具有音视频业务）音频、视频通话时退后台。 \_\_\_MD\_COMMENT\_DESC\_USD\_0\_\_\_ **说明：** 系统应用申请/更新该类型的长时任务，没有通知栏消息。\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-BackgroundTaskMode-MODE_VOIP = 8--><!--Device-BackgroundTaskMode-MODE_VOIP = 8-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_TASK_KEEPING

```TypeScript
MODE_TASK_KEEPING = 9
```

计算任务。 使用场景举例：杀毒软件。 **说明：** 仅对PC/2in1设备开放，或者非PC/2in1设备但申请了ACL权限为 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 的应用开放。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-BackgroundTaskMode-MODE_TASK_KEEPING = 9--><!--Device-BackgroundTaskMode-MODE_TASK_KEEPING = 9-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_AV_PLAYBACK_AND_RECORD

```TypeScript
MODE_AV_PLAYBACK_AND_RECORD = 12
```

多媒体相关业务。 使用场景举例：音视频播放、录制、音视频通话场景，场景需与长时任务子类型相匹配。在上述场景下，选择此类型或者对应的长时任务主类型均可。例如：音视频播放场景可以申请MODE\_AUDIO\_PLAYBACK或者 MODE\_AV\_PLAYBACK\_AND\_RECORD长时任务主类型。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundTaskMode-MODE_AV_PLAYBACK_AND_RECORD = 12--><!--Device-BackgroundTaskMode-MODE_AV_PLAYBACK_AND_RECORD = 12-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_SPECIAL_SCENARIO_PROCESSING

```TypeScript
MODE_SPECIAL_SCENARIO_PROCESSING = 13
```

特殊场景类型（仅对Phone、Tablet、PC/2in1设备开放）。 使用场景举例：应用在后台导出媒体文件、应用使用三方投播组件在后台进行投播，场景需与长时任务子类型相匹配。 **说明：** 1. 如果应用需要在后台长时间运行，可以通过[requestAuthFromUser]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口请求用户授权、通过[checkSpecialScenarioAuth]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口查询用户授权结果。 2. 从API version 24开始，仅对申请ACL权限\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的应用开放。API version 23及之前版本，仅对申请ACL权限\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_的应用开放，已经申请该权限的应用在API version 24之后不受影响。 3. 必须单独使用且不支持通知合并，即申请或更新长时任务时，长时任务类型只能有特殊场景类型，否则返回错误。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-BackgroundTaskMode-MODE_SPECIAL_SCENARIO_PROCESSING = 13--><!--Device-BackgroundTaskMode-MODE_SPECIAL_SCENARIO_PROCESSING = 13-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_NEARLINK

```TypeScript
MODE_NEARLINK = 14
```

星闪业务。 使用场景举例：通过星闪传输文件时退后台。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskMode-MODE_NEARLINK = 14--><!--Device-BackgroundTaskMode-MODE_NEARLINK = 14-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

