# @Consume: Implementing Two-Way Synchronization with Descendant Components

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

**@Provide** and **@Consume** are used together for state management V1 to implement two-way synchronization across component levels. This is applicable to scenarios where states need to be shared among multiple layers of nested components. It simplifies the communication logic between components by avoiding the complexity of layer-by-layer data transfer. As a data consumer, the variable decorated with **@Consume** establishes a bidirectional binding relationship with the variable decorated with **@Provide** through an alias or variable name. When a variable decorated with **@Provide** or **@Consume** changes, the change is automatically synchronized to the other decorator. An alias is preferred for matching. If no alias is set, a variable name is used for matching.

For details, see [@Provide and @Consume Decorators: Two-Way Synchronization with Descendant Components](../../../ui/state-management/arkts-provide-and-consume.md).

> **NOTE**
>
> This decorator is supported since API version 7.
>
> Since API version 20, **@Consume** decorated variables support default value assignment. If no matching variable decorated with **@Provide** is found, the **@Consume** decorated variable initializes with its default value. When a matching variable decorated with **@Provide** is found, the **@Consume** decorated variable uses the value of the **@Provide** decorated variable, and the default value is ignored.

## @Consume

const Consume: PropertyDecorator & ((value: string) => PropertyDecorator)

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| value  | string | No  | Alias. By default, a variable name is used. After an alias is set, the **@Consume** decorated variable matches and binds the variable decorated with **@Provide** using the alias, implementing bidirectional data synchronization across component levels.|

**Returns**

| Type| Description|
| --- | --- |
| PropertyDecorator | Property decorator. You do not need to concern yourself with this return value.|

**Example:**

```ts
@Entry
@Component
struct Index {
  @Provide message: string = 'aaa'; // The @Provide decorated variable provides data, and the variable name 'message' is used as the alias.

  build() {
    Column() {
      Child()
    }
  }
}

@Component
struct Child {
  @Consume message: string; // The @Consume decorated variable consumes the data. No alias is set, and the variable name 'message' is used to establish a pairing relationship with the @Provide decorated variable.

  build() {
    Column() {
      Text(`${this.message}`)
    }
  }
}
```
