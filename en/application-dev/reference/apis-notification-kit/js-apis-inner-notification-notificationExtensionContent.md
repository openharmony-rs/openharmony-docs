# NotificationExtensionContent
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **NotificationExtensionContent** module describes the notification extension content.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationExtensionContent

**System capability**: SystemCapability.Notification.Notification

| Name| Type| Read-Only| Optional| Description| 
| -------- | -------- | -------- | -------- | -------- |
| title | string | No| No|Notification title. It cannot be empty or exceed 1024 bytes. Excess content will be truncated.|
| text | string | No| No|Notification content. It cannot be empty or exceed 3072 bytes. Excess content will be truncated.|
