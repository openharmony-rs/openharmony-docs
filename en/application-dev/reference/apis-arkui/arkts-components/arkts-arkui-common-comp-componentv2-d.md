# @ComponentV2

```TypeScript
declare const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)
```

**@ComponentV2** is primarily used with state management V2. Compared with [@Component](../../../ui/state-management/arkts-create-custom-components.md), **@ComponentV2** supports deep observation and deep listening of objects. The decorator is highly easy to use and extensible, and is suitable for scenarios requiring deep observation of nested object states. Unless otherwise specified, custom components decorated with **@ComponentV2** behave the same as those decorated with **@Component**.

See the development guide: [@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md).

> **NOTE:** 

> - Since API version 26.0.0, the [ComponentOptions](arkts-arkui-common-comp-componentoptions-i.md)parameter of \@ComponentV2 supports the optional attributes `reusePool` and `poolAccepts` for configuring the global reuse pool. See the development guide:[Global Reuse: Centralized Component Recycling and Reuse](../../../ui/state-management/arkts-global-reuse-pool.md).

options: Options of the **@ComponentV2** decorator. Pass this parameter for custom configuration when the component freezing or global reuse feature needs to be enabled. If not specified, both the component freezing and global reuse features are disabled. ClassDecorator: Class decorator. Developers do not need to pay attention to this return value.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-unnamed-declare const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)--><!--Device-unnamed-declare const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
