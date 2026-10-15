# @Reusable

```TypeScript
declare const Reusable: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)
```

To reduce the performance overhead caused by repeatedly creating and destroying custom components, you can use \@Reusable to decorate custom components decorated by \@Component, thereby implementing component reuse. \@Reusable supports identifying different types of reusable components through **reuseId**, provides the **aboutToReuse** callback to receive reuse parameters, and supports configuring memory optimization policies. This decorator is applicable to scenarios that require repeatedly creating and destroying components, such as list scrolling and frequent switching of component display and hiding.

See the development guide: [\@Reusable Decorator: Reusing V1 Components](../../../ui/state-management/arkts-reusable.md).

options: Parameters of the reusable custom component, used to configure the memory optimization policy. If this parameter is not specified, no memory optimization policy is applied. You are advised to configure this parameter in scenarios where components are frequently created and destroyed to achieve memory optimization.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-declare const Reusable: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)--><!--Device-unnamed-declare const Reusable: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
