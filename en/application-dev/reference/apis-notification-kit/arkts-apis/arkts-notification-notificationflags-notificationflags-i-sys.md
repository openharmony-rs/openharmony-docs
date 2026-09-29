# NotificationFlags

```TypeScript
export interface NotificationFlags
```

Defines the notification flags.

**Since:** 8

<!--Device-unnamed-export interface NotificationFlags--><!--Device-unnamed-export interface NotificationFlags-End-->

**System capability:** SystemCapability.Notification.Notification

## reminderFlags

```TypeScript
readonly reminderFlags?: number
```

Settings of the input information reminder features.

- Bit 0: sound alert. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 1: locking the screen. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 2: banner. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 3: turning on the screen. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 4: vibration. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 5: notification icon in the status bar. The value **0** means to enable the feature, and **1** means the  
opposite.

**Type:** number

**Since:** 11

<!--Device-NotificationFlags-readonly reminderFlags?: long--><!--Device-NotificationFlags-readonly reminderFlags?: long-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
