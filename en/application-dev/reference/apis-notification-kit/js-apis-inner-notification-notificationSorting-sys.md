# NotificationSorting (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4faed534b39ef26ef8f9b647802a53e9f8d2b792 translatedAt=2026-10-09T10:12:38.085Z pushedAt=2026-10-12T08:05:06.647Z -->

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
| ranking     | number                                                             | Yes | No | Notification level. If not set, the default value is determined by the type of the [notification slot](../../notification/notification-glossary.md#notification-slot). |
| hashCode    | string                                                             | Yes| No| Unique ID of the notification.               |
