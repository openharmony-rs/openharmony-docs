# @ohos.notificationManager

本模块提供通知管理的能力，应用可使用本模块完成通知的完整生命周期管理。其中涉及通知的发布、更新与取消，通知渠道的创建与查询、通知能力授权状态的查询与申请、应用角标的设置、通知中心存量通知的查询等操作。

**API组合使用关系说明**：

本模块的接口围绕通知的"授权→发布→取消→渠道管理"的完整流程展开，各接口间存在明确的组合使用关系：

1. **授权查询与申请流程**：发布通知前，先通过isNotificationEnabled查询通知能力的授权状态。如果通知能力未授权，通过requestEnableNotification引导用户开启通知权限。

2. **通知发布与更新流程**：通过publish发布通知，通知内容通过NotificationRequest指定。如果新发布通知与已有通知的ID和标签相同，将自动更新已有通知。如果新发布通知与已有通知的ID或标签不相同，将创建新的通知。

3. **通知取消流程**：通过cancel取消指定ID的通知，通过cancelAll取消本应用所有通知，通过cancelGroup取消指定分组下的通知。

4. **通知渠道管理流程**：通过addSlot创建通知渠道，通过getSlot/getSlots查询通知渠道配置，通过removeSlot/removeAllSlots删除通知渠道。建议在发布通知前先创建对应类型的通知渠道。除了可以使用addSlot创建通知渠道，还可以在发布通知的NotificationRequest中携带notificationSlotType字段，如果对应类型的渠道不存在，会自动创建。

5. **角标管理流程**：通过setBadgeNumber设置角标数字，或者通过publish接口发布通知时，在NotificationRequest的badgeNumber字段里携带需要增加的角标数量。

6. **存量通知查询流程**：通过getActiveNotificationCount获取通知中心本应用存量通知数量，通过getActiveNotifications获取通知中心本应用存量通知详情。

> **说明：**  
>  
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 9

<!--Device-unnamed-declare namespace notificationManager--><!--Device-unnamed-declare namespace notificationManager-End-->

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addSlot](arkts-notification-notificationmanager-addslot-f.md#addslot-2) | 创建指定类型的通知渠道。使用callback异步回调。  通知渠道NotificationSlot定义了通知的提醒方式（如提示音、振动、横幅等）和级别。发布通知前，应用需先创建对应类型的通知渠道，或者发布通知时系统将自动创建对应类型的通知渠道。同一类型的通知渠道只能创建一个。 |
| [addSlot](arkts-notification-notificationmanager-addslot-f.md#addslot-3) | 创建指定类型的通知渠道。使用Promise异步回调。  通知渠道NotificationSlot定义了通知的提醒方式（如提示音、振动、横幅等）和级别。发布通知前，应用需先创建对应类型的通知渠道，或者发布通知时系统将自动创建对应类型的通知渠道。同一类型的通知渠道只能创建一个。 |
| [cancel](arkts-notification-notificationmanager-cancel-f.md#cancel) | 根据指定的通知ID取消已发布的通知。使用callback异步回调。  取消后，对应的通知将从通知中心、状态栏等位置移除，用户不再可见。与带label参数的notificationManager.cancel(id, label, callback)相比，此接口不传入label，将取消与指定ID匹配的通知。当发布通知，label不为空时，则需使用接口notificationManager.cancel(id, label, callback)取消通知。 |
| [cancel](arkts-notification-notificationmanager-cancel-f.md#cancel-1) | 根据通知ID和标签取消已发布的通知。使用callback异步回调。  取消后，对应的通知将从通知中心、状态栏等位置移除，用户不再可见。适用于需要精确取消某一条带有特定标签的通知的场景。与仅传入通知ID的notificationManager.cancel(id, callback)相比，此接口额外传入label参数，可精确取消同一ID下不同标签的通知。 |
| [cancel](arkts-notification-notificationmanager-cancel-f.md#cancel-2) | 根据通知ID和标签取消已发布的通知，若标签为空，则取消与指定通知ID匹配，标签为空的已发布通知。使用Promise异步回调。  取消后，对应的通知将从通知中心、状态栏等位置移除，用户不再可见。 |
| [cancelAll](arkts-notification-notificationmanager-cancelall-f.md#cancelall) | 取消当前应用所有已发布的通知。使用callback异步回调。  取消后，当前应用的所有通知将从通知中心、状态栏等位置移除，用户不再可见。适用于应用退出或用户手动清除全部通知的场景。 |
| [cancelAll](arkts-notification-notificationmanager-cancelall-f.md#cancelall-1) | 取消当前应用所有已发布的通知。使用Promise异步回调。  取消后，当前应用的所有通知将从通知中心、状态栏等位置移除，用户不再可见。适用于应用退出或用户手动清除全部通知的场景。 |
| [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md#cancelgroup) | 取消当前应用指定组下的通知。使用callback异步回调。  通知组groupName是在发布通知时通过NotificationRequest的groupName字段指定的分组标识。取消后，该组下所有通知将从通知中心移除。适用于需要按业务分组批量取消通知的场景。 |
| [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md#cancelgroup-1) | 取消当前应用指定组下的通知。使用Promise异步回调。  通知组groupName是在发布通知时通过NotificationRequest的groupName字段指定的分组标识。取消后，该组下所有通知将从通知中心移除。适用于需要按业务分组批量取消通知的场景。 |
| [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md#getactivenotificationcount) | 获取当前应用未删除的通知数。使用callback异步回调。 |
| [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md#getactivenotificationcount-1) | 获取当前应用未删除的通知数。使用Promise异步回调。 |
| [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md#getactivenotifications) | 获取当前应用未删除的通知列表。使用callback异步回调。 |
| [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md#getactivenotifications-1) | 获取当前应用未删除的通知列表。使用Promise异步回调。 |
| [getBadgeNumber](arkts-notification-notificationmanager-getbadgenumber-f.md#getbadgenumber) | 获取当前应用角标数量。使用Promise异步回调。  用于查询当前应用桌面图标上显示的角标数字。 |
| [getNotificationParameters](arkts-notification-notificationmanager-getnotificationparameters-f.md#getnotificationparameters) | 获取通知[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)中wantAgent字段的部分信息。使用Promise异步回调。 |
| [getNotificationSetting](arkts-notification-notificationmanager-getnotificationsetting-f.md#getnotificationsetting) | 获取应用程序的通知设置，包括锁屏通知、横幅通知、桌面角标、振动、铃声等开关状态。使用Promise异步回调。 |
| [getSlot](arkts-notification-notificationmanager-getslot-f.md#getslot) | 获取指定类型的通知渠道。使用callback异步回调。  用于查询已创建的通知渠道的详细配置信息，包括提醒方式、级别、锁屏显示等设置。需先通过addSlot创建对应类型的通知渠道，否则获取结果为空。 |
| [getSlot](arkts-notification-notificationmanager-getslot-f.md#getslot-1) | 获取指定类型的通知渠道。使用Promise异步回调。  用于查询已创建的通知渠道的详细配置信息，包括提醒方式、级别、锁屏显示等设置。需先通过addSlot创建对应类型的通知渠道，否则获取结果为空。 |
| [getSlots](arkts-notification-notificationmanager-getslots-f.md#getslots) | 获取当前应用的所有通知渠道。使用callback异步回调。  用于批量查询当前应用已创建的所有通知渠道的配置信息，包括各渠道的类型、提醒方式、级别等设置。适用于需要查看所有渠道配置的场景。 |
| [getSlots](arkts-notification-notificationmanager-getslots-f.md#getslots-1) | 获取当前应用的所有通知渠道。使用Promise异步回调。  用于批量查询当前应用已创建的所有通知渠道的配置信息，包括各渠道的类型、提醒方式、级别等设置。适用于需要查看所有渠道配置的场景。 |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md#isdistributedenabled) | 查询设备是否支持跨设备协同通知。使用callback异步回调。 |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md#isdistributedenabled-1) | 查询设备是否支持跨设备协同通知。使用Promise异步回调。 |
| [isGeofenceEnabled](arkts-notification-notificationmanager-isgeofenceenabled-f.md#isgeofenceenabled) | 检查地理围栏功能是否已启用。使用Promise异步回调。 |
| [isNotificationEnabledSync](arkts-notification-notificationmanager-isnotificationenabledsync-f.md#isnotificationenabledsync) | 同步查询当前应用通知授权状态。  用于在发布通知前快速检查当前应用是否被允许发送通知。此接口为同步接口，调用后立即返回结果，适用于需要在同步代码流程中获取使能状态的场景。 |
| [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md#issupporttemplate) | 在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。 |
| [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md#issupporttemplate-1) | 在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用Promise异步回调。 |
| [openNotificationSettings](arkts-notification-notificationmanager-opennotificationsettings-f.md#opennotificationsettings) | 拉起应用的通知设置界面，该页面以半模态形式呈现，可用于设置通知开关、通知提醒方式等。使用Promise异步回调。  适用于用户需要手动修改通知设置的场景，如用户拒绝授权后二次申请，或需要修改通知提醒方式（振动、响铃等）。当requestEnableNotification弹窗被用户拒绝后，开发者可调用此接口引导用户前往通知设置页面手动开启。 |
| [openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md#opennotificationsettingswithresult) | 拉起应用的通知设置界面，该页面以半模态形式呈现，可用于设置通知开关、通知提醒方式等。使用Promise异步回调，当半模态窗口关闭时返回用户设置的状态。  与openNotificationSettings相比，此接口在半模态窗口关闭时返回NotificationSetting对象，开发者可根据返回结果判断用户是否开启了通知权限，从而决定后续逻辑。 |
| [publish](arkts-notification-notificationmanager-publish-f.md#publish) | 发布通知。使用callback异步回调。  发布通知后，通知将以通知卡片的形式展示在设备的通知中心、状态栏等位置。如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知，实现通知的更新效果。 |
| [publish](arkts-notification-notificationmanager-publish-f.md#publish-1) | 发布通知。使用Promise异步回调。  发布通知后，通知将以通知卡片的形式展示在设备的通知中心、状态栏等位置。如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知，实现通知的更新效果。 |
| [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md#removeallslots) | 删除当前应用所有通知渠道。使用callback异步回调。  删除后，当前应用的所有通知渠道及其配置将被永久移除，后续发布通知时系统将自动创建对应类型的渠道。已通过这些渠道发布的通知不受影响，仍可在通知中心查看。适用于需要一次性清除所有渠道配置的场景。 |
| [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md#removeallslots-1) | 删除当前应用所有通知渠道。使用Promise异步回调。  删除后，当前应用的所有通知渠道及其配置将被永久移除，后续发布通知时系统将自动创建对应类型的渠道。已通过这些渠道发布的通知不受影响，仍可在通知中心查看。适用于需要一次性清除所有渠道配置的场景。 |
| [removeSlot](arkts-notification-notificationmanager-removeslot-f.md#removeslot) | 删除当前应用指定类型的通知渠道。使用callback异步回调。  删除后，对应类型的通知渠道及其配置将被永久移除，后续发布该类型通知时系统将自动创建默认渠道。已通过该渠道发布的通知不受影响，仍可在通知中心查看。适用于需要重新配置渠道时先删除再创建的场景。 |
| [removeSlot](arkts-notification-notificationmanager-removeslot-f.md#removeslot-1) | 删除当前应用指定类型的通知渠道。使用Promise异步回调。  删除后，对应类型的通知渠道及其配置将被永久移除，后续发布该类型通知时系统将自动创建默认渠道。已通过该渠道发布的通知不受影响，仍可在通知中心查看。适用于需要重新配置渠道时先删除再创建的场景。 |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification) | 当前应用请求通知使能。使用callback异步回调。 |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-1) | 应用需要获取用户授权才能发送通知。在通知发布前调用该接口，可以拉起通知授权弹窗，让用户选择是否允许发送通知。使用callback异步回调。 |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-2) | 当前应用请求通知使能。使用Promise异步回调。 |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-3) | 应用需要获取用户授权才能发送通知。在通知发布前调用该接口，可以拉起通知授权弹窗，让用户选择是否允许发送通知。使用Promise异步回调。 |
| [setBadgeNumber](arkts-notification-notificationmanager-setbadgenumber-f.md#setbadgenumber) | 设定角标个数，在应用的桌面图标上呈现。使用callback异步回调。  角标是应用桌面图标右上角显示的数字标识，用于提示用户有未处理的通知数量。设定后，桌面图标将显示对应角标数字。适用于需要在桌面图标上提示用户待处理消息数量的场景，如未读消息数、待办事项数等。 |
| [setBadgeNumber](arkts-notification-notificationmanager-setbadgenumber-f.md#setbadgenumber-1) | 设定角标个数，在应用的桌面图标上呈现。使用Promise异步回调。  角标是应用桌面图标右上角显示的数字标识，用于提示用户有未处理的通知数量。设定后，桌面图标将显示对应角标数字。适用于需要在桌面图标上提示用户待处理消息数量的场景，如未读消息数、待办事项数等。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addDoNotDisturbProfile](arkts-notification-notificationmanager-adddonotdisturbprofile-f-sys.md#adddonotdisturbprofile) | 添加勿扰模式配置信息。使用Promise异步回调。 |
| [addDoNotDisturbProfile](arkts-notification-notificationmanager-adddonotdisturbprofile-f-sys.md#adddonotdisturbprofile-1) | 向指定用户添加勿扰模式配置信息。使用Promise异步回调。 |
| [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot) | 创建通知渠道。使用callback异步回调。 |
| [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot-1) | 创建通知渠道。使用Promise异步回调。 |
| [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md#addslots) | 创建多个通知渠道。使用callback异步回调。 |
| [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md#addslots-1) | 创建多个通知渠道。使用Promise异步回调。 |
| [cancel](arkts-notification-notificationmanager-cancel-f-sys.md#cancel-3) | 代理取消当前用户其他应用的通知。使用Promise异步回调。  需要当前应用与其他应用存在代理关系，或者当前应用有ohos.permission.NOTIFICATION_AGENT_CONTROLLER权限。 |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md#cancelasbundle) | 取消代理通知。使用callback异步回调。 |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md#cancelasbundle-1) | 取消代理通知。使用Promise异步回调。 |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md#cancelasbundle-2) | 取消代理通知。使用Promise异步回调。 |
| [disableNotificationFeature](arkts-notification-notificationmanager-disablenotificationfeature-f-sys.md#disablenotificationfeature) | 将应用包名添加到通知发布权限管控名单，以阻止应用发布通知。支持启用或关闭该功能。 |
| [disableNotificationFeature](arkts-notification-notificationmanager-disablenotificationfeature-f-sys.md#disablenotificationfeature-1) | 将应用包名添加到通知发布权限管控名单，以阻止应用发布通知。使用Promise异步回调。 |
| [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md#displaybadge) | 设定指定应用的角标使能状态。使用callback异步回调。 |
| [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md#displaybadge-1) | 设定指定应用的角标使能状态。使用Promise异步回调。 |
| [getActiveNotificationByFilter](arkts-notification-notificationmanager-getactivenotificationbyfilter-f-sys.md#getactivenotificationbyfilter) | 获取满足条件的普通实况通知信息。使用callback异步回调。 |
| [getActiveNotificationByFilter](arkts-notification-notificationmanager-getactivenotificationbyfilter-f-sys.md#getactivenotificationbyfilter-1) | 获取满足条件的普通实况通知信息。使用Promise异步回调。 |
| [getAllActiveNotifications](arkts-notification-notificationmanager-getallactivenotifications-f-sys.md#getallactivenotifications) | 获取当前未删除的所有通知。使用callback异步回调。 |
| [getAllActiveNotifications](arkts-notification-notificationmanager-getallactivenotifications-f-sys.md#getallactivenotifications-1) | 获取当前未删除的所有通知。使用Promise异步回调。 |
| [getAllNotificationEnabledBundles](arkts-notification-notificationmanager-getallnotificationenabledbundles-f-sys.md#getallnotificationenabledbundles) | 获取允许通知的应用程序列表。使用Promise异步回调。 |
| [getAllNotificationEnabledBundles](arkts-notification-notificationmanager-getallnotificationenabledbundles-f-sys.md#getallnotificationenabledbundles-1) | 获取指定用户下允许通知的应用程序列表。使用Promise异步回调。 |
| [getBadgeDisplayStatusByBundles](arkts-notification-notificationmanager-getbadgedisplaystatusbybundles-f-sys.md#getbadgedisplaystatusbybundles) | 批量获取应用角标显示状态。使用Promise异步回调。 |
| [getBundlePriorityConfig](arkts-notification-notificationmanager-getbundlepriorityconfig-f-sys.md#getbundlepriorityconfig) | 获取应用的优先功能配置。 |
| [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md#getdeviceremindtype) | 获取通知的提醒方式。使用callback异步回调。 |
| [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md#getdeviceremindtype-1) | 获取通知的提醒方式。使用Promise异步回调。 |
| [getDistributedDeviceList](arkts-notification-notificationmanager-getdistributeddevicelist-f-sys.md#getdistributeddevicelist) | 查询支持跨设备协同通知的设备类型。使用Promise异步回调。 |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate) | 查询免打扰时间。使用callback异步回调。 |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-1) | 查询免打扰时间。使用Promise异步回调。 |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-2) | 查询指定用户的免打扰时间。使用callback异步回调。 |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-3) | 查询指定用户的免打扰时间。使用Promise异步回调。 |
| [getDoNotDisturbProfile](arkts-notification-notificationmanager-getdonotdisturbprofile-f-sys.md#getdonotdisturbprofile) | 查询勿扰模式配置信息。使用Promise异步回调。 |
| [getDoNotDisturbProfile](arkts-notification-notificationmanager-getdonotdisturbprofile-f-sys.md#getdonotdisturbprofile-1) | 查询指定用户的勿扰模式配置信息。使用Promise异步回调。 |
| [getNotificationStatisticsByBundle](arkts-notification-notificationmanager-getnotificationstatisticsbybundle-f-sys.md#getnotificationstatisticsbybundle) | 批量获取指定应用列表的通知统计信息，使用Promise异步回调。 |
| [getNotificationSwitch](arkts-notification-notificationmanager-getnotificationswitch-f-sys.md#getnotificationswitch) | 获取通知开关状态。使用Promise异步回调。 |
| [getPriorityEnabledByBundles](arkts-notification-notificationmanager-getpriorityenabledbybundles-f-sys.md#getpriorityenabledbybundles) | 批量获取应用通知优先级开关状态。使用Promise异步回调。 |
| [getPriorityStrategyByBundles](arkts-notification-notificationmanager-getprioritystrategybybundles-f-sys.md#getprioritystrategybybundles) | 批量获取应用通知优先策略。使用Promise异步回调。 |
| [getReminderInfoByBundles](arkts-notification-notificationmanager-getreminderinfobybundles-f-sys.md#getreminderinfobybundles) | 批量获取指定应用提醒信息。使用Promise异步回调。 |
| [getRingtoneInfoByBundle](arkts-notification-notificationmanager-getringtoneinfobybundle-f-sys.md#getringtoneinfobybundle) | 获取应用自定义铃声信息。使用Promise异步回调。 |
| [getSlotByBundle](arkts-notification-notificationmanager-getslotbybundle-f-sys.md#getslotbybundle) | 获取指定应用指定类型的通知渠道。使用Promise异步回调。  获取前需要先通过[addSlot](arkts-notification-notificationmanager-addslot-f.md#addslot-3)创建通知渠道。 |
| [getSlotFlagsByBundle](arkts-notification-notificationmanager-getslotflagsbybundle-f-sys.md#getslotflagsbybundle) | 获取指定应用的通知渠道标识位。使用Promise异步回调。 |
| [getSlotNumByBundle](arkts-notification-notificationmanager-getslotnumbybundle-f-sys.md#getslotnumbybundle) | 获取指定应用的通知渠道数量。使用callback异步回调。 |
| [getSlotNumByBundle](arkts-notification-notificationmanager-getslotnumbybundle-f-sys.md#getslotnumbybundle-1) | 获取指定应用的通知渠道数量。使用Promise异步回调。 |
| [getSlotsByBundle](arkts-notification-notificationmanager-getslotsbybundle-f-sys.md#getslotsbybundle) | 获取指定应用的所有通知渠道。使用callback异步回调。 |
| [getSlotsByBundle](arkts-notification-notificationmanager-getslotsbybundle-f-sys.md#getslotsbybundle-1) | 获取指定应用的所有通知渠道。使用Promise异步回调。 |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-getsyncnotificationenabledwithoutapp-f-sys.md#getsyncnotificationenabledwithoutapp) | 获取同步通知到未安装应用程序设备的开关是否开启(callback形式)。 |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-getsyncnotificationenabledwithoutapp-f-sys.md#getsyncnotificationenabledwithoutapp-1) | 获取同步通知到未安装应用程序设备的开关是否开启(Promise形式)。 |
| [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md#isbadgedisplayed) | 获取指定应用的角标使能状态。使用callback异步回调。 |
| [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md#isbadgedisplayed-1) | 获取指定应用的角标使能状态。使用Promise异步回调。 |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f-sys.md#isdistributedenabled-2) | 查询设备是否支持跨设备协同通知。使用Promise异步回调。 |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle) | 根据应用的包获取应用程序是否支持分布式通知。使用callback异步回调。 |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-1) | 查询指定应用是否支持分布式通知。使用Promise异步回调。 |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-2) | 获取指定应用是否支持跨设备协同。使用Promise异步回调。 |
| [isDistributedEnabledBySlot](arkts-notification-notificationmanager-isdistributedenabledbyslot-f-sys.md#isdistributedenabledbyslot) | 查询指定渠道的通知是否支持通知跨设备协同至指定类型设备。使用Promise异步回调。 |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled) | 获取指定应用的通知使能状态。使用callback异步回调。 |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-1) | 获取指定应用的通知使能状态。使用Promise异步回调。 |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-2) | 查询当前应用通知授权状态。使用callback异步回调。  用于在发布通知前检查当前应用是否被允许发送通知，避免在通知授权关闭时发布导致失败。 |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-3) | 查询当前应用通知授权状态。使用Promise异步回调。  用于在发布通知前检查当前应用是否被允许发送通知，避免在通知使能关闭时发布导致失败。 |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-4) | 获取指定用户ID下的通知使能状态。使用callback异步回调。 |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-5) | 获取指定用户下的通知使能状态。使用Promise异步回调。 |
| [isNotificationSlotEnabled](arkts-notification-notificationmanager-isnotificationslotenabled-f-sys.md#isnotificationslotenabled) | 获取指定应用的指定渠道类型的使能状态。使用callback异步回调。 |
| [isNotificationSlotEnabled](arkts-notification-notificationmanager-isnotificationslotenabled-f-sys.md#isnotificationslotenabled-1) | 获取指定应用的指定渠道类型的使能状态。使用Promise异步回调。 |
| [isNotificationSlotEnabledByBundles](arkts-notification-notificationmanager-isnotificationslotenabledbybundles-f-sys.md#isnotificationslotenabledbybundles) | 批量获取多个应用的指定渠道类型的使能状态。使用Promise异步回调。 |
| [isPriorityEnabled](arkts-notification-notificationmanager-ispriorityenabled-f-sys.md#ispriorityenabled) | 获取通知优先级总开关状态。 |
| [isPriorityEnabledByBundle](arkts-notification-notificationmanager-ispriorityenabledbybundle-f-sys.md#ispriorityenabledbybundle) | 获取应用通知优先级开关状态。 |
| [isPriorityIntelligentEnabled](arkts-notification-notificationmanager-ispriorityintelligentenabled-f-sys.md#ispriorityintelligentenabled) | 获取优先通知智能服务使能状态。使用Promise异步回调。 |
| [isSilentReminderEnabled](arkts-notification-notificationmanager-issilentreminderenabled-f-sys.md#issilentreminderenabled) | 查询静默提醒的开关状态。使用Promise进行异步回调。 |
| [isSmartReminderEnabled](arkts-notification-notificationmanager-issmartreminderenabled-f-sys.md#issmartreminderenabled) | 获取设备是否与其他设备协同智能提醒。使用Promise异步回调。 |
| [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md#issupportdonotdisturbmode) | 查询是否支持免打扰功能。使用callback异步回调。 |
| [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md#issupportdonotdisturbmode-1) | 查询是否支持免打扰功能。使用Promise异步回调。 |
| [off](arkts-notification-notificationmanager-off-f-sys.md#off) | 取消通知监听回调。 |
| [offBadgeNumberQuery](arkts-notification-notificationmanager-offbadgenumberquery-f-sys.md#offbadgenumberquery) | 取消应用角标数量查询回调。 |
| [on](arkts-notification-notificationmanager-on-f-sys.md#on) | 注册通知监听回调。通知服务将通知信息回调给校验程序，校验程序返回校验结果决定该通知是否发布，如营销类通知发布频率控制等。  系统中每个SlotType只允许存在一个注册者。 |
| [on](arkts-notification-notificationmanager-on-f-sys.md#on-1) | 注册通知监听回调。通知服务将通知信息回调给校验程序，校验程序返回校验结果决定该通知是否发布，如营销类通知发布频率控制等。使用Promise异步回调。  系统中每个SlotType只允许存在一个注册者。 |
| [onBadgeNumberQuery](arkts-notification-notificationmanager-onbadgenumberquery-f-sys.md#onbadgenumberquery) | 注册应用角标数量查询回调。 |
| [publish](arkts-notification-notificationmanager-publish-f-sys.md#publish-2) | 发布通知给指定的用户。使用callback异步回调。 |
| [publish](arkts-notification-notificationmanager-publish-f-sys.md#publish-3) | 发布通知给指定的用户。使用Promise异步回调。 |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md#publishasbundle) | 发布代理通知。使用callback异步回调。 |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md#publishasbundle-1) | 发布代理通知。使用Promise异步回调。 |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md#publishasbundle-2) | 发布代理通知。使用Promise异步回调。 |
| [removeDoNotDisturbProfile](arkts-notification-notificationmanager-removedonotdisturbprofile-f-sys.md#removedonotdisturbprofile) | 删除勿扰模式配置。使用Promise异步回调。 |
| [removeDoNotDisturbProfile](arkts-notification-notificationmanager-removedonotdisturbprofile-f-sys.md#removedonotdisturbprofile-1) | 删除指定用户的勿扰模式配置。使用Promise异步回调。 |
| [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md#removegroupbybundle) | 删除指定应用的指定组下的通知。使用callback异步回调。 |
| [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md#removegroupbybundle-1) | 删除指定应用的指定组下的通知。使用Promise异步回调。 |
| [setAdditionalConfig](arkts-notification-notificationmanager-setadditionalconfig-f-sys.md#setadditionalconfig) | 设置通知的系统附加配置信息。使用Promise异步回调。 |
| [setBadgeDisplayStatusByBundles](arkts-notification-notificationmanager-setbadgedisplaystatusbybundles-f-sys.md#setbadgedisplaystatusbybundles) | 批量设置指定应用是否显示角标。使用Promise异步回调。 |
| [setBadgeNumberByBundle](arkts-notification-notificationmanager-setbadgenumberbybundle-f-sys.md#setbadgenumberbybundle) | 代理其他应用设定角标个数。使用Promise异步回调。 |
| [setBundlePriorityConfig](arkts-notification-notificationmanager-setbundlepriorityconfig-f-sys.md#setbundlepriorityconfig) | 设置应用的优先功能配置。 |
| [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md#setdistributedenable) | 设置设备是否支持分布式通知。使用callback异步回调。 |
| [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md#setdistributedenable-1) | 设置设备是否支持分布式通知。使用Promise异步回调。 |
| [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle) | 设置指定应用是否支持分布式通知。使用callback异步回调。 |
| [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle-1) | 设置指定应用是否支持分布式通知。使用Promise异步回调。 |
| [setDistributedEnableByBundles](arkts-notification-notificationmanager-setdistributedenablebybundles-f-sys.md#setdistributedenablebybundles) | 批量设置应用是否支持跨设备协同。使用Promise异步回调。 |
| [setDistributedEnabled](arkts-notification-notificationmanager-setdistributedenabled-f-sys.md#setdistributedenabled) | 设置设备是否支持跨设备协同通知。使用Promise异步回调。 |
| [setDistributedEnabledByBundle](arkts-notification-notificationmanager-setdistributedenabledbybundle-f-sys.md#setdistributedenabledbybundle) | 设置指定应用是否支持跨设备协同。使用Promise异步回调。 |
| [setDistributedEnabledBySlot](arkts-notification-notificationmanager-setdistributedenabledbyslot-f-sys.md#setdistributedenabledbyslot) | 设置指定渠道的通知是否支持通知跨设备协同至指定类型设备。使用Promise异步回调。 |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate) | 设置免打扰时间。使用callback异步回调。 |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-1) | 设置免打扰时间。使用Promise异步回调。 |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-2) | 指定用户设置免打扰时间。使用callback异步回调。 |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-3) | 指定用户设置免打扰时间。使用Promise异步回调。 |
| [setGeofenceEnabled](arkts-notification-notificationmanager-setgeofenceenabled-f-sys.md#setgeofenceenabled) | 设置地理围栏的启用状态。使用Promise异步回调。 |
| [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md#setnotificationenable) | 设定指定应用的通知使能状态。使用callback异步回调。 |
| [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md#setnotificationenable-1) | 设定指定应用的通知使能状态。使用Promise异步回调。 |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md#setnotificationenableslot) | 设置指定应用的指定渠道类型的使能状态。使用callback异步回调。 |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md#setnotificationenableslot-1) | 设置指定应用的指定渠道类型的使能状态。使用callback异步回调。 |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md#setnotificationenableslot-2) | 设置指定应用的指定渠道类型的使能状态。使用promise异步回调。 |
| [setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md#setnotificationswitch) | 设置通知开关状态。使用Promise异步回调。 |
| [setPriorityEnabled](arkts-notification-notificationmanager-setpriorityenabled-f-sys.md#setpriorityenabled) | 设置通知优先级总开关。 |
| [setPriorityEnabledByBundle](arkts-notification-notificationmanager-setpriorityenabledbybundle-f-sys.md#setpriorityenabledbybundle) | 设置应用通知优先级开关。 |
| [setPriorityEnabledByBundles](arkts-notification-notificationmanager-setpriorityenabledbybundles-f-sys.md#setpriorityenabledbybundles) | 批量设置应用通知优先级开关状态。使用Promise异步回调。 |
| [setPriorityIntelligentEnabled](arkts-notification-notificationmanager-setpriorityintelligentenabled-f-sys.md#setpriorityintelligentenabled) | 设置优先通知智能服务使能状态。使用Promise异步回调。 |
| [setPriorityStrategyByBundles](arkts-notification-notificationmanager-setprioritystrategybybundles-f-sys.md#setprioritystrategybybundles) | 批量设置应用通知优先策略。使用Promise异步回调。 |
| [setReminderInfoByBundles](arkts-notification-notificationmanager-setreminderinfobybundles-f-sys.md#setreminderinfobybundles) | 批量设置指定应用提醒信息。使用Promise异步回调。 |
| [setRingtoneInfoByBundle](arkts-notification-notificationmanager-setringtoneinfobybundle-f-sys.md#setringtoneinfobybundle) | 设置应用自定义铃声信息。使用Promise异步回调。 |
| [setSilentReminderEnabled](arkts-notification-notificationmanager-setsilentreminderenabled-f-sys.md#setsilentreminderenabled) | 设置静默提醒的开关状态。使用Promise进行异步回调。 |
| [setSlotByBundle](arkts-notification-notificationmanager-setslotbybundle-f-sys.md#setslotbybundle) | 设置指定应用的通知渠道。使用callback异步回调。  设置前需要先通过[addSlot](arkts-notification-notificationmanager-addslot-f.md#addslot-3)创建通知渠道。 |
| [setSlotByBundle](arkts-notification-notificationmanager-setslotbybundle-f-sys.md#setslotbybundle-1) | 设置指定应用的通知渠道。使用Promise异步回调。  设置前需要先通过[addSlot](arkts-notification-notificationmanager-addslot-f.md#addslot-3)创建通知渠道。 |
| [setSlotFlagsByBundle](arkts-notification-notificationmanager-setslotflagsbybundle-f-sys.md#setslotflagsbybundle) | 设定指定应用的通知提醒方式开关。使用Promise异步回调。 |
| [setSmartReminderEnabled](arkts-notification-notificationmanager-setsmartreminderenabled-f-sys.md#setsmartreminderenabled) | 设置设备是否与其他设备协同智能提醒。使用Promise异步回调。 |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-setsyncnotificationenabledwithoutapp-f-sys.md#setsyncnotificationenabledwithoutapp) | 设置是否将通知同步到未安装应用程序的设备(callback形式)。 |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-setsyncnotificationenabledwithoutapp-f-sys.md#setsyncnotificationenabledwithoutapp-1) | 设置是否将通知同步到未安装应用程序的设备(Promise形式)。 |
| [setTargetDeviceStatus](arkts-notification-notificationmanager-settargetdevicestatus-f-sys.md#settargetdevicestatus) | 设置设备配对成功后的状态。当发布通知时，会根据各个设备的状态来确定当前设备的通知提醒方式。 |
| [snoozeNotification](arkts-notification-notificationmanager-snoozenotification-f-sys.md#snoozenotification) | 设置通知稍后提醒。该通知在指定时间后再次提醒，每次设置只会提醒一次，提醒方式与该通知相同。设置后该通知被删除。 |
| [subscribeSystemLiveView](arkts-notification-notificationmanager-subscribesystemliveview-f-sys.md#subscribesystemliveview) | 订阅系统实况窗。使用Promise异步回调。 |
| [triggerSystemLiveView](arkts-notification-notificationmanager-triggersystemliveview-f-sys.md#triggersystemliveview) | 触发系统实况窗。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [NotificationSetting](arkts-notification-notificationmanager-notificationsetting-i.md) | 通知提醒方式开关的设置状态。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundleNotificationStatistics](arkts-notification-notificationmanager-bundlenotificationstatistics-i-sys.md) | 描述指定应用通知统计信息。 |
| [ButtonOptions](arkts-notification-notificationmanager-buttonoptions-i-sys.md) | 描述触发按钮信息。 |
| [DistributedBundleEnableInfo](arkts-notification-notificationmanager-distributedbundleenableinfo-i-sys.md) | 描述多设备协同的包信息。 |
| [DoNotDisturbDate](arkts-notification-notificationmanager-donotdisturbdate-i-sys.md) | 免打扰时间选项。 |
| [DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md) | 勿扰模式的配置信息。 |
| [NotificationCheckInfo](arkts-notification-notificationmanager-notificationcheckinfo-i-sys.md) | 通知校验参数。 |
| [NotificationCheckResult](arkts-notification-notificationmanager-notificationcheckresult-i-sys.md) | 通知校验结果。 |
| [NotificationReminderInfo](arkts-notification-notificationmanager-notificationreminderinfo-i-sys.md) | 描述指定应用提醒方式信息。 |
| [RingtoneInfo](arkts-notification-notificationmanager-ringtoneinfo-i-sys.md) | 描述自定义铃声信息。 |
| [SystemLiveViewSubscriber](arkts-notification-notificationmanager-systemliveviewsubscriber-i-sys.md) | 系统实况窗订阅者。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContentType](arkts-notification-notificationmanager-contenttype-e.md) | 通知内容类型。 |
| [PriorityNotificationType](arkts-notification-notificationmanager-prioritynotificationtype-e.md) | 描述通知的优先级类型。 |
| [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) | 通知级别。  用于定义NotificationSlot的通知提醒行为级别，影响通知在状态栏的显示方式，是否展示横幅和提示音等。 |
| [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 通知渠道类型。  不同类型对应不同的SlotLevel，决定通知的提醒行为。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceRemindType](arkts-notification-notificationmanager-deviceremindtype-e-sys.md) | 通知提醒方式。 |
| [DoNotDisturbType](arkts-notification-notificationmanager-donotdisturbtype-e-sys.md) | 免打扰设置的时间类型。 |
| [NotificationControlFlagStatus](arkts-notification-notificationmanager-notificationcontrolflagstatus-e-sys.md) | 每个bit位都可以控制通知的提示方式。当notificationControlFlags和下表中枚举值进行按位或操作，则表示关闭其提示方式。 |
| [PriorityEnableStatus](arkts-notification-notificationmanager-priorityenablestatus-e-sys.md) | 描述应用通知的优先级开关状态。 |
| [PriorityNotificationType](arkts-notification-notificationmanager-prioritynotificationtype-e-sys.md) | 描述通知的优先级类型。 |
| [PriorityStrategyStatus](arkts-notification-notificationmanager-prioritystrategystatus-e-sys.md) | 描述应用通知的优先策略。 |
| [RingtoneType](arkts-notification-notificationmanager-ringtonetype-e-sys.md) | 描述自定义铃声类型。 |
| [SlotType](arkts-notification-notificationmanager-slottype-e-sys.md) | 通知渠道类型。  不同类型对应不同的SlotLevel，决定通知的提醒行为。 |
| [SourceType](arkts-notification-notificationmanager-sourcetype-e-sys.md) | 通知来源类型。 |
| [SwitchState](arkts-notification-notificationmanager-switchstate-e-sys.md) | 描述通知相关开关的设置状态。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | 指定应用的包信息。 |
| [DistributedOptions](arkts-notification-notificationmanager-distributedoptions-t.md) | 分布式选项。 |
| [NotificationActionButton](arkts-notification-notificationmanager-notificationactionbutton-t.md) | 通知中显示的操作按钮。 |
| [NotificationBasicContent](arkts-notification-notificationmanager-notificationbasiccontent-t.md) | 普通文本通知。 |
| [NotificationButton](arkts-notification-notificationmanager-notificationbutton-t.md) | 通知按钮。 |
| [NotificationCapsule](arkts-notification-notificationmanager-notificationcapsule-t.md) | 通知胶囊。 |
| [NotificationContent](arkts-notification-notificationmanager-notificationcontent-t.md) | 通知内容。 |
| [NotificationLongTextContent](arkts-notification-notificationmanager-notificationlongtextcontent-t.md) | 长文本通知。 |
| [NotificationMultiLineContent](arkts-notification-notificationmanager-notificationmultilinecontent-t.md) | 多行文本通知。 |
| [NotificationParameters](arkts-notification-notificationmanager-notificationparameters-t.md) | 描述NotificationRequest中wantAgent的部分信息。 |
| [NotificationPictureContent](arkts-notification-notificationmanager-notificationpicturecontent-t.md) | 附有图片的通知。 |
| [NotificationProgress](arkts-notification-notificationmanager-notificationprogress-t.md) | 通知进度。 |
| [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | 通知请求。 |
| [NotificationSlot](arkts-notification-notificationmanager-notificationslot-t.md) | 通知渠道。 |
| [NotificationSystemLiveViewContent](arkts-notification-notificationmanager-notificationsystemliveviewcontent-t.md) | 系统实况窗通知内容。 |
| [NotificationTemplate](arkts-notification-notificationmanager-notificationtemplate-t.md) | 通知模板。 |
| [NotificationTime](arkts-notification-notificationmanager-notificationtime-t.md) | 通知计时信息。 |
| [NotificationUserInput](arkts-notification-notificationmanager-notificationuserinput-t.md) | 保存用户输入的通知消息。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CoordinateSystemType](arkts-notification-notificationmanager-coordinatesystemtype-t-sys.md) | 表示地理围栏坐标系类型的枚举。 |
| [Geofence](arkts-notification-notificationmanager-geofence-t-sys.md) | 地理围栏的配置信息。 |
| [GroupInfo](arkts-notification-notificationmanager-groupinfo-t-sys.md) | 组通知定制信息。 |
| [LiveViewStatus](arkts-notification-notificationmanager-liveviewstatus-t-sys.md) | 描述普通实况通知的状态。 |
| [LiveViewTypes](arkts-notification-notificationmanager-liveviewtypes-t-sys.md) | 描述实况通知的类型。 |
| [MonitorEvent](arkts-notification-notificationmanager-monitorevent-t-sys.md) | 表示地理围栏的监控事件类型的枚举。 |
| [NotificationCheckRequest](arkts-notification-notificationmanager-notificationcheckrequest-t-sys.md) | 描述通知的鉴权信息。 |
| [NotificationFilter](arkts-notification-notificationmanager-notificationfilter-t-sys.md) | 描述查询普通实况窗时的筛选条件。 |
| [NotificationFlagStatus](arkts-notification-notificationmanager-notificationflagstatus-t-sys.md) | 描述通知标志状态。 |
| [NotificationFlags](arkts-notification-notificationmanager-notificationflags-t-sys.md) | 描述通知标志位。 |
| [NotificationIconButton](arkts-notification-notificationmanager-notificationiconbutton-t-sys.md) | 系统通知按钮。 |
| [NotificationLiveViewContent](arkts-notification-notificationmanager-notificationliveviewcontent-t-sys.md) | 描述普通实况通知。 |
| [NotificationSorting](arkts-notification-notificationmanager-notificationsorting-t-sys.md) | 提供有关活动通知的排序信息。 |
| [Trigger](arkts-notification-notificationmanager-trigger-t-sys.md) | 触发条件的具体信息。 |
| [TriggerType](arkts-notification-notificationmanager-triggertype-t-sys.md) | 触发条件的事件类型的枚举。 |
| [UnifiedGroupInfo](arkts-notification-notificationmanager-unifiedgroupinfo-t-sys.md) | 描述通知智能聚合信息字段。 |
<!--DelEnd-->

