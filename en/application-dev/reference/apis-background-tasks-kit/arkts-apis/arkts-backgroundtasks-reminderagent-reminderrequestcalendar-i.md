# ReminderRequestCalendar

Defines a reminder for a calendar event.

**Inheritance/Implementation:** ReminderRequestCalendar extends [ReminderRequest](arkts-backgroundtasks-reminderagent-reminderrequest-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ReminderRequestCalendar](arkts-backgroundtasks-reminderagentmanager-reminderrequestcalendar-i.md)

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## dateTime

```TypeScript
dateTime: LocalDateTime
```

Reminder time.

**Type:** [LocalDateTime](arkts-backgroundtasks-reminderagent-localdatetime-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** dateTime

**System capability:** SystemCapability.Notification.ReminderAgent

## repeatDays

```TypeScript
repeatDays?: Array<number>
```

Date on which the reminder repeats.

**Type:** Array&lt;number&gt;

**Since:** 7

**Deprecated since:** 9

**Substitutes:** repeatDays

**System capability:** SystemCapability.Notification.ReminderAgent

## repeatMonths

```TypeScript
repeatMonths?: Array<number>
```

Month in which the reminder repeats.

**Type:** Array&lt;number&gt;

**Since:** 7

**Deprecated since:** 9

**Substitutes:** repeatMonths

**System capability:** SystemCapability.Notification.ReminderAgent
