# InputEventInterceptAction

```TypeScript
declare enum InputEventInterceptAction
```

输入事件拦截动作枚举，用于控制输入事件是否继续传递到UI框架，适用于需要按业务规则允许或阻止输入事件继续传递的场景。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTINUE

```TypeScript
CONTINUE = 0
```

允许事件继续传递到UI框架。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BLOCK

```TypeScript
BLOCK = 1
```

阻止事件传递到UI框架。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
