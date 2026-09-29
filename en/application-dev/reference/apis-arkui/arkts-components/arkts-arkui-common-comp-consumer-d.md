# @Consumer

```TypeScript
declare const Consumer: (aliasName?: string) => PropertyDecorator
```

Decorates a data consumer to obtain data from a data source. It is used together with **\@Provider** in state management V2 to implement bidirectional data synchronization across component levels. If the variable decorated with **\@Consumer** does not find the variable decorated with **\@Provider** with the matching alias in the component tree, it uses its own initial value and does not perform data synchronization.

For details, see [@Provider and @Consumer Decorators: Synchronizing Across Component Levels in a Two-Way Manner](../../../ui/state-management/arkts-new-provider-and-consumer.md).

aliasName: Alias, which is used as the matching identifier for bidirectional data synchronization between variables decorated with **\@Consumer** and **\@Provider**. The alias must be the same as that of the **\@Provider** decorated variable. By default, the alias is the variable name. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-unnamed-declare const Consumer: (aliasName?: string) => PropertyDecorator--><!--Device-unnamed-declare const Consumer: (aliasName?: string) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
