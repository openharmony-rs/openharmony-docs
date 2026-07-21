# CommonEventSubscribeInfo

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=5b716a0e1c062ed98c8e1f363a9507fe09b52f56 translatedAt=2026-07-21T02:32:41.236Z pushedAt=2026-07-21T07:17:13.929Z -->

This module provides APIs for providing subscriber information. It allows you to configure parameters such as the subscribed common event type, publisher permission, publisher device ID, user ID, and subscription priority. This module is applicable to scenarios where an app needs to subscribe to system common events or custom common events and requires refined control over event sources.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> After users subscribing to custom common events, any application can send potential malicious common events to subscribers. The **publisherPermission** and **publisherBundleName** parameters of this module can be used to restrict the publisher scope of common events.

## Attributes

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

| Name               | Type          | Read Only| Optional| Description                                                        |
| ------------------- | -------------- | ---- | ---- | ------------------------------------------------------------ |
| events              | Array\<string> | No | No | Common events to subscribe to.                                        |
| publisherPermission | string         | No  | Yes  | Permission of the publisher. The value is an array of permission names defined by the system. This parameter specifies that the subscriber can only receive the common events from publishers with this permission. If this parameter is left empty, the subscriber can receive common events from all publishers.                                             |
| publisherDeviceId   | string         | No | Yes | Device ID, which is used to restrict the subscriber to receive only public events published by the specified device. Use [@ohos.deviceInfo](js-apis-device-info.md) to obtain the UDID as the device ID of the publisher. Not supported currently.        |
| userId              | number         | No | Yes | User ID, which is used to restrict the subscriber to receive only public events related to the specified user ID. If this parameter is not specified, the default value, which is the ID of the current user, will be used. The value must be an existing user ID in the system. Use [getOsAccountLocalId](./js-apis-osAccount.md#getosaccountlocalid9) to obtain the system user ID and use it as the user ID of the publisher.|
| priority            | number         | No  | Yes  | Subscriber priority. A larger value indicates a higher priority, and the subscriber with a higher priority receives ordered public events first. The value ranges from –100 to 1000. If the value exceeds the upper or lower limit, the upper or lower limit is used. The default value is **0**.                 |
| publisherBundleName<sup>11+</sup> | string  | No | Yes | Bundle name of the publisher to be subscribed to. This parameter is used to restrict the subscriber to receive only public events published by the publisher with the specified bundle name. If this parameter is not set, the subscriber can receive all public events published by the app.                |