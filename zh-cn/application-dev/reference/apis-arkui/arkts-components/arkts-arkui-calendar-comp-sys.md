# Calendar (System API)

提供一个月视图组件，用于显示日期、轮休和日程等信息。

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

设置日历配置。

**起始版本：** 7

**废弃版本：** 20

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-CalendarInterface-(value: {    date: { year: number; month: number; day: number };    currentData: MonthData;    preData: MonthData;    nextData: MonthData;    controller?: CalendarController;  }): CalendarAttribute--><!--Device-CalendarInterface-(value: {    date: { year: number; month: number; day: number };    currentData: MonthData;    preData: MonthData;    nextData: MonthData;    controller?: CalendarController;  }): CalendarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | {     date: { year: number; month: number; day: number };     currentData: MonthData;     preData: MonthData;     nextData: MonthData;     controller?: CalendarController;   } | 是 | 日历配置信息。<br>date: 设置为当前日期的日期，包含year、month和day。<br>currentData:当月数据。<br>preData: 上月数据。<br>nextData: 下月数据。<br>controller: 日历控制器。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CalendarDay](arkts-arkui-calendar-comp-calendarday-i-sys.md) | 日历日期信息。 |
| [CalendarRequestedData](arkts-arkui-calendar-comp-calendarrequesteddata-i-sys.md) | 定义CalendarRequestedData结构体。 |
| [CalendarSelectedDate](arkts-arkui-calendar-comp-calendarselecteddate-i-sys.md) | 定义CalendarSelectedDate结构体。 |
| [CurrentDayStyle](arkts-arkui-calendar-comp-currentdaystyle-i-sys.md) | CurrentDayStyle对象。 |
| [MonthData](arkts-arkui-calendar-comp-monthdata-i-sys.md) | 日期数据对象。 |
| [NonCurrentDayStyle](arkts-arkui-calendar-comp-noncurrentdaystyle-i-sys.md) | 非当月日期样式。 |
| [TodayStyle](arkts-arkui-calendar-comp-todaystyle-i-sys.md) | 今日样式。 |
| [WeekStyle](arkts-arkui-calendar-comp-weekstyle-i-sys.md) | 周样式。 |
| [WorkStateStyle](arkts-arkui-calendar-comp-workstatestyle-i-sys.md) | 工作状态样式。 |
