# @Component

```TypeScript
declare const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)
```

The **@Component** decorator can decorate a struct declared with the **struct** keyword. A struct decorated by **@Component** gains componentization capabilities, enabling UI encapsulation and reuse. It is suitable for scenarios such as building reusable custom components and splitting complex UIs. The **build** method must be implemented to describe the UI. A struct can be decorated by only one **@Component**.

For the development guide, see [Creating a Custom Component](../../../ui/state-management/arkts-create-custom-components.md).

> **NOTE:** 

> - Since API version 11, **@Component** can accept an optional parameter of the [ComponentOptions](arkts-arkui-common-comp-componentoptions-i.md) type.
> 
> - Since API version 26.0.0, **ComponentOptions** can accept the optional parameters **reusePool** and
> **poolAccepts** for configuring the global reuse pool. For the development guide, see
> [Global Reuse: Centralized Component Recycling and Reuse](../../../ui/state-management/arkts-global-reuse-pool.md).

options: Options of the **@Component** decorator, used to configure component freezing and global reuse. You can use **freezeWhenInactive** to control component freezing (applicable to scenarios where UI refresh is frozen when components such as page routing, **TabContent**, **LazyForEach**, and **Navigation** are inactive, to reduce unnecessary refreshes and optimize performance), and use **reusePool** and **poolAccepts** to configure the global reuse pool (applicable to scenarios where multiple parent components share reusable components of the same type and need to reuse recycled instances across parent components when switching via if or other means). For details about specific attributes, see **ComponentOptions**. When not specified, component freezing and global reuse are disabled. ClassDecorator: Class decorator. Developers do not need to pay attention to this return value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)--><!--Device-unnamed-declare const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
