# LocalDateTime

```TypeScript
interface LocalDateTime
```

Defines the time information for a calendar reminder.

**Since:** 9

<!--Device-reminderAgentManager-interface LocalDateTime--><!--Device-reminderAgentManager-interface LocalDateTime-End-->

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## day

```TypeScript
day: number
```

Day. The value ranges from 1 to 31.

**Type:** number

**Since:** 9

<!--Device-LocalDateTime-day: int--><!--Device-LocalDateTime-day: int-End-->

**System capability:** SystemCapability.Notification.ReminderAgent

## hour

```TypeScript
hour: number
```

Hour. The value ranges from 0 to 23.

**Type:** number

**Since:** 9

<!--Device-LocalDateTime-hour: int--><!--Device-LocalDateTime-hour: int-End-->

**System capability:** SystemCapability.Notification.ReminderAgent

## minute

```TypeScript
minute: number
```

Minute. The value ranges from 0 to 59.

**Type:** number

**Since:** 9

<!--Device-LocalDateTime-minute: int--><!--Device-LocalDateTime-minute: int-End-->

**System capability:** SystemCapability.Notification.ReminderAgent

## month

```TypeScript
month: number
```

Month. The value ranges from 1 to 12.

**Type:** number

**Since:** 9

<!--Device-LocalDateTime-month: int--><!--Device-LocalDateTime-month: int-End-->

**System capability:** SystemCapability.Notification.ReminderAgent

## second

```TypeScript
second?: number
```

Second. The value ranges from 0 to 59.

**Type:** number

**Since:** 9

<!--Device-LocalDateTime-second?: int--><!--Device-LocalDateTime-second?: int-End-->

**System capability:** SystemCapability.Notification.ReminderAgent

## year

```TypeScript
year: number
```

Year.

**Type:** number

**Since:** 9

<!--Device-LocalDateTime-year: int--><!--Device-LocalDateTime-year: int-End-->

**System capability:** SystemCapability.Notification.ReminderAgent
