# IvParamsSpec

加解密参数[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，用于在对称加解密时作为 [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_方法的参数。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_适用于CBC、CTR、OFB、CFB这些需要iv作为参数的加解密模式。 > **说明：** > > 传入[init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_方法前需要 > 指定其algName属性（来源于父类[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_）。

**继承/实现关系：** IvParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface IvParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface IvParamsSpec extends ParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## iv

```TypeScript
iv: DataBlob
```

加解密参数iv。常见长度如下： - AES的CBC|CTR|OFB|CFB模式：iv长度为16字节。 - 3DES的CBC|OFB|CFB模式：iv长度为8字节。 - SM4\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_10+\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_的CBC|CTR|OFB|CFB模式：iv长度为16字节。

**类型：** DataBlob

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IvParamsSpec-iv: DataBlob--><!--Device-IvParamsSpec-iv: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

