# @Observed: Observing Property Changes in Nested Class Objects

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=627767fa3527b3e4ea03a35d3df7c7dd0cac695b translatedAt=2026-09-02T11:22:19.369Z pushedAt=2026-09-03T01:55:52.476Z -->

**\@Observed** is a class decorator used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1) to observe property changes of nested class objects.

For details, see [@Observed and @ObjectLink Decorators: Observing Property Changes in Nested Class Objects](../../../ui/state-management/arkts-observed-and-objectlink.md).

> **NOTE**
>
> This decorator is supported since API version 7.

## @Observed

const Observed: ClassDecorator

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Example:**

```ts
// Use @Observed to make the property changes of the Info class observable by the ArkUI framework.
@Observed
class Info {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info('Tom');
  build() {
    Column() {
      Text(`name: ${this.info.name}`)
    }
  }
}
```



