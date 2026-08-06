# X25519PubKeySpec

密钥参数[AsyKeySpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，用于指定X25519算法中公钥包含的参数。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 方法创建密钥生成器。

**继承/实现关系：** X25519PubKeySpec extends [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface X25519PubKeySpec extends AsyKeySpec--><!--Device-cryptoFramework-interface X25519PubKeySpec extends AsyKeySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## pk

```TypeScript
pk: bigint
```

X25519算法中的公钥pk。

**类型：** bigint

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X25519PubKeySpec-pk: bigint--><!--Device-X25519PubKeySpec-pk: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

