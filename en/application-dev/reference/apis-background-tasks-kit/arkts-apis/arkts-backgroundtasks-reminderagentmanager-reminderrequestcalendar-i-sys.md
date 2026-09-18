# ReminderRequestCalendar

ReminderRequestCalendar extends ReminderRequest

Defines a reminder for a calendar event.

**Inheritance/Implementation:** ReminderRequestCalendar extends [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## rruleWantAgent

```TypeScript
rruleWantAgent?: WantAgent
```

Custom reminder, which specifies the ServiceExtensionAbility to start.

**Type:** [WantAgent](arkts-backgroundtasks-reminderagentmanager-wantagent-i.md)

**Since:** 12

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.
