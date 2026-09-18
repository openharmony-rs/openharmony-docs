# BackgroundTaskMode

Main type of a continuous task. It is usually used together with the subtype [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md). For details, see the mapping table. The two types are newly added in API version 21 for [requesting](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) and [updating](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) continuous tasks.

When the main type of the continuous task is **MODE_SPECIAL_SCENARIO_PROCESSING**, or that of a non-PC/2-in-1 device is **MODE_TASK_KEEPING**, you need to request the ACL permission [ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system) before calling APIs related to continuous tasks. In other scenarios, this permission is not required.

**Since:** 21

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_ALLOW_WIFI_AWARE

```TypeScript
MODE_ALLOW_WIFI_AWARE = 7
```

WLAN-related services.

**Since:** 21

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.
