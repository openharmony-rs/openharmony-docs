# ECCPubKeySpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)的子类，用于指定ECC算法中公钥包含的参数。 &lt;br&gt;在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createAsyKeyGeneratorBySpec) 方法创建密钥生成器。

**继承/实现关系：** ECCPubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface ECCPubKeySpec--><!--Device-cryptoFramework-interface ECCPubKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## params

```TypeScript
params: ECCCommonParamsSpec
```

指定ECC算法中公私钥都包含的公共参数。

**类型：** [ECCCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-ecccommonparamsspec-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCPubKeySpec-params: ECCCommonParamsSpec--><!--Device-ECCPubKeySpec-params: ECCCommonParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## pk

```TypeScript
pk: Point
```

指定ECC算法的公钥pk。

**类型：** Point

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECCPubKeySpec-pk: Point--><!--Device-ECCPubKeySpec-pk: Point-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

