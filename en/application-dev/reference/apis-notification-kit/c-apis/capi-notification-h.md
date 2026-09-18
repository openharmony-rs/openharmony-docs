# notification.h

## Overview

Defines APIs for notification services.

**Library**: libohnotification.so

**System capability**: SystemCapability.Notification.Notification

**Since**: 13

**Related module**: [NOTIFICATION](capi-notification.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [bool OH_Notification_IsNotificationEnabled(void)](#oh_notification_isnotificationenabled) | Checks whether the notification of the specified application is enabled. |

## Function description

### OH_Notification_IsNotificationEnabled()

```c
bool OH_Notification_IsNotificationEnabled(void)
```

**Description**

Checks whether the notification of the specified application is enabled.

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| bool | true  - Notification is enabled for the specified application.          false - Notification is not enabled for the specified application. |


