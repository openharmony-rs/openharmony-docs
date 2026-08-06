# DHCommonParamsSpec

密钥参数[AsyKeySpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，用于指定DH算法中公私钥包含的公共参数。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 方法创建密钥生成器。

**继承/实现关系：** DHCommonParamsSpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface DHCommonParamsSpec extends AsyKeySpec--><!--Device-cryptoFramework-interface DHCommonParamsSpec extends AsyKeySpec-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHCommonParamsSpec-g: bigint--><!--Device-DHCommonParamsSpec-g: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## l

```TypeScript
l: int
```

DH算法中私钥长度，单位为bits。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHCommonParamsSpec-l: int--><!--Device-DHCommonParamsSpec-l: int-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHCommonParamsSpec-p: bigint--><!--Device-DHCommonParamsSpec-p: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

