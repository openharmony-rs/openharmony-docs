# Priority

```TypeScript
export enum Priority
```

表示发送消息时的优先级枚举，各优先级对应关系请参考EventHandler等级定义。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

## IMMEDIATE

```TypeScript
IMMEDIATE = 1
```

立即执行优先级，对应EventHandler IMMEDIATE优先级。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 2
```

高优先级，对应EventHandler HIGH优先级。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 3
```

低优先级，对应EventHandler LOW优先级。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## IDLE

```TypeScript
IDLE = 4
```

后台优先级，对应EventHandler IDLE优先级。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

