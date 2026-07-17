# @Local: Representing the Internal State of Components

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

**@Local** is used in state management V2 to represent the internal state of components, enabling the observation of variables within custom components. It is applicable to scenarios where partial states (such as counters and switch states) need to be maintained and observed within custom components. Using **@Local** can simplify the internal state management logic of components. When the state changes, the UI is automatically refreshed without manual management.

For details, see [@Local Decorator: Representing the Internal State of Components](../../../ui/state-management/arkts-new-local.md).

> **NOTE**
>
> This decorator is supported since API version 12.

## @Local

const Local: PropertyDecorator

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Example:**

```ts
@Entry
@ComponentV2
struct LocalExample {
  @Local count: number = 0; // Define a Local variable.
  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```
