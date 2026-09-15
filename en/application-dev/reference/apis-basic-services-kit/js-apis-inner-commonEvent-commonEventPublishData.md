# CommonEventPublishData
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=227499a15769ff89e238d0afb653f1633e59b877 translatedAt=2026-07-21T08:26:18.275Z pushedAt=2026-07-22T06:40:31.858Z -->

This module encapsulates the data and attributes carried when a common event is published, including the event data (code/data), subscriber permissions, subscriber bundle name, whether the event is ordered or sticky, and additional parameters. It allows the publisher to precisely control the common event recipients, event delivery sequence, and sticky feature. This module is applicable to scenarios where the recipients need to be specified, custom event data needs to be transferred, and ordered/sticky common events need to be implemented.

> **NOTE**
>
> - This module supports both ArkTS-Dyn and ArkTS-Sta.
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> If there is no restriction, any app can subscribe to common events and read the information carried by the event. In this case, sensitive information should not be carried in common events. The **subscriberPermissions** and **bundleName** parameters of this module can be used to restrict the receiving scope of common events.

## Properties

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn Since:** 7

**ArkTS-Sta Since:** 23

| Name                 | Type                | Read Only| Optional| Description                        |
| --------------------- | -------------------- | ---- | ---- | ---------------------------- |
| bundleName            | string               | No  | Yes  | Bundle name of the subscriber, which is used to specify the subscriber to whom the common event is published. This parameter is left empty by default. When this parameter is empty, the bundle name of the subscriber is not specified, and all subscribers can receive the common event.<br>**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11. |
| code                  | ArkTS-Dyn: number<br/>ArkTS-Sta: int               | No  | Yes  | Common event data transferred by the publisher. The default value is **0**.<br>**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.       |
| data                  | string               | No  | Yes  | Common event data transferred by the publisher. The value is a string and cannot exceed 64 KB. If the value exceeds the limit, the event fails to be published. This parameter is left empty by default.<br>**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11. |
| subscriberPermissions | Array\<string>       | No  | Yes  | Subscriber permissions. Only subscribers with the specified permissions can receive the common event. This parameter is left empty by default. When this parameter is empty, the subscriber permissions are not specified, and all subscribers can receive the common event.<br>**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.             |
| isOrdered             | boolean              | No  | Yes  | Whether the common event is an ordered one. The default value is **false**.<br/> - **true**: This event is an ordered common event. Based on the priority set by the subscriber, the common event is preferentially sent to the subscriber with a higher priority. After the subscriber successfully receives the event, the common event is sent to the subscriber with a lower priority. Subscribers with the same priority receive common events in a random order.<br/> - **false**: This event is an unordered common event. Whether subscribers receive the event is not considered, and the common event which subscribers receive may not comply with the subscription sequence.           |
| isSticky              | boolean              | No  | Yes  | Whether the common event is a sticky one. The default value is **false**.<br/> - **true**: This event is a sticky common event, which allows subscribers to receive common events that have been sent before subscription.<br/> - **false**: This event is not a sticky common event, which allows subscribers to receive common events sent after subscription.<br>Only system applications and system services are allowed to send sticky events.<br>**Required permissions:** [ohos.permission.COMMONEVENT_STICKY](../../security/AccessToken/permissions-for-all.md#ohospermissioncommonevent_sticky) |
| parameters            | ArkTS-Dyn: {[key: string]: any}<br/>ArkTS-Sta: Record\<string, RecordData\> | No  | Yes  | Additional information of the common event transferred by the publisher, which carries custom parameters in key-value pairs. This parameter is left empty by default.<br>**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.       |