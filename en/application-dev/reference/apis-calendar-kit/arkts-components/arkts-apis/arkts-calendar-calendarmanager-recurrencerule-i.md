# RecurrenceRule

Describes the recurrence rule of a recurring event.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## count

```TypeScript
count?: number
```

Number of times that an event recurs. The value is a non-negative integer. If the value is a floating point number, it is rounded down. If this parameter is left empty, the default value is 0, indicating that the number of recurrence times is not limited and the event will continuously recur. If the value is negative, the effect is the same as that of 0. If count, interval, and expire are set at the same time, the restriction that is reached first prevails.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## daysOfMonth

```TypeScript
daysOfMonth?: number[]
```

Repeats by day of a month. If this parameter is not set, the default value is empty, indicating that there is no recurrence rule. The value range is [1, 31], corresponding to the first to the last days of each month. Other values are invalid and have the same effect as the empty value. The value 29, 30, or 31 is invalid if the corresponding date does not exist in the current month. The relevant field arrays are in one-to-one mapping. For example, if the values of monthsOfYear and daysOfMonth are [1, 2, 3], the event recurs on January 1, February 2, and March 3.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## daysOfWeek

```TypeScript
daysOfWeek?: number[]
```

Repeats by day of a week. If this parameter is not set, the default value is empty, indicating that there is no recurrence rule. The value range is [1, 7], corresponding to Monday to Sunday. Other values are invalid and have the same effect as the empty value. The relevant field arrays are in one-to-one mapping. For example, if the values of weeksOfMonth and daysOfWeek are [1, 2, 3], the event recurs on Monday of the first week, Tuesday of the second week, and Wednesday of the third week of each month.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## daysOfYear

```TypeScript
daysOfYear?: number[]
```

Repeats by day of a year. If this parameter is not set, the default value is empty, indicating that there is no recurrence rule. The value range is [1, 366], corresponding to the first to the last days of each year. Other values are invalid and have the same effect as the empty value. If this year only has 365 days, the value 366 is invalid.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## excludedDates

```TypeScript
excludedDates?: number[]
```

Excluded dates set for a duplicate calendar event, in timestamp format. The value must be exactly the same as the start time (hour, minute, and second) of the event. Otherwise, the setting does not take effect. This parameter is not specified by default. If the value is 0 or a negative number, it is treated as an empty value.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## expire

```TypeScript
expire?: number
```

End date of the recurrence period. The value is a 13-digit timestamp. If this parameter is not specified, the event has no end date.

If **expire**, **count**, and **interval** are set at the same time, the restriction that is reached first prevails.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## interval

```TypeScript
interval?: number
```

Recurrence interval of a recurring event. The value is a non-negative integer. If the value is a floating point number, it is rounded down. If this parameter is not specified, the default value is 0. If the value is 0, 1, or negative, the event recurs every day, week, month, or year. If interval, count, and expire are set at the same time, the restriction that is reached first prevails. This property is related to the recurrenceFrequency rule. The recurrence interval varies according to the recurrence rule. For example, if the interval value is 2, the following situations occur: Daily recurrence: The event recurs every two days. Weekly recurrence: The event recurs every two weeks. Monthly recurrence: The event recurs every two months. Yearly recurrence: The event recurs every two years.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## monthsOfYear

```TypeScript
monthsOfYear?: number[]
```

Repeats by month of a year. If this parameter is not set, the default value is empty, indicating that there is no recurrence rule. The value range is [1, 12], corresponding to the first to the last months of each year. Other values are invalid and have the same effect as the empty value.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## recurrenceFrequency

```TypeScript
recurrenceFrequency: RecurrenceFrequency
```

Type of the event recurrence rule.

**Type:** [RecurrenceFrequency](arkts-calendar-calendarmanager-recurrencefrequency-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## weeksOfMonth

```TypeScript
weeksOfMonth?: number[]
```

Repeats by week of a month. If this parameter is not set, the default value is empty, indicating that there is no recurrence rule. The value range is [1, 5], corresponding to the first to the last weeks of each month. Other values are invalid and have the same effect as the empty value. If this month only has four weeks, the value 5 is invalid.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## weeksOfYear

```TypeScript
weeksOfYear?: number[]
```

Repeats by week of a year. If this parameter is not set, the default value is empty, indicating that there is no recurrence rule. The value range is [1, 53], corresponding to the first to the last weeks of each year. Other values are invalid and have the same effect as the empty value.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData
