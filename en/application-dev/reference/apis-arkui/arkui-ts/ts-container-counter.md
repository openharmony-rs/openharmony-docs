# Counter
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

The **Counter** component provides an operation to increase or decrease the number.

>  **NOTE**
>
> This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## Child Components

Supported


## APIs

Counter()

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### enableInc<sup>10+</sup>

enableInc(value: boolean)

Sets whether to enable the increment button.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| value  | boolean | Yes  | Whether to enable the increment button.<br>Default value: **true**. **true**: Enable the increment button. **false**: Disable the increment button.|

### enableDec<sup>10+</sup>

enableDec(value: boolean)

Sets whether to enable the decrement button.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| value  | boolean | Yes  | Whether to enable the decrement button.<br>Default value: **true**. **true**: Enable the decrement button. **false**: Disable the decrement button.|

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onInc

onInc(event: VoidCallback)

Invoked when the value increases.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                          | Mandatory| Description                                |
| ------ | --------------------------------------------- | ---- | ----------------------------------- |
| event  | [VoidCallback](ts-types.md#voidcallback12)    | Yes  | Callback invoked when the value increases.       |

### onDec

onDec(event: VoidCallback)

Invoked when the value decreases.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                          | Mandatory| Description                                |
| ------ | --------------------------------------------- | ---- | ----------------------------------- |
| event  | [VoidCallback](ts-types.md#voidcallback12)    | Yes  | Callback invoked when the value decreases.       |


## Example

This example shows the basic usage of the **Counter** component. Users can touch the **+** or **-** button to adjust the value.

```ts
// xxx.ets
@Entry
@Component
struct CounterExample {
  @State value: number = 0;

  build() {
    Column() {
      Counter() {
        Text(this.value.toString())
      }.margin(100)
      .onInc(() => {
        this.value++;
      })
      .onDec(() => {
        this.value--;
      })
    }.width("100%")
  }
}
```

![en-us_image_0000001212378424](figures/en-us_image_0000001212378424.gif)
