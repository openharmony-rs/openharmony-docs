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

**起始版本：** 7

**废弃版本：** 20

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | {     date: { year: number; month: number; day: number };     currentData: MonthData;     preData: MonthData;     nextData: MonthData;     controller?: CalendarController;   } | 是 |  |

## 汇总

### 接口

| 名称 | 说明 |
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
