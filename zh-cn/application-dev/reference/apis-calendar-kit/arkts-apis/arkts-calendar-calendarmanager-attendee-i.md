# Attendee

会议日程参与者。

**起始版本：** 10

<!--Device-calendarManager-export interface Attendee--><!--Device-calendarManager-export interface Attendee-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## email

```TypeScript
email: string
```

会议日程参与者的邮箱，邮箱格式为“用户名@域名.后缀”，用户名部分只能包含字母、数字、下划线“_”、点 “.”、连字符 “-”。不能以点 “.” 开头或结尾。 不能连续出现两个点（即“..”）。长度建议为[0,5000]字符。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Attendee-email: string--><!--Device-Attendee-email: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## name

```TypeScript
name: string
```

会议日程参与者的姓名。长度建议为[0,5000]字符。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Attendee-name: string--><!--Device-Attendee-name: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## role

```TypeScript
role?: AttendeeRole
```

会议日程参与者的角色，不填时默认为空。

**类型：** AttendeeRole

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Attendee-role?: AttendeeRole--><!--Device-Attendee-role?: AttendeeRole-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## status

```TypeScript
status?: AttendeeStatus
```

会议日程参与者的状态，不填时默认为空。

**类型：** AttendeeStatus

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Attendee-status?: AttendeeStatus--><!--Device-Attendee-status?: AttendeeStatus-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## type

```TypeScript
type?: AttendeeType
```

会议日程参与者的类型，不填时默认为空。

**类型：** AttendeeType

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Attendee-type?: AttendeeType--><!--Device-Attendee-type?: AttendeeType-End-->

**系统能力：** SystemCapability.Applications.CalendarData

