# @ohos.notification

本模块提供通知管理的能力，包括发布、取消发布通知，创建、获取、移除通知通道，订阅、取消订阅通知，获取通知的使能状态、角标使能状态，获取通知的相关信息等。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** notificationSubscribe/notificationSubscribe

<!--Device-unnamed-declare namespace notification--><!--Device-unnamed-declare namespace notification-End-->

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addSlot](arkts-notification-notification-addslot-depr-f.md#addslot3) | 创建指定类型的通知通道（callback形式）。 |
| [addSlot](arkts-notification-notification-addslot-depr-f.md#addslot4) | 创建指定类型的通知通道（Promise形式）。 |
| [cancel](arkts-notification-notification-cancel-depr-f.md#cancel1) | 取消与指定通知ID相匹配的已发布通知（callback形式）。 |
| [cancel](arkts-notification-notification-cancel-depr-f.md#cancel2) | 通过通知ID和通知标签取消已发布的通知（callback形式）。 |
| [cancel](arkts-notification-notification-cancel-depr-f.md#cancel3) | 取消与指定通知ID相匹配的已发布通知，label可以指定也可以不指定（Promise形式）。 |
| [cancelAll](arkts-notification-notification-cancelall-depr-f.md#cancelall1) | 取消所有已发布的通知（callback形式）。 |
| [cancelAll](arkts-notification-notification-cancelall-depr-f.md#cancelall2) | 取消所有已发布的通知（Promise形式）。 |
| [cancelGroup](arkts-notification-notification-cancelgroup-depr-f.md#cancelgroup1) | 取消本应用指定组下的通知（Callback形式）。 |
| [cancelGroup](arkts-notification-notification-cancelgroup-depr-f.md#cancelgroup2) | 取消本应用指定组下的通知（Promise形式）。 |
| [getActiveNotificationCount](arkts-notification-notification-getactivenotificationcount-depr-f.md#getactivenotificationcount1) | 获取当前应用未删除的通知数（Callback形式）。 |
| [getActiveNotificationCount](arkts-notification-notification-getactivenotificationcount-depr-f.md#getactivenotificationcount2) | 获取当前应用未删除的通知数（Promise形式）。 |
| [getActiveNotifications](arkts-notification-notification-getactivenotifications-depr-f.md#getactivenotifications1) | 获取当前应用未删除的通知列表（Callback形式）。 |
| [getActiveNotifications](arkts-notification-notification-getactivenotifications-depr-f.md#getactivenotifications2) | 获取当前应用未删除的通知列表（Promise形式）。 |
| [getSlot](arkts-notification-notification-getslot-depr-f.md#getslot1) | 获取一个指定类型的通知通道（callback形式）。 |
| [getSlot](arkts-notification-notification-getslot-depr-f.md#getslot2) | 获取一个指定类型的通知通道（Promise形式）。 |
| [getSlots](arkts-notification-notification-getslots-depr-f.md#getslots1) | 获取此应用程序的所有通知通道（callback形式）。 |
| [getSlots](arkts-notification-notification-getslots-depr-f.md#getslots2) | 获取此应用程序的所有通知通道（Promise形式）。 |
| [isDistributedEnabled](arkts-notification-notification-isdistributedenabled-depr-f.md#isdistributedenabled1) | 查询设备是否支持分布式通知（Callback形式）。 |
| [isDistributedEnabled](arkts-notification-notification-isdistributedenabled-depr-f.md#isdistributedenabled2) | 查询设备是否支持分布式通知（Promise形式）。 |
| [isSupportTemplate](arkts-notification-notification-issupporttemplate-depr-f.md#issupporttemplate1) | 在使用[通知模板](arkts-notification-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。 |
| [isSupportTemplate](arkts-notification-notification-issupporttemplate-depr-f.md#issupporttemplate2) | 在使用[通知模板](arkts-notification-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用Promise异步回调。 |
| [publish](arkts-notification-notification-publish-depr-f.md#publish1) | 发布通知（callback形式）。 |
| [publish](arkts-notification-notification-publish-depr-f.md#publish2) | 发布通知（Promise形式）。 |
| [removeAllSlots](arkts-notification-notification-removeallslots-depr-f.md#removeallslots1) | 删除所有通知通道（callback形式）。 |
| [removeAllSlots](arkts-notification-notification-removeallslots-depr-f.md#removeallslots2) | 删除所有通知通道（Promise形式）。 |
| [removeSlot](arkts-notification-notification-removeslot-depr-f.md#removeslot1) | 删除指定类型的通知通道（callback形式）。 |
| [removeSlot](arkts-notification-notification-removeslot-depr-f.md#removeslot2) | 删除指定类型的通知通道（Promise形式）。 |
| [requestEnableNotification](arkts-notification-notification-requestenablenotification-depr-f.md#requestenablenotification1) | 应用请求通知使能（Callback形式）。 |
| [requestEnableNotification](arkts-notification-notification-requestenablenotification-depr-f.md#requestenablenotification2) | 应用请求通知使能（Promise形式）。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addSlot](arkts-notification-notification-addslot-depr-f-sys.md#addslot1) | 创建通知渠道。使用callback异步回调。 |
| [addSlot](arkts-notification-notification-addslot-depr-f-sys.md#addslot2) | 创建通知渠道。使用Promise异步回调。 |
| [addSlots](arkts-notification-notification-addslots-depr-f-sys.md#addslots1) | 创建多个通知通道（callback形式）。 |
| [addSlots](arkts-notification-notification-addslots-depr-f-sys.md#addslots2) | 创建多个通知通道（Promise形式）。 |
| [displayBadge](arkts-notification-notification-displaybadge-depr-f-sys.md#displaybadge1) | 设定指定应用的角标使能状态（Callback形式）。 |
| [displayBadge](arkts-notification-notification-displaybadge-depr-f-sys.md#displaybadge2) | 设定指定应用的角标使能状态（Promise形式）。 |
| [enableDistributed](arkts-notification-notification-enabledistributed-depr-f-sys.md#enabledistributed1) | 设置设备是否支持分布式通知（Callback形式）。 |
| [enableDistributed](arkts-notification-notification-enabledistributed-depr-f-sys.md#enabledistributed2) | 设置设备是否支持分布式通知（Promise形式）。 |
| [enableDistributedByBundle](arkts-notification-notification-enabledistributedbybundle-depr-f-sys.md#enabledistributedbybundle1) | 设置指定应用是否支持分布式通知（Callback形式）。 |
| [enableDistributedByBundle](arkts-notification-notification-enabledistributedbybundle-depr-f-sys.md#enabledistributedbybundle2) | 设置指定应用是否支持分布式通知（Promise形式）。 |
| [enableNotification](arkts-notification-notification-enablenotification-depr-f-sys.md#enablenotification1) | 设定指定应用的通知使能状态（Callback形式）。 |
| [enableNotification](arkts-notification-notification-enablenotification-depr-f-sys.md#enablenotification2) | 设定指定应用的通知使能状态（Promise形式）。 |
| [getAllActiveNotifications](arkts-notification-notification-getallactivenotifications-depr-f-sys.md#getallactivenotifications1) | 获取当前未删除的所有通知（Callback形式）。 |
| [getAllActiveNotifications](arkts-notification-notification-getallactivenotifications-depr-f-sys.md#getallactivenotifications2) | 获取当前未删除的所有通知（Promise形式）。 |
| [getDeviceRemindType](arkts-notification-notification-getdeviceremindtype-depr-f-sys.md#getdeviceremindtype1) | 获取通知的提醒方式（Callback形式）。 |
| [getDeviceRemindType](arkts-notification-notification-getdeviceremindtype-depr-f-sys.md#getdeviceremindtype2) | 获取通知的提醒方式（Promise形式）。 |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate1) | 查询免打扰时间（Callback形式）。 |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate2) | 查询免打扰时间（Promise形式）。 |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate3) | 查询指定用户的免打扰时间（Callback形式）。 |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate4) | 查询指定用户的免打扰时间（Promise形式）。 |
| [getSlotNumByBundle](arkts-notification-notification-getslotnumbybundle-depr-f-sys.md#getslotnumbybundle1) | 获取指定应用的通知通道数量（Callback形式）。 |
| [getSlotNumByBundle](arkts-notification-notification-getslotnumbybundle-depr-f-sys.md#getslotnumbybundle2) | 获取指定应用的通知通道数量（Promise形式）。 |
| [getSlotsByBundle](arkts-notification-notification-getslotsbybundle-depr-f-sys.md#getslotsbybundle1) | 获取指定应用的所有通知通道（Callback形式）。 |
| [getSlotsByBundle](arkts-notification-notification-getslotsbybundle-depr-f-sys.md#getslotsbybundle2) | 获取指定应用的所有通知通道（Promise形式）。 |
| [isBadgeDisplayed](arkts-notification-notification-isbadgedisplayed-depr-f-sys.md#isbadgedisplayed1) | 获取指定应用的角标使能状态（Callback形式）。 |
| [isBadgeDisplayed](arkts-notification-notification-isbadgedisplayed-depr-f-sys.md#isbadgedisplayed2) | 获取指定应用的角标使能状态（Promise形式）。 |
| [isDistributedEnabledByBundle](arkts-notification-notification-isdistributedenabledbybundle-depr-f-sys.md#isdistributedenabledbybundle1) | 根据应用的包获取应用程序是否支持分布式通知（Callback形式）。 |
| [isDistributedEnabledByBundle](arkts-notification-notification-isdistributedenabledbybundle-depr-f-sys.md#isdistributedenabledbybundle2) | 查询指定应用是否支持分布式通知（Promise形式）。 |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled1) | 获取指定应用的通知使能状态（Callback形式）。 |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled2) | 获取指定应用的通知使能状态（Promise形式）。 |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled3) | 获取通知使能状态（Callback形式）。 |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled4) | 获取通知使能状态（Promise形式）。 |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled5) | 获取指定用户ID下的通知使能状态。使用callback异步回调。 |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled6) | 获取指定用户下的通知使能状态。使用Promise异步回调。 |
| [publish](arkts-notification-notification-publish-depr-f-sys.md#publish3) | 发布通知给指定的用户。使用callback异步回调。 |
| [publish](arkts-notification-notification-publish-depr-f-sys.md#publish4) | 发布通知给指定的用户。使用Promise异步回调。 |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove1) | 删除指定通知（Callback形式）。 |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove2) | 删除指定通知（Promise形式）。 |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove3) | 删除指定通知（Callback形式）。 |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove4) | 删除指定通知（Promise形式）。 |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall1) | 删除指定应用的所有通知（Callback形式）。 |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall2) | 删除所有通知（Callback形式）。 |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall3) | 删除指定用户下的所有通知（callback形式）。 |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall4) | 删除指定用户下的所有通知（Promise形式）。 |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall5) | 删除指定应用的所有通知（Promise形式）。 |
| [removeGroupByBundle](arkts-notification-notification-removegroupbybundle-depr-f-sys.md#removegroupbybundle1) | 删除指定应用的指定组下的通知（Callback形式）。 |
| [removeGroupByBundle](arkts-notification-notification-removegroupbybundle-depr-f-sys.md#removegroupbybundle2) | 删除指定应用的指定组下的通知（Promise形式）。 |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate1) | 设置免打扰时间（Callback形式）。 |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate2) | 设置免打扰时间（Promise形式）。 |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate3) | 指定用户设置免打扰时间（Callback形式）。 |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate4) | 指定用户设置免打扰时间（Promise形式）。 |
| [setSlotByBundle](arkts-notification-notification-setslotbybundle-depr-f-sys.md#setslotbybundle1) | 设定指定应用的通知通道（Callback形式）。 |
| [setSlotByBundle](arkts-notification-notification-setslotbybundle-depr-f-sys.md#setslotbybundle2) | 设定指定应用的通知通道（Promise形式）。 |
| [subscribe](arkts-notification-notification-subscribe-depr-f-sys.md#subscribe1) | 订阅当前用户下所有应用的通知。使用callback异步回调。 |
| [subscribe](arkts-notification-notification-subscribe-depr-f-sys.md#subscribe2) | 订阅通知并指定订阅信息。使用callback异步回调。 |
| [subscribe](arkts-notification-notification-subscribe-depr-f-sys.md#subscribe3) | 订阅通知并指定订阅信息。使用Promise异步回调。 |
| [supportDoNotDisturbMode](arkts-notification-notification-supportdonotdisturbmode-depr-f-sys.md#supportdonotdisturbmode1) | 查询是否支持免打扰功能（Callback形式）。 |
| [supportDoNotDisturbMode](arkts-notification-notification-supportdonotdisturbmode-depr-f-sys.md#supportdonotdisturbmode2) | 查询是否支持免打扰功能（Promise形式）。 |
| [unsubscribe](arkts-notification-notification-unsubscribe-depr-f-sys.md#unsubscribe1) | 取消订阅（callbcak形式）。 |
| [unsubscribe](arkts-notification-notification-unsubscribe-depr-f-sys.md#unsubscribe2) | 取消订阅（Promise形式）。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleOption](arkts-notification-notification-bundleoption-depr-i.md) | 描述BundleOption信息，即应用的包信息。 |
| [NotificationKey](arkts-notification-notification-notificationkey-depr-i.md) | 通知键值。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DoNotDisturbDate](arkts-notification-notification-donotdisturbdate-depr-i-sys.md) | 免打扰时间选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContentType](arkts-notification-notification-contenttype-depr-e.md) | 通知内容类型。 |
| [SlotLevel](arkts-notification-notification-slotlevel-depr-e.md) | 通知级别。 |
| [SlotType](arkts-notification-notification-slottype-depr-e.md) | 通知渠道类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceRemindType](arkts-notification-notification-deviceremindtype-depr-e-sys.md) | 通知提醒方式。 |
| [DoNotDisturbType](arkts-notification-notification-donotdisturbtype-depr-e-sys.md) | 免打扰设置的时间类型。 |
| [RemoveReason](arkts-notification-notification-removereason-depr-e-sys.md) | 通知删除原因。 |
| [SourceType](arkts-notification-notification-sourcetype-depr-e-sys.md) | 通知来源类型。 |
<!--DelEnd-->
