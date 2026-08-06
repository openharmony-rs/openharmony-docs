# GcmParamsSpec

加解密参数[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，封装使用GCM AEAD模式进行加密或解密的参数，需要IV、AAD和认证 标签。它是[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的子类，用于在对称加解密时作为 [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_方法的参数。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_适用于GCM模式。 > **说明：** > > 1. 传入[init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法前需 > 要指定其algName属性（来源于父类[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_）。 > 2. 如果不需要aad或者aad长度为0，构造GcmParamsSpec时可以将aad的data属性设置为空的Uint8Array， > 即aad: { data: new Uint8Array() }。

**继承/实现关系：** GcmParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface GcmParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface GcmParamsSpec extends ParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## aad

```TypeScript
aad: DataBlob
```

指明加解密参数aad，长度为0~INT\_MAX字节。

**类型：** DataBlob

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GcmParamsSpec-aad: DataBlob--><!--Device-GcmParamsSpec-aad: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## authTag

```TypeScript
authTag: DataBlob
```

指明加解密参数authTag，长度为16字节。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_采用GCM模式加密时，需从 [doFinal()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [doFinalSync()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_输出的 [DataBlob]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中提取末尾16字节，作为 [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_或 [initSync()]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_方法中GcmParamsSpec的authTag。

**类型：** DataBlob

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GcmParamsSpec-authTag: DataBlob--><!--Device-GcmParamsSpec-authTag: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## iv

```TypeScript
iv: DataBlob
```

指明加解密参数iv，长度为1~128字节，常用为12字节。

**类型：** DataBlob

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GcmParamsSpec-iv: DataBlob--><!--Device-GcmParamsSpec-iv: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

