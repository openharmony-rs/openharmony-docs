# BigIntMode

```TypeScript
const enum BigIntMode
```

枚举BigInt的处理模式。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## DEFAULT

```TypeScript
DEFAULT = 0
```

不支持BigInt。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## PARSE_AS_BIGINT

```TypeScript
PARSE_AS_BIGINT = 1
```

将小于-(2^53-1)或大于(2^53-1)的整数解析为BigInt。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ALWAYS_PARSE_AS_BIGINT

```TypeScript
ALWAYS_PARSE_AS_BIGINT = 2
```

将所有整数解析为BigInt。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

