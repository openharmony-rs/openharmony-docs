# RSAPubKeySpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-asykeyspec-i.md)的子类，用于指定RSA算法中公钥包含的参数。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法
创建密钥生成器。

**继承/实现关系：** RSAPubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-asykeyspec-i.md)

**起始版本：** 10

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## params

```TypeScript
params: RSACommonParamsSpec
```

指定RSA算法中公私钥都包含的公共参数。

**类型：** RSACommonParamsSpec

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## pk

```TypeScript
pk: bigint
```

指定RSA算法的公钥pk。

**类型：** bigint

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

