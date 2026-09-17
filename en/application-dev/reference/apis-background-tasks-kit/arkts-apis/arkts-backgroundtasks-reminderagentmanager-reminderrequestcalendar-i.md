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

## dateTime

```TypeScript
dateTime: LocalDateTime
```

Reminder time.

**Type:** [LocalDateTime](arkts-backgroundtasks-reminderagentmanager-localdatetime-i.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## daysOfWeek

```TypeScript
daysOfWeek?: Array<number>
```

Days of a week when the reminder repeats. The value ranges from 1 to 7, corresponding to the data from Monday to Sunday. This parameter is left empty by default.

**Type:** Array&lt;number&gt;

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

## endDateTime

```TypeScript
endDateTime?: LocalDateTime
```

End time of the reminder.

**Type:** [LocalDateTime](arkts-backgroundtasks-reminderagentmanager-localdatetime-i.md)

**Since:** 12

**System capability:** SystemCapability.Notification.ReminderAgent

## repeatDays

```TypeScript
repeatDays?: Array<number>
```

Day in which the reminder repeats. The value range is [1, 31]. This parameter is left empty by default. This parameter must be used together with **repeatMonths**.

**Type:** Array&lt;number&gt;

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## repeatMonths

```TypeScript
repeatMonths?: Array<number>
```

Month in which the reminder repeats. The value range is [1, 12]. This parameter is left empty by default. This parameter must be used together with **repeatDays**.

**Type:** Array&lt;number&gt;

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent
