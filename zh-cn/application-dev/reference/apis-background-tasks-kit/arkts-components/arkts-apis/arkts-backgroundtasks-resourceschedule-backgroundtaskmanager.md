# @ohos.resourceschedule.backgroundTaskManager(后台任务管理)

本模块提供申请后台任务的接口。当应用退至后台时，开发者可以通过本模块接口为应用申请短时、长时任务，避免应用进程被终止或挂起。开发指导请参考[长时任务开发指南](../../../task-management/continuous-task.md)、[短时任务开发指南](../../../task-management/transient-task.md)。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-cancelsuspenddelay-f.md) | 取消短时任务。适用于应用任务已完成、需要提前释放后台资源等场景。 |
| [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md) | 获取所有长时任务信息，如长时任务ID、长时任务类型等，使用Promise异步回调。 |
| [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md) | 获取所有长时任务信息，如长时任务ID、长时任务类型等。可选择是否获取暂停的长时任务信息，使用Promise异步回调。 |
| [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md) | 获取本次短时任务的剩余时间，使用callback异步回调。 |
| [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md) | 获取本次短时任务的剩余时间，使用Promise异步回调。 |
| [getTransientTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-gettransienttaskinfo-f.md) | 获取所有短时任务信息，如当日剩余总配额等，使用Promise异步回调。 |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#offcontinuoustaskcancel) | 解除长时任务取消的监听，使用callback异步回调。 |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#offcontinuoustasksuspend) | 取消长时任务暂停的监听，使用callback异步回调。 |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#offcontinuoustaskactive) | 取消长时任务激活的监听，使用callback异步回调。 |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#oncontinuoustaskcancel) | 注册长时任务取消的监听，使用callback异步回调。 |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#oncontinuoustasksuspend) | 注册长时任务暂停的监听，使用callback异步回调。注册该回调后，如果系统首次检测到应用未执行相应的业务，不会直接取消长时任务，而是将长时任务标记为暂停状态，如果连续检测失败，仍会取消长时任务。 |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#oncontinuoustaskactive) | 注册长时任务激活的监听，使用callback异步回调。暂停的长时任务激活时回调。 |
| [requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md) | 申请短时任务。适用于应用即将退至后台、需要短暂延迟挂起以便完成关键操作（如保存数据、上传进度等）等场景。 |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | 申请长时任务，支持申请一种类型，使用callback异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过API version 21新增接口[startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)申请多个长时任务。<br>从API版本26.1.0开始，通过本接口申请的长时任务，包含数据传输类型时，可以通过[updateDataTransferProgress()](arkts-backgroundtasks-backgroundtaskmanager-updatedatatransferprogress-f.md)接口更新长时任务通知，可选择通知是否有进度环，进度为100时是否响铃。 |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | 申请长时任务，支持申请一种类型，使用Promise异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过API version 21新增接口[startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)申请多个长时任务。<br>从API版本26.1.0开始，通过本接口申请的长时任务，包含数据传输类型时，可以通过[updateDataTransferProgress()](arkts-backgroundtasks-backgroundtaskmanager-updatedatatransferprogress-f.md)接口更新长时任务通知，可选择通知是否有进度环，进度为100时是否响铃。 |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | 申请长时任务，支持申请多种类型，使用Promise异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过API version 21新增接口[startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)申请多个长时任务。<br>从API版本26.1.0开始，通过本接口申请的长时任务，包含数据传输类型时，可以通过[updateDataTransferProgress()](arkts-backgroundtasks-backgroundtaskmanager-updatedatatransferprogress-f.md)接口更新长时任务通知，可选择通知是否有进度环，进度为100时是否响铃。 |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | 申请长时任务，一个UIAbility（FA模型则为ServiceAbility）下支持通过本接口申请多个长时任务，使用Promise异步回调。通过本接口申请长时任务时，支持与已存在的长时任务合并通知，具体请参考[ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md)。<br>同一时间最多可存在10个长时任务，长时任务申请成功后，会有通知栏消息，没有提示音。<br>如果通过本接口申请的一个长时任务中同时包含多种类型，且包含数据传输类型，则在通知栏会发送2个长时任务通知，一个为数据传输类型，另一个为其他类型的合并通知。任意一个通知被移除时，长时任务取消，且另一个通知也会同步移除。接口返回的长时任务通知Id为数据传输类型的Id，主要用于数据传输的进度更新。<br>从API版本26.1.0开始，通过本接口申请长时任务时，支持包含数据传输类型的长时任务直接发送进度模版通知，可选择通知是否有进度环，进度为100时是否响铃，具体请参考[ProgressInfo](arkts-backgroundtasks-backgroundtaskmanager-progressinfo-i.md)。也可以通过[updateDataTransferProgress()](arkts-backgroundtasks-backgroundtaskmanager-updatedatatransferprogress-f.md)接口更新长时任务通知。 |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) | 取消当前UIAbility（FA模型则为ServiceAbility）下所有长时任务，使用callback异步回调。也可以通过[stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md)接口取消指定Id的长时任务。适用于应用功能已完成、应用即将退出等场景。 |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) | 取消当前UIAbility（FA模型则为ServiceAbility）下所有长时任务，使用Promise异步回调。也可以通过[stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md)接口取消指定Id的长时任务。适用于应用功能已完成、应用即将退出等场景。 |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) | 取消指定Id的长时任务，使用Promise异步回调。也可以通过[stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md)取消当前UIAbility下所有长时任务。。适用于应用功能已完成、应用即将退出等场景。 |
| [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) | 更新长时任务，使用Promise异步回调。更新成功后仅显示通知栏消息，不播放提示音。适用于应用功能切换（如从音视频播放切换到录音）等需要调整长时任务以匹配新业务的场景。 |
| [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) | 更新长时任务，使用Promise异步回调。更新成功后仅显示通知栏消息，不播放提示音。适用于应用功能切换（如从音视频播放切换到录音）等需要调整长时任务以匹配新业务的场景。 |
| [updateDataTransferProgress](arkts-backgroundtasks-backgroundtaskmanager-updatedatatransferprogress-f.md) | 更新长时任务通知。仅支持更新包含数据传输类型的长时任务通知。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [applyEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-applyefficiencyresources-f-sys.md) | 申请或释放能效资源。释放操作仅对本次申请的资源生效。 |
| [getAllEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-getallefficiencyresources-f-sys.md) | 获取已申请的所有能效资源信息，如能效资源类型等，使用Promise异步回调。 |
| [getBackgroundTaskState](arkts-backgroundtasks-backgroundtaskmanager-getbackgroundtaskstate-f-sys.md) | 获取长时任务授权信息。 |
| [obtainAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-obtainallcontinuoustasks-f-sys.md) | 获取所有长时任务信息，如长时任务ID、长时任务类型等。使用Promise异步回调。 |
| [resetAllEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-resetallefficiencyresources-f-sys.md) | 释放已申请的全部能效资源。 |
| [setBackgroundTaskState](arkts-backgroundtasks-backgroundtaskmanager-setbackgroundtaskstate-f-sys.md) | 设置长时任务授权信息。 |
| [subscribeContinuousTaskState](arkts-backgroundtasks-backgroundtaskmanager-subscribecontinuoustaskstate-f-sys.md) | 注册长时任务变化回调。 |
| [unsubscribeContinuousTaskState](arkts-backgroundtasks-backgroundtaskmanager-unsubscribecontinuoustaskstate-f-sys.md) | 解注册长时任务变化回调。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | 通常作为[startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)和[updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md)接口的入参，用于指定申请或更新的长时任务信息。其中： |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContinuousTaskActiveInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskactiveinfo-i.md) | 长时任务激活信息。 |
| [ContinuousTaskCancelInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskcancelinfo-i.md) | 长时任务取消信息。 |
| [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | 长时任务信息。 |
| [ContinuousTaskNotification](arkts-backgroundtasks-backgroundtaskmanager-continuoustasknotification-i.md) | 长时任务通知信息。 |
| [ContinuousTaskSuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendinfo-i.md) | 长时任务暂停信息。 |
| [DataTransferProgress](arkts-backgroundtasks-backgroundtaskmanager-datatransferprogress-i.md) | 长时任务通知进度信息。 |
| [DelaySuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-delaysuspendinfo-i.md) | 短时任务信息。 |
| [ProgressInfo](arkts-backgroundtasks-backgroundtaskmanager-progressinfo-i.md) | 通知进度信息。 |
| [SuspendMessage](arkts-backgroundtasks-backgroundtaskmanager-suspendmessage-i.md) | 长时任务暂停原因。 |
| [TransientTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-transienttaskinfo-i.md) | 所有短时任务信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BackgroundTaskStateInfo](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskstateinfo-i-sys.md) | 长时任务授权信息。 |
| [BackgroundTaskSubscriber](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubscriber-i-sys.md) | 后台任务监听。 |
| [EfficiencyResourcesInfo](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcesinfo-i-sys.md) | 能效资源信息。 |
| [EfficiencyResourcesRequest](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcesrequest-i-sys.md) | 能效资源申请参数。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e.md) | 长时任务类型。 |
| [BackgroundModeType](arkts-backgroundtasks-backgroundtaskmanager-backgroundmodetype-e.md) | 长时任务类型类别。 |
| [BackgroundSubMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundsubmode-e.md) | 长时任务子类型。 |
| [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md) | 长时任务主类型。 |
| [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md) | 长时任务子类型。 |
| [ContinuousTaskCancelReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskcancelreason-e.md) | 长时任务取消原因。 |
| [ContinuousTaskDetailedCancelReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskdetailedcancelreason-e.md) | 长时任务取消详细原因。 |
| [ContinuousTaskSuspendReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendreason-e.md) | 长时任务暂停原因。 |
| [UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md) | 用户授权结果，表示长时任务授权状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e-sys.md) | 长时任务类型。 |
| [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e-sys.md) | 长时任务主类型。 |
| [EfficiencyResourcesCpuLevel](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcescpulevel-e-sys.md) | 能效资源CPU级别。 |
| [ResourceType](arkts-backgroundtasks-backgroundtaskmanager-resourcetype-e-sys.md) | 能效资源类型。 |
<!--DelEnd-->
