# NotificationExtensionContent
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:36:08.135Z pushedAt=2026-06-30T10:57:36.994Z -->

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