# Calendar

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

**起始版本：** 7

**废弃版本：** 20

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-CalendarInterface-(value: {
    date: { year: number; month: number; day: number };
    currentData: MonthData;
    preData: MonthData;
    nextData: MonthData;
    controller?: CalendarController;
  }): CalendarAttribute--><!--Device-CalendarInterface-(value: {
    date: { year: number; month: number; day: number };
    currentData: MonthData;
    preData: MonthData;
    nextData: MonthData;
    controller?: CalendarController;
  }): CalendarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | {     date: { year: number; month: number; day: number };     currentData: MonthData;     preData: MonthData;     nextData: MonthData;     controller?: CalendarController;   } | 是 |  |

## 汇总

- [CalendarDay](arkts-arkui-calendar-calendarday-i-sys.md)
- [CalendarRequestedData](arkts-arkui-calendar-calendarrequesteddata-i-sys.md)
- [CalendarSelectedDate](arkts-arkui-calendar-calendarselecteddate-i-sys.md)
- [CurrentDayStyle](arkts-arkui-calendar-currentdaystyle-i-sys.md)
- [MonthData](arkts-arkui-calendar-monthdata-i-sys.md)
- [NonCurrentDayStyle](arkts-arkui-calendar-noncurrentdaystyle-i-sys.md)
- [TodayStyle](arkts-arkui-calendar-todaystyle-i-sys.md)
- [WeekStyle](arkts-arkui-calendar-weekstyle-i-sys.md)
- [WorkStateStyle](arkts-arkui-calendar-workstatestyle-i-sys.md)
