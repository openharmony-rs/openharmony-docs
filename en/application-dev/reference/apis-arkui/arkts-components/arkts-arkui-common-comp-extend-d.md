# @Extend

```TypeScript
declare const Extend: MethodDecorator & ((value: any) => MethodDecorator)
```

The @Extend decorator is used to extend the styles of specified components. It supports defining multiple style attributes in a unified manner within the decorated function, and enables flexible style reuse through parameter passing. This is suitable for scenarios where the same styles need to be applied to multiple components, reducing style code duplication.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
