# CommonEventSubscribeInfo

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=531db22a21215c0121639101d61b4ccd5426a88b translatedAt=2026-06-08T07:54:35.118Z pushedAt=2026-06-09T10:12:44.188Z -->

The **CommonEventSubscribeInfo** module provides APIs for providing subscriber information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> After users subscribing to custom common events, any application can send potential malicious common events to subscribers. Use the **publisherPermission** and **publisherBundleName** parameters of this module to restrict the publishing scope of common events.

## Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

| Name               | Type          | Read-Only| Optional| Description                                                        |
| ------------------- | -------------- | ---- | ---- | ------------------------------------------------------------ |
| events              | Array\<string> | No | No | Common events to subscribe to.                                        |
| publisherPermission | string         | No | Yes | Permission of the publisher. The subscriber can receive only the events from the publisher with this permission.                                            |
| publisherDeviceId   | string         | No | Yes | Device ID. Use [@ohos.deviceInfo](js-apis-device-info.md) to obtain the UDID as the device ID of the subscriber. Not supported currently.        |
| userId              | number         | No | Yes | User ID. If this parameter is not specified, the default value, which is the ID of the current user, will be used. The value must be an existing user ID in the system. Use [getOsAccountLocalId](./js-apis-osAccount.md#getosaccountlocalid9) to obtain the system account ID and use it as the user ID of the subscriber.|
| priority            | number         | No | Yes | Subscriber priority. The value ranges from –100 to +1000. If the value exceeds the upper or lower limit, the upper or lower limit is used.                |
| publisherBundleName<sup>11+</sup> | string  | No | Yes | Bundle name of the publisher to subscribe to.                |