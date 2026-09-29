# @Provider

```TypeScript
declare const Provider: (aliasName?: string) => PropertyDecorator
```

**@Provider** and [@Consumer](arkts-arkui-common-comp-consumer-d.md#consumer) are used together in [state management V2](../../../ui/state-management/arkts-state-management-overview.md) to implement bidirectional data synchronization across component levels. **@Provider** decorates a data provider to provide data for child components. It is applicable to scenarios where state data needs to be shared across multiple layers of components (with deep component layers) to avoid layer-by-layer data transfer. This simplifies the state management process and reduces the coupling between components.

For details, see [@Provider and @Consumer Decorators: Synchronizing Across Component Levels in a Two-Way Manner](../../../ui/state-management/arkts-new-provider-and-consumer.md).

Decorates a data provider to provide data for child components. It is used together with **@Consumer** in state management V2 to implement bidirectional data synchronization across component levels.

aliasName: Alias, which is used as the matching identifier for bidirectional data synchronization between variables decorated with **@Provider** and **@Consumer**. The alias must be the same as that of the **@Consumer** decorated variable. By default, the alias is the variable name. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-unnamed-declare const Provider: (aliasName?: string) => PropertyDecorator--><!--Device-unnamed-declare const Provider: (aliasName?: string) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
