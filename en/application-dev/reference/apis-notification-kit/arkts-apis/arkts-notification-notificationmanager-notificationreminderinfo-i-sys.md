# NotificationReminderInfo (System API)

```TypeScript
export interface NotificationReminderInfo
```

Describes the information about the application reminder.

**Since:** 21

<!--Device-notificationManager-export interface NotificationReminderInfo--><!--Device-notificationManager-export interface NotificationReminderInfo-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundle

```TypeScript
bundle: BundleOption
```

Bundle information of the application.

**Type:** [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md)

**Since:** 21

<!--Device-NotificationReminderInfo-bundle: BundleOption--><!--Device-NotificationReminderInfo-bundle: BundleOption-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## reminderFlags

```TypeScript
reminderFlags: number
```

Flag bits of the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode).

- **bit0**: ringtone. **0** indicates disabled, and **1** indicates enabled.  
- **bit1**: lock screen. **0** indicates disabled, and **1** indicates enabled.  
- **bit2**: banner. **0** indicates disabled, and **1** indicates enabled.  
- **bit3**: screen on. **0** indicates disabled, and **1** indicates enabled.  
- **bit4**: vibration. **0** indicates disabled, and **1** indicates enabled.  
- **bit5**: status bar notification icon. **0** indicates disabled, and **1** indicates enabled.

**Type:** number

**Since:** 21

<!--Device-NotificationReminderInfo-reminderFlags: long--><!--Device-NotificationReminderInfo-reminderFlags: long-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## silentReminderEnabled

```TypeScript
silentReminderEnabled: boolean
```

Whether the [silent reminder](../../../notification/notification-glossary.md#silent-reminder) switch is enabled (**true**: enabled, **false**: disabled).

**Type:** boolean

**Since:** 21

<!--Device-NotificationReminderInfo-silentReminderEnabled: boolean--><!--Device-NotificationReminderInfo-silentReminderEnabled: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
