# CalendarPicker

日历选择器组件，提供下拉日历弹窗，用户可快速选择日期。适用于需要用户选择具体日期的场景，如预订系统、日程安排、日期筛选等，提供直观的日历视图， 提升用户日期输入体验。
> **说明：** > > - 该组件从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件从API版本26.0.0开始支持WithTheme。
>

## 子组件 > > 无

## CalendarPicker

```TypeScript
CalendarPicker(options?: CalendarOptions)
```

日历选择器。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CalendarOptions](arkts-arkui-calendaroptions-i.md) | 否 | 配置日历选择器组件的参数。未设置该参数时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CalendarDialogOptions](arkts-arkui-calendardialogoptions-i.md) | 日历选择器弹窗选项。继承自[CalendarOptions](arkts-arkui-calendaroptions-i.md)。 |
| [CalendarOptions](arkts-arkui-calendaroptions-i.md) | 日历选择器组件的参数说明。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CalendarAlign](arkts-arkui-calendaralign-e.md) | 对齐方式类型。 |

## 示例

该示例通过calendarPicker实现了日历选择器组件，提供下拉日历弹窗。

```TypeScript
// xxx.ets
@Entry
@Component
struct CalendarPickerExample {
  private selectedDate: Date = new Date('2024-03-05');

  build() {
    Column() {
      Column() {
        CalendarPicker({ hintRadius: 10, selected: this.selectedDate })
          .edgeAlign(CalendarAlign.END)
          .textStyle({ color: '#ff182431', font: { size: 20, weight: FontWeight.Normal } })
          .margin(10)
          .onChange((value) => {
            console.info(`CalendarPicker onChange: ${value.toString()}`);
          })
      }.alignItems(HorizontalAlign.End).width("100%")

      Text('日历日期选择器').fontSize(30)
    }.width('100%').margin({ top: 350 })
  }
}
```

从API version 18开始，CalendarOptions中新增了start、end属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct CalendarPickerExample {
  private selectedDate: Date = new Date('2025-01-15');
  private startDate: Date = new Date('2025-01-05');
  private endDate: Date = new Date('2025-01-25');

  build() {
    Column() {
      Column() {
        CalendarPicker({ hintRadius: 10, selected: this.selectedDate, start: this.startDate, end: this.endDate })
          .edgeAlign(CalendarAlign.END)
          .textStyle({ color: '#ff182431', font: { size: 20, weight: FontWeight.Normal } })
          .margin(10)
          .onChange((value) => {
            console.info(`CalendarPicker onChange: ${value.toString()}`);
          })
      }.alignItems(HorizontalAlign.End).width("100%")
    }.width('100%').margin({ top: 350 })
  }
}
```

从API version 19开始，新增了markToday接口，CalendarOptions中新增了disabledDateRange属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct CalendarPickerExample {
  private disabledDateRange: DateRange[] = [
    { start: new Date('2025-01-01'), end: new Date('2025-01-02') },
    { start: new Date('2025-01-09'), end: new Date('2025-01-10') },
    { start: new Date('2025-01-15'), end: new Date('2025-01-16') },
    { start: new Date('2025-01-19'), end: new Date('2025-01-19') },
    { start: new Date('2025-01-22'), end: new Date('2025-01-25') }
  ];

  build() {
    Column() {
      CalendarPicker({ disabledDateRange: this.disabledDateRange })
        .margin(10)
        .markToday(true)
        .onChange((value) => {
          console.info(`CalendarPicker onChange: ${value.toString()}`);
        })
    }.alignItems(HorizontalAlign.End).width('100%')
  }
}
```
