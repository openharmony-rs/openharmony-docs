# GcmParamsSpec

加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md#ParamsSpec)的子类，封装使用GCM AEAD模式进行加密或解密的参数，需要IV、AAD和认证 标签。它是[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md#ParamsSpec)的子类，用于在对称加解密时作为 [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init)方法的参数。 &lt;br&gt;适用于GCM模式。 > **说明：** > > 1. 传入[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init)方法前需 > 要指定其algName属性（来源于父类[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md#ParamsSpec)）。 > 2. 如果不需要aad或者aad长度为0，构造GcmParamsSpec时可以将aad的data属性设置为空的Uint8Array， > 即aad: { data: new Uint8Array() }。

**继承/实现关系：** GcmParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md#ParamsSpec)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface GcmParamsSpec--><!--Device-cryptoFramework-interface GcmParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## aad

```TypeScript
aad: DataBlob
```

指明加解密参数aad，长度为0~INT_MAX字节。

**类型：** DataBlob

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GcmParamsSpec-aad: DataBlob--><!--Device-GcmParamsSpec-aad: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## authTag

```TypeScript
authTag: DataBlob
```

指明加解密参数authTag，长度为16字节。 &lt;br&gt;采用GCM模式加密时，需从 [doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#doFinal)或 [doFinalSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#doFinalSync)输出的 [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md#DataBlob)中提取末尾16字节，作为 [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init)或 [initSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#initSync)方法中GcmParamsSpec的authTag。

**类型：** DataBlob

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GcmParamsSpec-iv: DataBlob--><!--Device-GcmParamsSpec-iv: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

