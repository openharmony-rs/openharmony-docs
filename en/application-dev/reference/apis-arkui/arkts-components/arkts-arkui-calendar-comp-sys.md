# Calendar (System API)

Defines Calendar Component.

## Calendar

```TypeScript
Calendar(value: {
    date: { year: number; month: number; day: number };
    currentData: MonthData;
    preData: MonthData;
    nextData: MonthData;
    controller?: CalendarController;
  })
```

Set value.

**Since:** 7

**Deprecated since:** 20

**Model restriction:** This API can be used in both the stage model and FA model.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | {     date: { year: number; month: number; day: number };     currentData: MonthData;     preData: MonthData;     nextData: MonthData;     controller?: CalendarController;   } | Yes |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CalendarDay](arkts-arkui-calendar-comp-calendarday-i-sys.md) | Provides a monthly view component to display information such as date, shift break, and schedule. |
| [CalendarRequestedData](arkts-arkui-calendar-comp-calendarrequesteddata-i-sys.md) | Defines the struct of CalendarRequestedData. |
| [CalendarSelectedDate](arkts-arkui-calendar-comp-calendarselecteddate-i-sys.md) | Defines the struct of CalendarSelectedDate. |
| [CurrentDayStyle](arkts-arkui-calendar-comp-currentdaystyle-i-sys.md) | CurrentDayStyle object. |
| [MonthData](arkts-arkui-calendar-comp-monthdata-i-sys.md) | Date object. |
| [NonCurrentDayStyle](arkts-arkui-calendar-comp-noncurrentdaystyle-i-sys.md) | Non current day style. |
| [TodayStyle](arkts-arkui-calendar-comp-todaystyle-i-sys.md) | Non current day style. |
| [WeekStyle](arkts-arkui-calendar-comp-weekstyle-i-sys.md) | Week Style. |
| [WorkStateStyle](arkts-arkui-calendar-comp-workstatestyle-i-sys.md) | Work state style. |
