# CcmParamsSpec

加解密参数[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，封装使用CCM AEAD模式进行加密或解密的参数，需要IV、AAD和认证 标签。它是[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的子类，用于在对称加解密时作为 [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_方法的参数。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_适用于CCM模式。 > **说明：** > > 传入[init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法前需 > 要指定其algName属性（来源于父类[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_）。

**继承/实现关系：** CcmParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface CcmParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface CcmParamsSpec extends ParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## aad

```TypeScript
aad: DataBlob
```

指明加解密参数aad。aad最小长度为1字节，最大为2048字节。

**类型：** DataBlob

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CcmParamsSpec-aad: DataBlob--><!--Device-CcmParamsSpec-aad: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## authTag

```TypeScript
authTag: DataBlob
```

指明加解密参数authTag，长度为12字节。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_加密时，需从 [doFinal()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [doFinalSync()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_输出的 [DataBlob]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中提取末尾12字节，作为解密时 [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_或 [initSync()]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_方法中CcmParamsSpec的authTag。

**类型：** DataBlob

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CcmParamsSpec-authTag: DataBlob--><!--Device-CcmParamsSpec-authTag: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## iv

```TypeScript
iv: DataBlob
```

指明加解密参数iv，仅支持7字节。若传入iv长度超过7字节，超出范围将被截断。

**类型：** DataBlob

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CcmParamsSpec-iv: DataBlob--><!--Device-CcmParamsSpec-iv: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

