# NotificationTemplate

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:37:09.948Z pushedAt=2026-06-30T10:57:37.010Z -->

This module defines the notification template, which is used to specify the template type for a notification.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The predefined system templates are supported. You only need to provide the template name and related data for the system to automatically render the notification style that complies with the specifications.
> Application scenario: Currently, only the upload and download scenarios are supported.

## NotificationTemplate

**System capability**: SystemCapability.Notification.Notification

| Name| Type                  | Read Only| Optional| Description      |
| ---- | ---------------------- | ---- | ----|----------- |
| name | string | No | No | Template name. Currently, only the progress bar notification template indicating download progress is supported, with the value **downloadTemplate**. The string length cannot exceed 202 bytes; any excess will be truncated. It cannot be an empty string. |
| data | Record<string, Object> | No | No | Template data.<br> - **title**: Download title. Mandatory field, with the value being a string type.<br> - **fileName**: Download file name. Mandatory field, with the value being a string type.<br> - **progressValue**: Download progress, with the value being a numeric type. The recommended value range is 0 to 100, representing the percentage progress. When **progressValue** is less than or equal to 0, the progress is 0; when it is greater than or equal to 100, the progress ring disappears, indicating that the download is complete. |