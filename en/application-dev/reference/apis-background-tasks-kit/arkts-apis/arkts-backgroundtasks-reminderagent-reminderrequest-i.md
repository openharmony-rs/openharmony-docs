# ReminderRequest

Defines the reminder to publish.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## actionButton

```TypeScript
actionButton?: [ActionButton?, ActionButton?]
```

Button displayed in the reminder notification. (The parameter is optional. Up to two buttons are supported.)

**Type:** [ActionButton?, ActionButton?]

**Since:** 7

**Deprecated since:** 9

**Substitutes:** actionButton

**System capability:** SystemCapability.Notification.ReminderAgent

## content

```TypeScript
content?: string
```

Reminder content.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** content

**System capability:** SystemCapability.Notification.ReminderAgent

## expiredContent

```TypeScript
expiredContent?: string
```

Content to be displayed after the reminder expires.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** expiredContent

**System capability:** SystemCapability.Notification.ReminderAgent

## maxScreenWantAgent

```TypeScript
maxScreenWantAgent?: MaxScreenWantAgent
```

Information about the ability that is automatically started when the reminder arrives. If the device is in use, a notification will be displayed.

**Type:** [MaxScreenWantAgent](arkts-backgroundtasks-reminderagent-maxscreenwantagent-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** maxScreenWantAgent

**System capability:** SystemCapability.Notification.ReminderAgent

## notificationId

```TypeScript
notificationId?: number
```

Notification ID used by the reminder. If there are reminders with the same notification ID, the later one will overwrite the earlier one.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** notificationId

**System capability:** SystemCapability.Notification.ReminderAgent

## reminderType

```TypeScript
reminderType: ReminderType
```

Type of the reminder.

**Type:** [ReminderType](arkts-backgroundtasks-reminderagent-remindertype-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** reminderType

**System capability:** SystemCapability.Notification.ReminderAgent

## ringDuration

```TypeScript
ringDuration?: number
```

Ringing duration, in seconds. The default value is **1**. Unit: s.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** ringDuration

**System capability:** SystemCapability.Notification.ReminderAgent

## slotType

```TypeScript
slotType?: notification.SlotType
```

Type of the slot used by the reminder.

**Type:** [notification.SlotType](../../apis-notification-kit/arkts-apis/arkts-notification-notification-slottype-depr-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** slotType

**System capability:** SystemCapability.Notification.ReminderAgent

## snoozeContent

```TypeScript
snoozeContent?: string
```

Content to be displayed when the reminder is snoozing.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** snoozeContent

**System capability:** SystemCapability.Notification.ReminderAgent

## snoozeTimes

```TypeScript
snoozeTimes?: number
```

Number of reminder snooze times. The default value is **0**.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** snoozeTimes

**System capability:** SystemCapability.Notification.ReminderAgent

## timeInterval

```TypeScript
timeInterval?: number
```

Reminder snooze interval, in seconds. The default value is **0**. Unit: s.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** timeInterval

**System capability:** SystemCapability.Notification.ReminderAgent

## title

```TypeScript
title?: string
```

Reminder title.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** title

**System capability:** SystemCapability.Notification.ReminderAgent

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

Information about the ability that is redirected to when the notification is clicked.

**Type:** [WantAgent](arkts-backgroundtasks-reminderagent-wantagent-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** wantAgent

**System capability:** SystemCapability.Notification.ReminderAgent
