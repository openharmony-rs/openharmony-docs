# DHPubKeySpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)的子类，用于指定DH算法中公钥包含的参数。 &lt;br&gt;在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createAsyKeyGeneratorBySpec) 方法创建密钥生成器。

**继承/实现关系：** DHPubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface DHPubKeySpec--><!--Device-cryptoFramework-interface DHPubKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## params

```TypeScript
params: DHCommonParamsSpec
```

指定DH算法中公私钥都包含的公共参数。

**类型：** [DHCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-dhcommonparamsspec-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHPubKeySpec-params: DHCommonParamsSpec--><!--Device-DHPubKeySpec-params: DHCommonParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## pk

```TypeScript
pk: bigint
```

DH算法中的公钥pk。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHPubKeySpec-pk: bigint--><!--Device-DHPubKeySpec-pk: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

