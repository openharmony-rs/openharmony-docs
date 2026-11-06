# NotificationExtensionSubscriptionInfo
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:24:53.219Z pushedAt=2026-10-08T09:30:16.879Z -->

The **NotificationExtensionSubscriptionInfo** module describes the information about notification extension subscription.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationExtensionSubscriptionInfo

**System capability**: SystemCapability.Notification.Notification

| Name                | Type                | Read-Only| Optional| Description                  |
| -------------------- | ---------------------|---- | --- |----------------------|
| type                 | [notificationExtensionSubscription.SubscribeType](js-apis-notificationExtensionSubscription.md#subscribetype) | No | No  | Subscription type, specifying the subscription method for notification extension. Currently, only **SubscribeType.BLUETOOTH** is supported, indicating subscription to notifications via Bluetooth.                |
| addr                 | string                | No  | No  | Unique identifier of the device. When **type** is set to **SubscribeType.BLUETOOTH**, the corresponding Bluetooth device address is specified. Example: "11:22:33:AA:BB:FF".            |
