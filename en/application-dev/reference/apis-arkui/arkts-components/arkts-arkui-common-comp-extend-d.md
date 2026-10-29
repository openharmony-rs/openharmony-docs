# @Extend

```TypeScript
declare const Extend: MethodDecorator
  & ((value: any) => MethodDecorator) & ExtendVersionDecorator
```

The @Extend decorator is used to extend the styles of specified components. It supports defining multiple style attributes in a unified manner within the decorated function, and enables flexible style reuse through parameter passing. This is suitable for scenarios where the same styles need to be applied to multiple components, reducing style code duplication.

value: Target built-in UI component type (such as **Text** and **Column**) for which the style is to be extended. Pass in the component type rather than a component instance. Custom components are not supported. The style attributes defined in the @Extend decorator will be bound to this component type, so that they can be called on the component in a chained manner. MethodDecorator: Method decorator. Developers do not need to pay attention to this return value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Extend: MethodDecorator  & ((value: any) => MethodDecorator) & ExtendVersionDecorator--><!--Device-unnamed-declare const Extend: MethodDecorator  & ((value: any) => MethodDecorator) & ExtendVersionDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
