# UserAuthResult

用户授权结果。

**起始版本：** 22

<!--Device-backgroundTaskManager-export enum UserAuthResult--><!--Device-backgroundTaskManager-export enum UserAuthResult-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## NOT_SUPPORTED

```TypeScript
NOT_SUPPORTED = 0
```

不支持。例如：申请的长时任务主类型非MODE_SPECIAL_SCENARIO_PROCESSING时，不支持申请用户授权是否能在后台长时间运行。

**起始版本：** 22

<!--Device-UserAuthResult-NOT_SUPPORTED = 0--><!--Device-UserAuthResult-NOT_SUPPORTED = 0-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## NOT_DETERMINED

```TypeScript
NOT_DETERMINED = 1
```

用户未操作。

**起始版本：** 22

<!--Device-UserAuthResult-NOT_DETERMINED = 1--><!--Device-UserAuthResult-NOT_DETERMINED = 1-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## DENIED

```TypeScript
DENIED = 2
```

拒绝。

**起始版本：** 22

<!--Device-UserAuthResult-DENIED = 2--><!--Device-UserAuthResult-DENIED = 2-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## GRANTED_ONCE

```TypeScript
GRANTED_ONCE = 3
```

本次允许。

**说明：** 在应用退出时该授权记录会被清除

**起始版本：** 22

<!--Device-UserAuthResult-GRANTED_ONCE = 3--><!--Device-UserAuthResult-GRANTED_ONCE = 3-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## GRANTED_ALWAYS

```TypeScript
GRANTED_ALWAYS = 4
```

始终允许。

**说明：**

当接收到以下公共事件时，相关授权记录将被清除：

[COMMON_EVENT_PACKAGE_ADDED](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_added)、[COMMON_EVENT_PACKAGE_REMOVED](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_removed)、[COMMON_EVENT_BUNDLE_REMOVED](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_bundle_removed)、[COMMON_EVENT_PACKAGE_FULLY_REMOVED](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_fully_removed)、[COMMON_EVENT_PACKAGE_CHANGED](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_changed)。

**起始版本：** 22

<!--Device-UserAuthResult-GRANTED_ALWAYS = 4--><!--Device-UserAuthResult-GRANTED_ALWAYS = 4-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

