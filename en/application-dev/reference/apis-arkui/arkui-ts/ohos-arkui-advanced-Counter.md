# advanced.Counter
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xieziang-->
<!--Designer: @youzhi92-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

The **Counter** component enables precise numerical value adjustment.

>  **NOTE**
>
>  This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
>  If the **Counter** component has [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **Counter** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **Counter** component.

## Modules to Import

```ts
import { CounterType, CounterComponent, CounterOptions, DateData } from '@kit.ArkUI';
```

## Child Components

Not supported

## CounterComponent

CounterComponent({&nbsp;options:&nbsp;CounterOptions&nbsp;})

Defines a **Counter** component instance.

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                             | Mandatory| Decorator| Description                   |
| ------- | --------------------------------- | ---- | ---------- | ----------------------- |
| options | [CounterOptions](#counteroptions) | Yes  | @Prop      | Configuration parameters of the **Counter** component.|

## CounterOptions

Defines the counter type and style.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type      | Read-Only| Optional| Description                           |
| ----------- | ---------- | ---- | ------------------------------- | ------------------------------- |
| type | [CounterType](#countertype) | No | No | Type of the counter.|
| direction<sup>12+</sup> | [Direction](ts-appendix-enums.md#direction) | No| Yes| Layout direction.<br>Default value: **Direction.Auto**<br>If the value is **undefined**, the default value is used.|
| numberOptions | [NumberStyleOptions](#numberstyleoptions) | No  | Yes  | Style of the list or compact counter.<br>Default value: list or compact counter with value 0.<br>If the value is **undefined**, the default value is used.|
| inlineOptions | [InlineStyleOptions](#inlinestyleoptions) | No| Yes| Parameters of the inline numeric counter.<br>Default value: regular inline numeric counter with value 0.<br>If the value is **undefined**, the default value is used.|
| dateOptions | [DateStyleOptions](#datestyleoptions) | No| Yes| Style of the inline date counter.<br>Default value: date counter showing 0001/01/01.<br>If the value is **undefined**, the default value is used.|

The table below lists the counter type and style mapping.

| Counter Type            | Counter Style       |
| ----------------------- | ------------------ |
| CounterType.LIST        | NumberStyleOptions |
| CounterType.COMPACT     | NumberStyleOptions |
| CounterType.INLINE      | InlineStyleOptions |
| CounterType.INLINE_DATE | DateStyleOptions   |

## CounterType

Enumerates counter types.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value  | Description                       |
| ----------- | ---- | --------------------------- |
| LIST        | 0    | List counter.            |
| COMPACT     | 1    | Compact counter.            |
| INLINE      | 2    | Inline numeric counter.|
| INLINE_DATE | 3    | Inline date counter.      |

## CommonOptions

Defines common attributes and events for all counter types.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                     | Read-Only| Optional| Description                                                        |
| --------------- | ------------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| focusable       | boolean                   | No | Yes | Whether the counter is focusable.<br>**NOTE**<br>This attribute only applies to list and compact counters.<br>Default value: **true**.<br>**true**: focusable. **false**: not focusable.<br>If the value is **undefined**, the default value is used.|
| step            | number                    | No | Yes | Step of the counter.<br>Value range: an integer greater than or equal to 1.<br>Default value: **1**<br>If the value is out of the range, the default value is used.|
| onHoverIncrease | (isHover: boolean) => void | No | Yes | Callback invoked when the mouse pointer is moved over or away from the increase button of the counter.<br>**isHover**: whether the mouse pointer is hovering over the component. The value **true** means that the mouse pointer enters the component, and the value **false** means that the mouse pointer leaves the component.<br>Default value: no callback triggered.<br>If the value is **undefined**, the default value is used.|
| onHoverDecrease | (isHover: boolean) => void | No | Yes | Callback invoked when the mouse pointer is moved over or away from the decrease button of the counter.<br>**isHover**: whether the mouse pointer is hovering over the component. The value **true** means that the mouse pointer enters the component, and the value **false** means that the mouse pointer leaves the component.<br>Default value: no callback triggered.<br>If the value is **undefined**, the default value is used.|

## InlineStyleOptions

Defines the inline numeric counter attributes and events.

Inherits from [CommonOptions](#commonoptions).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                  | Read-Only| Optional| Description                                                  |
| --------- | ---------------------- | ---- | ------------------------------------------------------ | ------------------------------------------------------ |
| value     | number                 | No | Yes | Initial value of the counter.<br>Default value: **0**<br>Value range: [min, max].<br>When the value exceeds the allowed range, it is handled as follows: if the value is **undefined**, the default value is applied; otherwise, the maximum allowed value is used.|
| min       | number                 | No | Yes | Minimum value of the counter.<br>Default value: **0**<br>Value range: (-∞, +∞)<br>If the value is **undefined**, the default value is used.|
| max       | number                 | No | Yes | Maximum value of the counter.<br>Default value: **999**<br>Value range: (-∞, +∞)<br>If the value is **undefined**, the default value is used.|
| textWidth | number                 | No | Yes | Text width of the counter.<br>Default value: auto-adjusted width.<br>Value range: [0, +∞)<br>Unit: vp.<br>When the value exceeds the allowed range, it is handled as follows: if the value is **undefined**, the default value is applied; otherwise, the maximum allowed value is used.|
| onChange  | (value: number) => void | No | Yes | Callback invoked when the value changes. The current value is returned.<br>**value**: current value.<br>Default value: no callback triggered.<br>If the value is **undefined**, the default value is used.|

## NumberStyleOptions

Defines the list and compact counter attributes and events.

Inherits from [InlineStyleOptions](#inlinestyleoptions).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                                  | Read-Only| Optional| Description                                                        |
| --------------- | -------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| label           | [ResourceStr](ts-types.md#resourcestr) | No  | Yes  | Label of the counter.<br>Default value: **' '**<br>If the value is **undefined**, the default value is used.|
| onFocusIncrease | () => void                             | No  | Yes  | Callback invoked when the increase button of the counter gains focus.<br>Default value: no callback triggered.<br>If the value is **undefined**, the default value is used.|
| onFocusDecrease | () => void                             | No  | Yes  | Callback invoked when the decrease button of the counter gains focus.<br>Default value: no callback triggered.<br>If the value is **undefined**, the default value is used.|
| onBlurIncrease  | () => void                             | No  | Yes  | Callback invoked when the increase button of the counter loses focus.<br>Default value: no callback triggered.<br>If the value is **undefined**, the default value is used.|
| onBlurDecrease  | () => void                             | No  | Yes  | Callback invoked when the decrease button of the counter loses focus.<br>Default value: no callback triggered.<br>If the value is **undefined**, the default value is used.|

## DateStyleOptions

Defines the inline date counter attributes and events.

Inherits from [CommonOptions](#commonoptions).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                               | Read-Only| Optional| Description                                                     |
| ------------ | ----------------------------------- | ---- | --------------------------------------------------------- | --------------------------------------------------------- |
| year         | number                              | No | Yes | Initial year of the counter.<br>Default value: **1**<br>Value range: [1, 5000]<br>If the value is out of the range, the default value is used.|
| month        | number                              | No | Yes | Initial month of the counter.<br>Default value: **1**<br>Value range: [1, 12]<br>If the value is out of the range, the default value is used.|
| day          | number                              | No | Yes | Initial day of the counter.<br>Default value: **1**<br>Value range: [1, 31]<br>If the value is out of the range, the default value is used.|
| onDateChange | (date: [DateData](#datedata)) => void | No | Yes | Callback invoked when the date changes. The current date is returned.<br>**date**: current date.<br>If the value is **undefined**, the current date value is not displayed.|

## DateData

Defines date attributes, including year, month, and day.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ---- | ------------------------------------------------------------ |
| year  | number | No  | No  | Initial year of the counter.<br>Default value: **1**<br>Value range: [1, 5000]<br>If the value is out of the range, the default value is used.|
| month | number | No  | No  | Initial month of the counter.<br>Default value: **1**<br>Value range: [1, 12]<br>If the value is out of the range, the default value is used.|
| day   | number | No  | No  | Initial day of the counter.<br>Default value: **1**<br>Value range: [1, 31]<br>If the value is out of the range, the default value is used.|

### constructor

constructor(year: number, month: number, day: number)

DateData constructor for initializing date objects.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---------- | ------ |  ------ | ---------------------------- |
| year       | number |  Yes| Initial year of the counter.    |
| month      | number |  Yes| Initial month of the counter.    |
| day        | number |  Yes| Initial day of the counter.      |

### toString

toString(): string

Returns the current date in YYYY-MM-DD format.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type| Description|
| -------- | -------- |
| string | Current date.|

## Example

### Example 1: Implementing a List Counter

This example implements a list counter by setting **type** to **CounterType.LIST** and configuring **numberOptions**.

```ts
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

![listcounter](figures/listcounter.gif)

### Example 2: Implementing a Compact Counter

This example implements a compact counter by setting **type** to **CounterType.COMPACT** and configuring **numberOptions**.

```ts
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

![compactcounter](figures/compactcounter.gif)

### Example 3: Implementing an Inline Numeric Counter

This example implements an inline numeric counter by setting **type** to **CounterType.INLINE** and configuring **inlineOptions**.

```ts
import { CounterType, CounterComponent } from '@kit.ArkUI';

@Entry
@Component
struct NumberStyleExample {
  build() {
    Column() {
      // Inline numeric counter
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

![numberstyle](figures/numberstyle.gif)

### Example 4: Implementing an Inline Date Counter

This example implements an inline date counter by setting **type** to **CounterType.INLINE_DATE** and configuring **dateOptions**.

```ts
import { CounterType, CounterComponent, DateData } from '@kit.ArkUI';

@Entry
@Component
struct DataStyleExample {
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

![datestyle](figures/datestyle.gif)

### Example 5: Implementing a Mirrored Layout

This example implements a mirrored layout for list, compact, inline numeric, and inline date counters by setting **direction**.

```ts
import { CounterType, CounterComponent, DateData } from '@kit.ArkUI';

@Entry
@Component
struct CounterPage {
  @State currentDirection: Direction = Direction.Rtl

  build() {
    Column({}) {

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
        .width('80%')

      // Numeric counter
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
      }).margin({ top: 20 })

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
      }).margin({ top: 20 })
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
      }).margin({ top: 20 })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```

![datestyle](figures/counter_direction.png)
