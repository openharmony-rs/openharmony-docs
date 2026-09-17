# @ohos.notificationExtensionSubscription

The **notificationExtensionSubscription** module provides capabilities for managing notification extension, including opening the extension settings screen, subscribing to/unsubscribing from notification extension, and obtaining/ setting the notification authorization status.

**Since:** 22

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getSubscribeInfo](arkts-notification-notificationextensionsubscription-getsubscribeinfo-f.md) | Obtains the subscription information about the notification extension of this application. This API uses a promise to return the result. |
| [getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f.md) | Obtains the applications that are allowed to access device notifications for the current application. This API uses a promise to return the result. |
| [isUserGranted](arkts-notification-notificationextensionsubscription-isusergranted-f.md) | Checks whether the **Allow access to notifications on this device** switch is toggled on. This API uses a promise to return the result. |
| [openSubscriptionSettings](arkts-notification-notificationextensionsubscription-opensubscriptionsettings-f.md) | Opens the settings screen of notification extension subscription in a semi-modal dialog box. On this screen, the user can toggle on the **Allow access to notifications on this device** switch and grant access to notifications for specified applications. This API uses a promise to return the result. |
| [openSubscriptionSettingsWithResult](arkts-notification-notificationextensionsubscription-opensubscriptionsettingswithresult-f.md) | Opens the settings screen of notification extension subscription in a semi-modal dialog box. On this screen, the user can toggle on the **Allow access to notifications on this device** switch and grant access to notifications for specified applications. This API uses a promise to return the result. When the semi-modal window is closed, the user-defined authorization result is returned. |
| [subscribe](arkts-notification-notificationextensionsubscription-subscribe-f.md) | Subscribes to the notification extension. You can subscribe to the notification extension only after obtaining the unique address of the Bluetooth device by calling the APIs related to the [Bluetooth modules](../../../connectivity/connectivity-kit-intro.md#bluetooth). This API uses a promise to return the result. |
| [unsubscribe](arkts-notification-notificationextensionsubscription-unsubscribe-f.md) | Unsubscribes from the notification extension. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAllSubscriptionBundles](arkts-notification-notificationextensionsubscription-getallsubscriptionbundles-f-sys.md) | Obtains all applications that have requested the ohos.permission.SUBSCRIBE_NOTIFICATION permission and implemented [NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md). This API uses a promise to return the result. |
| [getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f-sys.md) | Obtains the applications that are allowed to access device notifications. This API uses a promise to return the result. |
| [getUserGrantedState](arkts-notification-notificationextensionsubscription-getusergrantedstate-f-sys.md) | Obtains the enabling state of the **Allow access to notifications on this device** switch of a specified application. This API uses a promise to return the result. |
| [setUserGrantedBundleState](arkts-notification-notificationextensionsubscription-setusergrantedbundlestate-f-sys.md) | Sets the enabling state of device notification access for the specified application. This API uses a promise to return the result. |
| [setUserGrantedState](arkts-notification-notificationextensionsubscription-setusergrantedstate-f-sys.md) | Sets the enabling state of the **Allow access to notifications on this device** switch for a specified application. This API uses a promise to return the result. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SubscribeType](arkts-notification-notificationextensionsubscription-subscribetype-e.md) | Describes the type that enables notification extension subscription. |

### Types

| Name | Description |
| --- | --- |
| [BundleOption](arkts-notification-notificationextensionsubscription-bundleoption-t.md) | Describes the bundle information of an application. |
| [GrantedBundleInfo](arkts-notification-notificationextensionsubscription-grantedbundleinfo-t.md) | Describes the bundle information of the authorized application. |
| [NotificationExtensionSubscriptionInfo](arkts-notification-notificationextensionsubscription-notificationextensionsubscriptioninfo-t.md) | Describes the information about the notification extension subscription. |
| [NotificationInfo](arkts-notification-notificationextensionsubscription-notificationinfo-t.md) | Describes the notification information delivered to the [onReceiveMessage](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md#onreceivemessage) callback of ExtensionAbility for notification subscriptions. |
| [UserGrantSetting](arkts-notification-notificationextensionsubscription-usergrantsetting-t.md) | Describes the user authorization settings. |
