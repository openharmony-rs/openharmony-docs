# @ohos.arkui.advanced.DatePickerComponent

## 导入模块

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md) | CommonOptions定义日期时间选择器的通用选项。 |
| [DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md) | DateOptions定义日期选择器的选项。 |
| [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) | DatePickerComponentOptions定义日期时间选择器组件的选项。 |
| [DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md) | DatePickerComponentResult定义日期时间选择器的选择结果，包含用户选择的年、月、日、时、分、秒信息，用于在onChange和onScrollStop回调中传递选择的具体日期时间值。 |
| [TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md) | TimeOptions定义时间选择器的选项。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [DatePickerComponent](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponent-s.md) | DatePickerComponent组件用于选择日期（年月日）和时间（时分秒）。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DateMode](arkts-arkui-arkui-advanced-datepickercomponent-datemode-e.md) | DateMode枚举用于定义日期选择器的模式。 |
| [DisplayMode](arkts-arkui-arkui-advanced-datepickercomponent-displaymode-e.md) | DisplayMode枚举用于定义选择器的显示模式。 |
| [TimeFormat](arkts-arkui-arkui-advanced-datepickercomponent-timeformat-e.md) | TimeFormat枚举用于定义时间选择器的格式。 |

## 示例

### 示例1（日期选择器）

该示例通过设置[DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md)中的displayMode为DisplayMode.DATE，实现日期选择器。

从API版本26.0.0开始，新增[DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md)参数。



```TypeScript
import { DatePickerComponent, DisplayMode, DateMode } from '@kit.ArkUI';

@Entry
@Component
struct DatePickerExample {
  @State selectedYear: number = 2026
  @State selectedMonth: number = 0
  @State selectedDay: number = 1

  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(this.selectedYear, this.selectedMonth, this.selectedDay),
            start: new Date('2020-03-01'),
            end: new Date('2030-10-31'),
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected date: ' + (result.year ?? 0) + '-' + ((result.month ?? 0) + 1) + '-' + (result.day ?? 0));
              if (result.year !== undefined) {
                this.selectedYear = result.year
              }
              if (result.month !== undefined) {
                this.selectedMonth = result.month
              }
              if (result.day !== undefined) {
                this.selectedDay = result.day
              }
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + (result.year ?? 0) + '-' + ((result.month ?? 0) + 1) + '-' + (result.day ?? 0));
            }
          }
        }
      })
    }
  }
}
```

### 示例2（时间选择器）

该示例通过设置[DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md)中的displayMode为DisplayMode.TIME，实现时间选择器。

从API版本26.0.0开始，新增[DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md)参数。



```TypeScript
import { DatePickerComponent, DisplayMode, TimeFormat } from '@kit.ArkUI';

@Entry
@Component
struct TimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.TIME,
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE,
            useMilitaryTime: true,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected time: ' + (result.hour ?? 0) + ':' + (result.minute ?? 0));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + (result.hour ?? 0) + ':' + (result.minute ?? 0));
            }
          }
        }
      })
    }
  }
}
```

### 示例3（日期时间选择器）

该示例通过设置[DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md)中的displayMode为DisplayMode.DATE_TIME，同时选择日期和时间。

从API版本26.0.0开始，新增[DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md)参数。



```TypeScript
import { DatePickerComponent, DisplayMode, DateMode, TimeFormat } from '@kit.ArkUI';

@Entry
@Component
struct DateTimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE_TIME,
          dateOptions: {
            mode: DateMode.DATE,
            lunar: false,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          },
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE_SECOND,
            useMilitaryTime: false,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          }
        }
      })
    }
  }
}
```

### 示例4（关闭循环模式）

该示例通过设置DateOptions中的loop为false，关闭选择器的循环滚动模式。

从API版本26.0.0开始，新增DateOptions参数。

```TypeScript
import { DatePickerComponent, DisplayMode, DateMode } from '@kit.ArkUI';

@Entry
@Component
struct NoLoopPickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(),
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            loop: false,
            onChange: (result) => {
              console.info('Selected date: ' + (result.year ?? 0) + '-' + ((result.month ?? 0) + 1) + '-' + (result.day ?? 0));
            }
          }
        }
      })
    }
  }
}
```
