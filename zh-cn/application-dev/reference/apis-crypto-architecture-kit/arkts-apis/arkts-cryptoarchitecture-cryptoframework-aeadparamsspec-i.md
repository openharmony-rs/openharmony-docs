# AeadParamsSpec

用于AEAD（带附加数据的认证加密）对称加解密的 [init()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法参数，继承自 [ParamsSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_适用于\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的CCM和GCM分组模式。 \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_适用于\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_的GCM分组模式。 \_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_适用于 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ 分组模式。 > **说明：** > > 在AES-CCM模式下使用AeadParamsSpec加密时： > - 如果加密时指定了tag长度，解密时也必须传入相同的长度。 > > - CCM模式下[update]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_与[doFinal]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_只能调用其 > 中一个进行加密或者解密，且每个方法只能调用一次。

**继承/实现关系：** AeadParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-cryptoFramework-interface AeadParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface AeadParamsSpec extends ParamsSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## authenticatedData

```TypeScript
authenticatedData?: Uint8Array
```

指定可选的附加认证数据。

**类型：** Uint8Array

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AeadParamsSpec-authenticatedData?: Uint8Array--><!--Device-AeadParamsSpec-authenticatedData?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## nonce

```TypeScript
nonce: Uint8Array
```

指明加解密参数nonce。 > **说明：** > - 对于AES-CCM，nonce长度的取值范围为7~13字节。 > - 对于AES-GCM，nonce长度范围为1~128字节，推荐使用12字节。 > - 对于SM4-GCM，nonce长度范围为1~128字节，推荐使用12字节。 > - 对于ChaCha20-Poly1305，nonce长度必须为12字节。

**类型：** Uint8Array

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AeadParamsSpec-nonce: Uint8Array--><!--Device-AeadParamsSpec-nonce: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## tagLen

```TypeScript
tagLen?: int
```

认证标签长度，单位为字节。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_加密时，标签将被添加到密文末尾。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_解密时，标签应位于密文末尾。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_取值应为整数。 > **说明：** > - 对于AES-CCM，默认值为12。支持的取值为4、6、8、10、12、14和16。 > - 对于AES-GCM，默认值为16。支持的取值为4、8、12、13、14、15和16。 > - 对于SM4-GCM，默认值为16。支持的取值为4、8、12、13、14、15和16。 > - 对于ChaCha20-Poly1305，默认值为16。支持的取值为16。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AeadParamsSpec-tagLen?: int--><!--Device-AeadParamsSpec-tagLen?: int-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

