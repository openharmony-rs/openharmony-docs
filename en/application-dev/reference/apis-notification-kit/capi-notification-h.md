# notification.h
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=097d84c08b6dd34c7fea7675d84d753092b8a960 translatedAt=2026-10-28T11:23:35.483Z pushedAt=2026-10-28T12:15:40.118Z nl=1 -->

## Overview

Defines APIs for notification services.

**File to include**: <NotificationKit/notification.h>

**Library**: libohnotification.so

**System capability**: SystemCapability.Notification.Notification

**Since**: 13

**Related module**: [NOTIFICATION](capi-notification.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [bool OH_Notification_IsNotificationEnabled(void)](#oh_notification_isnotificationenabled) | Checks whether the notification of the specified application is enabled.|

## Function Description

### OH_Notification_IsNotificationEnabled()

```c
bool OH_Notification_IsNotificationEnabled(void)
```

**Description**

Checks whether the notification of the specified application is enabled.

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| bool | **true**  - The notification of the application is enabled.<br>         **false** - The notification of the application is not enabled, or the query operation failed (for example, the IPC request failed or the notification service is not running). |


