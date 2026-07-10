# @Computed: Declaring Computed Properties

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

**@Computed** is a method decorator used to decorate **getter** methods in state management V2. For details, see [@Computed Decorator: Declaring Computed Properties](../../../ui/state-management/arkts-new-computed.md).

> **NOTE**
>
> This decorator is supported since API version 12.

## @Computed

const Computed: MethodDecorator

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Example:**

```ts
@Entry
@ComponentV2
  struct Index {
  @Local firstName: string = 'Hua';
  @Local lastName: string = 'Li';

  // Declare the computed getter function to avoid repeated calculation.
  @Computed
  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

  build() {
    Column() {
      Text(`${this.fullName}`)
    }
  }
}
```
