# DSACommonParamsSpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-asykeyspec-i.md)的子类，用于指定DSA算法中公私钥包含的公共参数，随机生成公/私钥。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法
创建密钥生成器。

**继承/实现关系：** DSACommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-asykeyspec-i.md)

**起始版本：** 10

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## g

```TypeScript
g: bigint
```

DSA算法的参数g。

**类型：** bigint

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## p

```TypeScript
p: bigint
```

DSA算法的素模数p。

**类型：** bigint

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## q

```TypeScript
q: bigint
```

DSA算法中密钥参数q（p-1的素因子）。

**类型：** bigint

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

