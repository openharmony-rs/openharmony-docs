# @ohos.arkui.advanced.CounterV2

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md) | CounterV2CommonOptions定义了CounterV2的共通属性和事件。 |
| [CounterV2DateData](arkts-arkui-arkui-advanced-counterv2-counterv2datedata-c.md) | CounterV2DateData定义了日期通用属性和方法，包括年、月、日。 |
| [CounterV2DateStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2datestyleoptions-c.md) | CounterV2DateStyleOptions定义日期内联型CounterV2的属性和事件。 |
| [CounterV2InlineStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2inlinestyleoptions-c.md) | CounterV2InlineStyleOptions定义了数值内联型CounterV2的属性和事件。 |
| [CounterV2NumberStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2numberstyleoptions-c.md) | CounterV2NumberStyleOptions定义了列表型和紧凑型CounterV2的属性和事件。 |
| [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) | CounterV2Options定义CounterV2类型及样式。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [CounterV2Component](arkts-arkui-arkui-advanced-counterv2-counterv2component-s.md) | CounterV2组件用于精确调节数值，包含列表型、紧凑型、数值内联型和日期内联型四种类型，适用于购物车数量调节、日期选择等场景。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md) | CounterV2Type指定CounterV2类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnCounterV2HoverCallback](arkts-arkui-oncounterv2hovercallback-t.md) | 定义CounterV2的鼠标悬浮回调类型。 |
| [OnDateCounterV2ChangeCallback](arkts-arkui-ondatecounterv2changecallback-t.md) | 定义日期内联型CounterV2的日期变化回调类型。 |
| [OnInlineCounterV2Change](arkts-arkui-oninlinecounterv2change-t.md) | 定义数值内联型CounterV2的值变化回调类型。 |

## 示例

### 示例1（列表型CounterV2）

该示例通过设置[CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).LIST和配置[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)的numberOptions属性，实现了列表型CounterV2。

从API版本26.0.0开始，[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)支持numberOptions属性。



```TypeScript
import { CounterV2Type, CounterV2Component } from '@kit.ArkUI';

@Entry
@ComponentV2
struct ListCounterExample {
  build() {
    Column() {
      // 列表型CounterV2
      CounterV2Component({
        options: {
          type: CounterV2Type.LIST,
          numberOptions: {
            label: '价格',
            min: 0,
            value: 5,
            max: 10,
          }
        }
      })
    }
  }
}
```

### 示例2（紧凑型CounterV2）

该示例通过设置[CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).COMPACT和配置[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)的numberOptions属性，实现紧凑型CounterV2。

从API版本26.0.0开始，[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)支持numberOptions属性。



```TypeScript
import { CounterV2Type, CounterV2Component } from '@kit.ArkUI';

@Entry
@ComponentV2
struct CompactCounterExample {
  build() {
    Column() {
      // 紧凑型CounterV2
      CounterV2Component({
        options: {
          type: CounterV2Type.COMPACT,
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

### 示例3（数值内联型CounterV2）

该示例通过设置[CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).INLINE和配置[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)的inlineOptions属性，实现数值内联型CounterV2。

从API版本26.0.0开始，[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)支持inlineOptions属性。



```TypeScript
import { CounterV2Type, CounterV2Component } from '@kit.ArkUI';

@Entry
@ComponentV2
struct NumberStyleExample {
  build() {
    Column() {
      // 数值内联型CounterV2
      CounterV2Component({
        options: {
          type: CounterV2Type.INLINE,
          inlineOptions: {
            value: 100,
            min: 10,
            step: 2,
            max: 1000,
            textWidth: 100,
            onChange: (value: number) => {
              console.info('onCounterV2Change Counter: ' + value.toString());
            }
          }
        }
      })
    }
  }
}
```

### 示例4（日期内联型CounterV2）

该示例通过设置[CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).INLINE_DATE和配置[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)的dateOptions属性，实现日期内联型CounterV2。

从API版本26.0.0开始，[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)支持dateOptions属性。



```TypeScript
import { CounterV2Type, CounterV2Component, CounterV2DateData } from '@kit.ArkUI';

@Entry
@ComponentV2
struct DateStyleExample {
  build() {
    Column() {
      // 日期内联型CounterV2
      CounterV2Component({
        options: {
          type: CounterV2Type.INLINE_DATE,
          dateOptions: {
            year: 2016,
            onDateChange: (date: CounterV2DateData) => {
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

该示例通过设置[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)的direction属性，实现列表型、紧凑型、数值内联型、日期内联型CounterV2的镜像布局。

从API版本26.0.0开始，[CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)支持direction属性。

```TypeScript
import { CounterV2Type, CounterV2Component, CounterV2DateData } from '@kit.ArkUI';

@Entry
@ComponentV2
struct CounterPage {
  @Local currentDirection: Direction = Direction.Rtl

  build() {
    Column({space: 20}) {

      // 列表型CounterV2
      CounterV2Component({
        options: {
          direction: this.currentDirection,
          type: CounterV2Type.LIST,
          numberOptions: {
            label: '价格',
            min: 0,
            value: 5,
            max: 10,
          }
        }
      })

      // 紧凑型CounterV2
      CounterV2Component({
        options: {
          direction: this.currentDirection,
          type: CounterV2Type.COMPACT,
          numberOptions: {
            label: '数量',
            value: 10,
            min: 0,
            max: 100,
            step: 10
          }
        }
      })

      // 数值内联型CounterV2
      CounterV2Component({
        options: {
          type: CounterV2Type.INLINE,
          direction: this.currentDirection,
          inlineOptions: {
            value: 100,
            min: 10,
            step: 2,
            max: 1000,
            textWidth: 100,
            onChange: (value: number) => {
              console.info('onCounterV2Change Counter: ' + value.toString());
            }
          }
        }
      })

      // 日期内联型CounterV2
      CounterV2Component({
        options: {
          direction: this.currentDirection,
          type: CounterV2Type.INLINE_DATE,
          dateOptions: {
            year: 2024,
            onDateChange: (date: CounterV2DateData) => {
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
