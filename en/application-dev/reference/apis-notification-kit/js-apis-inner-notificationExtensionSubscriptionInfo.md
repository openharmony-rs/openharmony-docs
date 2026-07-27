# NotificationExtensionSubscriptionInfo

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9aa812250f4e9aa6e205822b2fc097b3c5b2a47d translatedAt=2026-07-21T01:09:32.779Z pushedAt=2026-07-21T09:32:05.219Z -->

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