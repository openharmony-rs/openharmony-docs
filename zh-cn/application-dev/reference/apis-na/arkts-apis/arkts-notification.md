# @ohos.notification

本模块提供通知管理的能力，包括发布、取消发布通知，创建、获取、移除通知通道，订阅、取消订阅通知，获取通知的使能状态、角标使能状态，获取通知的相关信息等。

> **说明：**
>
> 从API version 9开始，该模块不再维护，建议使用[@ohos.notificationManager](../../apis-notification-kit/arkts-apis/arkts-notificationmanager.md#notificationManager)替代。
>
> 通知订阅和取消订阅仅对系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** notificationManager/notificationManager

**系统能力：** SystemCapability.Notification.Notification

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[addSlot](arkts-na-notification-addslot-f-sys.md#addSlot-1) | 创建通知渠道。使用callback异步回调。<br/> |
| <!--DelRow-->[addSlot](arkts-na-notification-addslot-f-sys.md#addSlot-2) | 创建通知渠道。使用Promise异步回调。<br/> |
| [addSlot](arkts-na-notification-addslot-f.md#addSlot-3) | 创建指定类型的通知通道（callback形式）。<br/> |
| [addSlot](arkts-na-notification-addslot-f.md#addSlot-4) | 创建指定类型的通知通道（Promise形式）。<br/> |
| <!--DelRow-->[addSlots](arkts-na-notification-addslots-f-sys.md#addSlots-1) | 创建多个通知通道（callback形式）。<br/> |
| <!--DelRow-->[addSlots](arkts-na-notification-addslots-f-sys.md#addSlots-2) | 创建多个通知通道（Promise形式）。<br/> |
| [cancel](arkts-na-notification-cancel-f.md#cancel-1) | 取消与指定通知ID相匹配的已发布通知（callback形式）。<br/> |
| [cancel](arkts-na-notification-cancel-f.md#cancel-2) | 通过通知ID和通知标签取消已发布的通知（callback形式）。<br/> |
| [cancel](arkts-na-notification-cancel-f.md#cancel-3) | 取消与指定通知ID相匹配的已发布通知，label可以指定也可以不指定（Promise形式）。<br/> |
| [cancelAll](arkts-na-notification-cancelall-f.md#cancelAll-1) | 取消所有已发布的通知（callback形式）。<br/> |
| [cancelAll](arkts-na-notification-cancelall-f.md#cancelAll-2) | 取消所有已发布的通知（Promise形式）。<br/> |
| [cancelGroup](arkts-na-notification-cancelgroup-f.md#cancelGroup-1) | 取消本应用指定组下的通知（Callback形式）。<br/> |
| [cancelGroup](arkts-na-notification-cancelgroup-f.md#cancelGroup-2) | 取消本应用指定组下的通知（Promise形式）。<br/> |
| <!--DelRow-->[displayBadge](arkts-na-notification-displaybadge-f-sys.md#displayBadge-1) | 设定指定应用的角标使能状态（Callback形式）。<br/> |
| <!--DelRow-->[displayBadge](arkts-na-notification-displaybadge-f-sys.md#displayBadge-2) | 设定指定应用的角标使能状态（Promise形式）。<br/> |
| <!--DelRow-->[enableDistributed](arkts-na-notification-enabledistributed-f-sys.md#enableDistributed-1) | 设置设备是否支持分布式通知（Callback形式）。<br/> |
| <!--DelRow-->[enableDistributed](arkts-na-notification-enabledistributed-f-sys.md#enableDistributed-2) | 设置设备是否支持分布式通知（Promise形式）。<br/> |
| <!--DelRow-->[enableDistributedByBundle](arkts-na-notification-enabledistributedbybundle-f-sys.md#enableDistributedByBundle-1) | 设置指定应用是否支持分布式通知（Callback形式）。<br/> |
| <!--DelRow-->[enableDistributedByBundle](arkts-na-notification-enabledistributedbybundle-f-sys.md#enableDistributedByBundle-2) | 设置指定应用是否支持分布式通知（Promise形式）。<br/> |
| <!--DelRow-->[enableNotification](arkts-na-notification-enablenotification-f-sys.md#enableNotification-1) | 设定指定应用的通知使能状态（Callback形式）。<br/> |
| <!--DelRow-->[enableNotification](arkts-na-notification-enablenotification-f-sys.md#enableNotification-2) | 设定指定应用的通知使能状态（Promise形式）。<br/> |
| [getActiveNotificationCount](arkts-na-notification-getactivenotificationcount-f.md#getActiveNotificationCount-1) | 获取当前应用未删除的通知数（Callback形式）。<br/> |
| [getActiveNotificationCount](arkts-na-notification-getactivenotificationcount-f.md#getActiveNotificationCount-2) | 获取当前应用未删除的通知数（Promise形式）。<br/> |
| [getActiveNotifications](arkts-na-notification-getactivenotifications-f.md#getActiveNotifications-1) | 获取当前应用未删除的通知列表（Callback形式）。<br/> |
| [getActiveNotifications](arkts-na-notification-getactivenotifications-f.md#getActiveNotifications-2) | 获取当前应用未删除的通知列表（Promise形式）。<br/> |
| <!--DelRow-->[getAllActiveNotifications](arkts-na-notification-getallactivenotifications-f-sys.md#getAllActiveNotifications-1) | 获取当前未删除的所有通知（Callback形式）。<br/> |
| <!--DelRow-->[getAllActiveNotifications](arkts-na-notification-getallactivenotifications-f-sys.md#getAllActiveNotifications-2) | 获取当前未删除的所有通知（Promise形式）。<br/> |
| <!--DelRow-->[getDeviceRemindType](arkts-na-notification-getdeviceremindtype-f-sys.md#getDeviceRemindType-1) | 获取通知的提醒方式（Callback形式）。<br/> |
| <!--DelRow-->[getDeviceRemindType](arkts-na-notification-getdeviceremindtype-f-sys.md#getDeviceRemindType-2) | 获取通知的提醒方式（Promise形式）。<br/> |
| <!--DelRow-->[getDoNotDisturbDate](arkts-na-notification-getdonotdisturbdate-f-sys.md#getDoNotDisturbDate-1) | 查询免打扰时间（Callback形式）。<br/> |
| <!--DelRow-->[getDoNotDisturbDate](arkts-na-notification-getdonotdisturbdate-f-sys.md#getDoNotDisturbDate-2) | 查询免打扰时间（Promise形式）。<br/> |
| <!--DelRow-->[getDoNotDisturbDate](arkts-na-notification-getdonotdisturbdate-f-sys.md#getDoNotDisturbDate-3) | 查询指定用户的免打扰时间（Callback形式）。<br/> |
| <!--DelRow-->[getDoNotDisturbDate](arkts-na-notification-getdonotdisturbdate-f-sys.md#getDoNotDisturbDate-4) | 查询指定用户的免打扰时间（Promise形式）。<br/> |
| [getSlot](arkts-na-notification-getslot-f.md#getSlot-1) | 获取一个指定类型的通知通道（callback形式）。<br/> |
| [getSlot](arkts-na-notification-getslot-f.md#getSlot-2) | 获取一个指定类型的通知通道（Promise形式）。<br/> |
| <!--DelRow-->[getSlotNumByBundle](arkts-na-notification-getslotnumbybundle-f-sys.md#getSlotNumByBundle-1) | 获取指定应用的通知通道数量（Callback形式）。<br/> |
| <!--DelRow-->[getSlotNumByBundle](arkts-na-notification-getslotnumbybundle-f-sys.md#getSlotNumByBundle-2) | 获取指定应用的通知通道数量（Promise形式）。<br/> |
| [getSlots](arkts-na-notification-getslots-f.md#getSlots-1) | 获取此应用程序的所有通知通道（callback形式）。<br/> |
| [getSlots](arkts-na-notification-getslots-f.md#getSlots-2) | 获取此应用程序的所有通知通道（Promise形式）。<br/> |
| <!--DelRow-->[getSlotsByBundle](arkts-na-notification-getslotsbybundle-f-sys.md#getSlotsByBundle-1) | 获取指定应用的所有通知通道（Callback形式）。<br/> |
| <!--DelRow-->[getSlotsByBundle](arkts-na-notification-getslotsbybundle-f-sys.md#getSlotsByBundle-2) | 获取指定应用的所有通知通道（Promise形式）。<br/> |
| <!--DelRow-->[isBadgeDisplayed](arkts-na-notification-isbadgedisplayed-f-sys.md#isBadgeDisplayed-1) | 获取指定应用的角标使能状态（Callback形式）。<br/> |
| <!--DelRow-->[isBadgeDisplayed](arkts-na-notification-isbadgedisplayed-f-sys.md#isBadgeDisplayed-2) | 获取指定应用的角标使能状态（Promise形式）。<br/> |
| [isDistributedEnabled](arkts-na-notification-isdistributedenabled-f.md#isDistributedEnabled-1) | 查询设备是否支持分布式通知（Callback形式）。<br/> |
| [isDistributedEnabled](arkts-na-notification-isdistributedenabled-f.md#isDistributedEnabled-2) | 查询设备是否支持分布式通知（Promise形式）。<br/> |
| <!--DelRow-->[isDistributedEnabledByBundle](arkts-na-notification-isdistributedenabledbybundle-f-sys.md#isDistributedEnabledByBundle-1) | 根据应用的包获取应用程序是否支持分布式通知（Callback形式）。<br/> |
| <!--DelRow-->[isDistributedEnabledByBundle](arkts-na-notification-isdistributedenabledbybundle-f-sys.md#isDistributedEnabledByBundle-2) | 查询指定应用是否支持分布式通知（Promise形式）。<br/> |
| <!--DelRow-->[isNotificationEnabled](arkts-na-notification-isnotificationenabled-f-sys.md#isNotificationEnabled-1) | 获取指定应用的通知使能状态（Callback形式）。<br/> |
| <!--DelRow-->[isNotificationEnabled](arkts-na-notification-isnotificationenabled-f-sys.md#isNotificationEnabled-2) | 获取指定应用的通知使能状态（Promise形式）。<br/> |
| <!--DelRow-->[isNotificationEnabled](arkts-na-notification-isnotificationenabled-f-sys.md#isNotificationEnabled-3) | 获取通知使能状态（Callback形式）。<br/> |
| <!--DelRow-->[isNotificationEnabled](arkts-na-notification-isnotificationenabled-f-sys.md#isNotificationEnabled-4) | 获取通知使能状态（Promise形式）。<br/> |
| <!--DelRow-->[isNotificationEnabled](arkts-na-notification-isnotificationenabled-f-sys.md#isNotificationEnabled-5) | 获取指定用户ID下的通知使能状态。使用callback异步回调。<br/> |
| <!--DelRow-->[isNotificationEnabled](arkts-na-notification-isnotificationenabled-f-sys.md#isNotificationEnabled-6) | 获取指定用户下的通知使能状态。使用Promise异步回调。<br/> |
| [isSupportTemplate](arkts-na-notification-issupporttemplate-f.md#isSupportTemplate-1) | 在使用[通知模板](../../apis-notification-kit/arkts-apis/arkts-notification-notificationtemplate-i.md#NotificationTemplate)发布通知前，<br/>可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。<br/> |
| [isSupportTemplate](arkts-na-notification-issupporttemplate-f.md#isSupportTemplate-2) | 在使用[通知模板](../../apis-notification-kit/arkts-apis/arkts-notification-notificationtemplate-i.md#NotificationTemplate)发布通知前，<br/>可以通过该接口查询是否支持对应的通知模板。使用Promise异步回调。<br/> |
| [publish](arkts-na-notification-publish-f.md#publish-1) | 发布通知（callback形式）。<br/> |
| [publish](arkts-na-notification-publish-f.md#publish-2) | 发布通知（Promise形式）。<br/> |
| <!--DelRow-->[publish](arkts-na-notification-publish-f-sys.md#publish-3) | 发布通知给指定的用户。使用callback异步回调。<br/> |
| <!--DelRow-->[publish](arkts-na-notification-publish-f-sys.md#publish-4) | 发布通知给指定的用户。使用Promise异步回调。<br/> |
| <!--DelRow-->[remove](arkts-na-notification-remove-f-sys.md#remove-1) | 删除指定通知（Callback形式）。<br/> |
| <!--DelRow-->[remove](arkts-na-notification-remove-f-sys.md#remove-2) | 删除指定通知（Promise形式）。<br/> |
| <!--DelRow-->[remove](arkts-na-notification-remove-f-sys.md#remove-3) | 删除指定通知（Callback形式）。<br/> |
| <!--DelRow-->[remove](arkts-na-notification-remove-f-sys.md#remove-4) | 删除指定通知（Promise形式）。<br/> |
| <!--DelRow-->[removeAll](arkts-na-notification-removeall-f-sys.md#removeAll-1) | 删除指定应用的所有通知（Callback形式）。<br/> |
| <!--DelRow-->[removeAll](arkts-na-notification-removeall-f-sys.md#removeAll-2) | 删除所有通知（Callback形式）。<br/> |
| <!--DelRow-->[removeAll](arkts-na-notification-removeall-f-sys.md#removeAll-3) | 删除指定用户下的所有通知（callback形式）。<br/> |
| <!--DelRow-->[removeAll](arkts-na-notification-removeall-f-sys.md#removeAll-4) | 删除指定用户下的所有通知（Promise形式）。<br/> |
| <!--DelRow-->[removeAll](arkts-na-notification-removeall-f-sys.md#removeAll-5) | 删除指定应用的所有通知（Promise形式）。<br/> |
| [removeAllSlots](arkts-na-notification-removeallslots-f.md#removeAllSlots-1) | 删除所有通知通道（callback形式）。<br/> |
| [removeAllSlots](arkts-na-notification-removeallslots-f.md#removeAllSlots-2) | 删除所有通知通道（Promise形式）。<br/> |
| <!--DelRow-->[removeGroupByBundle](arkts-na-notification-removegroupbybundle-f-sys.md#removeGroupByBundle-1) | 删除指定应用的指定组下的通知（Callback形式）。<br/> |
| <!--DelRow-->[removeGroupByBundle](arkts-na-notification-removegroupbybundle-f-sys.md#removeGroupByBundle-2) | 删除指定应用的指定组下的通知（Promise形式）。<br/> |
| [removeSlot](arkts-na-notification-removeslot-f.md#removeSlot-1) | 删除指定类型的通知通道（callback形式）。<br/> |
| [removeSlot](arkts-na-notification-removeslot-f.md#removeSlot-2) | 删除指定类型的通知通道（Promise形式）。<br/> |
| [requestEnableNotification](arkts-na-notification-requestenablenotification-f.md#requestEnableNotification-1) | 应用请求通知使能（Callback形式）。<br/> |
| [requestEnableNotification](arkts-na-notification-requestenablenotification-f.md#requestEnableNotification-2) | 应用请求通知使能（Promise形式）。<br/> |
| <!--DelRow-->[setDoNotDisturbDate](arkts-na-notification-setdonotdisturbdate-f-sys.md#setDoNotDisturbDate-1) | 设置免打扰时间（Callback形式）。<br/> |
| <!--DelRow-->[setDoNotDisturbDate](arkts-na-notification-setdonotdisturbdate-f-sys.md#setDoNotDisturbDate-2) | 设置免打扰时间（Promise形式）。<br/> |
| <!--DelRow-->[setDoNotDisturbDate](arkts-na-notification-setdonotdisturbdate-f-sys.md#setDoNotDisturbDate-3) | 指定用户设置免打扰时间（Callback形式）。<br/> |
| <!--DelRow-->[setDoNotDisturbDate](arkts-na-notification-setdonotdisturbdate-f-sys.md#setDoNotDisturbDate-4) | 指定用户设置免打扰时间（Promise形式）。<br/> |
| <!--DelRow-->[setSlotByBundle](arkts-na-notification-setslotbybundle-f-sys.md#setSlotByBundle-1) | 设定指定应用的通知通道（Callback形式）。<br/> |
| <!--DelRow-->[setSlotByBundle](arkts-na-notification-setslotbybundle-f-sys.md#setSlotByBundle-2) | 设定指定应用的通知通道（Promise形式）。<br/> |
| <!--DelRow-->[subscribe](arkts-na-notification-subscribe-f-sys.md#subscribe-1) | 订阅当前用户下所有应用的通知。使用callback异步回调。<br/> |
| <!--DelRow-->[subscribe](arkts-na-notification-subscribe-f-sys.md#subscribe-2) | 订阅通知并指定订阅信息。使用callback异步回调。<br/> |
| <!--DelRow-->[subscribe](arkts-na-notification-subscribe-f-sys.md#subscribe-3) | 订阅通知并指定订阅信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[supportDoNotDisturbMode](arkts-na-notification-supportdonotdisturbmode-f-sys.md#supportDoNotDisturbMode-1) | 查询是否支持免打扰功能（Callback形式）。<br/> |
| <!--DelRow-->[supportDoNotDisturbMode](arkts-na-notification-supportdonotdisturbmode-f-sys.md#supportDoNotDisturbMode-2) | 查询是否支持免打扰功能（Promise形式）。<br/> |
| <!--DelRow-->[unsubscribe](arkts-na-notification-unsubscribe-f-sys.md#unsubscribe-1) | 取消订阅（callbcak形式）。<br/> |
| <!--DelRow-->[unsubscribe](arkts-na-notification-unsubscribe-f-sys.md#unsubscribe-2) | 取消订阅（Promise形式）。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleOption](arkts-na-notification-bundleoption-i.md) | &gt; **说明：**<br/>&gt; &gt; 从 API version 7开始支持，从API version 9开始废弃。建议使用<br/>&gt; [notificationManager.BundleOption](../../apis-notification-kit/arkts-apis/arkts-notification-bundleoption-i.md#BundleOption)替代。<br/> |
| <!--DelRow-->[DoNotDisturbDate](arkts-na-notification-donotdisturbdate-i-sys.md) | &gt; **说明：**<br/>&gt; 从 API version 8开始支持，从API version 9开始废弃。建议使用<br/>[notificationManager.DoNotDisturbDate](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-donotdisturbdate-i-sys.md#DoNotDisturbDate)替代。<br/> |
| [NotificationKey](arkts-na-notification-notificationkey-i.md) | &gt; **说明：**<br/>&gt; 从 API version 7开始支持，从API version 9开始废弃。&lt;!--Del--&gt;建议使用<br/>&gt; [notificationManager.NotificationKey](../../apis-notification-kit/arkts-apis/arkts-notification-notificationsubscribe-notificationkey-i-sys.md#NotificationKey)替代。<br/>&gt; &lt;!--DelEnd--&gt;<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContentType](arkts-na-notification-contenttype-e.md) | 通知内容类型。<br/> |
| <!--DelRow-->[DeviceRemindType](arkts-na-notification-deviceremindtype-e-sys.md) | &gt; **说明：**<br/>&gt; 从 API version 8开始支持，从API version 9开始废弃。建议使用<br/>[notificationManager.DeviceRemindType](js-apis-notificationManager-sys.md#deviceremindtype)替代。<br/> |
| <!--DelRow-->[DoNotDisturbType](arkts-na-notification-donotdisturbtype-e-sys.md) | &gt; **说明：**<br/>&gt; 从 API version 8开始支持，从API version 9开始废弃。建议使用<br/>[notificationManager.DoNotDisturbType](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-donotdisturbtype-e-sys.md#DoNotDisturbType)替代。<br/> |
| <!--DelRow-->[RemoveReason](arkts-na-notification-removereason-e-sys.md) | &gt; **说明：**<br/>&gt; 从 API version 7开始支持，从API version 9开始废弃。建议使用<br/>[notificationManager.RemoveReason](js-apis-notificationSubscribe-sys.md#removereason)替代。<br/> |
| [SlotLevel](arkts-na-notification-slotlevel-e.md) | 通知级别。<br/> |
| [SlotType](arkts-na-notification-slottype-e.md) | 通知渠道类型。<br/> |
| <!--DelRow-->[SourceType](arkts-na-notification-sourcetype-e-sys.md) | &gt; **说明：**<br/>&gt; 从 API version 8开始支持，从API version 9开始废弃。建议使用<br/>[notificationManager.SourceType](js-apis-notificationManager-sys.md#sourcetype)替代。<br/> |

