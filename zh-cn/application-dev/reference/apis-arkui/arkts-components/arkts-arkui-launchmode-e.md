# LaunchMode

路由栈操作模式。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

系统默认的栈操作模式。

push操作会将指定的NavDestination入栈；replace操作会将当前栈顶NavDestination替换。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MOVE_TO_TOP_SINGLETON

```TypeScript
MOVE_TO_TOP_SINGLETON = 1
```

从栈底向栈顶查找，如果指定的名称已经存在，则将对应的NavDestination页面移到栈顶（replace操作会将最后的栈顶替换成指定的NavDestination），否则行为和STANDARD一致。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## POP_TO_SINGLETON

```TypeScript
POP_TO_SINGLETON = 2
```

从栈底向栈顶查找，如果指定的名称已经存在，则将其上方的NavDestination页面全部移除（replace操作会将最后的栈顶替换成指定的NavDestination），否则行为和STANDARD一致。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NEW_INSTANCE

```TypeScript
NEW_INSTANCE = 3
```

创建新的NavDestination实例。与STANDARD模式相比，该方法不会复用栈中同名实例。并且指定该模式时，新创建的页面默认会执行push动效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

