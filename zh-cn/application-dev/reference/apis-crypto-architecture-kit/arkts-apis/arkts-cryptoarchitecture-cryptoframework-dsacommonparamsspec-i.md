# DSACommonParamsSpec

密钥参数[AsyKeySpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，用于指定DSA算法中公私钥包含的公共参数，随机生成公/私钥。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 方法创建密钥生成器。

**继承/实现关系：** DSACommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface DSACommonParamsSpec extends AsyKeySpec--><!--Device-cryptoFramework-interface DSACommonParamsSpec extends AsyKeySpec-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DSACommonParamsSpec-g: bigint--><!--Device-DSACommonParamsSpec-g: bigint-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DSACommonParamsSpec-p: bigint--><!--Device-DSACommonParamsSpec-p: bigint-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DSACommonParamsSpec-q: bigint--><!--Device-DSACommonParamsSpec-q: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

