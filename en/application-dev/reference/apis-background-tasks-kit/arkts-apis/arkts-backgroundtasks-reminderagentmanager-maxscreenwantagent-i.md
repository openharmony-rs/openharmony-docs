# MaxScreenWantAgent

Describes the information about the ability that is started automatically and displayed in full-screen mode when a reminder is displayed in the notification center. This API is reserved.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## abilityName

```TypeScript
abilityName: string
```

Name of the target ability. (If the device is in use, only a notification banner is displayed.)

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## pkgName

```TypeScript
pkgName: string
```

Name of the target package. (If the device is in use, only a notification banner is displayed.)

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent
