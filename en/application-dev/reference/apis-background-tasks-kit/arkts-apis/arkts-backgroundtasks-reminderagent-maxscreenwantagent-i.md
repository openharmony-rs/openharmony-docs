# MaxScreenWantAgent

Provides the information about the target package and ability to start automatically when the reminder is displayed in full-screen mode. This API is reserved.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [MaxScreenWantAgent](arkts-backgroundtasks-reminderagentmanager-maxscreenwantagent-i.md)

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## abilityName

```TypeScript
abilityName: string
```

Name of the ability that is automatically started when the reminder arrives and the device is not in use.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** abilityName

**System capability:** SystemCapability.Notification.ReminderAgent

## pkgName

```TypeScript
pkgName: string
```

Name of the HAP that is automatically started when the reminder arrives and the device is not in use.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** pkgName

**System capability:** SystemCapability.Notification.ReminderAgent
