# @ohos.notificationSubscribe

The **notificationSubscribe** module provides APIs for notification subscription, notification unsubscription, subscription removal, and more. In general cases, only system applications can call these APIs.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [distributeOperation](arkts-notification-notificationsubscribe-distributeoperation-f-sys.md) | Triggers a notification for cross-device operations, such as tap-to-redirect and quick reply. This API uses a promise to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md) | Removes a notification based on the bundle information and notification key. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md) | Removes a notification based on the bundle information and notification key. This API uses a promise to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md) | Removes a notification based on the specified unique notification ID. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md) | Removes specified notifications. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md) | Removes a notification based on the specified unique notification ID. This API uses a promise to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md) | Removes specified notifications. This API uses a promise to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md) | Removes all notifications for a specified application. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md) | Removes all notifications. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md) | Removes all notifications for a specified user. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md) | Removes all notifications for a specified user. This API uses a promise to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md) | Removes all notifications for a specified application. This API uses a promise to return the result. |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md) | Subscribes to notifications of all applications under this user. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md) | Subscribes to a notification with the subscription information specified. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md) | Subscribes to a notification with the subscription information specified. This API uses a promise to return the result. |
| [subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md) | Subscribes to notifications. After the subscription, the new message is received through the callback in the subscriber. This API uses a promise to return the result. |
| [subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md) | Subscribes to notifications. After the subscription, the new message is received through the callback in the subscriber. This API uses a promise to return the result. |
| [subscribeSelf](arkts-notification-notificationsubscribe-subscribeself-f-sys.md) | Subscribes to notifications of the application and specifies subscription information. This API uses a promise to return the result. |
| [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md) | Unsubscribes from a notification. This API uses an asynchronous callback to return the result. |
| [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md) | Unsubscribes from a notification. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | Defines the notification key value. |
| [OperationInfo](arkts-notification-notificationsubscribe-operationinfo-i-sys.md) | Defines cross-device collaborative operation information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Defines the reasons for notification removal. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [BadgeNumberCallbackData](arkts-notification-notificationsubscribe-badgenumbercallbackdata-t-sys.md) | Describes the badge number of the application has changed. |
| [BundleOption](arkts-notification-notificationsubscribe-bundleoption-t-sys.md) | Describes the **BundleOption** information, that is, the bundle information of an application. |
| [EnabledNotificationCallbackData](arkts-notification-notificationsubscribe-enablednotificationcallbackdata-t-sys.md) | Describes the properties of the application that the permission to send notifications has changed. |
| [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationbybundlecallbackdata-t-sys.md) | Describes the bundle switch state for priority notification. |
| [EnabledPriorityNotificationCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationcallbackdata-t-sys.md) | Describes the main switch state for priority notification. |
| [EnabledSilentReminderCallbackData](arkts-notification-notificationsubscribe-enabledsilentremindercallbackdata-t-sys.md) | Describes the switch state for silent reminder notification. |
| [EnabledSilentReminderChangedCallback](arkts-notification-notificationsubscribe-enabledsilentreminderchangedcallback-t-sys.md) | Defines a callback function to listen for the enabling state changes of the application's silent reminder. |
| [NotificationClassification](arkts-notification-notificationsubscribe-notificationclassification-t-sys.md) | Describes the notification classification information. |
| [NotificationSubscribeInfo](arkts-notification-notificationsubscribe-notificationsubscribeinfo-t-sys.md) | The **NotificationSubscribeInfo** module provides APIs for defining the information about the publisher for notification subscription. |
| [NotificationSubscriber](arkts-notification-notificationsubscribe-notificationsubscriber-t-sys.md) | Provides callback methods for subscribers to receive and cancel notifications. |
| [NotificationSwitchChangedCallback](arkts-notification-notificationsubscribe-notificationswitchchangedcallback-t-sys.md) | Register the callback function type for notification switch state changes set by the interface of [notificationManager.setNotificationSwitch]{@link./@ohos.notificationManager:notificationManager.setNotificationSwitch}. |
| [NotificationSwitchChangedCallbackData](arkts-notification-notificationsubscribe-notificationswitchchangedcallbackdata-t-sys.md) | Describes the notification switch state changes callback data. |
| [SubscribeCallbackData](arkts-notification-notificationsubscribe-subscribecallbackdata-t-sys.md) | Provides methods that will be called back when the subscriber receives a new notification or a notification is canceled. |
| [VoiceContent](arkts-notification-notificationsubscribe-voicecontent-t-sys.md) | Describes the properties of the voice content of the received notification. |
| [VoiceContentOptions](arkts-notification-notificationsubscribe-voicecontentoptions-t-sys.md) | Describes the properties of the voice content options for notification subscription. |
<!--DelEnd-->
