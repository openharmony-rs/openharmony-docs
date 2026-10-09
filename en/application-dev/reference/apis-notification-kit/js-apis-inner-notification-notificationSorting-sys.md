# NotificationSorting (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:21:01.102Z pushedAt=2026-10-08T09:28:26.128Z -->

The **NotificationSorting** module provides APIs for defining the sorting information of active notifications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## NotificationSorting

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name     | Type             | Read-Only  | Optional| Description                    |
|-----------| ---------------- | -------|----- |-------------------------|
| slot        | [NotificationSlot](js-apis-inner-notification-notificationSlot.md) | Yes| No| Notification slot type.                 |
| ranking     | number                                                             | Yes | No | Notification level. If not set, the default value is determined by the [notification slot](../../notification/notification-glossary.md#notification-slot) type. |
| hashCode    | string                                                             | Yes| No| Unique ID of the notification.               |
