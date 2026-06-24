# AsyKeySpecType

```TypeScript
enum AsyKeySpecType
```

表示密钥参数类型的枚举。

**起始版本：** 10

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## COMMON_PARAMS_SPEC

```TypeScript
COMMON_PARAMS_SPEC = 0
```

表示公私钥中包含的公共参数。使用此类型的参数可以调用
[generateKeyPair](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generateKeyPair-1)
随机生成密钥对。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## PRIVATE_KEY_SPEC

```TypeScript
PRIVATE_KEY_SPEC = 1
```

表示私钥中包含的参数。使用此类型的参数可以调用
[generatePriKey](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generatePriKey-1)生成
指定的私钥。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## PUBLIC_KEY_SPEC

```TypeScript
PUBLIC_KEY_SPEC = 2
```

表示公钥中包含的参数。使用此类型的参数可以调用
[generatePubKey](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generatePubKey-1)生成
指定的公钥。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## KEY_PAIR_SPEC

```TypeScript
KEY_PAIR_SPEC = 3
```

表示公私钥中包含的全量参数。使用此类型的参数可以调用
[generateKeyPair](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md#generateKeyPair-1)
生成指定的密钥对。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

