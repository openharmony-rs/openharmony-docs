# Poly1305ParamsSpec

加解密参数[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的子类，封装使用ChaCha20-Poly1305 AEAD模式进行加密或解密的参数， 需要nonce、AAD和认证标签。它是 [ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_的子类，用于在对称加解密时作为 [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法的参数。 \_\_\_HTML\_TAG\_DESC\_USD\_12\_\_\_适用于\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 > **说明：** > > 传入[init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_方法前需要 > 指定其algName属性（来源于父类[ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_）。 > > 在ChaCha20-Poly1305加密时，需从 > [doFinal()]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_或 > [doFinalSync()]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_输出的 > [DataBlob]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_末尾提取16字节，作为解密时 > [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_或 > [initSync()]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_方法的参数 > [Poly1305ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_11\_\_\_中的authTag。

**继承/实现关系：** Poly1305ParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface Poly1305ParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface Poly1305ParamsSpec extends ParamsSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## aad

```TypeScript
aad: DataBlob
```

指明加解密参数aad。

**类型：** DataBlob

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Poly1305ParamsSpec-aad: DataBlob--><!--Device-Poly1305ParamsSpec-aad: DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## authTag

```TypeScript
authTag: DataBlob
```

指定加解密参数authTag，长度为16字节。

**类型：** DataBlob

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Poly1305ParamsSpec-authTag: DataBlob--><!--Device-Poly1305ParamsSpec-authTag: DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## iv

```TypeScript
iv: DataBlob
```

Nonce（通过iv字段传入），长度为12字节。

**类型：** DataBlob

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Poly1305ParamsSpec-iv: DataBlob--><!--Device-Poly1305ParamsSpec-iv: DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

