# @Sendable

```TypeScript
declare const Sendable: ClassDecorator
```

Defining Sendable ClassDecorator The Sendable decorator can be used only for classes. A class with this decorator is marked as sendable, and the class object can be shared globally. Since 12, the Sendable decorator can be used for function and typeAlias also. A function with this decorator is marked as sendable, and the function can be an shareable property of sendable-class object. A typeAlias with this decorator is marked as sendable, and the typeAlias can be used to declare properties, variables, and arguments that need to be assigned with sendable-function.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
