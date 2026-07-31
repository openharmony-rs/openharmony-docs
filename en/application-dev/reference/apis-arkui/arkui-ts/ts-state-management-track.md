# @Track: Implementing Class Object Property-Level Updates

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

**@Track** is used in state management V1 to observe property-level updates of class objects, reducing unnecessary UI re-rendering.

For details, see [@Track Decorator: Implementing Class Object Property-Level Updates](../../../ui/state-management/arkts-track.md).

> **NOTE**
>
> This decorator is supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## @Track

const Track: PropertyDecorator

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Example:**

```ts
class Info {
  // Add the observation capability for the property decorated with @Track.
  @Track id: number;
  age: string = '';

  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info(1);

  build() {
    Column() {
      Text(`id: ${this.info.id}`)
      Button('change')
        .onClick(() => {
          // Modify the property decorated with @Track to trigger a UI update.
          this.info.id++;
        })
    }
  }
}
```
