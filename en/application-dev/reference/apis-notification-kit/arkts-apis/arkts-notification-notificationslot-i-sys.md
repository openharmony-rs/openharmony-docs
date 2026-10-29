# NotificationSlot (System API)

```TypeScript
export interface NotificationSlot
```

Describes the [notification slot](../../../notification/notification-glossary.md#notification-slot). Different notification slots have different [notification reminder modes](../../../notification/notification-glossary.md#notification-reminder-mode).

**Since:** 7

<!--Device-unnamed-export interface NotificationSlot--><!--Device-unnamed-export interface NotificationSlot-End-->

**System capability:** SystemCapability.Notification.Notification

## authorizedStatus

```TypeScript
readonly authorizedStatus?: number
```

Authorization status.

- **0**: means the feature is authorized.  
- **1**: means the feature is to be authorized.

**Type:** number

**Since:** 12

<!--Device-NotificationSlot-readonly authorizedStatus?: int--><!--Device-NotificationSlot-readonly authorizedStatus?: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## reminderMode

```TypeScript
readonly reminderMode?: number
```

Reminder mode of the notification.

- Bit 0: sound alert. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 1: locking the screen. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 2: banner. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 3: turning on the screen. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 4: vibration. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 5: notification icon in the status bar. The value **0** means the feature is disabled, and **1** means  
enabled.

**Type:** number

**Since:** 11

<!--Device-NotificationSlot-readonly reminderMode?: int--><!--Device-NotificationSlot-readonly reminderMode?: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
