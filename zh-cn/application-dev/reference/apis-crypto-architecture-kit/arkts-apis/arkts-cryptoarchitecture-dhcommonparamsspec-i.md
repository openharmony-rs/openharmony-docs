# DHCommonParamsSpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-asykeyspec-i.md)的子类，用于指定DH算法中公私钥包含的公共参数。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法
创建密钥生成器。

**继承/实现关系：** DHCommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-asykeyspec-i.md)

**起始版本：** 11

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## g

```TypeScript
g: bigint
```

DH算法中的参数g。

**类型：** bigint

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## l

```TypeScript
l: number
```

DH算法中私钥长度，单位为bits。

**类型：** number

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## p

```TypeScript
p: bigint
```

指定DH算法中大素数p。

**类型：** bigint

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

