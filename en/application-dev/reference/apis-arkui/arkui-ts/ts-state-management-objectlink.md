# @ObjectLink: Observing Property Changes in Nested Class Objects

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

**@ObjectLink** is used in state management V1 to receive instances of classes decorated with **@Observed** and establish two-way data binding with the data source in a parent component.

For details, see [@Observed and @ObjectLink Decorators: Observing Property Changes in Nested Class Objects](../../../ui/state-management/arkts-observed-and-objectlink.md).

> **NOTE**
>
> This decorator is supported since API version 7.

## @ObjectLink

const ObjectLink: PropertyDecorator

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Example:**

```ts
@Observed
class Info {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

@Component
struct Child {
  @ObjectLink info: Info; // @ObjectLink receives the @State decorated variable of the parent component.
  build() {
    Column() {
      Text(`name: ${this.info.name}`)
    }
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info('Tom');
  build() {
    Column() {
      Child({info: this.info}) // The @State decorated variable is used as the initial value of @ObjectLink.
    }
  }
}
```
