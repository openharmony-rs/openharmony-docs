# NotificationSlot

The **NotificationSlot** module provides APIs for defining the notification slots. The notification reminder modes vary according to notification slots.

**Since:** 7

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

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## reminderMode

```TypeScript
readonly reminderMode?: number
```

Reminder mode of the notification.

- Bit 0: sound alert. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 1: locking the screen. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 2: banner. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 3: turning on the screen. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 4: vibration. The value **0** means to enable the feature, and **1** means the opposite.  
- Bit 5: notification icon in the status bar. The value **0** means to enable the feature, and **1** means the  
opposite.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
