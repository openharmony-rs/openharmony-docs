# @ohos.arkui.advanced.Counter

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md) | Defines the common attributes and events of the **Counter** component. |
| [CounterOptions](arkts-arkui-arkui-advanced-counter-counteroptions-c.md) | Defines the type and style of the **Counter** component. |
| [DateData](arkts-arkui-arkui-advanced-counter-datedata-c.md) | Defines date attributes and methods, including year, month, and day. |
| [DateStyleOptions](arkts-arkui-arkui-advanced-counter-datestyleoptions-c.md) | Defines the attributes and events of the inline date counter. |
| [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md) | Defines the inline numeric counter attributes and events. |
| [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md) | Defines the list and compact counter attributes and events. |

### Structs

| Name | Description |
| --- | --- |
| [CounterComponent](arkts-arkui-arkui-advanced-counter-countercomponent-s.md) | The **Counter** component is used for precise numerical value adjustment. It supports four styles: list, compact, inline numeric, and inline date, and is suitable for scenarios such as shopping quantity adjustment, parameter setting, and date selection. It provides flexible style configuration and event callback capabilities. |

### Enums

| Name | Description |
| --- | --- |
| [CounterType](arkts-arkui-arkui-advanced-counter-countertype-e.md) | Enumerates counter types. |

## Examples

### Example 1: Implementing a List Counter

This example implements a list counter by setting type to CounterType.LIST and configuring numberOptions.



```TypeScript
import { CounterType, CounterComponent } from '@kit.ArkUI';

@Entry
@Component
struct ListCounterExample {
  build() {
    Column() {
      // List counter
      CounterComponent({
        options: {
          type: CounterType.LIST,
          numberOptions: {
            label: "Price",
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

### Example 2: Implementing a Compact Counter

This example implements a compact counter by setting type to CounterType.COMPACT and configuring numberOptions.



```TypeScript
import { CounterType, CounterComponent } from '@kit.ArkUI';

@Entry
@Component
struct CompactCounterExample {
  build() {
    Column() {
      // Compact counter
      CounterComponent({
        options: {
          type: CounterType.COMPACT,
          numberOptions: {
            label: "Quantity",
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

### Example 3: Implementing an Inline Numeric Counter

This example implements an inline numeric counter by setting type to CounterType.INLINE and configuring inlineOptions.



```TypeScript
import { CounterType, CounterComponent } from '@kit.ArkUI';

@Entry
@Component
struct NumberStyleExample {
  build() {
    Column() {
      // Inline number counter
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

### Example 4: Implementing an Inline Date Counter

This example implements an inline date counter by setting type to CounterType.INLINE_DATE and configuring dateOptions.



```TypeScript
import { CounterType, CounterComponent, DateData } from '@kit.ArkUI';

@Entry
@Component
struct DateStyleExample {
  build() {
    Column() {
      // Inline date counter
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

### Example 5: Implementing a Mirrored Layout

This example sets the direction attribute to implement a mirrored layout for list, compact, inline numeric, and inline date counters.

```TypeScript
import { CounterType, CounterComponent, DateData } from '@kit.ArkUI';

@Entry
@Component
struct CounterPage {
  @State currentDirection: Direction = Direction.Rtl

  build() {
    Column({space: 20}) {

      // List counter
      CounterComponent({
        options: {
          direction: this.currentDirection,
          type: CounterType.LIST,
          numberOptions: {
            label: "Price",
            min: 0,
            value: 5,
            max: 10,
          }
        }
      })

      // Compact counter
      CounterComponent({
        options: {
          direction: this.currentDirection,
          type: CounterType.COMPACT,
          numberOptions: {
            label: "Quantity",
            value: 10,
            min: 0,
            max: 100,
            step: 10
          }
        }
      })

      // Inline numeric counter
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
      
      // Inline date counter
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
