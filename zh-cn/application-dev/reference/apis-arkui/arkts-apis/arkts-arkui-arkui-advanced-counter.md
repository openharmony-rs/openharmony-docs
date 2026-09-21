# @ohos.arkui.advanced.Counter

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md) | CommonOptions定义了Counter的通用属性和事件。 |
| [CounterOptions](arkts-arkui-arkui-advanced-counter-counteroptions-c.md) | CounterOptions定义了Counter类型及样式。 |
| [DateData](arkts-arkui-arkui-advanced-counter-datedata-c.md) | DateData定义了日期通用属性和方法，包括年、月、日。 |
| [DateStyleOptions](arkts-arkui-arkui-advanced-counter-datestyleoptions-c.md) | DateStyleOptions定义了日期内联型Counter的属性和事件。 |
| [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md) | InlineStyleOptions定义了数值内联型Counter的属性和事件。 |
| [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md) | NumberStyleOptions定义了列表型和紧凑型Counter的属性和事件。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [CounterComponent](arkts-arkui-arkui-advanced-counter-countercomponent-s.md) | Counter组件用于精确调节数值，支持列表型、紧凑型、数值内联型和日期内联型四种样式，适用于购物数量调节、参数设置、日期选择等场景，具有灵活的样式配置和事件回调能力。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CounterType](arkts-arkui-arkui-advanced-counter-countertype-e.md) | CounterType指定Counter类型。 |

## 示例

### 示例1（列表型Counter）

该示例通过设置为和配置，实现了列表型Counter。



```TypeScript
import { CounterType, CounterComponent } from '@kit.ArkUI';

@Entry
@Component
struct ListCounterExample {
  build() {
    Column() {
      // 列表型Counter
      CounterComponent({
        options: {
          type: CounterType.LIST,
          numberOptions: {
            label: '价格',
            min: 0,
            value: 5,
            max: 10
          }
        }
      })
    }
  }
}
```

### 示例2（紧凑型Counter）

该示例通过设置为和，实现了紧凑型Counter。



```TypeScript
import { CounterType, CounterComponent } from '@kit.ArkUI';

@Entry
@Component
struct CompactCounterExample {
  build() {
    Column() {
      // 紧凑型Counter
      CounterComponent({
        options: {
          type: CounterType.COMPACT,
          numberOptions: {
            label: '数量',
            value: 10,
            min: 0,
            max: 100,
            step: 10
          }
        }
      })
    }
  }
}
```

### 示例3（数值内联型Counter）

该示例通过设置为和，实现了数值内联型Counter。



```TypeScript
import { CounterType, CounterComponent } from '@kit.ArkUI';

@Entry
@Component
struct NumberStyleExample {
  build() {
    Column() {
      // 数值内联型Counter
      CounterComponent({
        options: {
          type: CounterType.INLINE,
          inlineOptions: {
            value: 100,
            min: 10,
            step: 2,
            max: 1000,
            textWidth: 100,
            onChange: (value: number) => {
              console.info('onCounterChange Counter: ' + value.toString());
            }
          }
        }
      })
    }
  }
}
```

### 示例4（日期内联型Counter）

该示例通过设置为和，实现了日期内联型Counter。



```TypeScript
import { CounterType, CounterComponent, DateData } from '@kit.ArkUI';

@Entry
@Component
struct DateStyleExample {
  build() {
    Column() {
      // 日期内联型Counter
      CounterComponent({
        options: {
          type: CounterType.INLINE_DATE,
          dateOptions: {
            year: 2016,
            onDateChange: (date: DateData) => {
              console.info('onDateChange Date: ' + date.toString());
            }
          }
        }
      })
    }
  }
}
```

### 示例5（镜像布局展示）

该示例通过设置direction属性，实现了列表型、紧凑型、数值内联型、日期内联型Counter的镜像布局。

```TypeScript
import { CounterType, CounterComponent, DateData } from '@kit.ArkUI';

@Entry
@Component
struct CounterPage {
  @State currentDirection: Direction = Direction.Rtl

  build() {
    Column({space: 20}) {

      // 列表型Counter
      CounterComponent({
        options: {
          direction: this.currentDirection,
          type: CounterType.LIST,
          numberOptions: {
            label: '价格',
            min: 0,
            value: 5,
            max: 10,
          }
        }
      })

      // 紧凑型Counter
      CounterComponent({
        options: {
          direction: this.currentDirection,
          type: CounterType.COMPACT,
          numberOptions: {
            label: '数量',
            value: 10,
            min: 0,
            max: 100,
            step: 10
          }
        }
      })

      // 数值内联型Counter
      CounterComponent({
        options: {
          type: CounterType.INLINE,
          direction: this.currentDirection,
          inlineOptions: {
            value: 100,
            min: 10,
            step: 2,
            max: 1000,
            textWidth: 100,
            onChange: (value: number) => {
              console.info('onCounterChange Counter: ' + value.toString());
            }
          }
        }
      })
      
      // 日期内联型Counter
      CounterComponent({
        options: {
          direction: this.currentDirection,
          type: CounterType.INLINE_DATE,
          dateOptions: {
            year: 2024,
            onDateChange: (date: DateData) => {
              console.info('onDateChange Date: ' + date.toString());
            }
          }
        }
      })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```
