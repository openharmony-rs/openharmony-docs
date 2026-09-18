# ReminderRequestAlarm

ReminderRequestAlarm extends ReminderRequest

Defines a reminder for an alarm.

**Inheritance/Implementation:** ReminderRequestAlarm extends [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## daysOfWeek

```TypeScript
daysOfWeek?: Array<number>
```

Days of a week when the reminder repeats. The value ranges from 1 to 7, corresponding to the data from Monday to Sunday. This parameter is left empty by default.

**Type:** Array&lt;number&gt;

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## hour

```TypeScript
hour: number
```

Hour portion of the reminder time. The value range is [0, 23].

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## minute

```TypeScript
minute: number
```

Minute portion of the reminder time. The value range is [0, 59].

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent
