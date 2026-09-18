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
| [CalendarDay](arkts-arkui-calendarday-i-sys.md) | Provides a monthly view component to display information such as date, shift break, and schedule. |
| [CalendarRequestedData](arkts-arkui-calendarrequesteddata-i-sys.md) | Defines the struct of CalendarRequestedData. |
| [CalendarSelectedDate](arkts-arkui-calendarselecteddate-i-sys.md) | Defines the struct of CalendarSelectedDate. |
| [CurrentDayStyle](arkts-arkui-currentdaystyle-i-sys.md) | CurrentDayStyle object. |
| [MonthData](arkts-arkui-monthdata-i-sys.md) | Date object. |
| [NonCurrentDayStyle](arkts-arkui-noncurrentdaystyle-i-sys.md) | Non current day style. |
| [TodayStyle](arkts-arkui-todaystyle-i-sys.md) | Non current day style. |
| [WeekStyle](arkts-arkui-weekstyle-i-sys.md) | Week Style. |
| [WorkStateStyle](arkts-arkui-workstatestyle-i-sys.md) | Work state style. |
