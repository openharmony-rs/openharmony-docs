# CommonEventData
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=8b332ba8e6e72c2d885a38003986f27dfb7e99d3 translatedAt=2026-10-09T12:27:29.828Z pushedAt=2026-10-10T06:11:28.393Z -->

Describes the data of a common event. The **CommonEventData** module is used to carry the common event data received by subscribers in common event subscription scenarios. The data includes the event name, publisher bundle name, code, data, and additional parameters. This module is applicable to scenarios where apps subscribe to and process common events and parse the data carried in the events.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Properties

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

| Name      | Type                | Read Only| Optional| Description                                                   |
| ---------- |-------------------- | ---- | ---- |  ------------------------------------------------------- |
| event      | string               | No  | No  | Name of the common event that is being received. The value can contain a maximum of 254 bytes. Excess content will be truncated. |
| bundleName | string               | No  | Yes  | Bundle name of the common event publisher. The default value is an empty string. The value can contain a maximum of 254 bytes. Excess content will be truncated. |
| code       | number               | No  | Yes  | Common event data received by the subscriber. The value of this field is the same as that of the **code** field in [CommonEventPublishData](./js-apis-inner-commonEvent-commonEventPublishData.md) when the publisher uses [commonEventManager.publish](./js-apis-commonEventManager.md#commoneventmanagerpublish-1) to publish a common event. The value ranges from –2147483648 to 2147483647. The default value is **0**.           |
| data       | string               | No  | Yes  | Common event data received by the subscriber. The data size cannot exceed 64 KB. The value of this field is the same as that of the **data** field in [CommonEventPublishData](./js-apis-inner-commonEvent-commonEventPublishData.md) when the publisher uses [commonEventManager.publish](./js-apis-commonEventManager.md#commoneventmanagerpublish-1) to publish a common event. |
| parameters | {[key: string]: any} | No  | Yes  | Additional information about the common event received by the subscriber. The value of this field is the same as that of the **data** field in [CommonEventPublishData](./js-apis-inner-commonEvent-commonEventPublishData.md) when the publisher uses [commonEventManager.publish](./js-apis-commonEventManager.md#commoneventmanagerpublish-1) to publish a common event.           |
