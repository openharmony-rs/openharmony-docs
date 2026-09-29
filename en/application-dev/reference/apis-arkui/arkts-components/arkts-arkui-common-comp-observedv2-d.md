# @ObservedV2

```TypeScript
declare const ObservedV2: ClassDecorator
```

**\@ObservedV2** is a class decorator used in [state management V2](../../../ui/state-management/arkts-state-management-overview.md). **\@ObservedV2** is used together with [@Trace](arkts-arkui-common-comp-trace-d.md#trace) to decorate classes and class properties, enhancing the observation capability for decorated classes and properties. Compared with [@Observed](arkts-arkui-common-comp-observed-d.md#observed) in [state management V1](../../../ui/state-management/arkts-state-management-overview.md), **\@ObservedV2** provides more fine-grained, property-level in-depth observation capabilities. It is suitable for scenarios where changes in nested object properties need to be precisely tracked to drive UI updates, effectively improving the performance and flexibility of state management.

For details, see [@ObservedV2 and @Trace Decorators: Observing Class Property Changes](../../../ui/state-management/arkts-new-observedV2-and-trace.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-unnamed-declare const ObservedV2: ClassDecorator--><!--Device-unnamed-declare const ObservedV2: ClassDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
