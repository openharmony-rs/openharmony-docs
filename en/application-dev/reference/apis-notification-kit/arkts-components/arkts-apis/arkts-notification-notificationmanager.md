# @ohos.notificationManager

This module provides notification management capabilities, allowing applications to manage the complete lifecycle of notifications. This includes operations such as publishing, updating, and canceling notifications, creating and querying notification slots, querying and requesting authorization status for notification capabilities, setting application badges, and querying stored notifications in the notification center.

**APIs used in combination**:

The APIs of this module follow the following workflow of notifications: Authorization → Publishing → Cancellation → Channel Management. The APIs are designed to be used in combination with one another.

1. **Authorization query and request process**: Before publishing a notification, first query the authorization
status of the notification capability through **isNotificationEnabled**. If the notification capability is not authorized, guide the user to enable the notification permission through **requestEnableNotification**.

2. **Notification publish and update process**: Publish a notification via the **publish** method, with the
notification content specified through **NotificationRequest**. If a newly published notification has the same ID and tag as an existing one, the existing notification will be automatically updated. If the ID or tag differs, a new notification will be created instead.

3. **Notification cancellation process**: Cancel a notification with a specified ID through **cancel**, cancel all
notifications of this application through **cancelAll**, and cancel notifications under a specified group through **cancelGroup**.

4. **Notification slot management process**: Create a notification slot through **addSlot**, query notification slot
configurations through **getSlot** / **getSlots**, and delete notification slots through **removeSlot** / **removeAllSlots**. It is recommended to create the corresponding type of notification slot before publishing a notification. In addition to using **addSlot** to create a notification slot, you can also carry the **notificationSlotType** field in the NotificationRequest when publishing a notification. If a slot of the corresponding type does not exist, it will be automatically created.

5. **Badge management process**: Set the badge number through **setBadgeNumber**, or when publishing a notification
through the **publish** API, carry the number of badges to be incremented in the **badgeNumber** field of NotificationRequest.

6. **Stored notification query process**: Obtain the number of stored notifications for this application in the
notification center through **getActiveNotificationCount**, and obtain the details of stored notifications for this application in the notification center through **getActiveNotifications**.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addSlot](arkts-notification-notificationmanager-addslot-f.md) | Adds a notification slot of a specified type. This API uses an asynchronous callback to return the result. |
| [addSlot](arkts-notification-notificationmanager-addslot-f.md) | Adds a notification slot of a specified type. This API uses a promise to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f.md) | Cancels a notification with the specified ID. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f.md) | Cancels a published notification based on the notification ID and label. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f.md) | Cancels a published notification based on the notification ID and label. This API uses a promise to return the result. |
| [cancelAll](arkts-notification-notificationmanager-cancelall-f.md) | Cancels all notifications of this application. This API uses an asynchronous callback to return the result. |
| [cancelAll](arkts-notification-notificationmanager-cancelall-f.md) | Cancels all notifications of this application. This API uses a promise to return the result. |
| [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md) | Cancels notifications under a notification group of this application. This API uses an asynchronous callback to return the result. |
| [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md) | Cancels notifications under a notification group of this application. This API uses a promise to return the result. |
| [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md) | Obtains the number of active notifications of this application. This API uses an asynchronous callback to return the result. |
| [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md) | Obtains the number of active notifications of this application. This API uses a promise to return the result. |
| [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md) | Obtains the active notifications of this application. This API uses an asynchronous callback to return the result. |
| [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md) | Obtains the active notifications of this application. This API uses a promise to return the result. |
| [getBadgeNumber](arkts-notification-notificationmanager-getbadgenumber-f.md) | Obtains the badge number of this application. This API uses a promise to return the result. |
| [getNotificationParameters](arkts-notification-notificationmanager-getnotificationparameters-f.md) | Obtains some information about the **wantAgent** field in [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md). This API uses a promise to return the result. |
| [getNotificationSetting](arkts-notification-notificationmanager-getnotificationsetting-f.md) | Obtains the notification settings of the application, including the switch statuses for lock screen notifications, banner notifications, desktop badges, vibration, and ringtone. This API uses a promise to return the result. |
| [getSlot](arkts-notification-notificationmanager-getslot-f.md) | Obtains a notification slot of a specified type. This API uses an asynchronous callback to return the result. |
| [getSlot](arkts-notification-notificationmanager-getslot-f.md) | Obtains a notification slot of a specified type. This API uses a promise to return the result. |
| [getSlots](arkts-notification-notificationmanager-getslots-f.md) | Obtains all notification slots of this application. This API uses an asynchronous callback to return the result. |
| [getSlots](arkts-notification-notificationmanager-getslots-f.md) | Obtains all notification slots of this application. This API uses a promise to return the result. |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md) | Checks whether the device supports cross-device notifications. This API uses an asynchronous callback to return the result. |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md) | Checks whether the device supports cross-device notifications. This API uses a promise to return the result. |
| [isGeofenceEnabled](arkts-notification-notificationmanager-isgeofenceenabled-f.md) | Checks whether geofencing is enabled. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md) | Queries the notification authorization status of the current application. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md) | Queries the notification authorization status of the current application. This API uses a promise to return the result. |
| [isNotificationEnabledSync](arkts-notification-notificationmanager-isnotificationenabledsync-f.md) | Synchronously queries the notification authorization status of the current application. |
| [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md) | Checks whether a specified template is supported before using [NotificationTemplate](arkts-notification-notificationtemplate-notificationtemplate-i.md) to publish a notification. This API uses an asynchronous callback to return the result. |
| [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md) | Checks whether a specified template is supported before using [NotificationTemplate](arkts-notification-notificationtemplate-notificationtemplate-i.md) to publish a notification. This API uses a promise to return the result. |
| [openNotificationSettings](arkts-notification-notificationmanager-opennotificationsettings-f.md) | Opens the notification settings page of the application, which is displayed in semi-modal mode and can be used to set the notification enabling and notification mode. This API uses a promise to return the result. |
| [openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md) | Opens the notification settings page of the application, which is presented in a semi-modal window and can be used to set notification switches, notification reminder methods, etc. This API uses a promise to return the user-set status when the semi-modal window is closed. |
| [publish](arkts-notification-notificationmanager-publish-f.md) | Publishes a notification. This API uses an asynchronous callback to return the result. |
| [publish](arkts-notification-notificationmanager-publish-f.md) | Publishes a notification. This API uses a promise to return the result. |
| [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) | Removes all notification slots for this application. This API uses an asynchronous callback to return the result. |
| [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) | Removes all notification slots for this application. This API uses a promise to return the result. |
| [removeSlot](arkts-notification-notificationmanager-removeslot-f.md) | Removes a notification slot of a specified type for this application. This API uses an asynchronous callback to return the result. |
| [removeSlot](arkts-notification-notificationmanager-removeslot-f.md) | Removes a notification slot of a specified type for this application. This API uses a promise to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md) | Requests notification to be enabled for this application. This API uses an asynchronous callback to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md) | Requests notification to be enabled for this application. You can call this API to display a dialog box prompting the user to enable notification for your application before publishing a notification. This API uses an asynchronous callback to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md) | Requests notification to be enabled for this application. This API uses a promise to return the result. |
| [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md) | Requests notification to be enabled for this application. You can call this API to display a dialog box prompting the user to enable notification for your application before publishing a notification. This API uses a promise to return the result. |
| [setBadgeNumber](arkts-notification-notificationmanager-setbadgenumber-f.md) | Sets the notification badge number. This API uses an asynchronous callback to return the result. |
| [setBadgeNumber](arkts-notification-notificationmanager-setbadgenumber-f.md) | Sets the notification badge number. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addDoNotDisturbProfile](arkts-notification-notificationmanager-adddonotdisturbprofile-f-sys.md) | Adds the Do Not Disturb profile. This API uses a promise to return the result. |
| [addDoNotDisturbProfile](arkts-notification-notificationmanager-adddonotdisturbprofile-f-sys.md) | Adds the Do Not Disturb profile for a specified user. This API uses a promise to return the result. |
| [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md) | Adds a notification slot. This API uses an asynchronous callback to return the result. |
| [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md) | Adds a notification slot. This API uses a promise to return the result. |
| [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md) | Adds an array of notification slots. This API uses an asynchronous callback to return the result. |
| [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md) | Adds an array of notification slots. This API uses a promise to return the result. |
| [cancel](arkts-notification-notificationmanager-cancel-f-sys.md) | Cancels the notification of other applications of the user. This API uses a promise to return the result. |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md) | Cancels a notification published through the reminder agent. This API uses an asynchronous callback to return the result. |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md) | Cancels a notification published through the reminder agent. This API uses a promise to return the result. |
| [cancelAsBundle](arkts-notification-notificationmanager-cancelasbundle-f-sys.md) | Cancels a notification published through the reminder agent. This API uses a promise to return the result. |
| [disableNotificationFeature](arkts-notification-notificationmanager-disablenotificationfeature-f-sys.md) | Disables the application from publishing notifications by adding the application bundle name to the permission control list. This function can be disabled as required. |
| [disableNotificationFeature](arkts-notification-notificationmanager-disablenotificationfeature-f-sys.md) | Disables the application from publishing notifications by adding the application bundle name to the permission control list. This API uses a promise to return the result. |
| [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md) | Sets whether to enable the notification badge for a specified application. This API uses an asynchronous callback to return the result. |
| [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md) | Sets whether to enable the notification badge for a specified application. This API uses a promise to return the result. |
| [getActiveNotificationByFilter](arkts-notification-notificationmanager-getactivenotificationbyfilter-f-sys.md) | Obtains information about the common live view that matches the specified filter criteria. This API uses an asynchronous callback to return the result. |
| [getActiveNotificationByFilter](arkts-notification-notificationmanager-getactivenotificationbyfilter-f-sys.md) | Obtains information about the common live view that matches the specified filter criteria. This API uses a promise to return the result. |
| [getAllActiveNotifications](arkts-notification-notificationmanager-getallactivenotifications-f-sys.md) | Obtains all active notifications. This API uses an asynchronous callback to return the result. |
| [getAllActiveNotifications](arkts-notification-notificationmanager-getallactivenotifications-f-sys.md) | Obtains all active notifications. This API uses a promise to return the result. |
| [getAllNotificationEnabledBundles](arkts-notification-notificationmanager-getallnotificationenabledbundles-f-sys.md) | Obtains a list of applications that allow notifications. This API uses a promise to return the result. |
| [getAllNotificationEnabledBundles](arkts-notification-notificationmanager-getallnotificationenabledbundles-f-sys.md) | Obtains the list of applications that are allowed to publish notifications by a specified user. This API uses a promise to return the result. |
| [getBadgeDisplayStatusByBundles](arkts-notification-notificationmanager-getbadgedisplaystatusbybundles-f-sys.md) | Batch obtains the display statuses of application badges. This API uses a promise to return the result. |
| [getBundlePriorityConfig](arkts-notification-notificationmanager-getbundlepriorityconfig-f-sys.md) | Obtains the priority configuration of an application. |
| [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md) | Obtains the notification reminder type. This API uses an asynchronous callback to return the result. |
| [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md) | Obtains the notification reminder type. This API uses a promise to return the result. |
| [getDistributedDeviceList](arkts-notification-notificationmanager-getdistributeddevicelist-f-sys.md) | Obtains the device types that enable cross-device notification. This API uses a promise to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md) | Obtains the DND time. This API uses an asynchronous callback to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md) | Obtains the DND time. This API uses a promise to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md) | Obtains the DND time of a specified user. This API uses an asynchronous callback to return the result. |
| [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md) | Obtains the DND time of a specified user. This API uses a promise to return the result. |
| [getDoNotDisturbProfile](arkts-notification-notificationmanager-getdonotdisturbprofile-f-sys.md) | Queries the Do Not Disturb profile. This API uses a promise to return the result. |
| [getDoNotDisturbProfile](arkts-notification-notificationmanager-getdonotdisturbprofile-f-sys.md) | Queries the Do Not Disturb profile of a specified user. This API uses a promise to return the result. |
| [getNotificationStatisticsByBundle](arkts-notification-notificationmanager-getnotificationstatisticsbybundle-f-sys.md) | Obtains notification statistics of a specified list of applications in batches. This API uses a promise to return the result. |
| [getNotificationSwitch](arkts-notification-notificationmanager-getnotificationswitch-f-sys.md) | Obtains the notification switch state. This API uses a promise to return the result. |
| [getPriorityEnabledByBundles](arkts-notification-notificationmanager-getpriorityenabledbybundles-f-sys.md) | Obtains whether priority notifications are enabled for applications in batches. This API uses a promise to return the result. |
| [getPriorityStrategyByBundles](arkts-notification-notificationmanager-getprioritystrategybybundles-f-sys.md) | Obtains the application priority notification strategies in batches. This API uses a promise to return the result. |
| [getReminderInfoByBundles](arkts-notification-notificationmanager-getreminderinfobybundles-f-sys.md) | Batch obtains reminders of specified applications. This API uses a promise to return the result. |
| [getRingtoneInfoByBundle](arkts-notification-notificationmanager-getringtoneinfobybundle-f-sys.md) | Obtains the custom ringtone information of an application. This API uses a promise to return the result. |
| [getSlotByBundle](arkts-notification-notificationmanager-getslotbybundle-f-sys.md) | Obtains a notification slot of a specified application. This API uses a promise to return the result. |
| [getSlotFlagsByBundle](arkts-notification-notificationmanager-getslotflagsbybundle-f-sys.md) | Obtains the notification slot flag of a specified application. This API uses a promise to return the result. |
| [getSlotNumByBundle](arkts-notification-notificationmanager-getslotnumbybundle-f-sys.md) | Obtains the number of notification slots of a specified application. This API uses an asynchronous callback to return the result. |
| [getSlotNumByBundle](arkts-notification-notificationmanager-getslotnumbybundle-f-sys.md) | Obtains the number of notification slots of a specified application. This API uses a promise to return the result. |
| [getSlotsByBundle](arkts-notification-notificationmanager-getslotsbybundle-f-sys.md) | Obtains the notification slots of a specified application. This API uses an asynchronous callback to return the result. |
| [getSlotsByBundle](arkts-notification-notificationmanager-getslotsbybundle-f-sys.md) | Obtains the notification slots of a specified application. This API uses a promise to return the result. |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-getsyncnotificationenabledwithoutapp-f-sys.md) | Obtains whether the notification sync feature is enabled for devices where the application is not installed. This API uses an asynchronous callback to return the result. |
| [getSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-getsyncnotificationenabledwithoutapp-f-sys.md) | Obtains whether the notification sync feature is enabled for devices where the application is not installed. This API uses a promise to return the result. |
| [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md) | Checks whether the notification badge is enabled for a specified application. This API uses an asynchronous callback to return the result. |
| [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md) | Checks whether the notification badge is enabled for a specified application. This API uses a promise to return the result. |
| [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f-sys.md) | Checks whether a device enables cross-device notification. This API uses a promise to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md) | Checks whether distributed notification is enabled for a specified application. This API uses an asynchronous callback to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md) | Checks whether distributed notification is enabled for a specified application. This API uses a promise to return the result. |
| [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md) | Obtains whether a specified application enables cross-device collaboration. This API uses a promise to return the result. |
| [isDistributedEnabledBySlot](arkts-notification-notificationmanager-isdistributedenabledbyslot-f-sys.md) | Queries whether notifications of a specified slot can be sent to devices of a specified type. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md) | Checks whether notification is enabled for the specified application. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md) | Checks whether notification is enabled for the specified application. This API uses a promise to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md) | Checks whether notification is enabled for a specified user. This API uses an asynchronous callback to return the result. |
| [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f-sys.md) | Checks whether notification is enabled for a specified user. This API uses a promise to return the result. |
| [isNotificationSlotEnabled](arkts-notification-notificationmanager-isnotificationslotenabled-f-sys.md) | Checks whether a notification slot type is enabled for the specified application. This API uses an asynchronous callback to return the result. |
| [isNotificationSlotEnabled](arkts-notification-notificationmanager-isnotificationslotenabled-f-sys.md) | Checks whether a notification slot type is enabled for the specified application. This API uses a promise to return the result. |
| [isNotificationSlotEnabledByBundles](arkts-notification-notificationmanager-isnotificationslotenabledbybundles-f-sys.md) | Checks whether a notification slot type is enabled for the specified applications in batch. This API uses a promise to return the result. |
| [isPriorityEnabled](arkts-notification-notificationmanager-ispriorityenabled-f-sys.md) | Checks whether the priority notification is enabled. |
| [isPriorityEnabledByBundle](arkts-notification-notificationmanager-ispriorityenabledbybundle-f-sys.md) | Checks whether the priority notification for a specified application is enabled. |
| [isPriorityIntelligentEnabled](arkts-notification-notificationmanager-ispriorityintelligentenabled-f-sys.md) | Obtains whether the intelligent priority notification service is enabled. This API uses a promise to return the result. |
| [isSilentReminderEnabled](arkts-notification-notificationmanager-issilentreminderenabled-f-sys.md) | Checks whether the silent reminder is enabled. This API uses a promise to return the result. |
| [isSmartReminderEnabled](arkts-notification-notificationmanager-issmartreminderenabled-f-sys.md) | Obtains a smart reminder for cross-device collaboration. This API uses a promise to return the result. |
| [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md) | Checks whether DND mode is supported. This API uses an asynchronous callback to return the result. |
| [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md) | Checks whether DND mode is supported. This API uses a promise to return the result. |
| [off](arkts-notification-notificationmanager-off-f-sys.md#offchecknotification) | Unsubscribes from notification events. |
| [offBadgeNumberQuery](arkts-notification-notificationmanager-offbadgenumberquery-f-sys.md) | Unregisters the callback for querying the number of application badges. |
| [on](arkts-notification-notificationmanager-on-f-sys.md#onchecknotification) | Subscribes to notification events. The notification service sends the notification information in the callback to the verification program. The verification program returns the verification result to determine whether to publish the notification, for example, controlling the publication frequency of marketing notifications. |
| [on](arkts-notification-notificationmanager-on-f-sys.md#onchecknotification) | Subscribes to notification events. The notification service sends the notification information in the callback to the verification program. The verification program returns the verification result to determine whether to publish the notification, for example, controlling the publication frequency of marketing notifications. This API uses a promise to return the result. |
| [onBadgeNumberQuery](arkts-notification-notificationmanager-onbadgenumberquery-f-sys.md) | Registers a callback for querying the number of application badges. |
| [publish](arkts-notification-notificationmanager-publish-f-sys.md) | Publishes a notification to a specified user. This API uses an asynchronous callback to return the result. |
| [publish](arkts-notification-notificationmanager-publish-f-sys.md) | Publishes a notification to a specified user. This API uses a promise to return the result. |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md) | Publishes a notification through the reminder agent. This API uses an asynchronous callback to return the result. |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md) | Publishes a notification through the reminder agent. This API uses a promise to return the result. |
| [publishAsBundle](arkts-notification-notificationmanager-publishasbundle-f-sys.md) | Publishes a notification through the reminder agent. This API uses a promise to return the result. |
| [removeDoNotDisturbProfile](arkts-notification-notificationmanager-removedonotdisturbprofile-f-sys.md) | Deletes the Do Not Disturb profile. This API uses a promise to return the result. |
| [removeDoNotDisturbProfile](arkts-notification-notificationmanager-removedonotdisturbprofile-f-sys.md) | Deletes the Do Not Disturb profile of a specified user. This API uses a promise to return the result. |
| [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md) | Removes notifications under a notification group of the specified application. This API uses an asynchronous callback to return the result. |
| [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md) | Removes notifications under a notification group of the specified application. This API uses a promise to return the result. |
| [setAdditionalConfig](arkts-notification-notificationmanager-setadditionalconfig-f-sys.md) | Sets the additional system configuration information of the notification. This API uses a promise to return the result. |
| [setBadgeDisplayStatusByBundles](arkts-notification-notificationmanager-setbadgedisplaystatusbybundles-f-sys.md) | Batch sets whether to display badges for specified applications. This API uses a promise to return the result. |
| [setBadgeNumberByBundle](arkts-notification-notificationmanager-setbadgenumberbybundle-f-sys.md) | Sets the badge count for other applications. This API uses a promise to return the result. |
| [setBundlePriorityConfig](arkts-notification-notificationmanager-setbundlepriorityconfig-f-sys.md) | Sets the priority configuration of an application. |
| [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md) | Sets whether to enable distributed notification on this device. This API uses an asynchronous callback to return the result. |
| [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md) | Sets whether to enable distributed notification on this device. This API uses a promise to return the result. |
| [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md) | Sets whether to enable distributed notification for a specified application. This API uses an asynchronous callback to return the result. |
| [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md) | Sets whether to enable distributed notification for a specified application. This API uses a promise to return the result. |
| [setDistributedEnableByBundles](arkts-notification-notificationmanager-setdistributedenablebybundles-f-sys.md) | Sets whether applications enable cross-device collaboration. This API uses a promise to return the result. |
| [setDistributedEnabled](arkts-notification-notificationmanager-setdistributedenabled-f-sys.md) | Sets whether the device of a specified type enables cross-device notification. This API uses a promise to return the result. |
| [setDistributedEnabledByBundle](arkts-notification-notificationmanager-setdistributedenabledbybundle-f-sys.md) | Sets whether a specified application enables cross-device collaboration. This API uses a promise to return the result. |
| [setDistributedEnabledBySlot](arkts-notification-notificationmanager-setdistributedenabledbyslot-f-sys.md) | Sets whether notifications of a specified slot can be sent to devices of a specified type through cross-device collaboration. This API uses a promise to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md) | Sets the DND time. This API uses an asynchronous callback to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md) | Sets the DND time. This API uses a promise to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md) | Sets the DND time for a specified user. This API uses an asynchronous callback to return the result. |
| [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md) | Sets the DND time for a specified user. This API uses a promise to return the result. |
| [setGeofenceEnabled](arkts-notification-notificationmanager-setgeofenceenabled-f-sys.md) | Sets the enabling state of geofencing. This API uses a promise to return the result. |
| [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md) | Sets whether to enable notification for a specified application. This API uses an asynchronous callback to return the result. |
| [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md) | Sets whether to enable notification for a specified application. This API uses a promise to return the result. |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md) | Sets the enabled status of a slot type for the specified application. This API uses an asynchronous callback to return the result. |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md) | Sets the enabled status of a slot type for the specified application. This API uses an asynchronous callback to return the result. |
| [setNotificationEnableSlot](arkts-notification-notificationmanager-setnotificationenableslot-f-sys.md) | Sets the enabled status of a slot type for the specified application. This API uses a promise to return the result. |
| [setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md) | Sets the notification switch state. This API uses a promise to return the result. |
| [setPriorityEnabled](arkts-notification-notificationmanager-setpriorityenabled-f-sys.md) | Sets the enabling status of the priority notification. |
| [setPriorityEnabledByBundle](arkts-notification-notificationmanager-setpriorityenabledbybundle-f-sys.md) | Sets the enabling status of the priority notification for an application. |
| [setPriorityEnabledByBundles](arkts-notification-notificationmanager-setpriorityenabledbybundles-f-sys.md) | Sets whether priority notifications are enabled for applications in batches. This API uses a promise to return the result. |
| [setPriorityIntelligentEnabled](arkts-notification-notificationmanager-setpriorityintelligentenabled-f-sys.md) | Sets the enabling status of the intelligent priority notification service. This API uses a promise to return the result. |
| [setPriorityStrategyByBundles](arkts-notification-notificationmanager-setprioritystrategybybundles-f-sys.md) | Sets the application priority notification strategies in batches. This API uses a promise to return the result. |
| [setReminderInfoByBundles](arkts-notification-notificationmanager-setreminderinfobybundles-f-sys.md) | Batch sets reminders for specified applications. This API uses a promise to return the result. |
| [setRingtoneInfoByBundle](arkts-notification-notificationmanager-setringtoneinfobybundle-f-sys.md) | Sets the custom ringtone information for an application. This API uses a promise to return the result. |
| [setSilentReminderEnabled](arkts-notification-notificationmanager-setsilentreminderenabled-f-sys.md) | Sets the enabling status of the silent reminder. This API uses a promise to return the result. |
| [setSlotByBundle](arkts-notification-notificationmanager-setslotbybundle-f-sys.md) | Sets the notification slot for a specified application. This API uses an asynchronous callback to return the result. |
| [setSlotByBundle](arkts-notification-notificationmanager-setslotbybundle-f-sys.md) | Sets the notification slot for a specified application. This API uses a promise to return the result. |
| [setSlotFlagsByBundle](arkts-notification-notificationmanager-setslotflagsbybundle-f-sys.md) | Sets the slot flags for a specified application. This API uses a promise to return the result. |
| [setSmartReminderEnabled](arkts-notification-notificationmanager-setsmartreminderenabled-f-sys.md) | Sets a smart reminder for cross-device collaboration. This API uses a promise to return the result. |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-setsyncnotificationenabledwithoutapp-f-sys.md) | Sets whether to enable the notification sync feature for devices where the application is not installed. This API uses an asynchronous callback to return the result. |
| [setSyncNotificationEnabledWithoutApp](arkts-notification-notificationmanager-setsyncnotificationenabledwithoutapp-f-sys.md) | Sets whether to enable the notification sync feature for devices where the application is not installed. This API uses a promise to return the result. |
| [setTargetDeviceStatus](arkts-notification-notificationmanager-settargetdevicestatus-f-sys.md) | Sets the status of a device after it is successfully connected. Device status determines the notification mode of the current device when a notification is published. |
| [snoozeNotification](arkts-notification-notificationmanager-snoozenotification-f-sys.md) | Snoozes a notification. The notification will be reminded again after the specified time. Each setting will trigger only one reminder, and the reminder mode will be the same as that of the notification.<br>The notification will be deleted after the setting. |
| [subscribeSystemLiveView](arkts-notification-notificationmanager-subscribesystemliveview-f-sys.md) | Subscribes to the system live view notification. This API uses a promise to return the result. |
| [triggerSystemLiveView](arkts-notification-notificationmanager-triggersystemliveview-f-sys.md) | Triggers a system live view notification. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [NotificationSetting](arkts-notification-notificationmanager-notificationsetting-i.md) | Describes the setting status of the notification mode switch. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BundleNotificationStatistics](arkts-notification-notificationmanager-bundlenotificationstatistics-i-sys.md) | Describes the notification statistics of a specified application. |
| [ButtonOptions](arkts-notification-notificationmanager-buttonoptions-i-sys.md) | Provides the button information of the notification. |
| [DistributedBundleEnableInfo](arkts-notification-notificationmanager-distributedbundleenableinfo-i-sys.md) | Describes the bundle information of an application that enables cross-device collaboration. |
| [DoNotDisturbDate](arkts-notification-notificationmanager-donotdisturbdate-i-sys.md) | Defines the DND time. |
| [DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md) | Do Not Disturb profile. |
| [NotificationCheckInfo](arkts-notification-notificationmanager-notificationcheckinfo-i-sys.md) | Describes the parameters of check notifications. |
| [NotificationCheckResult](arkts-notification-notificationmanager-notificationcheckresult-i-sys.md) | Describes the result of check notifications. |
| [NotificationReminderInfo](arkts-notification-notificationmanager-notificationreminderinfo-i-sys.md) | Describes the information about the application reminder. |
| [RingtoneInfo](arkts-notification-notificationmanager-ringtoneinfo-i-sys.md) | Describes the custom ringtone information. |
| [SystemLiveViewSubscriber](arkts-notification-notificationmanager-systemliveviewsubscriber-i-sys.md) | Subscriber of the system live view notification. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ContentType](arkts-notification-notificationmanager-contenttype-e.md) | Enumerates the notification content types. |
| [PriorityNotificationType](arkts-notification-notificationmanager-prioritynotificationtype-e.md) | Describes the priority type of a notification. |
| [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) | Enumerates the notification level. |
| [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Enumerates the notification slot types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DeviceRemindType](arkts-notification-notificationmanager-deviceremindtype-e-sys.md) | Defines the notification reminder type. |
| [DoNotDisturbType](arkts-notification-notificationmanager-donotdisturbtype-e-sys.md) | Defines the DND time type. |
| [NotificationControlFlagStatus](arkts-notification-notificationmanager-notificationcontrolflagstatus-e-sys.md) | Each bit can control the notification mode. When the bitwise OR operation is performed on **notificationControlFlags** and the enumerated values in the following table, the notification mode is disabled. |
| [PriorityEnableStatus](arkts-notification-notificationmanager-priorityenablestatus-e-sys.md) | Describes the enabling status of the priority notification for an application. |
| [PriorityNotificationType](arkts-notification-notificationmanager-prioritynotificationtype-e-sys.md) | Describes the priority type of a notification. |
| [PriorityStrategyStatus](arkts-notification-notificationmanager-prioritystrategystatus-e-sys.md) | Describes the application notification strategy. |
| [RingtoneType](arkts-notification-notificationmanager-ringtonetype-e-sys.md) | Enumerates the custom ringtone types. |
| [SlotType](arkts-notification-notificationmanager-slottype-e-sys.md) | Enumerates the notification slot types. |
| [SourceType](arkts-notification-notificationmanager-sourcetype-e-sys.md) | Defines the notification source type. |
| [SwitchState](arkts-notification-notificationmanager-switchstate-e-sys.md) | Describes the switch state of notifications. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | Describes the bundle information of an application. |
| [DistributedOptions](arkts-notification-notificationmanager-distributedoptions-t.md) | Describes distributed notification options. |
| [NotificationActionButton](arkts-notification-notificationmanager-notificationactionbutton-t.md) | Describes the operation button displayed in the notification. |
| [NotificationBasicContent](arkts-notification-notificationmanager-notificationbasiccontent-t.md) | Describes the normal text notification. |
| [NotificationButton](arkts-notification-notificationmanager-notificationbutton-t.md) | Describes the notification button. |
| [NotificationCapsule](arkts-notification-notificationmanager-notificationcapsule-t.md) | Describes the notification capsule. |
| [NotificationContent](arkts-notification-notificationmanager-notificationcontent-t.md) | Describes the notification content. |
| [NotificationLongTextContent](arkts-notification-notificationmanager-notificationlongtextcontent-t.md) | Describes the long text notification. |
| [NotificationMultiLineContent](arkts-notification-notificationmanager-notificationmultilinecontent-t.md) | Describes the multi-line text notification. |
| [NotificationParameters](arkts-notification-notificationmanager-notificationparameters-t.md) | Describes partial information about the **wantAgent** in the notification request. |
| [NotificationPictureContent](arkts-notification-notificationmanager-notificationpicturecontent-t.md) | Describes the picture-attached notification. |
| [NotificationProgress](arkts-notification-notificationmanager-notificationprogress-t.md) | Describes the notification progress. |
| [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | Describes the notification request. |
| [NotificationSlot](arkts-notification-notificationmanager-notificationslot-t.md) | Describes the notification slot. |
| [NotificationSystemLiveViewContent](arkts-notification-notificationmanager-notificationsystemliveviewcontent-t.md) | Describes the system live view notification. |
| [NotificationTemplate](arkts-notification-notificationmanager-notificationtemplate-t.md) | Describes the notification template. |
| [NotificationTime](arkts-notification-notificationmanager-notificationtime-t.md) | Describes the notification timing information. |
| [NotificationUserInput](arkts-notification-notificationmanager-notificationuserinput-t.md) | Describes the user input for the notification. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [CoordinateSystemType](arkts-notification-notificationmanager-coordinatesystemtype-t-sys.md) | Enumerates the coordinate systems of a geofence. |
| [Geofence](arkts-notification-notificationmanager-geofence-t-sys.md) | Defines the configuration of a geofence. |
| [GroupInfo](arkts-notification-notificationmanager-groupinfo-t-sys.md) | Defines the custom group notification information. |
| [LiveViewStatus](arkts-notification-notificationmanager-liveviewstatus-t-sys.md) | Enumerates the statuses of the common live view. |
| [LiveViewTypes](arkts-notification-notificationmanager-liveviewtypes-t-sys.md) | Enumerates live view types. |
| [MonitorEvent](arkts-notification-notificationmanager-monitorevent-t-sys.md) | Enumerates the event types of monitoring a geofence. |
| [NotificationCheckRequest](arkts-notification-notificationmanager-notificationcheckrequest-t-sys.md) | Describes the notification authentication information. |
| [NotificationFilter](arkts-notification-notificationmanager-notificationfilter-t-sys.md) | Describes the filter criteria for querying the live view. |
| [NotificationFlags](arkts-notification-notificationmanager-notificationflags-t-sys.md) | Defines the notification flags. |
| [NotificationFlagStatus](arkts-notification-notificationmanager-notificationflagstatus-t-sys.md) | Enumerates the notification flag states. |
| [NotificationIconButton](arkts-notification-notificationmanager-notificationiconbutton-t-sys.md) | System notification button. |
| [NotificationLiveViewContent](arkts-notification-notificationmanager-notificationliveviewcontent-t-sys.md) | Describes the common live view. |
| [NotificationSorting](arkts-notification-notificationmanager-notificationsorting-t-sys.md) | The **NotificationSorting** module provides APIs for defining the sorting information of active notifications. |
| [Trigger](arkts-notification-notificationmanager-trigger-t-sys.md) | Defines the details for triggering a geofence. |
| [TriggerType](arkts-notification-notificationmanager-triggertype-t-sys.md) | Enumerates the trigger types. |
| [UnifiedGroupInfo](arkts-notification-notificationmanager-unifiedgroupinfo-t-sys.md) | Describes the fields of notification intelligent unification information. |
<!--DelEnd-->
