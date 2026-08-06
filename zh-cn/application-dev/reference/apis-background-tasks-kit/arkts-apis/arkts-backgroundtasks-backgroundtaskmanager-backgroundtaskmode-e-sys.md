# BackgroundTaskMode

长时任务主类型。通常与长时任务子类型[BackgroundTaskSubmode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_配合使用，对照关系请参考长时任务主类型与子类型 对照表，两者共同作为API version 21新增的 [申请]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [更新]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_长时任务接口入参 ，用于指定长时任务类型。\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_仅当主类型为MODE\_SPECIAL\_SCENARIO\_PROCESSING特殊场景类型，或非PC/2in1设备主类型为MODE\_TASK\_KEEPING计算任务时，调用长时任务相关接口时需同时申 请ACL权限 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ ，其他场景无需申请该权限。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-backgroundTaskManager-export enum BackgroundTaskMode--><!--Device-backgroundTaskManager-export enum BackgroundTaskMode-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## MODE_ALLOW_WIFI_AWARE

```TypeScript
MODE_ALLOW_WIFI_AWARE = 7
```

WLAN相关业务。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

<!--Device-BackgroundTaskMode-MODE_ALLOW_WIFI_AWARE = 7--><!--Device-BackgroundTaskMode-MODE_ALLOW_WIFI_AWARE = 7-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

