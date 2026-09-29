# @Consume

```TypeScript
declare const Consume: PropertyDecorator & ((value: string) => PropertyDecorator)
```

[@Provide](arkts-arkui-common-comp-provide-d.md#provide) and **\@Consume** are used together for [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to implement two-way synchronization across component levels. This is applicable to scenarios where states need to be shared among multiple layers of nested components. It simplifies the communication logic between components by avoiding the complexity of layer-by-layer data transfer. As a data consumer, the variable decorated with **\@Consume** establishes a bidirectional binding relationship with the variable decorated with **\@Provide** through an alias or variable name. When a variable decorated with **\@Provide** or **\@Consume** changes, the change is automatically synchronized to the other party. An alias is preferred for matching. If no alias is set, a variable name is used for matching.

For details, see [@Provide and @Consume Decorators: Two-Way Synchronization with Descendant Components](../../../ui/state-management/arkts-provide-and-consume.md).

> **NOTE:** 
> 
> Since API version 20, **\@Consume** decorated variables support default value assignment. If no matching variable
> decorated with **\@Provide** is found, the **\@Consume** decorated variable initializes with its default value.
> When a matching variable decorated with **\@Provide** is found, the **\@Consume** decorated variable uses the
> value of the \@Provide decorated variable, and the default value is ignored.
> 
> Since API version 20, cross-BuilderNode pairing of **\@Provide** / **\@Consume** decorated variables is supported.
> In the BuilderNode scenario, a BuilderNode constructs nodes before being mounted to the tree. Therefore, the
> **\@Consume** decorated variable defined inside the BuilderNode must be assigned a default value. After the
> BuilderNode is mounted to the tree, the framework retrieves the **\@Provide** decorated variable closest to the
> BuilderNode again and establishes a two-way synchronization relationship with the variable.

value: Used to set an alias. If no alias is specified, a variable name is used by default. When an alias is set, an **\@Consume** decorated variable matches and binds to an **\@Provide** decorated variable through the alias. When no alias is set, matching and binding are performed through a variable name, implementing two-way data synchronization across component levels. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Consume: PropertyDecorator & ((value: string) => PropertyDecorator)--><!--Device-unnamed-declare const Consume: PropertyDecorator & ((value: string) => PropertyDecorator)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
