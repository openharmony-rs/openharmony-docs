# LocalDateTime

用于日历类提醒设置时指定时间信息。

**起始版本：** 23

<!--Device-reminderAgentManager-interface LocalDateTime--><!--Device-reminderAgentManager-interface LocalDateTime-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## day

```TypeScript
day: int
```

日，取值范围是[1, 31]。

**类型：** int

**起始版本：** 23

<!--Device-LocalDateTime-day: int--><!--Device-LocalDateTime-day: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## hour

```TypeScript
hour: int
```

时，取值范围是[0, 23]。

**类型：** int

**起始版本：** 23

<!--Device-LocalDateTime-hour: int--><!--Device-LocalDateTime-hour: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## minute

```TypeScript
minute: int
```

分，取值范围是[0, 59]。

**类型：** int

**起始版本：** 23

<!--Device-LocalDateTime-minute: int--><!--Device-LocalDateTime-minute: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## month

```TypeScript
month: int
```

月，取值范围是[1, 12]。

**类型：** int

**起始版本：** 23

<!--Device-LocalDateTime-month: int--><!--Device-LocalDateTime-month: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## second

```TypeScript
second?: int
```

秒，取值范围是[0, 59]。

**类型：** int

**起始版本：** 23

<!--Device-LocalDateTime-second?: int--><!--Device-LocalDateTime-second?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## year

```TypeScript
year: int
```

年

**类型：** int

**起始版本：** 23

<!--Device-LocalDateTime-year: int--><!--Device-LocalDateTime-year: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

