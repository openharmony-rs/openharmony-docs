# NotificationSortingMap (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:22:21.600Z pushedAt=2026-10-08T09:28:29.841Z -->

The **NotificationSortingMap** module provides APIs for defining the sorting information of active notifications in all subscribed notifications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## NotificationSortingMap

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name       | Type    | Read Only| Optional| Description                                      |
| ----------- | ------- | --- | ----- |------------------------------------------ |
| sortings    | Record<string, [NotificationSorting](js-apis-inner-notification-notificationSorting-sys.md)\> | Yes | No  | [Notification sorting](../../notification/notification-glossary.md#notification-sorting) information.                                   |
| sortedHashCode | Array<string\> | Yes| No | Hash codes for notification sorting.|
