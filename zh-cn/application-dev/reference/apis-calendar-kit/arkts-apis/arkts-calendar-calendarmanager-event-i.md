# Event

日程对象，包含日程标题、开始时间、结束时间等信息。

**起始版本：** 10

<!--Device-calendarManager-interface Event--><!--Device-calendarManager-interface Event-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## attendee

```TypeScript
attendee?: Attendee[]
```

会议日程参与者。不填时，默认为null。

**类型：** Attendee[]

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-attendee?: Attendee[]--><!--Device-Event-attendee?: Attendee[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## description

```TypeScript
description?: string
```

日程描述。长度建议为[0,5000]字符，不填时，默认为空字符串。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-description?: string--><!--Device-Event-description?: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## endTime

```TypeScript
endTime: number
```

日程结束时间，需要13位时间戳。全天日程时，该字段转换为传入日期24:00对应的时间戳。 *

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-endTime: number--><!--Device-Event-endTime: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## id

```TypeScript
id?: number
```

日程id。当调用[addEvent()](arkts-calendar-calendarmanager-calendar-i.md#addevent-1)、[addEvents()](arkts-calendar-calendarmanager-calendar-i.md#addevents-1)创建日程时，不填写此参数；当调用[deleteEvent()](arkts-calendar-calendarmanager-calendar-i.md#deleteevent-1)、[deleteEvents()](arkts-calendar-calendarmanager-calendar-i.md#deleteevents-1)删除日程时，日程id数组，日程id需为整数，传入其他非法入参会报错。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-id?: number--><!--Device-Event-id?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## identifier

```TypeScript
identifier?: string
```

写入方可指定日程唯一标识。长度建议为[0,5000]字符，不填时，默认为null。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Event-identifier?: string--><!--Device-Event-identifier?: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## instanceEndTime

```TypeScript
instanceEndTime?: number
```

日程实例结束时间，需要13位时间戳。当调用[addEvent()](arkts-calendar-calendarmanager-calendar-i.md#addevent-1)、[addEvents()](arkts-calendar-calendarmanager-calendar-i.md#addevents-1)创建日程时，不填写此参数。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Event-instanceEndTime?: number--><!--Device-Event-instanceEndTime?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## instanceStartTime

```TypeScript
instanceStartTime?: number
```

日程实例开始时间，需要13位时间戳。当调用[addEvent()](arkts-calendar-calendarmanager-calendar-i.md#addevent-1)、[addEvents()](arkts-calendar-calendarmanager-calendar-i.md#addevents-1)创建日程时，不填写此参数。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Event-instanceStartTime?: number--><!--Device-Event-instanceStartTime?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## isAllDay

```TypeScript
isAllDay?: boolean
```

是否为全天日程。当取值为true时，说明为全天日程；当取值为false时，说明不是全天日程，默认为非全天日程。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-isAllDay?: boolean--><!--Device-Event-isAllDay?: boolean-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## isLunar

```TypeScript
isLunar?: boolean
```

是否为农历日程。当取值为true时，说明为农历日程；当取值为false时，说明不是农历日程，默认为非农历日程。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Event-isLunar?: boolean--><!--Device-Event-isLunar?: boolean-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## location

```TypeScript
location?: Location
```

日程地点。不填时，默认为undefined。

**类型：** Location

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-location?: Location--><!--Device-Event-location?: Location-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## recurrenceRule

```TypeScript
recurrenceRule?: RecurrenceRule
```

日程重复规则，设置了此字段的日程为重复日程。不填时，默认为非重复日程。

**类型：** RecurrenceRule

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-recurrenceRule?: RecurrenceRule--><!--Device-Event-recurrenceRule?: RecurrenceRule-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## reminderTime

```TypeScript
reminderTime?: number[]
```

日程提醒时间，单位为分钟。填写x分钟，即距开始时间提前x分钟提醒，不填时，默认为不提醒。为负值时表示延期多长时间提醒。全天日程时此字段表示上午9:00前x分钟提醒，可取负值，负值表示上午9:00后多长时间提醒。

**类型：** number[]

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-reminderTime?: number[]--><!--Device-Event-reminderTime?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## service

```TypeScript
service?: EventService
```

<!--RP1-->日程服务。不填时，默认没有一键服务。暂不支持此功能。<!--RP1End-->

**类型：** EventService

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-service?: EventService--><!--Device-Event-service?: EventService-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## startTime

```TypeScript
startTime: number
```

日程开始时间，需要13位时间戳。全天日程时，该字段转换为传入日期00:00对应的时间戳。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-startTime: number--><!--Device-Event-startTime: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## timeZone

```TypeScript
timeZone?: string
```

日程时区。日程时区。长度建议为[0,5000]字符，不填或异常值时，默认为当前所在时区，当需要创建与当前不一样的时区时，可填入对应的时区。可通过[systemDateTime.getTimezone()](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-systemdatetime-gettimezone-f.md#gettimezone-1)获取当前系统时区。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-timeZone?: string--><!--Device-Event-timeZone?: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## title

```TypeScript
title?: string
```

日程标题。长度建议为[0,5000]字符，不填时，默认为空字符串。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-title?: string--><!--Device-Event-title?: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## type

```TypeScript
type: EventType
```

日程类型。

**类型：** EventType

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Event-type: EventType--><!--Device-Event-type: EventType-End-->

**系统能力：** SystemCapability.Applications.CalendarData

