# @State

```TypeScript
declare const State: PropertyDecorator
```

**@State** is used for [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to convert common variables within a custom component into state variables. When the state variables change, the UI in the component is re-rendered. It is applicable to scenarios where mutable states need to be managed within a component.

For details, see [@State Decorator: State Owned by Component](../../../ui/state-management/arkts-state.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const State: PropertyDecorator--><!--Device-unnamed-declare const State: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
