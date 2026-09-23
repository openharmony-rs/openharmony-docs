# NotificationSortingMap (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4bb0b56d7d67b2ab3ff0955bce487aba3399fade translatedAt=2026-09-22T02:13:41.855Z pushedAt=2026-09-22T08:29:58.369Z -->

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
<!--no_check-->