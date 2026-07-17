# TimeZoneType

时区类型。用于时区变更时，按照变更后的时区重新计算提醒的目标时间。

**起始版本：** 26.0.0

<!--Device-reminderAgentManager-export enum TimeZoneType--><!--Device-reminderAgentManager-export enum TimeZoneType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认。修改时区，提醒时间的计算方式与固定时区的行为相同；修改时间，提醒时间的计算方式与跟随系统时区的行为相同。建议根据业务场景，明确指定FIXED_TIME_ZONE或者SYSTEM_TIME_ZONE类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeZoneType-DEFAULT = 0--><!--Device-TimeZoneType-DEFAULT = 0-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## FIXED_TIME_ZONE

```TypeScript
FIXED_TIME_ZONE = 1
```

固定时区，用于抢票、开会等场景。例如：设备在东八区创建08:00的提醒，那么无论设备时区如何变化，都会在东八区的08:00提醒，即在东四区显示为04:00，修改系统时间不影响提醒目标时间。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeZoneType-FIXED_TIME_ZONE = 1--><!--Device-TimeZoneType-FIXED_TIME_ZONE = 1-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## SYSTEM_TIME_ZONE

```TypeScript
SYSTEM_TIME_ZONE = 2
```

跟随系统时区，用于早起闹钟、定点运动、睡觉等场景，例如：设备在东八区创建08:00的提醒，在东四区仍为08:00的提醒，修改系统时间不影响提醒目标时间。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeZoneType-SYSTEM_TIME_ZONE = 2--><!--Device-TimeZoneType-SYSTEM_TIME_ZONE = 2-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

