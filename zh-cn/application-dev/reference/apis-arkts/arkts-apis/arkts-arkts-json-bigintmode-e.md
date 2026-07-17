# BigIntMode

枚举BigInt的处理模式。

**起始版本：** 12

<!--Device-json-const enum BigIntMode--><!--Device-json-const enum BigIntMode-End-->

**系统能力：** SystemCapability.Utils.Lang

## DEFAULT

```TypeScript
DEFAULT = 0
```

不支持BigInt。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BigIntMode-DEFAULT = 0--><!--Device-BigIntMode-DEFAULT = 0-End-->

**系统能力：** SystemCapability.Utils.Lang

## PARSE_AS_BIGINT

```TypeScript
PARSE_AS_BIGINT = 1
```

将小于-(2^53-1)或大于(2^53-1)的整数解析为BigInt。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BigIntMode-PARSE_AS_BIGINT = 1--><!--Device-BigIntMode-PARSE_AS_BIGINT = 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## ALWAYS_PARSE_AS_BIGINT

```TypeScript
ALWAYS_PARSE_AS_BIGINT = 2
```

将所有整数解析为BigInt。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BigIntMode-ALWAYS_PARSE_AS_BIGINT = 2--><!--Device-BigIntMode-ALWAYS_PARSE_AS_BIGINT = 2-End-->

**系统能力：** SystemCapability.Utils.Lang

