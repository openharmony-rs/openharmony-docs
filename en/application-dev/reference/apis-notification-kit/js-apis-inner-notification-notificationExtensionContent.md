# NotificationExtensionContent
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4faed534b39ef26ef8f9b647802a53e9f8d2b792 translatedAt=2026-10-09T10:05:26.664Z pushedAt=2026-10-12T08:05:06.633Z -->

The **NotificationExtensionContent** module describes the notification extension content.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationExtensionContent

**System capability**: SystemCapability.Notification.Notification

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| title | string | No | No | Notification title.<br>It cannot be an empty string. The size cannot exceed 1024 bytes, and any excess will be truncated. |
| text | string | No | No | Notification body content.<br>It cannot be an empty string. The size cannot exceed 3072 bytes, and any excess will be truncated. |