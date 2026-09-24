# NotificationSorting (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4bb0b56d7d67b2ab3ff0955bce487aba3399fade translatedAt=2026-09-22T02:13:31.145Z pushedAt=2026-09-22T08:29:58.368Z -->

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
<!--no_check-->