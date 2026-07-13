# KeyPair

非对称密钥对包含公钥和私钥。

可以通过非对称密钥生成器[AsyKeyGenerator](arkts-cryptoarchitecture-asykeygenerator-i.md)、
[AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-asykeygeneratorbyspec-i.md)来生成。

> **说明：**
>
> KeyPair对象中的pubKey对象和priKey对象是KeyPair对象的成员。当KeyPair对象超出作用域时，其内部的pubKey对象和priKey对象将被析构。
>
> 业务方使用时应持有KeyPair对象的引用，而非内部pubKey或priKey对象的引用。

**起始版本：** 9

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

## priKey

```TypeScript
readonly priKey: PriKey
```

私钥。

**类型：** PriKey

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

## pubKey

```TypeScript
readonly pubKey: PubKey
```

公钥。

**类型：** PubKey

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

