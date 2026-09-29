# @Provide

```TypeScript
declare const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)
```

**@Provide** and [@Consume](arkts-arkui-common-comp-consume-d.md#consume) are used together for [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to implement two-way synchronization across component levels. This is applicable to scenarios where state data needs to be transferred across multiple component levels to avoid layer-by-layer transfer. It can solve the problem of complex state transfer when there are many component levels. Variables decorated with **@Provide** are used as data sources. Bidirectional binding relationships are established between the data sources and variables decorated with **@Consume** through aliases or variable names. When a variable decorated with **@Provide** or **@Consume** changes, the change is automatically synchronized to the other party.

For details, see [@Provide and @Consume Decorators: Two-Way Synchronization with Descendant Components](../../../ui/state-management/arkts-provide-and-consume.md).

value: Used to set an alias or used as an alias that can be overridden. <br> If the type is string, the value is directly used as an alias. Descendant components can access data through this alias. <br> When the type is ProvideOptions, if **allowOverride** is set, the value will be used as an alias and the alias can be overridden; if **allowOverride** is not set, an alias is a variable name and cannot be overridden. <br> When this parameter is not specified, a variable name is used and cannot be overridden. If an **@Provide** decorated variable is defined with the same name in this case, an error will be reported at runtime. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)--><!--Device-unnamed-declare const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
