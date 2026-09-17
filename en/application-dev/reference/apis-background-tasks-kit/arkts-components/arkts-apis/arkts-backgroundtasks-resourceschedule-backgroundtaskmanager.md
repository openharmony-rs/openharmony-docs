# @ohos.resourceschedule.backgroundTaskManager(Background Task Management)

The **backgroundTaskManager** module provides APIs to request background tasks. You can use the APIs to request transient tasks, continuous tasks, or efficiency resources to prevent the application process from being terminated or suspended when your application is switched to the background. For details, see [Continuous Task](../../../task-management/continuous-task.md) and [Transient Task](../../../task-management/transient-task.md).

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancelSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-cancelsuspenddelay-f.md) | Cancels a transient task. |
| [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md) | Obtains all continuous task information, including the task ID and type. This API uses a promise to return the result. |
| [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md) | Obtains all continuous task information, including the task ID and type. It supports specifying whether to include suspended tasks and uses a promise to return the result. |
| [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md) | Obtains the remaining time of a transient task. This API uses an asynchronous callback to return the result. |
| [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md) | Obtains the remaining time of a transient task. This API uses a promise to return the result. |
| [getTransientTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-gettransienttaskinfo-f.md) | Obtains all transient task information, including the remaining quota of the current day. This API uses a promise to return the result. |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#offcontinuoustaskcancel) | Unsubscribes from continuous task cancellation events. This API uses an asynchronous callback to return the result. |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#offcontinuoustasksuspend) | Unregisters from the listener for continuous task suspension. This API uses an asynchronous callback to return the result. |
| [off](arkts-backgroundtasks-backgroundtaskmanager-off-f.md#offcontinuoustaskactive) | Unregisters from the listener for continuous task activation. This API uses an asynchronous callback to return the result. |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#oncontinuoustaskcancel) | Subscribes to continuous task cancellation events. This API uses an asynchronous callback to return the result. |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#oncontinuoustasksuspend) | Registers a listener for continuous task suspension. This API uses an asynchronous callback to return the result. After the callback is registered, if the system detects for the first time that the application does not execute the corresponding service, the system does not directly cancel the continuous task. Instead, it will mark the task as suspended. If the detection failures persist, the system will cancel the continuous task. |
| [on](arkts-backgroundtasks-backgroundtaskmanager-on-f.md#oncontinuoustaskactive) | Registers a listener for continuous task activation. This API uses an asynchronous callback to return the result. The application returns to the foreground to activate the suspended continuous task. |
| [requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md) | Requests a transient task. |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | Requests a continuous task of a specific type. This API uses an asynchronous callback to return the result. After a continuous task is successfully requested, there will be a notification message without prompt tone. A UIAbility (ServiceAbility in the FA model) can request only one continuous task at a time through this API. You can request multiple continuous tasks by calling [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) added in API version 21. |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | Requests a continuous task of a specific type. This API uses a promise to return the result. After a continuous task is successfully requested, there will be a notification message without prompt tone. A UIAbility (ServiceAbility in the FA model) can request only one continuous task at a time through this API. You can request multiple continuous tasks by calling [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) added in API version 21. |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | Requests continuous tasks of multiple types. This API uses a promise to return the result. After a continuous task is successfully requested, there will be a notification message without prompt tone. A UIAbility (ServiceAbility in the FA model) can request only one continuous task at a time through this API. You can request multiple continuous tasks by calling [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) added in API version 21. |
| [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) | Requests a continuous task. This API allows a UIAbility (ServiceAbility in the FA model) to request multiple continuous tasks and uses a promise to return the result. When using this API to request a continuous task, its notification can be combined with that of an existing continuous task. For details, see [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md). |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) | Cancels all continuous tasks in the current UIAbility (ServiceAbility in the FA model). This API uses an asynchronous callback to return the result. You can also call the [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) API to cancel a continuous task with the specified ID. |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) | Cancels all continuous tasks in the current UIAbility (ServiceAbility in the FA model). This API uses a promise to return the result. You can also call the [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) API to cancel a continuous task with the specified ID. |
| [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) | Cancels a continuous task with the specified ID. This API uses a promise to return the result. You can also call the [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) API to cancel all continuous tasks in the current UIAbility. |
| [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) | Updates continuous tasks of multiple types. This API uses a promise to return the result. After a continuous task is successfully updated, there will be a notification message without prompt tone. |
| [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) | Updates a continuous task. This API uses a promise to return the result. After a continuous task is successfully updated, there will be a notification message without prompt tone. |
| [updateDataTransferProgress](arkts-backgroundtasks-backgroundtaskmanager-updatedatatransferprogress-f.md) | Update notification. Only data transfer ContinuousTasks are supported. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [applyEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-applyefficiencyresources-f-sys.md) | Requests efficiency resources. |
| [getAllEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-getallefficiencyresources-f-sys.md) | Obtains all information about the requested efficiency resources, including the resource type. This API uses a promise to return the result. |
| [getBackgroundTaskState](arkts-backgroundtasks-backgroundtaskmanager-getbackgroundtaskstate-f-sys.md) | Obtains the authorization information of a continuous task. |
| [obtainAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-obtainallcontinuoustasks-f-sys.md) | Obtains all continuous task information, including the task ID and type. This API uses a promise to return the result. |
| [resetAllEfficiencyResources](arkts-backgroundtasks-backgroundtaskmanager-resetallefficiencyresources-f-sys.md) | Releases all efficiency resources. |
| [setBackgroundTaskState](arkts-backgroundtasks-backgroundtaskmanager-setbackgroundtaskstate-f-sys.md) | Sets the authorization information of a continuous task. |
| [subscribeContinuousTaskState](arkts-backgroundtasks-backgroundtaskmanager-subscribecontinuoustaskstate-f-sys.md) | Registers a callback to listen for the continuous task change events. |
| [unsubscribeContinuousTaskState](arkts-backgroundtasks-backgroundtaskmanager-unsubscribecontinuoustaskstate-f-sys.md) | Unregisters the callback for continuous task changes. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | Specifies details of the continuous task being requested or updated. It is typically used as input for the [startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) and [updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) APIs. Note that: |

### Interfaces

| Name | Description |
| --- | --- |
| [ContinuousTaskActiveInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskactiveinfo-i.md) | Describes the activation information of a continuous task. |
| [ContinuousTaskCancelInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskcancelinfo-i.md) | Describes the information about the cancellation of a continuous task. |
| [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | Describes the continuous task information. |
| [ContinuousTaskNotification](arkts-backgroundtasks-backgroundtaskmanager-continuoustasknotification-i.md) | Describes the information about a continuous-task notification. |
| [ContinuousTaskSuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendinfo-i.md) | Describes the information about a suspended continuous task. |
| [DataTransferProgress](arkts-backgroundtasks-backgroundtaskmanager-datatransferprogress-i.md) | Information about continuousTask notification progress. |
| [DelaySuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-delaysuspendinfo-i.md) | Defines the information about the transient task. |
| [ProgressInfo](arkts-backgroundtasks-backgroundtaskmanager-progressinfo-i.md) | Notify progress data. |
| [SuspendMessage](arkts-backgroundtasks-backgroundtaskmanager-suspendmessage-i.md) | Describes the reason why a continuous task is suspended. |
| [TransientTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-transienttaskinfo-i.md) | Describes all transient task information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BackgroundTaskStateInfo](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskstateinfo-i-sys.md) | Defines the authorization information of a continuous task. |
| [BackgroundTaskSubscriber](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubscriber-i-sys.md) | Represents a listener object used to listen for background task state changes. |
| [EfficiencyResourcesInfo](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcesinfo-i-sys.md) | Defines the efficiency resource information. |
| [EfficiencyResourcesRequest](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcesrequest-i-sys.md) | Describes the parameters for requesting efficiency resources. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e.md) | Defines the type of a continuous task. |
| [BackgroundModeType](arkts-backgroundtasks-backgroundtaskmanager-backgroundmodetype-e.md) | Defines the type of a continuous task. |
| [BackgroundSubMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundsubmode-e.md) | Defines the subtype of a continuous task. |
| [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md) | Main type of a continuous task. It is usually used together with the subtype [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md). For details, see the mapping table. The two types are newly added in API version 21 for [requesting](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) and [updating](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) continuous tasks. |
| [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md) | Defines the subtype of a continuous task. It is usually used together with the main type [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md). For details, see the mapping table. The two types are newly added in API version 21 for requesting and updating continuous tasks. |
| [ContinuousTaskCancelReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskcancelreason-e.md) | Describes the reason for canceling a continuous task. |
| [ContinuousTaskDetailedCancelReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskdetailedcancelreason-e.md) | Describes the detailed reason for canceling a continuous task. |
| [ContinuousTaskSuspendReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendreason-e.md) | Describes the reason why a continuous task is suspended. |
| [UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md) | Represents the user authorization result. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e-sys.md) | Defines the type of a continuous task. |
| [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e-sys.md) | Main type of a continuous task. It is usually used together with the subtype [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md). For details, see the mapping table. The two types are newly added in API version 21 for [requesting](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) and [updating](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) continuous tasks. |
| [EfficiencyResourcesCpuLevel](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcescpulevel-e-sys.md) | Defines the CPU level of the efficiency resource. |
| [ResourceType](arkts-backgroundtasks-backgroundtaskmanager-resourcetype-e-sys.md) | Enumerates the efficiency resource types. |
<!--DelEnd-->
