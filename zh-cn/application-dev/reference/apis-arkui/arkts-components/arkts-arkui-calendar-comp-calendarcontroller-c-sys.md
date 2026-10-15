# CalendarController（系统接口）

```TypeScript
declare class CalendarController
```

日历控制器。

**起始版本：** 7

**废弃版本：** 20

<!--Device-unnamed-declare class CalendarController--><!--Device-unnamed-declare class CalendarController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## backToToday

```TypeScript
backToToday()
```

回到今天。

**起始版本：** 7

**废弃版本：** 20

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-CalendarController-backToToday()--><!--Device-CalendarController-backToToday()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor()
```

构造函数。

**起始版本：** 7

**废弃版本：** 20

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-CalendarController-constructor()--><!--Device-CalendarController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## goTo

```TypeScript
goTo(value: { year: number; month: number; day: number })
```

跳转到指定日期。

**起始版本：** 7

**废弃版本：** 20

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-CalendarController-goTo(value: { year: number; month: number; day: number })--><!--Device-CalendarController-goTo(value: { year: number; month: number; day: number })-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { year: number; month: number; day: number } | 是 | 跳转的目标日期。<br>year: 目标年份。<br>month: 目标月份。<br>day: 目标日期。 |
