# @ohos.notificationManager(NotificationManager)

This module provides notification management capabilities. Applications can use this module to implement the complete lifecycle management of notifications, including publishing, updating, and canceling notifications; creating and querying [notification slots](../../../notification/notification-glossary.md#notification-slot); querying and requesting the authorization status of the notification capability; setting app badges; and querying existing notifications in the [notification center](../../../notification/notification-glossary.md#notification-center).

**APIs used in combination**:

The APIs of this module follow the following workflow of notifications: Authorization → Publishing → Cancellation → Channel Management. The APIs are designed to be used in combination with one another.

1. **Authorization query and request process**: Before publishing a notification, first query the authorization
status of the notification capability through **isNotificationEnabled**. If the notification capability is not authorized, guide the user to enable the notification permission through **requestEnableNotification**.
2. **Notification publishing and updating process**: Publish a notification through **publish**, and specify the
[notification content](../../../notification/notification-glossary.md#notification-content) through **NotificationRequest**. If the ID and label of the newly published notification are the same as those of an existing notification, the existing notification is automatically updated. If the ID or label of the newly published notification differs from those of an existing notification, a new notification is created.
3. **Notification cancellation process**: Cancel a notification with a specified ID through **cancel**, cancel all
notifications of this application through **cancelAll**, and cancel notifications under a specified group through **cancelGroup**.
4. **Notification slot management process**: Create a notification slot through **addSlot**, query notification slot
configurations through **getSlot**\/**getSlots**, and delete notification slots through **removeSlot**\/**removeAllSlots**. It is recommended to create the corresponding type of notification slot before publishing a notification. In addition to using **addSlot** to create a notification slot, you can also carry the **notificationSlotType** field in the [NotificationRequest](arkts-notification-notificationrequest-i.md) when publishing a notification. If a slot of the corresponding type does not exist, it will be automatically created.
5. **Badge management process**: Set the badge number through **setBadgeNumber**, or when publishing a notification
through the **publish** API, carry the number of badges to be incremented in the **badgeNumber** field of [NotificationRequest](arkts-notification-notificationrequest-i.md).
6. **Existing notification query process**: Obtain the number of existing notifications for this application in the
notification center through **getActiveNotificationCount**, and obtain the details of existing notifications for this application in the notification center through **getActiveNotifications**.

**Since:** 9

<!--Device-unnamed-declare namespace notificationManager--><!--Device-unnamed-declare namespace notificationManager-End-->

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addSlot](arkts-notification-notificationmanager-addslot-f.md#addslot-3) | Creates a [notification slot](../../../notification/notification-glossary.md#notification-slot) of the specified type. This API uses an asynchronous callback. |
| [addSlot](arkts-notification-notificationmanager-addslot-f.md#addslot-4) | Creates a [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified type. This API uses a promise to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f.md#cancel-1) | Cancels a notification with the specified ID. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f.md#cancel-2) | Cancels a published notification based on the notification ID and label. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f.md#cancel-3) | Cancels a published notification based on the notification ID and label. This API uses a promise to return the result. |
| [cancelAll](arkts-notification-notificationmanager-cancelall-f.md#cancelall-1) | Cancels all notifications of this application. This API uses an asynchronous callback to return the result. |
| [cancelAll](arkts-notification-notificationmanager-cancelall-f.md#cancelall-2) | Cancels all notifications of this application. This API uses a promise to return the result. |
| [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md#cancelgroup-1) | Cancels notifications under a notification group of this application. This API uses an asynchronous callback to return the result. |
| [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md#cancelgroup-2) | Cancels notifications under a notification group of this application. This API uses a promise to return the result. |
| [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md#getactivenotificationcount-1) | Obtains the number of active notifications of this application. This API uses an asynchronous callback to return the result. |
| [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md#getactivenotificationcount-2) | Obtains the number of active notifications of this application. This API uses a promise to return the result. |
| [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md#getactivenotifications-1) | Obtains the active notifications of this application. This API uses an asynchronous callback to return the result. |
| [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md#getactivenotifications-2) | Obtains the active notifications of this application. This API uses a promise to return the result. |
| [getBadgeNumber](arkts-notification-notificationmanager-getbadgenumber-f.md#getbadgenumber-1) | Obtains the badge number of this application. This API uses a promise to return the result. |
| [getNotificationParameters](arkts-notification-notificationmanager-getnotificationparameters-f.md#getnotificationparameters-1) | Obtains some information about the **wantAgent** field in [NotificationRequest](arkts-notification-notificationrequest-i.md). This API uses a promise to return the result. |
| [getNotificationSetting](arkts-notification-notificationmanager-getnotificationsetting-f.md#getnotificationsetting-1) | Obtains the [notification setting](../../../notification/notification-glossary.md#notification-setting) of the application, including the switch states of lock screen notifications, banner notifications, home screen badges, vibration, ringtone, and so on. This API uses a promise to return the result. |
| [getSlot](arkts-notification-notificationmanager-getslot-f.md#getslot-1) | Obtains a [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified type. This API uses an asynchronous callback to return the result. |
| [getSlot](arkts-notification-notificationmanager-getslot-f.md#getslot-3) | Obtains a [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified type. This API uses a promise to return the result. |
| [getSlots](arkts-notification-notificationmanager-getslots-f.md#getslots-1) | Obtains all [notification slots](../../../notification/notification-glossary.md#notification-slot) of the current application. This API uses an asynchronous callback to return the result. |
| [getSlots](arkts-notification-notificationmanager-getslots-f.md#getslots-2) | Obtains all [notification slots](../../../notification/notification-glossary.md#notification-slot) of the current application. This API uses a promise to return the result. |
| [isGeofenceEnabled](arkts-notification-notificationmanager-isgeofenceenabled-f.md#isgeofenceenabled-1) | Checks whether the [geofence](../../../notification/notification-glossary.md#geofence) feature is enabled. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md#isnotificationenabled-3) | Checks the [notification authorization](../../../notification/notification-glossary.md#notification-authorization) status of the current application. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md#isnotificationenabled-4) | Checks the [notification authorization](../../../notification/notification-glossary.md#notification-authorization) status of the current application. This API uses a promise to return the result. |
| [isNotificationEnabledSync](arkts-notification-notificationmanager-isnotificationenabledsync-f.md#isnotificationenabledsync-1) | Synchronously checks the [notification authorization](../../../notification/notification-glossary.md#notification-authorization) status of the current application. |
| [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md#issupporttemplate-1) | Checks whether a specified template is supported before using [NotificationTemplate](arkts-notification-notificationtemplate-i.md) to publish a notification. This API uses an asynchronous callback to return the result. |
| [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md#issupporttemplate-2) | Checks whether a specified template is supported before using [NotificationTemplate](arkts-notification-notificationtemplate-i.md) to publish a notification. This API uses a promise to return the result. |
| [openNotificationSettings](arkts-notification-notificationmanager-opennotificationsettings-f.md#opennotificationsettings-1) | Brings up the [notification setting](../../../notification/notification-glossary.md#notification-setting) page of the application. The page is presented in semi-modal form and can be used to set the notification switch, [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode), and so on. This API uses a promise to return the result. |
| [openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md#opennotificationsettingswithresult-1) | Brings up the [notification setting](../../../notification/notification-glossary.md#notification-setting) page of the application. The page is presented in semi-modal form and can be used to set the notification switch, [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode), and so on. This API uses a promise to return the result, and returns the status set by the user when the semi-modal window is closed. |
| [publish](arkts-notification-notificationmanager-publish-f.md#publish-1) | Publishes a notification. This API uses an asynchronous callback to return the result. |
| [publish](arkts-notification-notificationmanager-publish-f.md#publish-2) | Publishes a notification. This API uses a promise to return the result. |
| [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md#removeallslots-1) | Removes all [notification slots](../../../notification/notification-glossary.md#notification-slot) of the current application. This API uses an asynchronous callback to return the result. |
| [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md#removeallslots-2) | Removes all [notification slots](../../../notification/notification-glossary.md#notification-slot) for this application. This API uses a promise to return the result. |
| [removeSlot](arkts-notification-notificationmanager-removeslot-f.md#removeslot-1) | Removes a [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified type for the current application. This API uses an asynchronous callback to return the result. |
| [removeSlot](arkts-notification-notificationmanager-removeslot-f.md#removeslot-2) | Removes a [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified type for the current application. This API uses a promise to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-2) | An application must obtain user authorization before it can send notifications. Calling this API before publishing a notification brings up the [notification authorization](../../../notification/notification-glossary.md#notification-authorization) dialog box, allowing the user to choose whether to allow notifications to be sent. This API uses an asynchronous callback to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-4) | An application must obtain user authorization before it can send notifications. Calling this API before publishing a notification brings up the [notification authorization](../../../notification/notification-glossary.md#notification-authorization) dialog box, allowing the user to choose whether to allow notifications to be sent. This API uses a promise to return the result. |
| [setBadgeNumber](arkts-notification-notificationmanager-setbadgenumber-f.md#setbadgenumber-1) | Sets the notification badge number. This API uses an asynchronous callback to return the result. |
| [setBadgeNumber](arkts-notification-notificationmanager-setbadgenumber-f.md#setbadgenumber-2) | Sets the notification badge number. This API uses a promise to return the result. |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md#isdistributedenabled-1) | Checks whether the device supports [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) notifications. This API uses an asynchronous callback to return the result. |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md#isdistributedenabled-2) | Checks whether the device supports [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) notifications. This API uses a promise to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-1) | Requests notification authorization for this application. This API uses an asynchronous callback to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-3) | Requests notification authorization for this application. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addDoNotDisturbProfile](arkts-notification-notificationmanager-adddonotdisturbprofile-f-sys.md#adddonotdisturbprofile-1) | Adds the Do Not Disturb profile. This API uses a promise to return the result. |
| [addDoNotDisturbProfile](arkts-notification-notificationmanager-adddonotdisturbprofile-f-sys.md#adddonotdisturbprofile-2) | Adds the Do Not Disturb profile for a specified user. This API uses a promise to return the result. |
| [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot-1) | Creates a [notification slot](../../../notification/notification-glossary.md#notification-slot). This API uses an asynchronous callback to return the result. |
| [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot-2) | Creates a [notification slot](../../../notification/notification-glossary.md#notification-slot). This API uses a promise to return the result. |
| [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md#addslots-1) | Creates multiple [notification slots](../../../notification/notification-glossary.md#notification-slot). This API uses an asynchronous callback to return the result. |
| [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md#addslots-2) | Creates multiple [notification slots](../../../notification/notification-glossary.md#notification-slot). This API uses a promise to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f-sys.md#cancel-4) | Cancels the notification of other applications of the user. This API uses a promise to return the result. |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md#cancelasbundle-1) | Cancels a [proxy notification](../../../notification/notification-glossary.md#notification-proxy). This API uses an asynchronous callback to return the result. |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md#cancelasbundle-2) | Cancels a [proxy notification](../../../notification/notification-glossary.md#notification-proxy). This API uses a promise to return the result. |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md#cancelasbundle-3) | Cancels a [proxy notification](../../../notification/notification-glossary.md#notification-proxy). This API uses a promise to return the result. |
| [disableNotificationFeature](arkts-notification-notificationmanager-disablenotificationfeature-f-sys.md#disablenotificationfeature-1) | Disables the application from publishing notifications by adding the application bundle name to the permission control list. This function can be disabled as required. |
| [disableNotificationFeature](arkts-notification-notificationmanager-disablenotificationfeature-f-sys.md#disablenotificationfeature-2) | Disables the application from publishing notifications by adding the application bundle name to the permission control list. This API uses a promise to return the result. |
| [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md#displaybadge-1) | Sets whether to enable the notification badge for a specified application. This API uses an asynchronous callback to return the result. |
| [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md#displaybadge-2) | Sets whether to enable the notification badge for a specified application. This API uses a promise to return the result. |
| [getActiveNotification](arkts-notification-notificationmanager-getactivenotification-f-sys.md#getactivenotification-1) | Obtains an active notification based on **hashCode**. This API uses a promise to return the result. |
| [getActiveNotificationByFilter](arkts-notification-notificationmanager-getactivenotificationbyfilter-f-sys.md#getactivenotificationbyfilter-1) | Obtains the [normal live view](../../../notification/notification-glossary.md#normal-live-view) notification information that meets the conditions. This API uses an asynchronous callback to return the result. |
| [getActiveNotificationByFilter](arkts-notification-notificationmanager-getactivenotificationbyfilter-f-sys.md#getactivenotificationbyfilter-3) | Obtains the [normal live view](../../../notification/notification-glossary.md#normal-live-view) notification information that meets the conditions. This API uses a promise to return the result. |
| [getAllActiveNotifications](arkts-notification-notificationmanager-getallactivenotifications-f-sys.md#getallactivenotifications-1) | Obtains all active notifications. This API uses an asynchronous callback to return the result. |
| [getAllActiveNotifications](arkts-notification-notificationmanager-getallactivenotifications-f-sys.md#getallactivenotifications-2) | Obtains all active notifications. This API uses a promise to return the result. |
| [getAllNotificationEnabledBundles](arkts-notification-notificationmanager-getallnotificationenabledbundles-f-sys.md#getallnotificationenabledbundles-1) | Obtains a list of applications that allow notifications. This API uses a promise to return the result. |
| [getAllNotificationEnabledBundles](arkts-notification-notificationmanager-getallnotificationenabledbundles-f-sys.md#getallnotificationenabledbundles-2) | Obtains the list of applications that allow notifications for a specified user. This API uses a promise to return the result. |
| [getBadgeDisplayStatusByBundles](arkts-notification-notificationmanager-getbadgedisplaystatusbybundles-f-sys.md#getbadgedisplaystatusbybundles-1) | Obtains the display statuses of application badges in batches. This API uses a promise to return the result. |
| [getBundlePriorityConfig](arkts-notification-notificationmanager-getbundlepriorityconfig-f-sys.md#getbundlepriorityconfig-1) | Obtains the priority configuration of an application, including the keyword-based priority notification recognition rules. This API uses a promise to return the result. |
| [getDistributedDeviceList](arkts-notification-notificationmanager-getdistributeddevicelist-f-sys.md#getdistributeddevicelist-1) | Queries the device types that support [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) notifications. This API uses a promise to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-1) | Obtains the DND time. This API uses an asynchronous callback to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-2) | Obtains the DND time. This API uses a promise to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-3) | Obtains the DND time of a specified user. This API uses an asynchronous callback to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md#getdonotdisturbdate-4) | Obtains the DND time of a specified user. This API uses a promise to return the result. |
| [getDoNotDisturbProfile](arkts-notification-notificationmanager-getdonotdisturbprofile-f-sys.md#getdonotdisturbprofile-1) | Queries the Do Not Disturb profile. This API uses a promise to return the result. |
| [getDoNotDisturbProfile](arkts-notification-notificationmanager-getdonotdisturbprofile-f-sys.md#getdonotdisturbprofile-2) | Queries the Do Not Disturb profile of a specified user. This API uses a promise to return the result. |
| [getNotificationStatisticsByBundle](arkts-notification-notificationmanager-getnotificationstatisticsbybundle-f-sys.md#getnotificationstatisticsbybundle-1) | Obtains notification statistics of a specified list of applications in batches. This API uses a promise to return the result. |
| [getNotificationSwitch](arkts-notification-notificationmanager-getnotificationswitch-f-sys.md#getnotificationswitch-1) | Obtains the notification switch state. This API uses a promise to return the result. |
| [getPriorityEnabledByBundles](arkts-notification-notificationmanager-getpriorityenabledbybundles-f-sys.md#getpriorityenabledbybundles-1) | Obtains whether notification priority is enabled for applications in batches. This API uses a promise to return the result. |
| [getPriorityStrategyByBundles](arkts-notification-notificationmanager-getprioritystrategybybundles-f-sys.md#getprioritystrategybybundles-1) | Obtains the application notification priority strategies in batches. This API uses a promise to return the result. |
| [getReminderInfoByBundles](arkts-notification-notificationmanager-getreminderinfobybundles-f-sys.md#getreminderinfobybundles-1) | Batch obtains reminders of specified applications. This API uses a promise to return the result. |
| [getRingtoneInfoByBundle](arkts-notification-notificationmanager-getringtoneinfobybundle-f-sys.md#getringtoneinfobybundle-1) | Obtains the [customized ringtone](../../../notification/notification-glossary.md#customized-ringtone) information of an application. This API uses a promise to return the result. |
| [getSlotByBundle](arkts-notification-notificationmanager-getslotbybundle-f-sys.md#getslotbybundle-1) | Obtains the [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified type for a specified application. This API uses a promise to return the result. |
| [getSlotFlagsByBundle](arkts-notification-notificationmanager-getslotflagsbybundle-f-sys.md#getslotflagsbybundle-1) | Obtains the [notification slot](../../../notification/notification-glossary.md#notification-slot) flag of a specified application. This API uses a promise to return the result. |
| [getSlotNumByBundle](arkts-notification-notificationmanager-getslotnumbybundle-f-sys.md#getslotnumbybundle-1) | Obtains the number of [notification slots](../../../notification/notification-glossary.md#notification-slot) of a specified application. This API uses an asynchronous callback to return the result. |
| [getSlotNumByBundle](arkts-notification-notificationmanager-getslotnumbybundle-f-sys.md#getslotnumbybundle-2) | Obtains the number of [notification slots](../../../notification/notification-glossary.md#notification-slot) of a specified application. This API uses a promise to return the result. |
| [getSlotsByBundle](arkts-notification-notificationmanager-getslotsbybundle-f-sys.md#getslotsbybundle-1) | Obtains all [notification slots](../../../notification/notification-glossary.md#notification-slot) of a specified application. This API uses an asynchronous callback to return the result. |
| [getSlotsByBundle](arkts-notification-notificationmanager-getslotsbybundle-f-sys.md#getslotsbybundle-2) | Obtains all [notification slots](../../../notification/notification-glossary.md#notification-slot) of a specified application. This API uses a promise to return the result. |
| [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md#isbadgedisplayed-1) | Checks whether the notification badge is enabled for a specified application. This API uses an asynchronous callback to return the result. |
| [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md#isbadgedisplayed-2) | Checks whether the notification badge is enabled for a specified application. This API uses a promise to return the result. |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f-sys.md#isdistributedenabled-3) | Queries whether the device supports [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) notifications. This API uses a promise to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-3) | Obtains whether a specified application supports [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration). This API uses a promise to return the result. |
| [isDistributedEnabledBySlot](arkts-notification-notificationmanager-isdistributedenabledbyslot-f-sys.md#isdistributedenabledbyslot-1) | Queries whether notifications of a specified slot support [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) to devices of a specified type. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-1) | Checks whether notification is enabled for the specified application. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-2) | Checks whether notification is enabled for the specified application. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-5) | Checks whether notification is enabled for a specified user. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md#isnotificationenabled-6) | Checks whether notification is enabled for a specified user. This API uses a promise to return the result. |
| [isNotificationSlotEnabled](arkts-notification-notificationmanager-isnotificationslotenabled-f-sys.md#isnotificationslotenabled-1) | Checks whether a notification slot type is enabled for the specified application. This API uses an asynchronous callback to return the result. |
| [isNotificationSlotEnabled](arkts-notification-notificationmanager-isnotificationslotenabled-f-sys.md#isnotificationslotenabled-2) | Obtains whether a notification slot type is enabled for the specified application. This API uses a promise to return the result. |
| [isNotificationSlotEnabledByBundles](arkts-notification-notificationmanager-isnotificationslotenabledbybundles-f-sys.md#isnotificationslotenabledbybundles-1) | Obtains the enabled state of a specified slot type for multiple applications in batches. This API uses a promise to return the result. All applications share the same slot type. Applications for which no slot has been created will not be returned. |
| [isPriorityEnabled](arkts-notification-notificationmanager-ispriorityenabled-f-sys.md#ispriorityenabled-1) | Checks whether the priority notification is enabled. |
| [isPriorityEnabledByBundle](arkts-notification-notificationmanager-ispriorityenabledbybundle-f-sys.md#ispriorityenabledbybundle-1) | Checks whether the priority notification for a specified application is enabled. |
| [isPriorityIntelligentEnabled](arkts-notification-notificationmanager-ispriorityintelligentenabled-f-sys.md#ispriorityintelligentenabled-1) | Obtains the enabled status of the intelligent [priority notification](../../../notification/notification-glossary.md#priority-notification) service. This API uses a promise to return the result. |
| [isSilentReminderEnabled](arkts-notification-notificationmanager-issilentreminderenabled-f-sys.md#issilentreminderenabled-1) | Queries the switch status of [silent reminder](../../../notification/notification-glossary.md#silent-reminder). This API uses a promise to return the result. |
| [isSmartReminderEnabled](arkts-notification-notificationmanager-issmartreminderenabled-f-sys.md#issmartreminderenabled-1) | Obtains a smart reminder for cross-device collaboration. This API uses a promise to return the result. |
| [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md#issupportdonotdisturbmode-1) | Checks whether DND mode is supported. This API uses an asynchronous callback to return the result. |
| [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md#issupportdonotdisturbmode-2) | Checks whether DND mode is supported. This API uses a promise to return the result. |
| [off('checkNotification')](arkts-notification-notificationmanager-off-f-sys.md#offchecknotification) | Unsubscribes from notification events. |
| [offBadgeNumberQuery](arkts-notification-notificationmanager-offbadgenumberquery-f-sys.md#offbadgenumberquery-1) | Unregisters the callback for querying the number of application badges. |
| [on('checkNotification')](arkts-notification-notificationmanager-on-f-sys.md#onchecknotification) | Subscribes to notification events. The notification service sends the notification information in the callback to the verification program. The verification program returns the verification result to determine whether to publish the notification, for example, controlling the publication frequency of marketing notifications. |
| [on('checkNotification')](arkts-notification-notificationmanager-on-f-sys.md#onchecknotification) | Subscribes to notification events. The notification service sends the notification information in the callback to the verification program. The verification program returns the verification result to determine whether to publish the notification, for example, controlling the publication frequency of marketing notifications. This API uses a promise to return the result. |
| [onBadgeNumberQuery](arkts-notification-notificationmanager-onbadgenumberquery-f-sys.md#onbadgenumberquery-1) | Registers a callback for querying the number of application badges. |
| [publish](arkts-notification-notificationmanager-publish-f-sys.md#publish-3) | Publishes a notification to a specified user. This API uses an asynchronous callback to return the result. |
| [publish](arkts-notification-notificationmanager-publish-f-sys.md#publish-4) | Publishes a notification to a specified user. This API uses a promise to return the result. |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md#publishasbundle-1) | Publishes a [proxy notification](../../../notification/notification-glossary.md#notification-proxy). This API uses an asynchronous callback to return the result. |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md#publishasbundle-2) | Publishes a [proxy notification](../../../notification/notification-glossary.md#notification-proxy). This API uses a promise to return the result. |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md#publishasbundle-3) | Publishes a [proxy notification](../../../notification/notification-glossary.md#notification-proxy). This API uses a promise to return the result. |
| [removeDoNotDisturbProfile](arkts-notification-notificationmanager-removedonotdisturbprofile-f-sys.md#removedonotdisturbprofile-1) | Deletes the Do Not Disturb profile. This API uses a promise to return the result. |
| [removeDoNotDisturbProfile](arkts-notification-notificationmanager-removedonotdisturbprofile-f-sys.md#removedonotdisturbprofile-2) | Deletes the Do Not Disturb profile of a specified user. This API uses a promise to return the result. |
| [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md#removegroupbybundle-1) | Removes notifications under a notification group of the specified application. This API uses an asynchronous callback to return the result. |
| [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md#removegroupbybundle-2) | Removes notifications under a notification group of the specified application. This API uses a promise to return the result. |
| [setAdditionalConfig](arkts-notification-notificationmanager-setadditionalconfig-f-sys.md#setadditionalconfig-1) | Sets the additional system configuration information of the notification. This API uses a promise to return the result. |
| [setBadgeDisplayStatusByBundles](arkts-notification-notificationmanager-setbadgedisplaystatusbybundles-f-sys.md#setbadgedisplaystatusbybundles-1) | Batch sets whether to display badges for specified applications. This API uses a promise to return the result. |
| [setBadgeNumberByBundle](arkts-notification-notificationmanager-setbadgenumberbybundle-f-sys.md#setbadgenumberbybundle-1) | Sets the badge count for other applications. This API uses a promise to return the result. |
| [setBundlePriorityConfig](arkts-notification-notificationmanager-setbundlepriorityconfig-f-sys.md#setbundlepriorityconfig-1) | Sets the priority configuration of an application, including the keyword-based priority notification recognition rules. This API uses a promise to return the result. |
| [setDistributedEnableByBundles](arkts-notification-notificationmanager-setdistributedenablebybundles-f-sys.md#setdistributedenablebybundles-1) | Sets whether applications support [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) in batches. This API uses a promise to return the result. |
| [setDistributedEnabled](arkts-notification-notificationmanager-setdistributedenabled-f-sys.md#setdistributedenabled-1) | Sets whether the device supports [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) notifications. This API uses a promise to return the result. |
| [setDistributedEnabledByBundle](arkts-notification-notificationmanager-setdistributedenabledbybundle-f-sys.md#setdistributedenabledbybundle-1) | Sets whether a specified application supports [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration). This API uses a promise to return the result. |
| [setDistributedEnabledBySlot](arkts-notification-notificationmanager-setdistributedenabledbyslot-f-sys.md#setdistributedenabledbyslot-1) | Sets whether notifications of a specified slot support [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) to devices of a specified type. This API uses a promise to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-1) | Sets the DND time. This API uses an asynchronous callback to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-2) | Sets the DND time. This API uses a promise to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-3) | Sets the DND time for a specified user. This API uses an asynchronous callback to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-4) | Sets the DND time for a specified user. This API uses a promise to return the result. |
| [setGeofenceEnabled](arkts-notification-notificationmanager-setgeofenceenabled-f-sys.md#setgeofenceenabled-1) | Sets the enabled status of the [geofence](../../../notification/notification-glossary.md#geofence). This API uses a promise to return the result. |
| [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md#setnotificationenable-1) | Sets whether to enable notification for a specified application. This API uses an asynchronous callback to return the result. |
| [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md#setnotificationenable-2) | Sets whether to enable notification for a specified application. This API uses a promise to return the result. |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md#setnotificationenableslot-1) | Sets the enabled status of a slot type for the specified application. This API uses an asynchronous callback to return the result. |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md#setnotificationenableslot-2) | Sets the enabled status of a slot type for the specified application. This API uses an asynchronous callback to return the result. |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md#setnotificationenableslot-3) | Sets the enabled status of the specified notification slot type for the specified application. This API uses a promise to return the result. |
| [setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md#setnotificationswitch-1) | Sets the notification switch state. This API uses a promise to return the result. |
| [setPriorityEnabled](arkts-notification-notificationmanager-setpriorityenabled-f-sys.md#setpriorityenabled-1) | Sets the enabling status of the priority notification. |
| [setPriorityEnabledByBundle](arkts-notification-notificationmanager-setpriorityenabledbybundle-f-sys.md#setpriorityenabledbybundle-1) | Sets the enabling status of the priority notification for an application. |
| [setPriorityEnabledByBundles](arkts-notification-notificationmanager-setpriorityenabledbybundles-f-sys.md#setpriorityenabledbybundles-1) | Sets whether notification priority is enabled for applications in batches. This API uses a promise to return the result. |
| [setPriorityIntelligentEnabled](arkts-notification-notificationmanager-setpriorityintelligentenabled-f-sys.md#setpriorityintelligentenabled-1) | Sets the enabled status of the intelligent service for [priority notifications](../../../notification/notification-glossary.md#priority-notification). This API uses a promise to return the result. |
| [setPriorityStrategyByBundles](arkts-notification-notificationmanager-setprioritystrategybybundles-f-sys.md#setprioritystrategybybundles-1) | Sets the application notification priority strategies in batches. This API uses a promise to return the result. |
| [setReminderInfoByBundles](arkts-notification-notificationmanager-setreminderinfobybundles-f-sys.md#setreminderinfobybundles-1) | Batch sets reminders for specified applications. This API uses a promise to return the result. |
| [setRingtoneInfoByBundle](arkts-notification-notificationmanager-setringtoneinfobybundle-f-sys.md#setringtoneinfobybundle-1) | Sets the [customized ringtone](../../../notification/notification-glossary.md#customized-ringtone) information of an application. This API uses a promise to return the result. |
| [setSilentReminderEnabled](arkts-notification-notificationmanager-setsilentreminderenabled-f-sys.md#setsilentreminderenabled-1) | Sets the switch status of [silent reminder](../../../notification/notification-glossary.md#silent-reminder). This API uses a promise to return the result. |
| [setSlotByBundle](arkts-notification-notificationmanager-setslotbybundle-f-sys.md#setslotbybundle-1) | Sets the [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified application. This API uses an asynchronous callback to return the result. |
| [setSlotByBundle](arkts-notification-notificationmanager-setslotbybundle-f-sys.md#setslotbybundle-2) | Sets the [notification slot](../../../notification/notification-glossary.md#notification-slot) of a specified application. This API uses a promise to return the result. |
| [setSlotFlagsByBundle](arkts-notification-notificationmanager-setslotflagsbybundle-f-sys.md#setslotflagsbybundle-1) | Sets the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode) switch of a specified application. This API uses a promise to return the result. |
| [setSmartReminderEnabled](arkts-notification-notificationmanager-setsmartreminderenabled-f-sys.md#setsmartreminderenabled-1) | Sets a smart reminder for cross-device collaboration. This API uses a promise to return the result. |
| [setTargetDeviceStatus](arkts-notification-notificationmanager-settargetdevicestatus-f-sys.md#settargetdevicestatus-1) | Sets the status after device pairing succeeds. When a notification is published, the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode) of the current device is determined based on the status of each device. |
| [snoozeNotification](arkts-notification-notificationmanager-snoozenotification-f-sys.md#snoozenotification-1) | Sets [notification snooze](../../../notification/notification-glossary.md#notification-snooze). The notification is reminded again after the specified time. Each setting triggers only one reminder, and the reminder mode is the same as that of the notification. |
| [subscribeSystemLiveView](arkts-notification-notificationmanager-subscribesystemliveview-f-sys.md#subscribesystemliveview-1) | Subscribes to a [system live view](../../../notification/notification-glossary.md#system-live-view). This API uses a promise to return the result. |
| [triggerSystemLiveView](arkts-notification-notificationmanager-triggersystemliveview-f-sys.md#triggersystemliveview-1) | Triggers a [system live view](../../../notification/notification-glossary.md#system-live-view). This API uses a promise to return the result. |
| [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md#getdeviceremindtype-1) | Obtains the notification reminder type. This API uses an asynchronous callback to return the result. |
| [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md#getdeviceremindtype-2) | Obtains the notification reminder type. This API uses a promise to return the result. |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-getsyncnotificationenabledwithoutapp-f-sys.md#getsyncnotificationenabledwithoutapp-1) | Obtains whether the notification sync feature is enabled for devices where the application is not installed. This API uses an asynchronous callback to return the result. |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-getsyncnotificationenabledwithoutapp-f-sys.md#getsyncnotificationenabledwithoutapp-2) | Obtains whether the notification sync feature is enabled for devices where the application is not installed. This API uses a promise to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-1) | Obtains whether an application supports [distributed notification](../../../notification/notification-glossary.md#distributed-notification) based on the application bundle. This API uses an asynchronous callback to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-2) | Queries whether a specified application supports [distributed notification](../../../notification/notification-glossary.md#distributed-notification). This API uses a promise to return the result. |
| [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md#setdistributedenable-1) | Sets whether to enable [distributed notification](../../../notification/notification-glossary.md#distributed-notification) on this device. This API uses an asynchronous callback to return the result. |
| [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md#setdistributedenable-2) | Sets whether to enable [distributed notification](../../../notification/notification-glossary.md#distributed-notification) on this device. This API uses a promise to return the result. |
| [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle-1) | Sets whether to enable [distributed notification](../../../notification/notification-glossary.md#distributed-notification) for a specified application. This API uses an asynchronous callback to return the result. |
| [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle-2) | Sets whether to enable [distributed notification](../../../notification/notification-glossary.md#distributed-notification) for a specified application. This API uses a promise to return the result. |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-setsyncnotificationenabledwithoutapp-f-sys.md#setsyncnotificationenabledwithoutapp-1) | Sets whether to enable the notification sync feature for devices where the application is not installed. This API uses an asynchronous callback to return the result. |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-setsyncnotificationenabledwithoutapp-f-sys.md#setsyncnotificationenabledwithoutapp-2) | Sets whether to enable the notification sync feature for devices where the application is not installed. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [NotificationSetting](arkts-notification-notificationmanager-notificationsetting-i.md) | Defines the setting status of the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode) switch. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BundleNotificationStatistics](arkts-notification-notificationmanager-bundlenotificationstatistics-i-sys.md) | Describes the notification statistics of a specified application. |
| [ButtonOptions](arkts-notification-notificationmanager-buttonoptions-i-sys.md) | Provides the button information of the notification. |
| [DistributedBundleEnableInfo](arkts-notification-notificationmanager-distributedbundleenableinfo-i-sys.md) | Describes the bundle information of an application that enables cross-device collaboration. |
| [DoNotDisturbDate](arkts-notification-notificationmanager-donotdisturbdate-i-sys.md) | Defines the DND time. |
| [DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md) | Defines the configuration information of the Do Not Disturb mode. |
| [NotificationCheckInfo](arkts-notification-notificationmanager-notificationcheckinfo-i-sys.md) | Defines the [notification check](../../../notification/notification-glossary.md#notification-check) parameters. |
| [NotificationCheckResult](arkts-notification-notificationmanager-notificationcheckresult-i-sys.md) | Defines the [notification check](../../../notification/notification-glossary.md#notification-check) result. |
| [NotificationReminderInfo](arkts-notification-notificationmanager-notificationreminderinfo-i-sys.md) | Describes the information about the application reminder. |
| [RingtoneInfo](arkts-notification-notificationmanager-ringtoneinfo-i-sys.md) | Describes the [customized ringtone](../../../notification/notification-glossary.md#customized-ringtone) information. |
| [SystemLiveViewSubscriber](arkts-notification-notificationmanager-systemliveviewsubscriber-i-sys.md) | Defines the [system live view](../../../notification/notification-glossary.md#system-live-view) subscriber. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | Describes the bundle information of an application. |
| [DistributedOptions](arkts-notification-notificationmanager-distributedoptions-t.md) | Describes distributed notification options. |
| [NotificationActionButton](arkts-notification-notificationmanager-notificationactionbutton-t.md) | Describes the operation button displayed in the notification. |
| [NotificationBasicContent](arkts-notification-notificationmanager-notificationbasiccontent-t.md) | Describes the normal text notification. |
| [NotificationButton](arkts-notification-notificationmanager-notificationbutton-t.md) | Defines the [notification button](../../../notification/notification-glossary.md#notification-button). |
| [NotificationCapsule](arkts-notification-notificationmanager-notificationcapsule-t.md) | Defines the [notification capsule](../../../notification/notification-glossary.md#notification-capsule). |
| [NotificationContent](arkts-notification-notificationmanager-notificationcontent-t.md) | Defines the [notification content](../../../notification/notification-glossary.md#notification-content). |
| [NotificationLongTextContent](arkts-notification-notificationmanager-notificationlongtextcontent-t.md) | Describes the long text notification. |
| [NotificationMultiLineContent](arkts-notification-notificationmanager-notificationmultilinecontent-t.md) | Describes the multi-line text notification. |
| [NotificationParameters](arkts-notification-notificationmanager-notificationparameters-t.md) | Describes part of the information about the wantAgent in the [notification request](../../../notification/notification-glossary.md#notification-request). |
| [NotificationPictureContent](arkts-notification-notificationmanager-notificationpicturecontent-t.md) | Describes the picture-attached notification. |
| [NotificationProgress](arkts-notification-notificationmanager-notificationprogress-t.md) | Defines the [notification progress](../../../notification/notification-glossary.md#notification-progress). |
| [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | Defines the [notification request](../../../notification/notification-glossary.md#notification-request). |
| [NotificationSlot](arkts-notification-notificationmanager-notificationslot-t.md) | Defines the [notification slot](../../../notification/notification-glossary.md#notification-slot). |
| [NotificationSystemLiveViewContent](arkts-notification-notificationmanager-notificationsystemliveviewcontent-t.md) | Defines the [system live view](../../../notification/notification-glossary.md#system-live-view) [notification content](../../../notification/notification-glossary.md#notification-content). |
| [NotificationTemplate](arkts-notification-notificationmanager-notificationtemplate-t.md) | Describes the notification template. |
| [NotificationTime](arkts-notification-notificationmanager-notificationtime-t.md) | Describes the notification timing information. |
| [NotificationUserInput](arkts-notification-notificationmanager-notificationuserinput-t.md) | Describes the user input for the notification. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [CoordinateSystemType](arkts-notification-notificationmanager-coordinatesystemtype-t-sys.md) | Enumerates the coordinate system types of the [geofence](../../../notification/notification-glossary.md#geofence). |
| [Geofence](arkts-notification-notificationmanager-geofence-t-sys.md) | Defines the configuration information of the [geofence](../../../notification/notification-glossary.md#geofence). |
| [GroupInfo](arkts-notification-notificationmanager-groupinfo-t-sys.md) | Defines the custom [group notification](../../../notification/notification-glossary.md#group-notification) information. |
| [LiveViewStatus](arkts-notification-notificationmanager-liveviewstatus-t-sys.md) | Describes the status of the [normal live view notification](../../../notification/notification-glossary.md#normal-live-view). |
| [LiveViewTypes](arkts-notification-notificationmanager-liveviewtypes-t-sys.md) | Describes the type of the [live view notification](../../../notification/notification-glossary.md#live-view-notification). |
| [MonitorEvent](arkts-notification-notificationmanager-monitorevent-t-sys.md) | Enumerates the monitoring event types of the [geofence](../../../notification/notification-glossary.md#geofence). |
| [NotificationCheckRequest](arkts-notification-notificationmanager-notificationcheckrequest-t-sys.md) | Describes the notification authentication information. |
| [NotificationFilter](arkts-notification-notificationmanager-notificationfilter-t-sys.md) | Describes the filter criteria for querying live view notifications. |
| [NotificationFlags](arkts-notification-notificationmanager-notificationflags-t-sys.md) | Describes the [notification flags](../../../notification/notification-glossary.md#notification-flags). |
| [NotificationFlagStatus](arkts-notification-notificationmanager-notificationflagstatus-t-sys.md) | Enumerates the notification flag states. |
| [NotificationIconButton](arkts-notification-notificationmanager-notificationiconbutton-t-sys.md) | Defines the system [notification button](../../../notification/notification-glossary.md#notification-button). |
| [NotificationLiveViewContent](arkts-notification-notificationmanager-notificationliveviewcontent-t-sys.md) | Describes the [normal live view notification](../../../notification/notification-glossary.md#normal-live-view). |
| [NotificationSorting](arkts-notification-notificationmanager-notificationsorting-t-sys.md) | The **NotificationSorting** module provides APIs for defining the sorting information of active notifications. |
| [Trigger](arkts-notification-notificationmanager-trigger-t-sys.md) | Defines the details for triggering a geofence. |
| [TriggerType](arkts-notification-notificationmanager-triggertype-t-sys.md) | Enumerates the trigger types. |
| [UnifiedGroupInfo](arkts-notification-notificationmanager-unifiedgroupinfo-t-sys.md) | Describes the information fields of notification [smart aggregation](../../../notification/notification-glossary.md#notification-smart-aggregation). |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ContentType](arkts-notification-notificationmanager-contenttype-e.md) | Enumerates the [notification content types](../../../notification/notification-glossary.md#content-type). |
| [PriorityNotificationType](arkts-notification-notificationmanager-prioritynotificationtype-e.md) | Describes the priority type of a notification. |
| [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) | Enumerates the notification level. |
| [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Enumerates the [notification slot](../../../notification/notification-glossary.md#notification-slot) types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DeviceRemindType](arkts-notification-notificationmanager-deviceremindtype-e-sys.md) | Defines the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode). |
| [DoNotDisturbType](arkts-notification-notificationmanager-donotdisturbtype-e-sys.md) | Defines the DND time type. |
| [NotificationControlFlagStatus](arkts-notification-notificationmanager-notificationcontrolflagstatus-e-sys.md) | Each bit can control the notification mode. When the bitwise OR operation is performed on **notificationControlFlags** and the enumerated values in the following table, the notification mode is disabled. |
| [PriorityEnableStatus](arkts-notification-notificationmanager-priorityenablestatus-e-sys.md) | Describes the enabling status of the priority notification for an application. |
| [PriorityNotificationType](arkts-notification-notificationmanager-prioritynotificationtype-e-sys.md) | Describes the priority type of a notification. |
| [PriorityStrategyStatus](arkts-notification-notificationmanager-prioritystrategystatus-e-sys.md) | Describes the application notification strategy. |
| [RingtoneType](arkts-notification-notificationmanager-ringtonetype-e-sys.md) | Describes the [customized ringtone](../../../notification/notification-glossary.md#customized-ringtone) type. |
| [SlotType](arkts-notification-notificationmanager-slottype-e-sys.md) | Enumerates the [notification slot](../../../notification/notification-glossary.md#notification-slot) types. |
| [SourceType](arkts-notification-notificationmanager-sourcetype-e-sys.md) | Defines the notification source type. |
| [SwitchState](arkts-notification-notificationmanager-switchstate-e-sys.md) | Describes the switch state of notifications. |
<!--DelEnd-->
