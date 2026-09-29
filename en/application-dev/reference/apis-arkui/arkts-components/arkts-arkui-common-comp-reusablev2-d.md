# @ReusableV2

```TypeScript
declare const ReusableV2: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)
```

To reduce the performance overhead caused by repeatedly creating and destroying custom components, developers can use the **@ReusableV2** decorator on custom components decorated by [@ComponentV2](arkts-arkui-common-comp-componentv2-d.md#componentv2) to achieve component reuse. This is applicable to scenarios where components need to be repeatedly created and destroyed, such as list scrolling and frequent toggling of component visibility, and supports configuring memory optimization strategies through parameters.

Declares a reusable custom component. This decorator must be used together with **@ComponentV2** to decorate a custom component for component reuse.

See the development guide: [@ReusableV2 Decorator: Reusing V2 Components](../../../ui/state-management/arkts-new-reusableV2.md).

For the principles and applicable scenarios of component reuse, see [Component Reuse](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-component-reuse).

options: Configuration parameters of the reusable custom component, used to configure the memory optimization policy. This parameter can be configured for optimization in scenarios where a large number of reusable components exist (for example, dozens or more reusable component instances on the same page), or when the device memory is limited and the app memory usage is high. No memory optimization policy is applied by default.**Since:** 26.0.0 ClassDecorator: Class decorator. You do not need to pay attention to this return value.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare const ReusableV2: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)--><!--Device-unnamed-declare const ReusableV2: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
