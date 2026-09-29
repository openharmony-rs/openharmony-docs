# @Track

```TypeScript
declare const Track: PropertyDecorator
```

**@Track** is used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to implement property-level precise observation by decorating specified properties of a class object. When a property decorated with **@Track** changes, the system updates only the UI components that depend on that property, thereby reducing unnecessary UI re-rendering. It is applicable to scenarios where a class object contains many properties and redundant UI refreshes need to be reduced to optimize rendering performance.

For details, see [@Track Decorator: Implementing Class Object Property-Level Updates](../../../ui/state-management/arkts-track.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-unnamed-declare const Track: PropertyDecorator--><!--Device-unnamed-declare const Track: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
