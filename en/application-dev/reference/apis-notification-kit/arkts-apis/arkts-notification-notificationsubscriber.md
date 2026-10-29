# notificationSubscriber(NotificationSubscriber)

## Summary

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BadgeEnabledChangedCallback](arkts-notification-notificationsubscriber-badgeenabledchangedcallback-i-sys.md) | type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) =&gt; void |
| [BadgeNumberCallbackData](arkts-notification-notificationsubscriber-badgenumbercallbackdata-i-sys.md) | Returns the changes of the application badge number. |
| [EnabledNotificationCallbackData](arkts-notification-notificationsubscriber-enablednotificationcallbackdata-i-sys.md) | Returns the changes of the application badge enabled state. |
| [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-notificationsubscriber-enabledprioritynotificationbybundlecallbackdata-i-sys.md) | Returns the changes of the enabled state of the application notification priority. |
| [EnabledPriorityNotificationCallbackData](arkts-notification-notificationsubscriber-enabledprioritynotificationcallbackdata-i-sys.md) | Returns the changes of the enabled state of the notification priority. |
| [EnabledSilentReminderCallbackData](arkts-notification-notificationsubscriber-enabledsilentremindercallbackdata-i-sys.md) | Returns the changes of the [silent reminder](../../../notification/notification-glossary.md#silent-reminder) switch state of application notifications. |
| [NotificationClassification](arkts-notification-notificationsubscriber-notificationclassification-i-sys.md) | Returns the notification classification information. |
| [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | The **NotificationSubscriber** module serves as the input parameter of [subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md) and provides callbacks for receiving or cancelling notifications. |
| [NotificationSwitchChangedCallbackData](arkts-notification-notificationsubscriber-notificationswitchchangedcallbackdata-i-sys.md) | Returns the changes of the notification switch state. |
| [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | Returns notification information carrying system property values. |
| [VoiceContent](arkts-notification-notificationsubscriber-voicecontent-i-sys.md) | Returns the notification voice broadcast content. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [EnabledSilentReminderChangedCallback](arkts-notification-enabledsilentreminderchangedcallback-t-sys.md) | Triggered for registering the [silent reminder](../../../notification/notification-glossary.md#silent-reminder) enabled state change of application notifications. |
| [NotificationSwitchChangedCallback](arkts-notification-notificationswitchchangedcallback-t-sys.md) | Registers the callback for notification switch state changes set by the [notificationManager.setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md) API. |
| [SystemUpdateCallback](arkts-notification-systemupdatecallback-t-sys.md) | Returns the notification information carrying system property values. |
<!--DelEnd-->
