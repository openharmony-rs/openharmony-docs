# @ohos.resourceschedule.backgroundTaskManager

本模块提供申请后台任务的接口。当应用退至后台时，开发者可以通过本模块接口为应用申请短时、长时任务，避免应用进程被终止或挂起。开发指导请参考
[长时任务开发指南](../../../../task-management/continuous-task.md)、[短时任务开发指南](../../../../task-management/transient-task.md)。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[applyEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-applyefficiencyresources-f-sys.md#applyEfficiencyResources-1) | 申请能效资源。<br/> |
| [cancelSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-cancelsuspenddelay-f.md#cancelSuspendDelay-1) | 取消短时任务。<br/> |
| [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md#getAllContinuousTasks-1) | 获取所有长时任务信息，如长时任务ID、长时任务类型等，使用Promise异步回调。<br/> |
| [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md#getAllContinuousTasks-2) | 获取所有长时任务信息，如长时任务ID、长时任务类型等。可选择是否获取暂停的长时任务信息，使用Promise异步回调。<br/> |
| <!--DelRow-->[getAllEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-getallefficiencyresources-f-sys.md#getAllEfficiencyResources-1) | 获取已申请的所有能效资源信息，如能效资源类型等，使用Promise异步回调。<br/> |
| <!--DelRow-->[getBackgroundTaskState](arkts-backgroundtasks-backgroundtaskmanager-getbackgroundtaskstate-f-sys.md#getBackgroundTaskState-1) | 获取长时任务授权信息。<br/> |
| [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md#getRemainingDelayTime-1) | 获取本次短时任务的剩余时间，使用callback异步回调。<br/> |
| [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md#getRemainingDelayTime-2) | 获取本次短时任务的剩余时间，使用Promise异步回调。<br/> |
| [getTransientTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-gettransienttaskinfo-f.md#getTransientTaskInfo-1) | 获取所有短时任务信息，如当日剩余总配额等，使用Promise异步回调。<br/> |
| <!--DelRow-->[obtainAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-obtainallcontinuoustasks-f-sys.md#obtainAllContinuousTasks-1) | 获取所有长时任务信息，如长时任务ID、长时任务类型等。使用Promise异步回调。<br/> |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#off-1) | 解除长时任务取消的监听，使用callback异步回调。<br/> |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#off-2) | 取消长时任务暂停的监听，使用callback异步回调。<br/> |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#off-3) | 取消长时任务激活的监听，使用callback异步回调。<br/> |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#on-1) | 注册长时任务取消的监听，使用callback异步回调。<br/> |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#on-2) | 注册长时任务暂停的监听，使用callback异步回调。注册该回调后，如果系统首次检测到应用未执行相应的业务，不会直接取消长时任务，而是将长时任务标记为暂停状态，如果连续检测失败，仍会取消长时任务。<br/><br/>长时任务处于暂停状态时，应用退后台会被挂起，回前台自动激活。<br/> |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#on-3) | 注册长时任务激活的监听，使用callback异步回调。应用回前台激活暂停的长时任务。<br/> |
| [requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md#requestSuspendDelay-1) | 申请短时任务。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 短时任务的申请和使用过程中的约束与限制请参考[指南](../../../../task-management/transient-task.md#约束与限制)。<br/> |
| <!--DelRow-->[resetAllEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-resetallefficiencyresources-f-sys.md#resetAllEfficiencyResources-1) | 释放已申请的全部能效资源。<br/> |
| <!--DelRow-->[setBackgroundTaskState](arkts-backgroundtasks-backgroundtaskmanager-setbackgroundtaskstate-f-sys.md#setBackgroundTaskState-1) | 设置长时任务授权信息。<br/> |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-1) | 申请长时任务，支持申请一种类型，使用callback异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过<br/>API version 21新增接口<br/>[startBackgroundRunning](backgroundTaskManager.startBackgroundRunning(context: Context, request:ContinuousTaskRequest))<br/>申请多个长时任务。<br/> |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-2) | 申请长时任务，支持申请一种类型，使用Promise异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过<br/>API version 21新增接口<br/>[startBackgroundRunning](backgroundTaskManager.startBackgroundRunning(context: Context, request:ContinuousTaskRequest))<br/>申请多个长时任务。<br/> |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-3) | 申请长时任务，支持申请多种类型，使用Promise异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过<br/>API version 21新增接口<br/>[startBackgroundRunning](backgroundTaskManager.startBackgroundRunning(context: Context, request:ContinuousTaskRequest))<br/>申请多个长时任务。<br/> |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-4) | 申请长时任务，一个UIAbility（FA模型则为ServiceAbility）下支持通过本接口申请多个长时任务，使用Promise异步回调。通过本接口申请长时任务时，支持与已存在的长时任务合并通知，具体请参考<br/>[ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md#ContinuousTaskRequest)。&lt;/br&gt;同一时间最多可存在10个长时任务，长时任务申请成功后，会有通知栏消息，<br/>没有提示音。&lt;/br&gt;如果通过本接口申请的一个长时任务中同时包含多种类型，且包含数据传输类型，则在通知栏会发送2个长时任务通知，一个为数据传输类型，另一个为其他类型的合并通知。任意一个通知被移除时，长时任务取消，且另一个通知也会同<br/>步移除。接口返回的长时任务通知Id为数据传输类型的Id，主要用于数据传输的进度更新。<br/> |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopBackgroundRunning-1) | 取消当前UIAbility（FA模型则为ServiceAbility）下所有长时任务，使用callback异步回调。也可以通过<br/>[stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopBackgroundRunning-3)<br/>接口取消指定Id的长时任务。<br/> |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopBackgroundRunning-2) | 取消当前UIAbility（FA模型则为ServiceAbility）下所有长时任务，使用Promise异步回调。也可以通过<br/>[stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopBackgroundRunning-3)<br/>接口取消指定Id的长时任务。<br/> |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopBackgroundRunning-3) | 取消指定Id的长时任务，使用Promise异步回调。也可以通过<br/>[stopBackgroundRunning](backgroundTaskManager.stopBackgroundRunning(context: Context, callback:AsyncCallback&lt;void&gt;))<br/>取消当前UIAbility下所有长时任务。<br/> |
| <!--DelRow-->[subscribeContinuousTaskState](arkts-backgroundtasks-backgroundtaskmanager-subscribecontinuoustaskstate-f-sys.md#subscribeContinuousTaskState-1) | 注册长时任务变化回调。<br/> |
| <!--DelRow-->[unsubscribeContinuousTaskState](arkts-backgroundtasks-backgroundtaskmanager-unsubscribecontinuoustaskstate-f-sys.md#unsubscribeContinuousTaskState-1) | 解注册长时任务变化回调。<br/> |
| [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updateBackgroundRunning-1) | 更新长时任务类型，使用Promise异步回调。长时任务更新成功后，会有通知栏消息，没有提示音。&lt;/br&gt;更新长时任务前，可以通过<br/>[getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md#getAllContinuousTasks-1)接口获取当前所有长时任务信息，如果当前没有已经<br/>存在的长时任务，会更新失败。&lt;/br&gt;该接口仅支持更新如下三个接口申请的长时任务：&lt;/br&gt;<br/>[startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback:AsyncCallback&lt;void&gt;): void](backgroundTaskManager.startBackgroundRunning(context: Context, bgMode:BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback&lt;void&gt;))<br/>&lt;/br&gt;<br/>[startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise&lt;void&gt;]{@linkbackgroundTaskManager.startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent)}<br/>&lt;/br&gt;<br/>[startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent):Promise&lt;ContinuousTaskNotification&gt;]{@link backgroundTaskManager.startBackgroundRunning(context: Context,bgModes: string[], wantAgent: WantAgent)}<br/> |
| [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updateBackgroundRunning-2) | 更新长时任务，使用Promise异步回调。长时任务更新成功后，会有通知栏消息，没有提示音。<br/><br/>更新长时任务还存在如下约束限制：<br/><br/>1. 本接口仅支持更新如下接口申请的长时任务：[startBackgroundRunning(context: Context, request: ContinuousTaskRequest):Promise&lt;ContinuousTaskNotification&gt;](backgroundTaskManager.startBackgroundRunning(context: Context,request: ContinuousTaskRequest))。<br/>2. 已经合并的长时任务，且后台任务主类型和子类型均相同，仅支持更新ContinuousTaskRequest.wantAgent中的wants信息（abilityName等），如果类型不同，更新失败。<br/>3. 如果待更新的长时任务或指定的更新类型中包含数据传输类型，直接返回失败。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | 通常作为<br/>[startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-4)<br/>和<br/>[updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updateBackgroundRunning-2)<br/>接口的入参，用于指定申请或更新的长时任务信息。其中：<br/><br/>1. 通过[startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-4)接口申请长时任务时，如果待申请长时任务与当前应用下已存在长时任务，两者的主类型和子类型均相同，且combinedTaskNotification均取值为true，则会合并通知。否则不会合并通知。<br/>2. 如果长时任务本身没有通知，则不会合并，长时任务类型是否会通知请参考[BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md#BackgroundTaskMode)。<br/>3. 如果长时任务类型中包含数据传输类型，则不会合并通知。<br/>4. 通知合并后不能取消合并，已合并的不能更新成不合并。<br/>5. 通知合并后，点击通知栏消息，会跳转到第一个申请的长时任务对应的UIAbility，如果调用了更新接口，则跳转到最后一次更新的长时任务对应的UIAbility。<br/>6. 通过[updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updateBackgroundRunning-2)接口更新长时任务时，传入的continuousTaskId必须存在，否则更新失败。<br/>7. 从API version 22开始支持特殊场景类型[MODE_SPECIAL_SCENARIO_PROCESSING](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md#BackgroundTaskMode)的长时任务。必须单独使用且不支持通知合并，即申请或更新长时任务时，长时任务类型只能有特殊场景类型，否则返回错误。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[BackgroundTaskStateInfo](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskstateinfo-i-sys.md) | 长时任务授权信息。<br/> |
| <!--DelRow-->[BackgroundTaskSubscriber](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubscriber-i-sys.md) | 后台任务监听。<br/> |
| [ContinuousTaskActiveInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskactiveinfo-i.md) | 长时任务激活信息。<br/> |
| [ContinuousTaskCancelInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskcancelinfo-i.md) | 长时任务取消信息。<br/> |
| [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | 长时任务信息。<br/> |
| [ContinuousTaskNotification](arkts-backgroundtasks-backgroundtaskmanager-continuoustasknotification-i.md) | 长时任务通知信息。<br/> |
| [ContinuousTaskSuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendinfo-i.md) | 长时任务暂停信息。<br/> |
| [DelaySuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-delaysuspendinfo-i.md) | 短时任务信息。<br/> |
| <!--DelRow-->[EfficiencyResourcesInfo](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcesinfo-i-sys.md) | 能效资源信息。<br/> |
| <!--DelRow-->[EfficiencyResourcesRequest](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcesrequest-i-sys.md) | 能效资源申请参数。<br/> |
| [SuspendMessage](arkts-backgroundtasks-backgroundtaskmanager-suspendmessage-i.md) | 长时任务暂停原因。<br/> |
| [TransientTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-transienttaskinfo-i.md) | 所有短时任务信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e.md) | 长时任务类型。<br/> |
| <!--DelRow-->[BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e-sys.md) | 长时任务类型。<br/> |
| [BackgroundModeType](arkts-backgroundtasks-backgroundtaskmanager-backgroundmodetype-e.md) | 长时任务类型类别。<br/> |
| [BackgroundSubMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundsubmode-e.md) | 长时任务子类型。<br/> |
| [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md) | 长时任务主类型。通常与长时任务子类型[BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md#BackgroundTaskSubmode)配合使用，对照关系请参考长时任务主类型与子类型<br/>对照表，两者共同作为API version 21新增的<br/>[申请](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-4)、<br/>[更新](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updateBackgroundRunning-2)长时任务接口入参<br/>，用于指定长时任务类型。&lt;/br&gt;仅当主类型为MODE_SPECIAL_SCENARIO_PROCESSING特殊场景类型，或非PC/2in1设备主类型为MODE_TASK_KEEPING计算任务时，调用长时任务相关接口时需同时申<br/>请ACL权限<br/>[ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system)<br/>，其他场景无需申请该权限。<br/> |
| <!--DelRow-->[BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e-sys.md) | 长时任务主类型。通常与长时任务子类型[BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md#BackgroundTaskSubmode)配合使用，对照关系请参考长时任务主类型与子类型<br/>对照表，两者共同作为API version 21新增的<br/>[申请](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startBackgroundRunning-4)、<br/>[更新](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updateBackgroundRunning-2)长时任务接口入参<br/>，用于指定长时任务类型。&lt;/br&gt;仅当主类型为MODE_SPECIAL_SCENARIO_PROCESSING特殊场景类型，或非PC/2in1设备主类型为MODE_TASK_KEEPING计算任务时，调用长时任务相关接口时需同时申<br/>请ACL权限<br/>[ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system)<br/>，其他场景无需申请该权限。<br/> |
| [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md) | 长时任务子类型。通常与长时任务主类型[BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md#BackgroundTaskMode)配合使用，对照关系请参考长时任务主类型与子类型对照表，两者<br/>共同作为API version 21新增的申请、更新长时任务接口入参，用于指定长时任务类型。<br/> |
| [ContinuousTaskCancelReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskcancelreason-e.md) | 长时任务取消原因。<br/> |
| [ContinuousTaskDetailedCancelReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskdetailedcancelreason-e.md) | 长时任务取消详细原因。<br/> |
| [ContinuousTaskSuspendReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendreason-e.md) | 长时任务暂停原因。<br/> |
| <!--DelRow-->[EfficiencyResourcesCpuLevel](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcescpulevel-e-sys.md) | 能效资源CPU级别。<br/> |
| <!--DelRow-->[ResourceType](arkts-backgroundtasks-backgroundtaskmanager-resourcetype-e-sys.md) | 能效资源类型。<br/> |
| [UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md) | 用户授权结果。<br/> |

