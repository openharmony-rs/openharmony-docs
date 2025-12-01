# NotificationExtensionSubscriptionInfo
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **NotificationExtensionSubscriptionInfo** module describes the information about notification extension subscription.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationExtensionSubscriptionInfo

**System capability**: SystemCapability.Notification.Notification

| Name                | Type                | Read-Only| Optional| Description                  |
| -------------------- | ---------------------|---- | --- |----------------------|
| type                 | [notificationExtensionSubscription.SubscribeType](js-apis-notificationExtensionSubscription.md#subscribetype) | No| No | Subscription type, including Bluetooth.               |
| addr                 | string                | No| No | MAC address, which is a unique identifier of the device. Example: 11:22:33:AA:BB:FF           |
