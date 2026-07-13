# @ohos.notificationManager

本模块提供通知管理的能力，包括发布、更新、取消通知，创建、获取、移除通知渠道，获取发布通知应用的使能状态，获取通知的相关信息等。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addSlot](arkts-notification-addslot-f.md#addslot-3) | 创建指定类型的通知渠道。使用callback异步回调。 |
| [addSlot](arkts-notification-addslot-f.md#addslot-4) | 创建指定类型的通知渠道。使用Promise异步回调。 |
| [cancel](arkts-notification-cancel-f.md#cancel-1) | 根据指定的通知ID取消已发布的通知。使用callback异步回调。 |
| [cancel](arkts-notification-cancel-f.md#cancel-2) | 根据通知ID和标签取消已发布的通知。使用callback异步回调。 |
| [cancel](arkts-notification-cancel-f.md#cancel-3) | 根据通知ID和标签取消已发布的通知，若标签为空，则取消与指定通知ID匹配的已发布通知。使用Promise异步回调。 |
| [cancelAll](arkts-notification-cancelall-f.md#cancelall-1) | 取消当前应用所有已发布的通知。使用callback异步回调。 |
| [cancelAll](arkts-notification-cancelall-f.md#cancelall-2) | 取消当前应用所有已发布的通知。使用Promise异步回调。 |
| [cancelGroup](arkts-notification-cancelgroup-f.md#cancelgroup-1) | 取消当前应用指定组下的通知。使用callback异步回调。 |
| [cancelGroup](arkts-notification-cancelgroup-f.md#cancelgroup-2) | 取消当前应用指定组下的通知。使用Promise异步回调。 |
| [getActiveNotificationCount](arkts-notification-getactivenotificationcount-f.md#getactivenotificationcount-1) | 获取当前应用未删除的通知数。使用callback异步回调。 |
| [getActiveNotificationCount](arkts-notification-getactivenotificationcount-f.md#getactivenotificationcount-2) | 获取当前应用未删除的通知数。使用Promise异步回调。 |
| [getActiveNotifications](arkts-notification-getactivenotifications-f.md#getactivenotifications-1) | 获取当前应用未删除的通知列表。使用callback异步回调。 |
| [getActiveNotifications](arkts-notification-getactivenotifications-f.md#getactivenotifications-2) | 获取当前应用未删除的通知列表。使用Promise异步回调。 |
| [getBadgeNumber](arkts-notification-getbadgenumber-f.md#getbadgenumber-1) | 获取当前应用角标数量。使用Promise异步回调。 |
| [getNotificationParameters](arkts-notification-getnotificationparameters-f.md#getnotificationparameters-1) | 获取通知[NotificationRequest](arkts-notification-notificationrequest-i.md)中wantAgent字段的部分信息。使用Promise异步回调。 |
| [getNotificationSetting](arkts-notification-getnotificationsetting-f.md#getnotificationsetting-1) | 获取应用程序的通知设置。使用Promise异步回调。 |
| [getSlot](arkts-notification-getslot-f.md#getslot-1) | 获取指定类型的通知渠道。使用callback异步回调。 |
| [getSlot](arkts-notification-getslot-f.md#getslot-2) | 获取指定类型的通知渠道。使用Promise异步回调。 |
| [getSlots](arkts-notification-getslots-f.md#getslots-1) | 获取当前应用的所有通知渠道。使用callback异步回调。 |
| [getSlots](arkts-notification-getslots-f.md#getslots-2) | 获取当前应用的所有通知渠道。使用Promise异步回调。 |
| [isDistributedEnabled](arkts-notification-isdistributedenabled-f.md#isdistributedenabled-1) | 查询设备是否支持跨设备协同通知。使用callback异步回调。 |
| [isDistributedEnabled](arkts-notification-isdistributedenabled-f.md#isdistributedenabled-2) | 查询设备是否支持跨设备协同通知。使用Promise异步回调。 |
| [isGeofenceEnabled](arkts-notification-isgeofenceenabled-f.md#isgeofenceenabled-1) | 检查地理围栏功能是否已启用。使用Promise异步回调。 |
| [isNotificationEnabledSync](arkts-notification-isnotificationenabledsync-f.md#isnotificationenabledsync-1) | 同步查询当前应用通知使能状态。 |
| [isSupportTemplate](arkts-notification-issupporttemplate-f.md#issupporttemplate-1) | 在使用[通知模板](arkts-notification-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。 |
| [isSupportTemplate](arkts-notification-issupporttemplate-f.md#issupporttemplate-2) | 在使用[通知模板](arkts-notification-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用Promise异步回调。 |
| [openNotificationSettings](arkts-notification-opennotificationsettings-f.md#opennotificationsettings-1) | 拉起应用的通知设置界面，该页面以半模态形式呈现，可用于设置通知开关、通知提醒方式等。使用Promise异步回调。 |
| [openNotificationSettingsWithResult](arkts-notification-opennotificationsettingswithresult-f.md#opennotificationsettingswithresult-1) | 拉起应用的通知设置界面，该页面以半模态形式呈现，可用于设置通知开关、通知提醒方式等。使用Promise异步回调, 当半模态窗口关闭时返回用户设置的状态。 |
| [publish](arkts-notification-publish-f.md#publish-1) | 发布通知。使用callback异步回调。如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知。 |
| [publish](arkts-notification-publish-f.md#publish-2) | 发布通知。使用Promise异步回调。如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知。 |
| [removeAllSlots](arkts-notification-removeallslots-f.md#removeallslots-1) | 删除当前应用所有通知渠道。使用callback异步回调。 |
| [removeAllSlots](arkts-notification-removeallslots-f.md#removeallslots-2) | 删除当前应用所有通知渠道。使用Promise异步回调。 |
| [removeSlot](arkts-notification-removeslot-f.md#removeslot-1) | 删除当前应用指定类型的通知渠道。使用callback异步回调。 |
| [removeSlot](arkts-notification-removeslot-f.md#removeslot-2) | 删除当前应用指定类型的通知渠道。使用Promise异步回调。 |
| [requestEnableNotification](arkts-notification-requestenablenotification-f.md#requestenablenotification-1) | 当前应用请求通知使能。使用callback异步回调。@link notificationManager.requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |
| [requestEnableNotification](arkts-notification-requestenablenotification-f.md#requestenablenotification-2) | 应用需要获取用户授权才能发送通知。在通知发布前调用该接口，可以拉起通知授权弹窗，让用户选择是否允许发送通知。使用callback异步回调。@link @ohos.app.ability.UIExtensionContentSession:UIExtensionContentSession.loadContent}成功），方可使用该接口&gt; 。&gt;&gt; - 在使用该接口拉起通知授权弹窗后，如果用户拒绝授权，将无法使用该接口再次拉起弹窗。开发者可以调用&gt; [openNotificationSettingsWithResult](arkts-notification-opennotificationsettingswithresult-f.md#opennotificationsettingswithresult-1)二次申请授权，拉起通知管理弹窗&gt; 。 |
| [requestEnableNotification](arkts-notification-requestenablenotification-f.md#requestenablenotification-3) | 当前应用请求通知使能。使用Promise异步回调。@link notificationManager.requestEnableNotification(context: UIAbilityContext)}替代。 |
| [requestEnableNotification](arkts-notification-requestenablenotification-f.md#requestenablenotification-4) | 应用需要获取用户授权才能发送通知。在通知发布前调用该接口，可以拉起通知授权弹窗，让用户选择是否允许发送通知。使用Promise异步回调。@link @ohos.app.ability.UIExtensionContentSession:UIExtensionContentSession.loadContent}成功），方可使用该接口&gt; 。&gt;&gt; - 在使用该接口拉起通知授权弹窗后，如果用户拒绝授权，将无法使用该接口再次拉起弹窗。开发者可以调用&gt; [openNotificationSettingsWithResult](arkts-notification-opennotificationsettingswithresult-f.md#opennotificationsettingswithresult-1)二次申请授权，拉起通知管理弹窗&gt; 。 |
| [setBadgeNumber](arkts-notification-setbadgenumber-f.md#setbadgenumber-1) | 设定角标个数，在应用的桌面图标上呈现。使用callback异步回调。 |
| [setBadgeNumber](arkts-notification-setbadgenumber-f.md#setbadgenumber-2) | 设定角标个数，在应用的桌面图标上呈现。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addDoNotDisturbProfile](arkts-notification-adddonotdisturbprofile-f-sys.md#adddonotdisturbprofile-1) | 添加勿扰模式配置信息。使用Promise异步回调。 |
| [addDoNotDisturbProfile](arkts-notification-adddonotdisturbprofile-f-sys.md#adddonotdisturbprofile-2) | 向指定用户添加勿扰模式配置信息。使用Promise异步回调。 |
| [addSlot](arkts-notification-addslot-f-sys.md#addslot-1) | 创建通知渠道。使用callback异步回调。 |
| [addSlot](arkts-notification-addslot-f-sys.md#addslot-2) | 创建通知渠道。使用Promise异步回调。 |
| [addSlots](arkts-notification-addslots-f-sys.md#addslots-1) | 创建多个通知渠道。使用callback异步回调。 |
| [addSlots](arkts-notification-addslots-f-sys.md#addslots-2) | 创建多个通知渠道。使用Promise异步回调。 |
| [cancel](arkts-notification-cancel-f-sys.md#cancel-4) | 代理取消当前用户其他应用的通知。使用Promise异步回调。需要当前应用与其他应用存在代理关系，或者当前应用有ohos.permission.NOTIFICATION_AGENT_CONTROLLER权限。 |
| [cancelAsBundle](arkts-notification-cancelasbundle-f-sys.md#cancelasbundle-1) | 取消代理通知。使用callback异步回调。 |
| [cancelAsBundle](arkts-notification-cancelasbundle-f-sys.md#cancelasbundle-2) | 取消代理通知。使用Promise异步回调。 |
| [cancelAsBundle](arkts-notification-cancelasbundle-f-sys.md#cancelasbundle-3) | 取消代理通知。使用Promise异步回调。 |
| [disableNotificationFeature](arkts-notification-disablenotificationfeature-f-sys.md#disablenotificationfeature-1) | 将应用包名添加到通知发布权限管控名单，以阻止应用发布通知。支持启用或关闭该功能。 |
| [disableNotificationFeature](arkts-notification-disablenotificationfeature-f-sys.md#disablenotificationfeature-2) | 将应用包名添加到通知发布权限管控名单，以阻止应用发布通知。使用Promise异步回调。 |
| [displayBadge](arkts-notification-displaybadge-f-sys.md#displaybadge-1) | 设定指定应用的角标使能状态。使用callback异步回调。 |
| [displayBadge](arkts-notification-displaybadge-f-sys.md#displaybadge-2) | 设定指定应用的角标使能状态。使用Promise异步回调。 |
| [getActiveNotificationByFilter](arkts-notification-getactivenotificationbyfilter-f-sys.md#getactivenotificationbyfilter-1) | 获取满足条件的普通实况通知信息。使用callback异步回调。 |
| [getActiveNotificationByFilter](arkts-notification-getactivenotificationbyfilter-f-sys.md#getactivenotificationbyfilter-2) | 获取满足条件的普通实况通知信息。使用Promise异步回调。 |
| [getAllActiveNotifications](arkts-notification-getallactivenotifications-f-sys.md#getallactivenotifications-1) | 获取当前未删除的所有通知。使用callback异步回调。 |
| [getAllActiveNotifications](arkts-notification-getallactivenotifications-f-sys.md#getallactivenotifications-2) | 获取当前未删除的所有通知。使用Promise异步回调。 |
| [getAllNotificationEnabledBundles](arkts-notification-getallnotificationenabledbundles-f-sys.md#getallnotificationenabledbundles-1) | 获取允许通知的应用程序列表。使用Promise异步回调。 |
| [getAllNotificationEnabledBundles](arkts-notification-getallnotificationenabledbundles-f-sys.md#getallnotificationenabledbundles-2) | 获取指定用户下允许通知的应用程序列表。使用Promise异步回调。 |
| [getBadgeDisplayStatusByBundles](arkts-notification-getbadgedisplaystatusbybundles-f-sys.md#getbadgedisplaystatusbybundles-1) | 批量获取应用角标显示状态。使用Promise异步回调。 |
| [getBundlePriorityConfig](arkts-notification-getbundlepriorityconfig-f-sys.md#getbundlepriorityconfig-1) | 获取应用的优先功能配置。 |
| [getDeviceRemindType](arkts-notification-getdeviceremindtype-f-sys.md#getdeviceremindtype-1) | 获取通知的提醒方式。使用callback异步回调。 |
| [getDeviceRemindType](arkts-notification-getdeviceremindtype-f-sys.md#getdeviceremindtype-2) | 获取通知的提醒方式。使用Promise异步回调。 |
| [getDistributedDeviceList](arkts-notification-getdistributeddevicelist-f-sys.md#getdistributeddevicelist-1) | 查询支持跨设备协同通知的设备类型。使用Promise异步回调。 |
| [getDoNotDisturbDate](arkts-notification-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-1) | 查询免打扰时间。使用callback异步回调。 |
| [getDoNotDisturbDate](arkts-notification-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-2) | 查询免打扰时间。使用Promise异步回调。 |
| [getDoNotDisturbDate](arkts-notification-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-3) | 查询指定用户的免打扰时间。使用callback异步回调。 |
| [getDoNotDisturbDate](arkts-notification-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-4) | 查询指定用户的免打扰时间。使用Promise异步回调。 |
| [getDoNotDisturbProfile](arkts-notification-getdonotdisturbprofile-f-sys.md#getdonotdisturbprofile-1) | 查询勿扰模式配置信息。使用Promise异步回调。 |
| [getDoNotDisturbProfile](arkts-notification-getdonotdisturbprofile-f-sys.md#getdonotdisturbprofile-2) | 查询指定用户的勿扰模式配置信息。使用Promise异步回调。 |
| [getNotificationStatisticsByBundle](arkts-notification-getnotificationstatisticsbybundle-f-sys.md#getnotificationstatisticsbybundle-1) | 批量获取指定应用列表的通知统计信息，使用Promise异步回调。 |
| [getNotificationSwitch](arkts-notification-getnotificationswitch-f-sys.md#getnotificationswitch-1) | 获取通知开关状态。使用Promise异步回调。 |
| [getPriorityEnabledByBundles](arkts-notification-getpriorityenabledbybundles-f-sys.md#getpriorityenabledbybundles-1) | 批量获取应用通知优先级开关状态。使用Promise异步回调。 |
| [getPriorityStrategyByBundles](arkts-notification-getprioritystrategybybundles-f-sys.md#getprioritystrategybybundles-1) | 批量获取应用通知优先策略。使用Promise异步回调。 |
| [getReminderInfoByBundles](arkts-notification-getreminderinfobybundles-f-sys.md#getreminderinfobybundles-1) | 批量获取指定应用提醒信息。使用Promise异步回调。 |
| [getRingtoneInfoByBundle](arkts-notification-getringtoneinfobybundle-f-sys.md#getringtoneinfobybundle-1) | 获取应用自定义铃声信息。使用Promise异步回调。 |
| [getSlotByBundle](arkts-notification-getslotbybundle-f-sys.md#getslotbybundle-1) | 获取指定应用指定类型的通知渠道。使用Promise异步回调。获取前需要先通过[addSlot](arkts-notification-addslot-f-sys.md#addslot-1)创建通知渠道。 |
| [getSlotFlagsByBundle](arkts-notification-getslotflagsbybundle-f-sys.md#getslotflagsbybundle-1) | 获取指定应用的通知渠道标识位。使用Promise异步回调。 |
| [getSlotNumByBundle](arkts-notification-getslotnumbybundle-f-sys.md#getslotnumbybundle-1) | 获取指定应用的通知渠道数量。使用callback异步回调。 |
| [getSlotNumByBundle](arkts-notification-getslotnumbybundle-f-sys.md#getslotnumbybundle-2) | 获取指定应用的通知渠道数量。使用Promise异步回调。 |
| [getSlotsByBundle](arkts-notification-getslotsbybundle-f-sys.md#getslotsbybundle-1) | 获取指定应用的所有通知渠道。使用callback异步回调。 |
| [getSlotsByBundle](arkts-notification-getslotsbybundle-f-sys.md#getslotsbybundle-2) | 获取指定应用的所有通知渠道。使用Promise异步回调。 |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-getsyncnotificationenabledwithoutapp-f-sys.md#getsyncnotificationenabledwithoutapp-1) | 获取同步通知到未安装应用程序设备的开关是否开启(callback形式)。 |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-getsyncnotificationenabledwithoutapp-f-sys.md#getsyncnotificationenabledwithoutapp-2) | 获取同步通知到未安装应用程序设备的开关是否开启(Promise形式)。 |
| [isBadgeDisplayed](arkts-notification-isbadgedisplayed-f-sys.md#isbadgedisplayed-1) | 获取指定应用的角标使能状态。使用callback异步回调。 |
| [isBadgeDisplayed](arkts-notification-isbadgedisplayed-f-sys.md#isbadgedisplayed-2) | 获取指定应用的角标使能状态。使用Promise异步回调。 |
| [isDistributedEnabled](arkts-notification-isdistributedenabled-f-sys.md#isdistributedenabled-3) | 查询设备是否支持跨设备协同通知。使用Promise异步回调。 |
| [isDistributedEnabledByBundle](arkts-notification-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-1) | 根据应用的包获取应用程序是否支持分布式通知。使用callback异步回调。 |
| [isDistributedEnabledByBundle](arkts-notification-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-2) | 查询指定应用是否支持分布式通知。使用Promise异步回调。 |
| [isDistributedEnabledByBundle](arkts-notification-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-3) | 获取指定应用是否支持跨设备协同。使用Promise异步回调。 |
| [isDistributedEnabledBySlot](arkts-notification-isdistributedenabledbyslot-f-sys.md#isdistributedenabledbyslot-1) | 查询指定渠道的通知是否支持通知跨设备协同至指定类型设备。使用Promise异步回调。 |
| [isNotificationEnabled](arkts-notification-isnotificationenabled-f-sys.md#isnotificationenabled-1) | 获取指定应用的通知使能状态。使用callback异步回调。 |
| [isNotificationEnabled](arkts-notification-isnotificationenabled-f-sys.md#isnotificationenabled-2) | 获取指定应用的通知使能状态。使用Promise异步回调。 |
| [isNotificationEnabled](arkts-notification-isnotificationenabled-f-sys.md#isnotificationenabled-3) | 查询当前应用通知使能状态。使用callback异步回调。 |
| [isNotificationEnabled](arkts-notification-isnotificationenabled-f-sys.md#isnotificationenabled-4) | 查询当前应用通知使能状态。使用Promise异步回调。 |
| [isNotificationEnabled](arkts-notification-isnotificationenabled-f-sys.md#isnotificationenabled-5) | 获取指定用户ID下的通知使能状态。使用callback异步回调。 |
| [isNotificationEnabled](arkts-notification-isnotificationenabled-f-sys.md#isnotificationenabled-6) | 获取指定用户下的通知使能状态。使用Promise异步回调。 |
| [isNotificationSlotEnabled](arkts-notification-isnotificationslotenabled-f-sys.md#isnotificationslotenabled-1) | 获取指定应用的指定渠道类型的使能状态。使用callback异步回调。 |
| [isNotificationSlotEnabled](arkts-notification-isnotificationslotenabled-f-sys.md#isnotificationslotenabled-2) | 获取指定应用的指定渠道类型的使能状态。使用Promise异步回调。 |
| [isNotificationSlotEnabledByBundles](arkts-notification-isnotificationslotenabledbybundles-f-sys.md#isnotificationslotenabledbybundles-1) | 批量获取多个应用的指定渠道类型的使能状态。使用Promise异步回调。 |
| [isPriorityEnabled](arkts-notification-ispriorityenabled-f-sys.md#ispriorityenabled-1) | 获取通知优先级总开关状态。 |
| [isPriorityEnabledByBundle](arkts-notification-ispriorityenabledbybundle-f-sys.md#ispriorityenabledbybundle-1) | 获取应用通知优先级开关状态。 |
| [isPriorityIntelligentEnabled](arkts-notification-ispriorityintelligentenabled-f-sys.md#ispriorityintelligentenabled-1) | 获取优先通知智能服务使能状态。使用Promise异步回调。 |
| [isSilentReminderEnabled](arkts-notification-issilentreminderenabled-f-sys.md#issilentreminderenabled-1) | 查询静默提醒的开关状态。使用Promise进行异步回调。 |
| [isSmartReminderEnabled](arkts-notification-issmartreminderenabled-f-sys.md#issmartreminderenabled-1) | 获取设备是否与其他设备协同智能提醒。使用Promise异步回调。 |
| [isSupportDoNotDisturbMode](arkts-notification-issupportdonotdisturbmode-f-sys.md#issupportdonotdisturbmode-1) | 查询是否支持免打扰功能。使用callback异步回调。 |
| [isSupportDoNotDisturbMode](arkts-notification-issupportdonotdisturbmode-f-sys.md#issupportdonotdisturbmode-2) | 查询是否支持免打扰功能。使用Promise异步回调。 |
| [off](arkts-notification-off-f-sys.md#off-1) | 取消通知监听回调。 |
| [offBadgeNumberQuery](arkts-notification-offbadgenumberquery-f-sys.md#offbadgenumberquery-1) | 取消应用角标数量查询回调。 |
| [on](arkts-notification-on-f-sys.md#on-1) | 注册通知监听回调。通知服务将通知信息回调给校验程序，校验程序返回校验结果决定该通知是否发布，如营销类通知发布频率控制等。系统中每个[SlotType](arkts-notification-slottype-e.md)只允许存在一个注册者。 |
| [on](arkts-notification-on-f-sys.md#on-2) | 注册通知监听回调。通知服务将通知信息回调给校验程序，校验程序返回校验结果决定该通知是否发布，如营销类通知发布频率控制等。使用Promise异步回调。系统中每个[SlotType](arkts-notification-slottype-e.md)只允许存在一个注册者。 |
| [onBadgeNumberQuery](arkts-notification-onbadgenumberquery-f-sys.md#onbadgenumberquery-1) | 注册应用角标数量查询回调。 |
| [publish](arkts-notification-publish-f-sys.md#publish-3) | 发布通知给指定的用户。使用callback异步回调。 |
| [publish](arkts-notification-publish-f-sys.md#publish-4) | 发布通知给指定的用户。使用Promise异步回调。 |
| [publishAsBundle](arkts-notification-publishasbundle-f-sys.md#publishasbundle-1) | 发布代理通知。使用callback异步回调。 |
| [publishAsBundle](arkts-notification-publishasbundle-f-sys.md#publishasbundle-2) | 发布代理通知。使用Promise异步回调。 |
| [publishAsBundle](arkts-notification-publishasbundle-f-sys.md#publishasbundle-3) | 发布代理通知。使用Promise异步回调。 |
| [removeDoNotDisturbProfile](arkts-notification-removedonotdisturbprofile-f-sys.md#removedonotdisturbprofile-1) | 删除勿扰模式配置。使用Promise异步回调。 |
| [removeDoNotDisturbProfile](arkts-notification-removedonotdisturbprofile-f-sys.md#removedonotdisturbprofile-2) | 删除指定用户的勿扰模式配置。使用Promise异步回调。 |
| [removeGroupByBundle](arkts-notification-removegroupbybundle-f-sys.md#removegroupbybundle-1) | 删除指定应用的指定组下的通知。使用callback异步回调。 |
| [removeGroupByBundle](arkts-notification-removegroupbybundle-f-sys.md#removegroupbybundle-2) | 删除指定应用的指定组下的通知。使用Promise异步回调。 |
| [setAdditionalConfig](arkts-notification-setadditionalconfig-f-sys.md#setadditionalconfig-1) | 设置通知的系统附加配置信息。使用Promise异步回调。 |
| [setBadgeDisplayStatusByBundles](arkts-notification-setbadgedisplaystatusbybundles-f-sys.md#setbadgedisplaystatusbybundles-1) | 批量设置指定应用是否显示角标。使用Promise异步回调。 |
| [setBadgeNumberByBundle](arkts-notification-setbadgenumberbybundle-f-sys.md#setbadgenumberbybundle-1) | 代理其他应用设定角标个数。使用Promise异步回调。 |
| [setBundlePriorityConfig](arkts-notification-setbundlepriorityconfig-f-sys.md#setbundlepriorityconfig-1) | 设置应用的优先功能配置。 |
| [setDistributedEnable](arkts-notification-setdistributedenable-f-sys.md#setdistributedenable-1) | 设置设备是否支持分布式通知。使用callback异步回调。 |
| [setDistributedEnable](arkts-notification-setdistributedenable-f-sys.md#setdistributedenable-2) | 设置设备是否支持分布式通知。使用Promise异步回调。 |
| [setDistributedEnableByBundle](arkts-notification-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle-1) | 设置指定应用是否支持分布式通知。使用callback异步回调。 |
| [setDistributedEnableByBundle](arkts-notification-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle-2) | 设置指定应用是否支持分布式通知。使用Promise异步回调。 |
| [setDistributedEnableByBundles](arkts-notification-setdistributedenablebybundles-f-sys.md#setdistributedenablebybundles-1) | 批量设置应用是否支持跨设备协同。使用Promise异步回调。 |
| [setDistributedEnabled](arkts-notification-setdistributedenabled-f-sys.md#setdistributedenabled-1) | 设置设备是否支持跨设备协同通知。使用Promise异步回调。 |
| [setDistributedEnabledByBundle](arkts-notification-setdistributedenabledbybundle-f-sys.md#setdistributedenabledbybundle-1) | 设置指定应用是否支持跨设备协同。使用Promise异步回调。 |
| [setDistributedEnabledBySlot](arkts-notification-setdistributedenabledbyslot-f-sys.md#setdistributedenabledbyslot-1) | 设置指定渠道的通知是否支持通知跨设备协同至指定类型设备。使用Promise异步回调。 |
| [setDoNotDisturbDate](arkts-notification-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-1) | 设置免打扰时间。使用callback异步回调。 |
| [setDoNotDisturbDate](arkts-notification-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-2) | 设置免打扰时间。使用Promise异步回调。 |
| [setDoNotDisturbDate](arkts-notification-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-3) | 指定用户设置免打扰时间。使用callback异步回调。 |
| [setDoNotDisturbDate](arkts-notification-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-4) | 指定用户设置免打扰时间。使用Promise异步回调。 |
| [setGeofenceEnabled](arkts-notification-setgeofenceenabled-f-sys.md#setgeofenceenabled-1) | 设置地理围栏的启用状态。使用Promise异步回调。 |
| [setNotificationEnable](arkts-notification-setnotificationenable-f-sys.md#setnotificationenable-1) | 设定指定应用的通知使能状态。使用callback异步回调。 |
| [setNotificationEnable](arkts-notification-setnotificationenable-f-sys.md#setnotificationenable-2) | 设定指定应用的通知使能状态。使用Promise异步回调。 |
| [setNotificationEnableSlot](arkts-notification-setnotificationenableslot-f-sys.md#setnotificationenableslot-1) | 设置指定应用的指定渠道类型的使能状态。使用callback异步回调。 |
| [setNotificationEnableSlot](arkts-notification-setnotificationenableslot-f-sys.md#setnotificationenableslot-2) | 设置指定应用的指定渠道类型的使能状态。使用callback异步回调。 |
| [setNotificationEnableSlot](arkts-notification-setnotificationenableslot-f-sys.md#setnotificationenableslot-3) | 设置指定应用的指定渠道类型的使能状态。使用promise异步回调。 |
| [setNotificationSwitch](arkts-notification-setnotificationswitch-f-sys.md#setnotificationswitch-1) | 设置通知开关状态。使用Promise异步回调。 |
| [setPriorityEnabled](arkts-notification-setpriorityenabled-f-sys.md#setpriorityenabled-1) | 设置通知优先级总开关。 |
| [setPriorityEnabledByBundle](arkts-notification-setpriorityenabledbybundle-f-sys.md#setpriorityenabledbybundle-1) | 设置应用通知优先级开关。 |
| [setPriorityEnabledByBundles](arkts-notification-setpriorityenabledbybundles-f-sys.md#setpriorityenabledbybundles-1) | 批量设置应用通知优先级开关状态。使用Promise异步回调。 |
| [setPriorityIntelligentEnabled](arkts-notification-setpriorityintelligentenabled-f-sys.md#setpriorityintelligentenabled-1) | 设置优先通知智能服务使能状态。使用Promise异步回调。 |
| [setPriorityStrategyByBundles](arkts-notification-setprioritystrategybybundles-f-sys.md#setprioritystrategybybundles-1) | 批量设置应用通知优先策略。使用Promise异步回调。 |
| [setReminderInfoByBundles](arkts-notification-setreminderinfobybundles-f-sys.md#setreminderinfobybundles-1) | 批量设置指定应用提醒信息。使用Promise异步回调。 |
| [setRingtoneInfoByBundle](arkts-notification-setringtoneinfobybundle-f-sys.md#setringtoneinfobybundle-1) | 设置应用自定义铃声信息。使用Promise异步回调。 |
| [setSilentReminderEnabled](arkts-notification-setsilentreminderenabled-f-sys.md#setsilentreminderenabled-1) | 设置静默提醒的开关状态。使用Promise进行异步回调。 |
| [setSlotByBundle](arkts-notification-setslotbybundle-f-sys.md#setslotbybundle-1) | 设置指定应用的通知渠道。使用callback异步回调。设置前需要先通过[addSlot](arkts-notification-addslot-f-sys.md#addslot-1)创建通知渠道。 |
| [setSlotByBundle](arkts-notification-setslotbybundle-f-sys.md#setslotbybundle-2) | 设置指定应用的通知渠道。使用Promise异步回调。设置前需要先通过[addSlot](arkts-notification-addslot-f-sys.md#addslot-1)创建通知渠道。 |
| [setSlotFlagsByBundle](arkts-notification-setslotflagsbybundle-f-sys.md#setslotflagsbybundle-1) | 设定指定应用的通知提醒方式开关。使用Promise异步回调。 |
| [setSmartReminderEnabled](arkts-notification-setsmartreminderenabled-f-sys.md#setsmartreminderenabled-1) | 设置设备是否与其他设备协同智能提醒。使用Promise异步回调。 |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-setsyncnotificationenabledwithoutapp-f-sys.md#setsyncnotificationenabledwithoutapp-1) | 设置是否将通知同步到未安装应用程序的设备(callback形式)。 |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-setsyncnotificationenabledwithoutapp-f-sys.md#setsyncnotificationenabledwithoutapp-2) | 设置是否将通知同步到未安装应用程序的设备(Promise形式)。 |
| [setTargetDeviceStatus](arkts-notification-settargetdevicestatus-f-sys.md#settargetdevicestatus-1) | 设置设备配对成功后的状态。当发布通知时，会根据各个设备的状态来确定当前设备的通知提醒方式。 |
| [snoozeNotification](arkts-notification-snoozenotification-f-sys.md#snoozenotification-1) | 设置通知稍后提醒。该通知在指定时间后再次提醒，每次设置只会提醒一次，提醒方式与该通知相同。设置后该通知被删除。 |
| [subscribeSystemLiveView](arkts-notification-subscribesystemliveview-f-sys.md#subscribesystemliveview-1) | 订阅系统实况窗。使用Promise异步回调。 |
| [triggerSystemLiveView](arkts-notification-triggersystemliveview-f-sys.md#triggersystemliveview-1) | 触发系统实况窗。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [NotificationSetting](arkts-notification-notificationsetting-i.md) | 通知提醒方式开关的设置状态。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundleNotificationStatistics](arkts-notification-bundlenotificationstatistics-i-sys.md) | 描述指定应用通知统计信息。 |
| [ButtonOptions](arkts-notification-buttonoptions-i-sys.md) | 描述触发按钮信息。 |
| [DistributedBundleEnableInfo](arkts-notification-distributedbundleenableinfo-i-sys.md) | 描述多设备协同的包信息。 |
| [DoNotDisturbDate](arkts-notification-donotdisturbdate-i-sys.md) | 免打扰时间选项。 |
| [DoNotDisturbProfile](arkts-notification-donotdisturbprofile-i-sys.md) | 勿扰模式的配置信息。 |
| [NotificationCheckInfo](arkts-notification-notificationcheckinfo-i-sys.md) | 通知校验参数。 |
| [NotificationCheckResult](arkts-notification-notificationcheckresult-i-sys.md) | 通知校验结果。 |
| [NotificationReminderInfo](arkts-notification-notificationreminderinfo-i-sys.md) | 描述指定应用提醒方式信息。 |
| [RingtoneInfo](arkts-notification-ringtoneinfo-i-sys.md) | 描述自定义铃声信息。 |
| [SystemLiveViewSubscriber](arkts-notification-systemliveviewsubscriber-i-sys.md) | 系统实况窗订阅者。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContentType](arkts-notification-contenttype-e.md) | 通知内容类型。 |
| [PriorityNotificationType](arkts-notification-prioritynotificationtype-e.md) | 描述通知的优先级类型。 |
| [SlotLevel](arkts-notification-slotlevel-e.md) | 通知级别。 |
| [SlotType](arkts-notification-slottype-e.md) | 通知渠道类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceRemindType](arkts-notification-deviceremindtype-e-sys.md) | 通知提醒方式。 |
| [DoNotDisturbType](arkts-notification-donotdisturbtype-e-sys.md) | 免打扰设置的时间类型。 |
| [NotificationControlFlagStatus](arkts-notification-notificationcontrolflagstatus-e-sys.md) | 每个bit位都可以控制通知的提示方式。当notificationControlFlags和下表中枚举值进行按位或操作，则表示关闭其提示方式。 |
| [PriorityEnableStatus](arkts-notification-priorityenablestatus-e-sys.md) | 描述应用通知的优先级开关状态。 |
| [PriorityNotificationType](arkts-notification-prioritynotificationtype-e-sys.md) | 描述通知的优先级类型。 |
| [PriorityStrategyStatus](arkts-notification-prioritystrategystatus-e-sys.md) | 描述应用通知的优先策略。 |
| [RingtoneType](arkts-notification-ringtonetype-e-sys.md) | 描述自定义铃声类型。 |
| [SlotType](arkts-notification-slottype-e-sys.md) | 通知渠道类型。 |
| [SourceType](arkts-notification-sourcetype-e-sys.md) | 通知来源类型。 |
| [SwitchState](arkts-notification-switchstate-e-sys.md) | 描述通知相关开关的设置状态。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BundleOption](arkts-notification-bundleoption-t.md) | 指定应用的包信息。 |
| [DistributedOptions](arkts-notification-distributedoptions-t.md) | 分布式选项。 |
| [NotificationActionButton](arkts-notification-notificationactionbutton-t.md) | 通知中显示的操作按钮。 |
| [NotificationBasicContent](arkts-notification-notificationbasiccontent-t.md) | 普通文本通知。 |
| [NotificationButton](arkts-notification-notificationbutton-t.md) | 通知按钮。 |
| [NotificationCapsule](arkts-notification-notificationcapsule-t.md) | 通知胶囊。 |
| [NotificationContent](arkts-notification-notificationcontent-t.md) | 通知内容。 |
| [NotificationLongTextContent](arkts-notification-notificationlongtextcontent-t.md) | 长文本通知。 |
| [NotificationMultiLineContent](arkts-notification-notificationmultilinecontent-t.md) | 多行文本通知。 |
| [NotificationParameters](arkts-notification-notificationparameters-t.md) | 描述NotificationRequest中wantAgent的部分信息。 |
| [NotificationPictureContent](arkts-notification-notificationpicturecontent-t.md) | 附有图片的通知。 |
| [NotificationProgress](arkts-notification-notificationprogress-t.md) | 通知进度。 |
| [NotificationRequest](arkts-notification-notificationrequest-t.md) | 通知请求。 |
| [NotificationSlot](arkts-notification-notificationslot-t.md) | 通知渠道。 |
| [NotificationSystemLiveViewContent](arkts-notification-notificationsystemliveviewcontent-t.md) | 系统实况窗通知内容。 |
| [NotificationTemplate](arkts-notification-notificationtemplate-t.md) | 通知模板。 |
| [NotificationTime](arkts-notification-notificationtime-t.md) | 通知计时信息。 |
| [NotificationUserInput](arkts-notification-notificationuserinput-t.md) | 保存用户输入的通知消息。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CoordinateSystemType](arkts-notification-coordinatesystemtype-t-sys.md) | 表示地理围栏坐标系类型的枚举。 |
| [Geofence](arkts-notification-geofence-t-sys.md) | 地理围栏的配置信息。 |
| [GroupInfo](arkts-notification-groupinfo-t-sys.md) | 组通知定制信息。 |
| [LiveViewStatus](arkts-notification-liveviewstatus-t-sys.md) | 描述普通实况通知的状态。 |
| [LiveViewTypes](arkts-notification-liveviewtypes-t-sys.md) | 描述实况通知的类型。 |
| [MonitorEvent](arkts-notification-monitorevent-t-sys.md) | 表示地理围栏的监控事件类型的枚举。 |
| [NotificationCheckRequest](arkts-notification-notificationcheckrequest-t-sys.md) | 描述通知的鉴权信息。 |
| [NotificationFilter](arkts-notification-notificationfilter-t-sys.md) | 描述查询普通实况窗时的筛选条件。 |
| [NotificationFlagStatus](arkts-notification-notificationflagstatus-t-sys.md) | 描述通知标志状态。 |
| [NotificationFlags](arkts-notification-notificationflags-t-sys.md) | 描述通知标志位。 |
| [NotificationIconButton](arkts-notification-notificationiconbutton-t-sys.md) | 系统通知按钮。 |
| [NotificationLiveViewContent](arkts-notification-notificationliveviewcontent-t-sys.md) | 描述普通实况通知。 |
| [NotificationSorting](arkts-notification-notificationsorting-t-sys.md) | 提供有关活动通知的排序信息。 |
| [Trigger](arkts-notification-trigger-t-sys.md) | 触发条件的具体信息。 |
| [TriggerType](arkts-notification-triggertype-t-sys.md) | 触发条件的事件类型的枚举。 |
| [UnifiedGroupInfo](arkts-notification-unifiedgroupinfo-t-sys.md) | 描述通知智能聚合信息字段。 |
<!--DelEnd-->

