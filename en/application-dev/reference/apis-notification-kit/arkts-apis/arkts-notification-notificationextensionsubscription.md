# @ohos.notificationExtensionSubscription(notificationExtensionSubscription)

This module provides the capabilities for managing notification extensions, including opening the notification extension subscription settings page, subscribing to and unsubscribing from notification extensions, and obtaining and setting the [notification authorization](../../../notification/notification-glossary.md#notification-authorization) status.

**Since:** 22

<!--Device-unnamed-declare namespace notificationExtensionSubscription--><!--Device-unnamed-declare namespace notificationExtensionSubscription-End-->

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [disableUserGrantedByBundle](arkts-notification-notificationextensionsubscription-disableusergrantedbybundle-f.md#disableusergrantedbybundle-1) | Disables the switch status of a specified app in the list of obtained local notifications in this app. This API uses a promise to return the result. |
| [getSubscribeInfo](arkts-notification-notificationextensionsubscription-getsubscribeinfo-f.md#getsubscribeinfo-1) | Obtains the subscription information about the notification extension of this application. This API uses a promise to return the result. |
| [getUserGrantedBundleIcon](arkts-notification-notificationextensionsubscription-getusergrantedbundleicon-f.md#getusergrantedbundleicon-1) | Queries the icons of apps whose switch is turned on in the list of obtained local notifications in this app. This API uses a promise to return the result. |
| [getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f.md#getusergrantedenabledbundles-2) | Obtains the applications that are allowed to access device notifications for the current application. This API uses a promise to return the result. |
| [isUserGranted](arkts-notification-notificationextensionsubscription-isusergranted-f.md#isusergranted-1) | Checks whether the **Allow access to notifications on this device** switch is toggled on. This API uses a promise to return the result. |
| [openSubscriptionSettings](arkts-notification-notificationextensionsubscription-opensubscriptionsettings-f.md#opensubscriptionsettings-1) | Opens the settings screen of notification extension subscription in a semi-modal dialog box. On this screen, the user can toggle on the **Allow access to notifications on this device** switch and grant access to notifications for specified applications. This API uses a promise to return the result. |
| [openSubscriptionSettingsWithResult](arkts-notification-notificationextensionsubscription-opensubscriptionsettingswithresult-f.md#opensubscriptionsettingswithresult-1) | Opens the settings screen of notification extension subscription in a semi-modal dialog box. On this screen, the user can toggle on the **Allow access to notifications on this device** switch and grant access to notifications for specified applications. This API uses a promise to return the result. When the semi-modal window is closed, the user-defined authorization result is returned. |
| [subscribe](arkts-notification-notificationextensionsubscription-subscribe-f.md#subscribe-1) | Subscribes to the notification extension. You can subscribe to the notification extension only after obtaining the unique address of the Bluetooth device by calling the APIs related to the [Bluetooth modules](../../../connectivity/connectivity-kit-intro.md#bluetooth). This API uses a promise to return the result. |
| [unsubscribe](arkts-notification-notificationextensionsubscription-unsubscribe-f.md#unsubscribe-1) | Unsubscribes from the notification extension. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAllSubscriptionBundles](arkts-notification-notificationextensionsubscription-getallsubscriptionbundles-f-sys.md#getallsubscriptionbundles-1) | Obtains all applications that have the [ohos.permission.SUBSCRIBE_NOTIFICATION](../../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification) permission and have implemented [NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md). This API uses a promise to return the result. |
| [getUserGrantedEnabledBundles](arkts-notification-notificationextensionsubscription-getusergrantedenabledbundles-f-sys.md#getusergrantedenabledbundles-1) | Obtains the applications that are allowed to access device notifications. This API uses a promise to return the result. |
| [getUserGrantedState](arkts-notification-notificationextensionsubscription-getusergrantedstate-f-sys.md#getusergrantedstate-1) | Obtains the enabling state of the **Allow access to notifications on this device** switch of a specified application. This API uses a promise to return the result. |
| [setUserGrantedBundleState](arkts-notification-notificationextensionsubscription-setusergrantedbundlestate-f-sys.md#setusergrantedbundlestate-1) | Sets the enabling state of device notification access for the specified application. This API uses a promise to return the result. |
| [setUserGrantedState](arkts-notification-notificationextensionsubscription-setusergrantedstate-f-sys.md#setusergrantedstate-1) | Sets the enabling state of the **Allow access to notifications on this device** switch for a specified application. This API uses a promise to return the result. |
| [subscribeNotification](arkts-notification-notificationextensionsubscription-subscribenotification-f-sys.md#subscribenotification-1) | Subscribes to notifications based on the priority strategy. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [BundleOption](arkts-notification-notificationextensionsubscription-bundleoption-t.md) | Describes the bundle information of an application. |
| [GrantedBundleInfo](arkts-notification-notificationextensionsubscription-grantedbundleinfo-t.md) | Describes the bundle information of the authorized application. |
| [NotificationExtensionSubscriptionInfo](arkts-notification-notificationextensionsubscription-notificationextensionsubscriptioninfo-t.md) | Describes the information about the notification extension subscription. |
| [NotificationInfo](arkts-notification-notificationextensionsubscription-notificationinfo-t.md) | Defines the notification information in the [onReceiveMessage](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md#onreceivemessage) callback of the [notification subscription](../../../notification/notification-glossary.md#notification-subscription) extension ability. |
| [UserGrantSetting](arkts-notification-notificationextensionsubscription-usergrantsetting-t.md) | Describes the user authorization settings. |

### Enums

| Name | Description |
| --- | --- |
| [SubscribeType](arkts-notification-notificationextensionsubscription-subscribetype-e.md) | Describes the type that enables notification extension subscription. |
