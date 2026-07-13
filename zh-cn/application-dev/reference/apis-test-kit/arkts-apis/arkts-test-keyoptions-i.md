# KeyOptions

表示按键操作的选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Test.UiTest

## key1

```TypeScript
key1?: number
```

操作期间要按下的第一个键码。
如果未设置，将不会注入任何按键事件。
如果仅设置 key2 而未设置 key1，将会导致业务错误 17000007。

**类型：** number

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## key2

```TypeScript
key2?: number
```

操作期间要按下的第一个键码。
如果未设置，将不会注入任何按键事件。
如果仅设置 key2 而未设置 key1，将会导致业务错误 17000007。

**类型：** number

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

