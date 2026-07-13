# AsyKeySpecType

表示密钥参数类型的枚举。

**起始版本：** 10

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## COMMON_PARAMS_SPEC

```TypeScript
COMMON_PARAMS_SPEC = 0
```

表示公私钥中包含的公共参数。使用此类型的参数可以调用
[generateKeyPair](arkts-cryptoarchitecture-asykeygeneratorbyspec-i.md#generatekeypair-1)
随机生成密钥对。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## PRIVATE_KEY_SPEC

```TypeScript
PRIVATE_KEY_SPEC = 1
```

表示私钥中包含的参数。使用此类型的参数可以调用
[generatePriKey](arkts-cryptoarchitecture-asykeygeneratorbyspec-i.md#generateprikey-1)生成
指定的私钥。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## PUBLIC_KEY_SPEC

```TypeScript
PUBLIC_KEY_SPEC = 2
```

表示公钥中包含的参数。使用此类型的参数可以调用
[generatePubKey](arkts-cryptoarchitecture-asykeygeneratorbyspec-i.md#generatepubkey-1)生成
指定的公钥。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## KEY_PAIR_SPEC

```TypeScript
KEY_PAIR_SPEC = 3
```

表示公私钥中包含的全量参数。使用此类型的参数可以调用
[generateKeyPair](arkts-cryptoarchitecture-asykeygeneratorbyspec-i.md#generatekeypair-1)
生成指定的密钥对。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

