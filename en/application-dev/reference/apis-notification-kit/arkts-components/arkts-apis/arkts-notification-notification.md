# @ohos.notification

The **Notification** module provides notification management capabilities, covering notifications, notification slots, notification subscription, notification enabled status, and notification badge status.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [notificationManager](arkts-notification-notificationmanager.md)

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addSlot](arkts-notification-notification-addslot-depr-f.md#addslot) | Adds a notification slot of a specified type. This API uses an asynchronous callback to return the result. |
| [addSlot](arkts-notification-notification-addslot-depr-f.md#addslot) | Adds a notification slot of a specified type. This API uses a promise to return the result. |
| [cancel](arkts-notification-notification-cancel-depr-f.md#cancel) | Cancels a notification with the specified ID. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-notification-notification-cancel-depr-f.md#cancel) | Cancels a notification with the specified ID and label. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-notification-notification-cancel-depr-f.md#cancel) | Cancels a notification with the specified ID and optional label. This API uses a promise to return the result. |
| [cancelAll](arkts-notification-notification-cancelall-depr-f.md#cancelall) | Cancels all notifications. This API uses an asynchronous callback to return the result. |
| [cancelAll](arkts-notification-notification-cancelall-depr-f.md#cancelall) | Cancels all notifications. This API uses a promise to return the result. |
| [cancelGroup](arkts-notification-notification-cancelgroup-depr-f.md#cancelgroup) | Cancels notifications under a notification group of this application. This API uses an asynchronous callback to return the result. |
| [cancelGroup](arkts-notification-notification-cancelgroup-depr-f.md#cancelgroup) | Cancels notifications under a notification group of this application. This API uses a promise to return the result. |
| [getActiveNotificationCount](arkts-notification-notification-getactivenotificationcount-depr-f.md#getactivenotificationcount) | Obtains the number of active notifications of this application. This API uses an asynchronous callback to return the result. |
| [getActiveNotificationCount](arkts-notification-notification-getactivenotificationcount-depr-f.md#getactivenotificationcount) | Obtains the number of active notifications of this application. This API uses a promise to return the result. |
| [getActiveNotifications](arkts-notification-notification-getactivenotifications-depr-f.md#getactivenotifications) | Obtains active notifications of this application. This API uses an asynchronous callback to return the result. |
| [getActiveNotifications](arkts-notification-notification-getactivenotifications-depr-f.md#getactivenotifications) | Obtains active notifications of this application. This API uses a promise to return the result. |
| [getSlot](arkts-notification-notification-getslot-depr-f.md#getslot) | Obtains a notification slot of a specified type. This API uses an asynchronous callback to return the result. |
| [getSlot](arkts-notification-notification-getslot-depr-f.md#getslot) | Obtains a notification slot of a specified type. This API uses a promise to return the result. |
| [getSlots](arkts-notification-notification-getslots-depr-f.md#getslots) | Obtains all notification slots. This API uses an asynchronous callback to return the result. |
| [getSlots](arkts-notification-notification-getslots-depr-f.md#getslots) | Obtains all notification slots of this application. This API uses a promise to return the result. |
| [isDistributedEnabled](arkts-notification-notification-isdistributedenabled-depr-f.md#isdistributedenabled) | Checks whether this device supports distributed notifications. This API uses an asynchronous callback to return the result. |
| [isDistributedEnabled](arkts-notification-notification-isdistributedenabled-depr-f.md#isdistributedenabled) | Checks whether this device supports distributed notifications. This API uses a promise to return the result. |
| [isSupportTemplate](arkts-notification-notification-issupporttemplate-depr-f.md#issupporttemplate) | Checks whether a specified template is supported before using [NotificationTemplate](arkts-notification-notificationtemplate-notificationtemplate-i.md) to publish a notification. This API uses an asynchronous callback to return the result. |
| [isSupportTemplate](arkts-notification-notification-issupporttemplate-depr-f.md#issupporttemplate) | Checks whether a specified template is supported before using [NotificationTemplate](arkts-notification-notificationtemplate-notificationtemplate-i.md) to publish a notification. This API uses a promise to return the result. |
| [publish](arkts-notification-notification-publish-depr-f.md#publish) | Publishes a notification. This API uses an asynchronous callback to return the result. |
| [publish](arkts-notification-notification-publish-depr-f.md#publish) | Publishes a notification. This API uses a promise to return the result. |
| [removeAllSlots](arkts-notification-notification-removeallslots-depr-f.md#removeallslots) | Removes all notification slots. This API uses an asynchronous callback to return the result. |
| [removeAllSlots](arkts-notification-notification-removeallslots-depr-f.md#removeallslots) | Removes all notification slots. This API uses a promise to return the result. |
| [removeSlot](arkts-notification-notification-removeslot-depr-f.md#removeslot) | Removes a notification slot of a specified type. This API uses an asynchronous callback to return the result. |
| [removeSlot](arkts-notification-notification-removeslot-depr-f.md#removeslot) | Removes a notification slot of a specified type. This API uses a promise to return the result. |
| [requestEnableNotification](arkts-notification-notification-requestenablenotification-depr-f.md#requestenablenotification) | Requests notification to be enabled for this application. This API uses an asynchronous callback to return the result. |
| [requestEnableNotification](arkts-notification-notification-requestenablenotification-depr-f.md#requestenablenotification) | Requests notification to be enabled for this application. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addSlot](arkts-notification-notification-addslot-depr-f-sys.md#addslot) | Adds a notification slot. This API uses an asynchronous callback to return the result. |
| [addSlot](arkts-notification-notification-addslot-depr-f-sys.md#addslot) | Adds a notification slot. This API uses a promise to return the result. |
| [addSlots](arkts-notification-notification-addslots-depr-f-sys.md#addslots) | Adds an array of notification slots. This API uses an asynchronous callback to return the result. |
| [addSlots](arkts-notification-notification-addslots-depr-f-sys.md#addslots) | Adds an array of notification slots. This API uses a promise to return the result. |
| [displayBadge](arkts-notification-notification-displaybadge-depr-f-sys.md#displaybadge) | Sets whether to enable the notification badge for a specified application. This API uses an asynchronous callback to return the result. |
| [displayBadge](arkts-notification-notification-displaybadge-depr-f-sys.md#displaybadge) | Sets whether to enable the notification badge for a specified application. This API uses a promise to return the result. |
| [enableDistributed](arkts-notification-notification-enabledistributed-depr-f-sys.md#enabledistributed) | Sets whether this device supports distributed notifications. This API uses an asynchronous callback to return the result. |
| [enableDistributed](arkts-notification-notification-enabledistributed-depr-f-sys.md#enabledistributed) | Sets whether this device supports distributed notifications. This API uses a promise to return the result. |
| [enableDistributedByBundle](arkts-notification-notification-enabledistributedbybundle-depr-f-sys.md#enabledistributedbybundle) | Sets whether a specified application supports distributed notifications. This API uses an asynchronous callback to return the result. |
| [enableDistributedByBundle](arkts-notification-notification-enabledistributedbybundle-depr-f-sys.md#enabledistributedbybundle) | Sets whether a specified application supports distributed notifications. This API uses a promise to return the result. |
| [enableNotification](arkts-notification-notification-enablenotification-depr-f-sys.md#enablenotification) | Sets whether to enable notification for a specified application. This API uses an asynchronous callback to return the result. |
| [enableNotification](arkts-notification-notification-enablenotification-depr-f-sys.md#enablenotification) | Sets whether to enable notification for a specified application. This API uses a promise to return the result. |
| [getAllActiveNotifications](arkts-notification-notification-getallactivenotifications-depr-f-sys.md#getallactivenotifications) | Obtains all active notifications. This API uses an asynchronous callback to return the result. |
| [getAllActiveNotifications](arkts-notification-notification-getallactivenotifications-depr-f-sys.md#getallactivenotifications) | Obtains all active notifications. This API uses a promise to return the result. |
| [getDeviceRemindType](arkts-notification-notification-getdeviceremindtype-depr-f-sys.md#getdeviceremindtype) | Obtains the notification reminder type. This API uses an asynchronous callback to return the result. |
| [getDeviceRemindType](arkts-notification-notification-getdeviceremindtype-depr-f-sys.md#getdeviceremindtype) | Obtains the notification reminder type. This API uses a promise to return the result. |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate) | Obtains the DND time. This API uses an asynchronous callback to return the result. |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate) | Obtains the DND time. This API uses a promise to return the result. |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate) | Obtains the DND time of a specified user. This API uses an asynchronous callback to return the result. |
| [getDoNotDisturbDate](arkts-notification-notification-getdonotdisturbdate-depr-f-sys.md#getdonotdisturbdate) | Obtains the DND time of a specified user. This API uses a promise to return the result. |
| [getSlotNumByBundle](arkts-notification-notification-getslotnumbybundle-depr-f-sys.md#getslotnumbybundle) | Obtains the number of notification slots of a specified application. This API uses an asynchronous callback to return the result. |
| [getSlotNumByBundle](arkts-notification-notification-getslotnumbybundle-depr-f-sys.md#getslotnumbybundle) | Obtains the number of notification slots of a specified application. This API uses a promise to return the result. |
| [getSlotsByBundle](arkts-notification-notification-getslotsbybundle-depr-f-sys.md#getslotsbybundle) | Obtains the notification slots of a specified application. This API uses an asynchronous callback to return the result. |
| [getSlotsByBundle](arkts-notification-notification-getslotsbybundle-depr-f-sys.md#getslotsbybundle) | Obtains the notification slots of a specified application. This API uses a promise to return the result. |
| [isBadgeDisplayed](arkts-notification-notification-isbadgedisplayed-depr-f-sys.md#isbadgedisplayed) | Checks whether the notification badge is enabled for a specified application. This API uses an asynchronous callback to return the result. |
| [isBadgeDisplayed](arkts-notification-notification-isbadgedisplayed-depr-f-sys.md#isbadgedisplayed) | Checks whether the notification badge is enabled for a specified application. This API uses a promise to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notification-isdistributedenabledbybundle-depr-f-sys.md#isdistributedenabledbybundle) | Obtains whether an application supports distributed notifications based on the bundle. This API uses an asynchronous callback to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notification-isdistributedenabledbybundle-depr-f-sys.md#isdistributedenabledbybundle) | Checks whether a specified application supports distributed notifications. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled) | Checks whether notification is enabled for a specified application. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled) | Checks whether notification is enabled for a specified application. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled) | Checks whether notification is enabled for this application. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled) | Checks whether notification is enabled for this application. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled) | Checks whether notification is enabled for a specified user. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notification-isnotificationenabled-depr-f-sys.md#isnotificationenabled) | Checks whether notification is enabled for a specified user. This API uses a promise to return the result. |
| [publish](arkts-notification-notification-publish-depr-f-sys.md#publish) | Publishes a notification to a specified user. This API uses an asynchronous callback to return the result. |
| [publish](arkts-notification-notification-publish-depr-f-sys.md#publish) | Publishes a notification to a specified user. This API uses a promise to return the result. |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove) | Removes a notification for a specified bundle. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove) | Removes a notification for a specified bundle. This API uses a promise to return the result. |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove) | Removes a notification for a specified bundle. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notification-remove-depr-f-sys.md#remove) | Removes a notification for a specified bundle. This API uses a promise to return the result. |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall) | Removes all notifications for a specified application. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall) | Removes all notifications. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall) | Removes all notifications for a specified user. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall) | Removes all notifications for a specified user. This API uses a promise to return the result. |
| [removeAll](arkts-notification-notification-removeall-depr-f-sys.md#removeall) | Removes all notifications for a specified application. This API uses a promise to return the result. |
| [removeGroupByBundle](arkts-notification-notification-removegroupbybundle-depr-f-sys.md#removegroupbybundle) | Removes notifications under a notification group of a specified application. This API uses an asynchronous callback to return the result. |
| [removeGroupByBundle](arkts-notification-notification-removegroupbybundle-depr-f-sys.md#removegroupbybundle) | Removes notifications under a notification group of a specified application. This API uses a promise to return the result. |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate) | Sets the DND time. This API uses an asynchronous callback to return the result. |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate) | Sets the DND time. This API uses a promise to return the result. |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate) | Sets the DND time for a specified user. This API uses an asynchronous callback to return the result. |
| [setDoNotDisturbDate](arkts-notification-notification-setdonotdisturbdate-depr-f-sys.md#setdonotdisturbdate) | Sets the DND time for a specified user. This API uses a promise to return the result. |
| [setSlotByBundle](arkts-notification-notification-setslotbybundle-depr-f-sys.md#setslotbybundle) | Sets the notification slot for a specified application. This API uses an asynchronous callback to return the result. |
| [setSlotByBundle](arkts-notification-notification-setslotbybundle-depr-f-sys.md#setslotbybundle) | Sets the notification slot for a specified application. This API uses a promise to return the result. |
| [subscribe](arkts-notification-notification-subscribe-depr-f-sys.md#subscribe) | Subscribes to notifications of all applications under this user. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-notification-notification-subscribe-depr-f-sys.md#subscribe) | Subscribes to a notification with the subscription information specified. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-notification-notification-subscribe-depr-f-sys.md#subscribe) | Subscribes to a notification with the subscription information specified. This API uses a promise to return the result. |
| [supportDoNotDisturbMode](arkts-notification-notification-supportdonotdisturbmode-depr-f-sys.md#supportdonotdisturbmode) | Checks whether DND mode is supported. This API uses an asynchronous callback to return the result. |
| [supportDoNotDisturbMode](arkts-notification-notification-supportdonotdisturbmode-depr-f-sys.md#supportdonotdisturbmode) | Checks whether DND mode is supported. This API uses a promise to return the result. |
| [unsubscribe](arkts-notification-notification-unsubscribe-depr-f-sys.md#unsubscribe) | Unsubscribes from a notification. This API uses an asynchronous callback to return the result. |
| [unsubscribe](arkts-notification-notification-unsubscribe-depr-f-sys.md#unsubscribe) | Unsubscribes from a notification. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BundleOption](arkts-notification-notification-bundleoption-depr-i.md) | Describes the **BundleOption** information, that is, the bundle information of an application. |
| [NotificationKey](arkts-notification-notification-notificationkey-depr-i.md) | Notification key. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DoNotDisturbDate](arkts-notification-notification-donotdisturbdate-depr-i-sys.md) | Defines the DND time. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ContentType](arkts-notification-notification-contenttype-depr-e.md) | Enumerates the notification content types. |
| [SlotLevel](arkts-notification-notification-slotlevel-depr-e.md) | Enumerates the notification level. |
| [SlotType](arkts-notification-notification-slottype-depr-e.md) | Enumerates the notification slot types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DeviceRemindType](arkts-notification-notification-deviceremindtype-depr-e-sys.md) | Defines the notification reminder type. |
| [DoNotDisturbType](arkts-notification-notification-donotdisturbtype-depr-e-sys.md) | Defines the DND time type. |
| [RemoveReason](arkts-notification-notification-removereason-depr-e-sys.md) | Reason for removing the notification. |
| [SourceType](arkts-notification-notification-sourcetype-depr-e-sys.md) | Defines the notification source type. |
<!--DelEnd-->
