# ReminderRequestTimer

ReminderRequestTimer extends ReminderRequest

Defines a reminder for a scheduled timer.

**Inheritance/Implementation:** ReminderRequestTimer extends [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## repeatCount

```TypeScript
repeatCount?: number
```

Number of repetitions. The default value is **0**, indicating infinite repetitions. This parameter must be used together with **repeatInterval**.

The value range is [0, +∞). If the value is out of range, error code 401 is returned.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## repeatInterval

```TypeScript
repeatInterval?: number
```

Repeat interval. There is no default value. If no value is set, there is no repeat interval. This parameter must be used together with **repeatCount**.

The value range is [86400, +∞), in seconds. If the value is out of range, error code 401 is returned.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## triggerTimeInSeconds

```TypeScript
triggerTimeInSeconds: number
```

Number of seconds in the countdown timer.

Unit: s

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent
