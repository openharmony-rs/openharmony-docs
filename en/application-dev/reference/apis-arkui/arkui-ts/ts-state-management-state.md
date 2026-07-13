# @State: State Owned by Component

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

**@State** is used for state management V1 to convert common variables in a custom component into state variables. When the state variables change, the UI in the component is re-rendered. It is applicable to scenarios where mutable states need to be managed within a component.

For details, see [@State Decorator: State Owned by Component](../../../ui/state-management/arkts-state.md).

> **NOTE**
>
> This decorator is supported since API version 7.

## @State

const State: PropertyDecorator

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Example:**

```ts
@Entry
@Component
struct StateExample {
  @State count: number = 0; // State variable.

  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```
