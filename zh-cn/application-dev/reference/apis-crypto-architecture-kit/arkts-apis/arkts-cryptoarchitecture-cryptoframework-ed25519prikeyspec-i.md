# ED25519PriKeySpec

密钥参数[AsyKeySpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，用于指定Ed25519算法中私钥包含的参数。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 方法创建密钥生成器。

**继承/实现关系：** ED25519PriKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface ED25519PriKeySpec extends AsyKeySpec--><!--Device-cryptoFramework-interface ED25519PriKeySpec extends AsyKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## sk

```TypeScript
sk: bigint
```

Ed25519算法中的私钥sk。

**类型：** bigint

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ED25519PriKeySpec-sk: bigint--><!--Device-ED25519PriKeySpec-sk: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

