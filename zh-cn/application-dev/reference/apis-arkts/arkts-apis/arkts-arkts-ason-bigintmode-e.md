# BigIntMode

定义处理BigInt模式的枚举。

**起始版本：** 12

<!--Device-ASON-const enum BigIntMode--><!--Device-ASON-const enum BigIntMode-End-->

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

当整数小于-(2^53-1)或大于(2^53-1)时，解析为BigInt。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BigIntMode-PARSE_AS_BIGINT = 1--><!--Device-BigIntMode-PARSE_AS_BIGINT = 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## ALWAYS_PARSE_AS_BIGINT

```TypeScript
ALWAYS_PARSE_AS_BIGINT = 2
```

所有整数都解析为BigInt。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BigIntMode-ALWAYS_PARSE_AS_BIGINT = 2--><!--Device-BigIntMode-ALWAYS_PARSE_AS_BIGINT = 2-End-->

**系统能力：** SystemCapability.Utils.Lang

