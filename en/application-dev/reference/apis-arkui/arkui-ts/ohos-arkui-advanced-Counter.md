# advanced.Counter

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @weixin_45530366-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f61ce95179b4c1b9fc3671fde09ef06c73b5f91d translatedAt=2026-08-28T01:30:51.553Z pushedAt=2026-08-28T09:09:12.920Z -->

The **Counter** component is used for precise numerical value adjustment. It supports four styles: list, compact, inline numeric, and inline date, and is suitable for scenarios such as shopping quantity adjustment, parameter setting, and date selection. It provides flexible style configuration and event callback capabilities.

> **NOTE**
>
> - This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - If the **Counter** component has [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) set, the compilation toolchain generates an additional node named \_\_Common\_\_ and attaches the universal attributes or events to \_\_Common\_\_ instead of directly applying them to the **Counter** component. This may cause the universal attributes or events to not take effect or behave unexpectedly. Therefore, setting universal attributes and events for the **Counter** component is not recommended.

## Modules to Import

```ts
import { CounterType, CounterComponent, CounterOptions, DateData } from '@kit.ArkUI';
```

## Child Components

Not supported

## CounterComponent

CounterComponent({&nbsp;options:&nbsp;CounterOptions&nbsp;})

Creates a **Counter** component instance.

**Decorator:** @Component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                             | Mandatory| Decorator| Description                   |
| ------- | --------------------------------- | ---- | ---------- | ----------------------- |
| options | [CounterOptions](#counteroptions) | Yes | \@Prop | Configuration options for the type and style of the **Counter** component, including type (Counter type), **direction** (layout direction), **numberOptions** (list and compact styles), **inlineOptions** (inline number style), and **dateOptions** (inline date style). |

## CounterOptions

Defines the type and style of the **Counter** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type      | Read-Only| Optional| Description                           |
| ----------- | ---------- | ---- | ------------------------------- | ------------------------------- |
| type | [CounterType](#countertype) | No | No | Type of the current Counter. It must be used with the corresponding style parameters. For details about the mapping, see the Counter Type and Style Mapping table. |
| direction<sup>12+</sup> | [Direction](ts-appendix-enums.md#direction) | No | Yes | Layout direction. This parameter is passed when adapting to right-to-left languages (such as Arabic) or implementing a mirrored layout. **Direction.Auto**: automatically follows the system language direction (default). **Direction.Ltr**: left-to-right layout, applicable to most languages. **Direction.Rtl**: right-to-left layout, applicable to RTL languages such as Arabic.<br>Default value: **Direction.Auto**<br>If this parameter is set to **undefined**, the default value is used. |
| numberOptions | [NumberStyleOptions](#numberstyleoptions) | No | Yes | Style of the list-type or compact-type Counter. It must be used with the type set to **CounterType.LIST** or **CounterType.COMPACT**.<br>Default value: a list-type or compact-type Counter with the counter displayed as **0**.<br>If this parameter is set to **undefined**, the default value is used. |
| inlineOptions | [InlineStyleOptions](#inlinestyleoptions) | No | Yes | Style of the inline number Counter. It must be used with the type set to **CounterType.INLINE**.<br>Default value: an inline number Counter with the counter displayed as **0**.<br>If this parameter is set to **undefined**, the default value is used. |
| dateOptions | [DateStyleOptions](#datestyleoptions) | No | Yes | Style of the inline date Counter. It must be used with the type set to **CounterType.INLINE_DATE**.<br>Default value: an inline date Counter displaying **0001/01/01**.<br>If this parameter is set to **undefined**, the default value is used. |

When you select a **Counter** type, you must select the corresponding **Counter** style. If the style parameter does not match the type, the default style of that type is used.

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
| INLINE      | 2    | Inline number counter. |
| INLINE_DATE | 3    | Inline date counter.       |

## CommonOptions

Defines the common attributes and events of the **Counter** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                     | Read-Only| Optional| Description                                                        |
| --------------- | ------------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| focusable       | boolean                   | No  | Yes  | Whether the Counter can obtain focus.<br>**Note:** This attribute takes effect for the list and compact types of Counter, but not for the inline number and inline date types.<br>Default value: **true**<br>**true**: The Counter can obtain focus (selected when the Counter needs to be operated via keyboard or focus navigation); **false**: The Counter cannot obtain focus (selected when focus interaction is not required).<br>If the value is **undefined**, the default value is used. |
| step            | number                    | No  | Yes  | Step of the Counter. This is used when you need to quickly adjust the value (for example, by setting a step greater than the default value 1) or precisely control the amount of each change.<br>Value range: an integer greater than or equal to 1.<br>Default value: **1**<br>If the value is out of range, the default value is used.<br>If the value is **undefined**, the default value is used. |
| onHoverIncrease | (isHover: boolean) => void | No  | Yes  | Callback triggered when the mouse enters or leaves the increase button of the Counter.<br>Use case: pass in this callback when you need to perform custom operations (such as changing the button style or displaying a tooltip) when the mouse hovers over the increase button.<br>**isHover**: whether the mouse hovers over the increase button. The value is **true** when the mouse enters and **false** when it leaves.<br>Default value: no callback is triggered when the mouse enters or leaves the increase button of the Counter.<br>If the value is **undefined**, the default value is used. |
| onHoverDecrease | (isHover: boolean) => void | No  | Yes  | Callback triggered when the mouse enters or leaves the decrease button of the Counter.<br>Use case: pass in this callback when you need to perform custom operations (such as changing the button style or displaying a tooltip) when the mouse hovers over the decrease button.<br>**isHover**: whether the mouse hovers over the decrease button. The value is **true** when the mouse enters and **false** when it leaves.<br>Default value: no callback is triggered when the mouse enters or leaves the decrease button of the Counter.<br>If the value is **undefined**, the default value is used. |

## InlineStyleOptions

Defines the inline numeric counter attributes and events.

Inherits from [CommonOptions](#commonoptions).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                  | Read-Only| Optional| Description                                                  |
| --------- | ---------------------- | ---- | ------------------------------------------------------ | ------------------------------------------------------ |
| value     | number                 | No  | Yes  | Initial value of **Counter**.<br>Default value: **0**<br>Value range: [min, max], where **min** and **max** correspond to the minimum and maximum values of **Counter** respectively (the default value of **min** is **0** and **max** is **999**).<br>If the value exceeds the range, **min** is used when the value is less than **min**, and **max** is used when the value is greater than **max**. |
| min       | number                 | No  | Yes  | Minimum value of **Counter**.<br>Default value: **0**<br>Value range: (-∞, max]<br>If the value exceeds the range (that is, the set value is greater than **max**), **max** is used.<br>If the value is **undefined**, the default value is used. |
| max       | number                 | No  | Yes  | Maximum value of **Counter**.<br>Default value: **999**<br>Value range: [min, +∞)<br>If the value exceeds the range (that is, the set value is less than **min**), **min** is used.<br>If the value is **undefined**, the default value is used. |
| textWidth | number                 | No  | Yes  | Width of the number text.<br>Default value: adaptive text width.<br>Value range: [0, +∞)<br>Unit: vp<br>If the value exceeds the range (that is, the set value is less than 0), **0** is used.<br>If the value is **undefined**, the default value is used.|
| onChange  | (value: number) => void | No  | Yes  | Callback invoked when the value changes, returning the current value. Use case: pass in this callback when you need to perform custom operations upon value changes (such as updating associated UI, logging, saving state, etc.).<br>**value**: current displayed value.<br>Default value: the callback is not triggered when the value changes.<br>If the value is **undefined**, the default value is used. |

> **NOTE**
>
> 1. **min** must be less than or equal to **max**. If **min** is greater than **max**, **max** is used.

## NumberStyleOptions

Defines the list and compact counter attributes and events.

Inherits from [InlineStyleOptions](#inlinestyleoptions) and includes all attributes of that API. This section only describes the newly added attributes. For inherited attributes, see the parent API.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                                  | Read-Only| Optional| Description                                                        |
| --------------- | -------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| label           | [ResourceStr](ts-types.md#resourcestr) | No   | Yes  | Label text of the Counter.<br>Usage scenario: pass this parameter when you need to display descriptive text (such as 'Price', 'Quantity', etc.) next to the Counter.<br>Default value: '' <br>If the value is **undefined**, the default value is used. |
| onFocusIncrease | () => void                             | No   | Yes  | Callback invoked when the increase button of the current Counter component gains focus.<br>Usage scenario: pass this callback when you need to perform custom operations (such as changing styles, logging, etc.) when the increase button gains focus.<br>Default value: the callback is not triggered when the increase button gains focus.<br>If the value is **undefined**, the default value is used. |
| onFocusDecrease | () => void                             | No   | Yes  | Callback invoked when the decrease button of the current Counter component gains focus.<br>Usage scenario: pass this callback when you need to perform custom operations (such as changing styles, logging, etc.) when the decrease button gains focus.<br>Default value: the callback is not triggered when the decrease button gains focus.<br>If the value is **undefined**, the default value is used. |
| onBlurIncrease  | () => void                             | No   | Yes  | Callback invoked when the increase button of the current Counter component loses focus.<br>Usage scenario: pass this callback when you need to perform custom operations (such as validating input, saving state, etc.) when the increase button loses focus.<br>Default value: the callback is not triggered when the increase button loses focus.<br>If the value is **undefined**, the default value is used. |
| onBlurDecrease  | () => void                             | No   | Yes  | Callback invoked when the decrease button of the current Counter component loses focus.<br>Usage scenario: pass this callback when you need to perform custom operations (such as validating input, saving state, etc.) when the decrease button loses focus.<br>Default value: the callback is not triggered when the decrease button loses focus.<br>If the value is **undefined**, the default value is used. |

## DateStyleOptions

Defines the attributes and events of the inline date counter.

Inherits from [CommonOptions](#commonoptions).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                               | Read-Only| Optional| Description                                                     |
| ------------ | ----------------------------------- | ---- | --------------------------------------------------------- | --------------------------------------------------------- |
| year         | number                              | No  | Yes  | Initial year of the inline date type.<br>Default value: **1**<br>Value range: [1, 5000]<br>If the value is out of the range, the default value is used.<br>If the value is **undefined**, the default value is used. |
| month        | number                              | No  | Yes  | Initial month of the inline date type.<br>Default value: **1**<br>Value range: [1, 12]<br>If the value is out of the range, the default value is used.<br>If the value is **undefined**, the default value is used. |
| day          | number                              | No  | Yes  | Initial day of the inline date type.<br>Default value: **1**<br>Value range: [1, 31]<br>**Note:** The specific value range of days in each month is determined by the actual number of days in that month.<br>If the value is out of the range, the default value is used.<br>If the value is **undefined**, the default value is used. |
| onDateChange | (date: [DateData](#datedata)) => void | No  | Yes  | Callback invoked when the date changes to return the current date. Use case: Pass in this callback when you need to perform custom operations (such as updating associated UI, logging, saving state, etc.) upon date changes.<br>**date**: currently displayed date value.<br>Default value: no callback is triggered.<br>If the value is **undefined**, the default value is used. |

## DateData

Defines date attributes and methods, including year, month, and day.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ---- | ------------------------------------------------------------ |
| year  | number | No   | No   | Year of the inline date type. Value range: [1, 5000]. |
| month | number | No   | No   | Month of the inline date type. Value range: [1, 12]. |
| day   | number | No   | No   | Day of the inline date type. Value range: [1, 31]. The specific value is determined by the actual number of days in the month. |

### constructor

constructor(year: number, month: number, day: number)

DateData constructor for initializing date objects.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---------- | ------ |  ------ | ---------------------------- |
| year       | number | Yes | Year of the inline date type. Value range: [1, 5000]. |
| month      | number | Yes | Month of the inline date type. Value range: [1, 12]. |
| day        | number | Yes | Day of the inline date type. Value range: [1, 31]. The specific value is determined by the actual number of days in the month. |

### toString

toString(): string

Returns the current date value in the string format, which is **YYYY-MM-DD**.

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

![numberstyle](figures/numberstyle.gif)

### Example 4: Implementing an Inline Date Counter

This example implements an inline date counter by setting **type** to **CounterType.INLINE_DATE** and configuring **dateOptions**.

```ts
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

![datestyle](figures/datestyle.gif)

### Example 5: Implementing a Mirrored Layout

This example sets the **direction** attribute to implement a mirrored layout for list, compact, inline numeric, and inline date counters.

```ts
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

![direction](figures/counter_direction.png)