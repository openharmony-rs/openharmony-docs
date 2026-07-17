# LocalDateTime

用于日历类提醒设置时指定时间信息。

**起始版本：** 9

<!--Device-reminderAgentManager-interface LocalDateTime--><!--Device-reminderAgentManager-interface LocalDateTime-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## day

```TypeScript
day: number
```

日，取值范围是[1, 31]。

**类型：** number

**起始版本：** 9

<!--Device-LocalDateTime-day: int--><!--Device-LocalDateTime-day: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## hour

```TypeScript
hour: number
```

时，取值范围是[0, 23]。

**类型：** number

**起始版本：** 9

<!--Device-LocalDateTime-hour: int--><!--Device-LocalDateTime-hour: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## minute

```TypeScript
minute: number
```

分，取值范围是[0, 59]。

**类型：** number

**起始版本：** 9

<!--Device-LocalDateTime-minute: int--><!--Device-LocalDateTime-minute: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## month

```TypeScript
month: number
```

月，取值范围是[1, 12]。

**类型：** number

**起始版本：** 9

<!--Device-LocalDateTime-month: int--><!--Device-LocalDateTime-month: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## second

```TypeScript
second?: number
```

秒，取值范围是[0, 59]。

**类型：** number

**起始版本：** 9

<!--Device-LocalDateTime-second?: int--><!--Device-LocalDateTime-second?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## year

```TypeScript
year: number
```

年

**类型：** number

**起始版本：** 9

<!--Device-LocalDateTime-year: int--><!--Device-LocalDateTime-year: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

