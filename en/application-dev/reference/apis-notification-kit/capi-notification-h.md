# notification.h
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4faed534b39ef26ef8f9b647802a53e9f8d2b792 translatedAt=2026-10-09T10:03:11.249Z pushedAt=2026-10-12T08:05:06.625Z -->

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
| bool | **true** - Notification is enabled for the specified application.<br>         **false** - Notification is not enabled for the specified application.|


