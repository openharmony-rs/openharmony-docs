# EnabledPriorityNotificationCallbackData (System API)

```TypeScript
export interface EnabledPriorityNotificationCallbackData
```

Returns the changes of the enabled state of the notification priority.

**Since:** 23

<!--Device-unnamed-export interface EnabledPriorityNotificationCallbackData--><!--Device-unnamed-export interface EnabledPriorityNotificationCallbackData-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## enable

```TypeScript
readonly enable: boolean
```

Priority enabled state of all notifications.

- **true**: Allow setting as [priority notification](../../../notification/notification-glossary.md#priority-notification).  
- **false**: Prohibit setting as priority notification.

**Type:** boolean

**Since:** 23

<!--Device-EnabledPriorityNotificationCallbackData-readonly enable: boolean--><!--Device-EnabledPriorityNotificationCallbackData-readonly enable: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
