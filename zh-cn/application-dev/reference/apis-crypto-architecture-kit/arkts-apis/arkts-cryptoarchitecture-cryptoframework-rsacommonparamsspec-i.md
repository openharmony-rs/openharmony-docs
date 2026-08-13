# RSACommonParamsSpec

密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)的子类，用于指定RSA算法中公私钥包含的公共参数，随机生成公/私钥。 &lt;br&gt;在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createAsyKeyGeneratorBySpec) 方法创建密钥生成器。

**继承/实现关系：** RSACommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md#AsyKeySpec)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface RSACommonParamsSpec--><!--Device-cryptoFramework-interface RSACommonParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## n

```TypeScript
n: bigint
```

指定模数n。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RSACommonParamsSpec-n: bigint--><!--Device-RSACommonParamsSpec-n: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

