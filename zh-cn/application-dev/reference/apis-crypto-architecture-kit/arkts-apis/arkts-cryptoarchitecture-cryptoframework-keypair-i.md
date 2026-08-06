# KeyPair

非对称密钥对包含公钥和私钥。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_可以通过非对称密钥生成器[AsyKeyGenerator]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、 [AsyKeyGeneratorBySpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_来生成。 > **说明：** > > KeyPair对象中的pubKey对象和priKey对象是KeyPair对象的成员。当KeyPair对象超出作用域时，其内部的pubKey对象和priKey对象将被析构。 > > 业务方使用时应持有KeyPair对象的引用，而非内部pubKey或priKey对象的引用。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface KeyPair--><!--Device-cryptoFramework-interface KeyPair-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyPair-readonly priKey: PriKey--><!--Device-KeyPair-readonly priKey: PriKey-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyPair-readonly pubKey: PubKey--><!--Device-KeyPair-readonly pubKey: PubKey-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

