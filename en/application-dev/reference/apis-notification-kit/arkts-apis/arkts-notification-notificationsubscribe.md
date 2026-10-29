# @ohos.notificationSubscribe(NotificationSubscribe)

This module provides [notification subscription](../../../notification/notification-glossary.md#notification-subscription), unsubscription, notification removal, and other capabilities. Generally, only system applications have the permissions for these operations.

**Since:** 9

<!--Device-unnamed-declare namespace notificationSubscribe--><!--Device-unnamed-declare namespace notificationSubscribe-End-->

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
| [distributeOperation](arkts-notification-notificationsubscribe-distributeoperation-f-sys.md#distributeoperation-1) | Triggers the [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) operation of the specified notification (for example, cross-device notification click-to-redirect and cross-device quick reply). This API uses a promise to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-1) | Removes a notification based on the bundle information and notification key. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-2) | Removes a notification based on the bundle information and notification key. This API uses a promise to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-3) | Removes a notification based on the specified unique notification ID. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-4) | Removes specified notifications. This API uses an asynchronous callback to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-5) | Removes a notification based on the specified unique notification ID. This API uses a promise to return the result. |
| [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-6) | Removes specified notifications. This API uses a promise to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-1) | Removes all notifications for a specified application. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-2) | Removes all notifications. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-3) | Removes all notifications for a specified user. This API uses an asynchronous callback to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-4) | Removes all notifications for a specified user. This API uses a promise to return the result. |
| [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md#removeall-5) | Removes all notifications for a specified application. This API uses a promise to return the result. |
| [subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md#subscribenotification-1) | Subscribes to notifications. After the subscription, the new message is received through the callback in the subscriber. This API uses a promise to return the result. |
| [subscribeNotification](arkts-notification-notificationsubscribe-subscribenotification-f-sys.md#subscribenotification-2) | Subscribes to notifications. After the subscription, the new message is received through the callback in the subscriber. This API uses a promise to return the result. |
| [subscribeSelf](arkts-notification-notificationsubscribe-subscribeself-f-sys.md#subscribeself-1) | Subscribes to notifications of this application. This API uses a promise to return the result. |
| [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md#unsubscribe-1) | Unsubscribes from a notification. This API uses an asynchronous callback to return the result. |
| [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md#unsubscribe-2) | Unsubscribes from a notification. This API uses a promise to return the result. |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-1) | Subscribes to notifications of all applications under this user. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-2) | Subscribes to a notification with the subscription information specified. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-3) | Subscribes to a notification with the subscription information specified. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | Defines the notification key value. |
| [OperationInfo](arkts-notification-notificationsubscribe-operationinfo-i-sys.md) | Describes the [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) operation information. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [BadgeNumberCallbackData](arkts-notification-notificationsubscribe-badgenumbercallbackdata-t-sys.md) | Returns the changes of the application badge number. |
| [BundleOption](arkts-notification-notificationsubscribe-bundleoption-t-sys.md) | Describes the **BundleOption** information, that is, the bundle information of an application. |
| [EnabledNotificationCallbackData](arkts-notification-notificationsubscribe-enablednotificationcallbackdata-t-sys.md) | Returns the changes of the application badge enabled state. |
| [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationbybundlecallbackdata-t-sys.md) | Returns the changes of the enabled state of the application notification priority. |
| [EnabledPriorityNotificationCallbackData](arkts-notification-notificationsubscribe-enabledprioritynotificationcallbackdata-t-sys.md) | Returns the changes of the enabled state of the notification priority. |
| [EnabledSilentReminderCallbackData](arkts-notification-notificationsubscribe-enabledsilentremindercallbackdata-t-sys.md) | Returns the changes of the [silent reminder](../../../notification/notification-glossary.md#silent-reminder) switch state of application notifications. |
| [EnabledSilentReminderChangedCallback](arkts-notification-notificationsubscribe-enabledsilentreminderchangedcallback-t-sys.md) | Triggered for registering the [silent reminder](../../../notification/notification-glossary.md#silent-reminder) enabled state change of application notifications. |
| [NotificationClassification](arkts-notification-notificationsubscribe-notificationclassification-t-sys.md) | Returns the notification classification information. |
| [NotificationSubscribeInfo](arkts-notification-notificationsubscribe-notificationsubscribeinfo-t-sys.md) | The **NotificationSubscribeInfo** module provides APIs for defining the information about the notification subscriber. |
| [NotificationSubscriber](arkts-notification-notificationsubscribe-notificationsubscriber-t-sys.md) | Provides callback methods for subscribers to receive and cancel notifications. |
| [NotificationSwitchChangedCallback](arkts-notification-notificationsubscribe-notificationswitchchangedcallback-t-sys.md) | Registers the callback for notification switch state changes set by the [notificationManager.setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md) API. |
| [NotificationSwitchChangedCallbackData](arkts-notification-notificationsubscribe-notificationswitchchangedcallbackdata-t-sys.md) | Returns the changes of the notification switch state. |
| [SubscribeCallbackData](arkts-notification-notificationsubscribe-subscribecallbackdata-t-sys.md) | Returns notification information carrying system property values. |
| [VoiceContent](arkts-notification-notificationsubscribe-voicecontent-t-sys.md) | Returns the notification voice broadcast content. |
| [VoiceContentOptions](arkts-notification-notificationsubscribe-voicecontentoptions-t-sys.md) | Describes the properties of the voice content options for notification subscription. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Defines the reasons for notification removal. |
<!--DelEnd-->
