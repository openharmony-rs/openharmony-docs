# ActionButton

Describes the button displayed for a reminder.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## title

```TypeScript
title: string
```

Text on the button.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## titleResource

```TypeScript
titleResource?: string
```

Resource ID of the title. This parameter is used to read the title information after the system language is switched.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

## type

```TypeScript
type: ActionButtonType
```

Button type.

**Type:** [ActionButtonType](arkts-backgroundtasks-reminderagentmanager-actionbuttontype-e.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent
