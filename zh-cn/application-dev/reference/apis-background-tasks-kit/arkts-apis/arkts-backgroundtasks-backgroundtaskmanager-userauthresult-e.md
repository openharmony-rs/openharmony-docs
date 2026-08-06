# UserAuthResult

用户授权结果。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-backgroundTaskManager-export enum UserAuthResult--><!--Device-backgroundTaskManager-export enum UserAuthResult-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## NOT_SUPPORTED

```TypeScript
NOT_SUPPORTED = 0
```

不支持。例如：申请的长时任务主类型非MODE\_SPECIAL\_SCENARIO\_PROCESSING时，不支持申请用户授权是否能在后台长时间运行。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-UserAuthResult-NOT_SUPPORTED = 0--><!--Device-UserAuthResult-NOT_SUPPORTED = 0-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## NOT_DETERMINED

```TypeScript
NOT_DETERMINED = 1
```

用户未操作。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-UserAuthResult-NOT_DETERMINED = 1--><!--Device-UserAuthResult-NOT_DETERMINED = 1-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## DENIED

```TypeScript
DENIED = 2
```

拒绝。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-UserAuthResult-DENIED = 2--><!--Device-UserAuthResult-DENIED = 2-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## GRANTED_ONCE

```TypeScript
GRANTED_ONCE = 3
```

本次允许。 **说明：** 在应用退出时该授权记录会被清除

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-UserAuthResult-GRANTED_ONCE = 3--><!--Device-UserAuthResult-GRANTED_ONCE = 3-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## GRANTED_ALWAYS

```TypeScript
GRANTED_ALWAYS = 4
```

始终允许。 **说明：** 当接收到以下公共事件时，相关授权记录将被清除： \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 、 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ 、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ 、 \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_ 、 \_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_ 。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-UserAuthResult-GRANTED_ALWAYS = 4--><!--Device-UserAuthResult-GRANTED_ALWAYS = 4-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

