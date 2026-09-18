# @Sendable

```TypeScript
declare const Sendable: ClassDecorator
```

Defining Sendable ClassDecorator The Sendable decorator can be used only for classes. A class with this decorator is marked as sendable, and the class object can be shared globally. Since 12, the Sendable decorator can be used for function and typeAlias also. A function with this decorator is marked as sendable, and the function can be an shareable property of sendable-class object. A typeAlias with this decorator is marked as sendable, and the typeAlias can be used to declare properties, variables, and arguments that need to be assigned with sendable-function.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
