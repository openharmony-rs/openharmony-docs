# NotificationFlags (System API)

```TypeScript
export interface NotificationFlags
```

Describes the [notification flags](../../../notification/notification-glossary.md#notification-flags). An application can use `NotificationFlags` to reduce the notification reminder methods as needed.

**Since:** 8

<!--Device-unnamed-export interface NotificationFlags--><!--Device-unnamed-export interface NotificationFlags-End-->

**System capability:** SystemCapability.Notification.Notification

## reminderFlags

```TypeScript
readonly reminderFlags?: number
```

Settings of the input information reminder features.

- Bit 0: sound alert. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 1: locking the screen. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 2: banner. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 3: turning on the screen. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 4: vibration. The value **0** means the feature is disabled, and **1** means enabled.  
- Bit 5: notification icon in the status bar. The value **0** means the feature is disabled, and **1** means  
enabled.

**Type:** number

**Since:** 11

<!--Device-NotificationFlags-readonly reminderFlags?: long--><!--Device-NotificationFlags-readonly reminderFlags?: long-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
