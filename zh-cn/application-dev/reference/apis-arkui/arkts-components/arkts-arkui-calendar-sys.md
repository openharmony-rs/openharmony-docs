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
| CalendarDay | Provides a monthly view component to display information such as date, shift break, and schedule. |
| CalendarRequestedData | Defines the struct of CalendarRequestedData. |
| CalendarSelectedDate | Defines the struct of CalendarSelectedDate. |
| CurrentDayStyle | CurrentDayStyle object. |
| MonthData | Date object. |
| NonCurrentDayStyle | Non current day style. |
| TodayStyle | Non current day style. |
| WeekStyle | Week Style. |
| WorkStateStyle | Work state style. |
