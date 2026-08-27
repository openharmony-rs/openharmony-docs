# BigIntMode

定义处理BigInt的模式。由于JSON规范不支持BigInt类型，且Number精度范围为-(2^53-1)到(2^53-1)，本模块提供三种模式以适配不同场景的整数精度需求。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## DEFAULT

```TypeScript
DEFAULT = 0
```

不支持BigInt，超大整数可能丢失精度。适用于不需要处理超大整数的常规JSON解析场景。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## PARSE_AS_BIGINT

```TypeScript
PARSE_AS_BIGINT = 1
```

当整数小于-(2^53-1)或大于(2^53-1)时，解析为BigInt，普通整数仍按number处理。适用于JSON中可能包含超出安全整数范围的大整数、但普通整数不需要BigInt的场景。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ALWAYS_PARSE_AS_BIGINT

```TypeScript
ALWAYS_PARSE_AS_BIGINT = 2
```

所有整数都解析为BigInt。适用于需要所有整数都以BigInt形式保留精度的场景，如高精度数值计算。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
