# NotificationExtensionSubscriptionInfo

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:37:14.050Z pushedAt=2026-06-30T10:57:37.011Z -->

The **NotificationExtensionSubscriptionInfo** module describes the information about notification extension subscription.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationExtensionSubscriptionInfo

**System capability**: SystemCapability.Notification.Notification

| Name                | Type                | Read-Only| Optional| Description                  |
| -------------------- | ---------------------|---- | --- |----------------------|
| type                 | [notificationExtensionSubscription.SubscribeType](js-apis-notificationExtensionSubscription.md#subscribetype) | No | No  | Subscription type, specifying the subscription method for notification extension. Currently, only **SubscribeType.BLUETOOTH** is supported, indicating subscription to notifications via Bluetooth.                |
| addr                 | string                | No| No | MAC address, which is a unique identifier of the device. Example: 11:22:33:AA:BB:FF           |