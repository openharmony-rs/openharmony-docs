# RecurrenceRule

重复日程重复规则。

**起始版本：** 10

<!--Device-calendarManager-export interface RecurrenceRule--><!--Device-calendarManager-export interface RecurrenceRule-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## count

```TypeScript
count?: number
```

重复日程的重复次数，取值为非负整数，浮点数输入将向下取整，不填时默认为0，表示不会限定重复次数，会一直重复。取值为负时，效果等同于取值为0。当count与interval和expire同时设置时，以先到达的限制条件及效果为准。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-count?: number--><!--Device-RecurrenceRule-count?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## daysOfMonth

```TypeScript
daysOfMonth?: number[]
```

按照一个月第几天重复。不填时，默认为空，表示没有一个月第几天重复的规则。范围为[1, 31]，[1, 31]对应1到31号，其他值为无效值，与空值效果相同。若当月没有29号、30号或31号，则29、30、31也为无效值。该字段数组与其相关字段数组为一一对应关系，如monthsOfYear为[1, 2, 3]，daysOfMonth为[1, 2, 3]，则表示按照一月一号，二月二号，三月三号进行重复。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-daysOfMonth?: number[]--><!--Device-RecurrenceRule-daysOfMonth?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## daysOfWeek

```TypeScript
daysOfWeek?: number[]
```

按照一周第几天重复。不填时，默认为空，表示没有一周第几天重复的规则。范围为[1, 7]，对应周一到周日，其他值为无效值，与空值效果相同。该字段数组与其相关字段数组为一一对应关系，如weeksOfMonth为[1, 2, 3]，daysOfWeek为[1, 2, 3]，则表示按照每月的第一周的周一，第二周的周二，第三周的周三进行重复。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-daysOfWeek?: number[]--><!--Device-RecurrenceRule-daysOfWeek?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## daysOfYear

```TypeScript
daysOfYear?: number[]
```

按照一年第几天重复。不填时，默认为空，表示没有一年第几天重复的规则。范围为[1, 366]，[1, 366]表示一年的1到366天，其他值为无效值，与空值效果相同。若当年没有366天，366也为无效值。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-daysOfYear?: number[]--><!--Device-RecurrenceRule-daysOfYear?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## excludedDates

```TypeScript
excludedDates?: number[]
```

重复日程的排除日期，参数取值为时间戳格式，不填时，默认为空，表示没有排除的日期，0或负数为无效值，与空值效果相同。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-excludedDates?: number[]--><!--Device-RecurrenceRule-excludedDates?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## expire

```TypeScript
expire?: number
```

重复周期截止日。格式为13位时间戳，不填时则日程无截止日期。

当expire与count和interval同时设置时，以先到达的限制条件及效果为准。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-expire?: number--><!--Device-RecurrenceRule-expire?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## interval

```TypeScript
interval?: number
```

重复日程的重复周期，取值为非负整数，浮点数输入将向下取整。不填时默认为0，当取值为0、1或负值时，表示日程每天/周/月/年重复一次。当interval与count和expire同时设置时，以先到达的限制条件及效果为准。此属性与recurrenceFrequency重复规则相关，不同的重复规则下，表示的重复周期不同，以interval取2为例，分为以下几种情况：每天重复时：表示日程每两天重复一次。每周重复时：表示日程每两周重复一次。每月重复时：表示日程每两月重复一次。每年重复时：表示日程每两年重复一次。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-interval?: number--><!--Device-RecurrenceRule-interval?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## monthsOfYear

```TypeScript
monthsOfYear?: number[]
```

按照一年中第几个月重复。不填时，默认为空，表示没有一年第几个月重复的规则。范围为[1, 12]，[1, 12]为每年的1到12月，其他值为无效值，与空值效果相同。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-monthsOfYear?: number[]--><!--Device-RecurrenceRule-monthsOfYear?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## recurrenceFrequency

```TypeScript
recurrenceFrequency: RecurrenceFrequency
```

日程重复规则类型。

**类型：** RecurrenceFrequency

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-recurrenceFrequency: RecurrenceFrequency--><!--Device-RecurrenceRule-recurrenceFrequency: RecurrenceFrequency-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## weeksOfMonth

```TypeScript
weeksOfMonth?: number[]
```

按照一个月第几周重复。不填时，默认为空，表示没有一个月第几周重复的规则。范围为[1, 5]，[1, 5]为每月的第1到第5周，其他值为无效值，与空值效果相同。若当月没有第五周，5也为无效值。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-weeksOfMonth?: number[]--><!--Device-RecurrenceRule-weeksOfMonth?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## weeksOfYear

```TypeScript
weeksOfYear?: number[]
```

按照一年中第几周重复。不填时，默认为空，表示没有一年第几周重复的规则。范围为[1, 53]，[1, 53]为每年的第1到第53周，其他值为无效值，与空值效果相同。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RecurrenceRule-weeksOfYear?: number[]--><!--Device-RecurrenceRule-weeksOfYear?: number[]-End-->

**系统能力：** SystemCapability.Applications.CalendarData

