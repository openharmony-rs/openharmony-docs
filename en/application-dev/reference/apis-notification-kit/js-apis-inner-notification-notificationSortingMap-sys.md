# NotificationSortingMap (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=c840b9a8f02f445d6c590b1f99e03469a633d5eb translatedAt=2026-11-13T02:20:25.192Z pushedAt=2026-11-13T09:44:30.413Z nl=1 -->

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
| sortings    | Record<string, [NotificationSorting](js-apis-inner-notification-notificationSorting-sys.md)\> | Yes | No  | Notification sorting information.                                   |
| sortedHashCode | Array<string\> | Yes| No | Hash codes for notification sorting.|
