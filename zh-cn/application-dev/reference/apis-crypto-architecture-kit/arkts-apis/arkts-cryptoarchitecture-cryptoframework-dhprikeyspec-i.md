# DHPriKeySpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)的子类，用于指定DH算法中私钥包含的参数。

在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createAsyKeyGeneratorBySpec-1)方法
创建密钥生成器。

**继承/实现关系：** DHPriKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)

**起始版本：** 11

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## params

```TypeScript
params: DHCommonParamsSpec
```

指定DH算法中公私钥都包含的公共参数。

**类型：** DHCommonParamsSpec

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

## sk

```TypeScript
sk: bigint
```

DH算法中的私钥sk。

**类型：** bigint

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

