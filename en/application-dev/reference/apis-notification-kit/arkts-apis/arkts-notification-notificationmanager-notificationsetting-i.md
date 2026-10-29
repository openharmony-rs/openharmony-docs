# NotificationSetting

```TypeScript
export interface NotificationSetting
```

Defines the setting status of the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode) switch.

**Since:** 20

<!--Device-notificationManager-export interface NotificationSetting--><!--Device-notificationManager-export interface NotificationSetting-End-->

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## badgeNumberEnabled

```TypeScript
badgeNumberEnabled?: boolean
```

Whether to enable the numeric display of the [notification badge](../../../notification/notification-glossary.md#notification-badge).

- **true**: enabled.  
- **false**: disabled.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSetting-badgeNumberEnabled?: boolean--><!--Device-NotificationSetting-badgeNumberEnabled?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## bannerEnabled

```TypeScript
bannerEnabled?: boolean
```

Whether to enable the banner notification.

- **true**: enable.  
- **false**: disable.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSetting-bannerEnabled?: boolean--><!--Device-NotificationSetting-bannerEnabled?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## lockScreenEnabled

```TypeScript
lockScreenEnabled?: boolean
```

Whether to enable the lock screen notification.

- **true**: enable.  
- **false**: disable.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSetting-lockScreenEnabled?: boolean--><!--Device-NotificationSetting-lockScreenEnabled?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## notificationEnabled

```TypeScript
notificationEnabled?: boolean
```

Whether to enable the application notification.

- **true**: enable.  
- **false**: disable.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSetting-notificationEnabled?: boolean--><!--Device-NotificationSetting-notificationEnabled?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## soundEnabled

```TypeScript
soundEnabled: boolean
```

Whether to enable the sound.

- **true**: enable.  
- **false**: disable.

**Type:** boolean

**Since:** 20

<!--Device-NotificationSetting-soundEnabled: boolean--><!--Device-NotificationSetting-soundEnabled: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## vibrationEnabled

```TypeScript
vibrationEnabled: boolean
```

Whether to enable vibration.

- **true**: enable.  
- **false**: disable.

**Type:** boolean

**Since:** 20

<!--Device-NotificationSetting-vibrationEnabled: boolean--><!--Device-NotificationSetting-vibrationEnabled: boolean-End-->

**System capability:** SystemCapability.Notification.Notification
