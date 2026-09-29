# @Prop

```TypeScript
declare const Prop: PropertyDecorator
```

**@Prop** is used for [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to receive values passed from external sources and establish a one-way synchronization relationship with parent components. When the state variables decorated with [@State](arkts-arkui-common-comp-state-d.md#state) in the parent component change, the changes are synchronously updated to the corresponding **@Prop** decorated variables in the child component, triggering the child component to re-render. **@Prop** uses a unidirectional data flow mechanism. Changes to **@Prop** decorated variables in child components take effect only within the child components and are not synchronized back to the parent component. This is applicable when child components need to respond to state changes of parent components but do not need to modify the parent component's state reversely.

For details, see [@Prop Decorator: Implementing One-Way Synchronization from Parent to Child Components](../../../ui/state-management/arkts-prop.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Prop: PropertyDecorator--><!--Device-unnamed-declare const Prop: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
