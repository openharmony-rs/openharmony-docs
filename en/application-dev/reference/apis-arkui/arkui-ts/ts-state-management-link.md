# @Link: Two-Way Synchronization Between Parent and Child Components

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=79e4597a11fe0470e85a7a6ec526decbb0cbcff4 translatedAt=2026-07-15T07:36:24.771Z pushedAt=2026-07-15T08:48:52.774Z -->

**\@Link** is used for [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1) to receive the reference of the state variable passed by the parent component and establish two-way data binding between the parent and child components. It is applicable to scenarios where the parent component's state needs to be directly changed in the child component and the communication between the parent and child components needs to be simplified.

For details, see [@Link Decorator: Implementing Two-Way Synchronization Between Parent and Child Components](../../../ui/state-management/arkts-link.md).

> **NOTE**
>
> This decorator is supported since API version 7.

## @Link

const Link: PropertyDecorator

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Example:**

```ts
@Component
struct Child {
  // Use @Link to declare a variable that has bidirectional binding behavior and establish bidirectional synchronization with the data source of the parent component.
  @Link msg: string;

  build() {
    Column() {
      Text(this.msg)
      Button('change')
        .onClick(() => {
          // The modification will be synchronized to the parent component.
          this.msg += '~';
        })
    }
  }
}

@Entry
@Component
struct LinkExample {
  // Use @State to declare a state variable as the data source of @Link.
  @State message: string = 'Hello';

  build() {
    Column() {
      // Create a child component Child and use @Link to bind message to msg of the child component in two-way mode.
      Child({ msg: this.message })
    }
  }
}
```