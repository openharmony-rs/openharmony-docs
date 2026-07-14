# BackgroundTaskMode

长时任务主类型。通常与长时任务子类型[BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtasksubmode-e.md)配合使用，对照关系请参考长时任务主类型与子类型
对照表，两者共同作为API version 21新增的
[申请](arkts-backgroundtasks-startbackgroundrunning-f.md#startbackgroundrunning-4)、
[更新](arkts-backgroundtasks-updatebackgroundrunning-f.md#updatebackgroundrunning-2)长时任务接口入参
，用于指定长时任务类型。</br>仅当主类型为MODE_SPECIAL_SCENARIO_PROCESSING特殊场景类型，或非PC/2in1设备主类型为MODE_TASK_KEEPING计算任务时，调用长时任务相关接口时需同时申
请ACL权限
[ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system)
，其他场景无需申请该权限。

**起始版本：** 21

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_ALLOW_WIFI_AWARE

```TypeScript
MODE_ALLOW_WIFI_AWARE = 7
```

WLAN相关业务。

**起始版本：** 21

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

