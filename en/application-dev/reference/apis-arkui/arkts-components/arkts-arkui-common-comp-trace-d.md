# @Trace

```TypeScript
declare const Trace: PropertyDecorator
```

**@Trace** is a property decorator used in [state management V2](../../../ui/state-management/arkts-state-management-overview.md). [@ObservedV2](arkts-arkui-common-comp-observedv2-d.md#observedv2) and **@Trace** are used together to decorate classes and class properties, enhancing the observation capability for decorated classes and properties. That is, they can recursively observe changes in property values of nested objects and trigger automatic UI refresh. They are applicable to scenarios where precise observation and management of class property changes are required.

For details, see [@ObservedV2 and @Trace Decorators: Observing Class Property Changes](../../../ui/state-management/arkts-new-observedV2-and-trace.md).

Declares an observable property. **@Trace** must be used together with **@ObservedV2** and takes effect only in classes decorated with **@ObservedV2**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-unnamed-declare const Trace: PropertyDecorator--><!--Device-unnamed-declare const Trace: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
