# ActionButton

Describes the button displayed for a reminder.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## dataShareUpdate

```TypeScript
dataShareUpdate?: DataShareUpdate
```

The application database will be updated after a click on the button.

**Type:** [DataShareUpdate](arkts-backgroundtasks-reminderagentmanager-datashareupdate-i-sys.md)

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

Information about the ability that is displayed after the button is clicked.

**Type:** [WantAgent](arkts-backgroundtasks-reminderagentmanager-wantagent-i.md)

**Since:** 10

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.
