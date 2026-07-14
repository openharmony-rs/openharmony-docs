# CcmParamsSpec

加解密参数[ParamsSpec](arkts-cryptoarchitecture-paramsspec-i.md)的子类，封装使用CCM AEAD模式进行加密或解密的参数，需要IV、AAD和认证
标签。它是[ParamsSpec](arkts-cryptoarchitecture-paramsspec-i.md)的子类，用于在对称加解密时作为
[init()](arkts-cryptoarchitecture-cipher-i.md#init-4)方法的参数。

适用于CCM模式。

> **说明：**
>
> 传入[init()](arkts-cryptoarchitecture-cipher-i.md#init-4)方法前需
> 要指定其algName属性（来源于父类[ParamsSpec](arkts-cryptoarchitecture-paramsspec-i.md)）。

**继承/实现关系：** CcmParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-paramsspec-i.md)

**起始版本：** 9

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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## authTag

```TypeScript
authTag: DataBlob
```

指明加解密参数authTag，长度为12字节。

采用CCM模式加密时，需从
[doFinal()](arkts-cryptoarchitecture-cipher-i.md#dofinal-2)或
[doFinalSync()](arkts-cryptoarchitecture-cipher-i.md#dofinalsync-1)输出的
[DataBlob](arkts-cryptoarchitecture-datablob-i.md)中提取末尾12字节，作为解密时
[init()](arkts-cryptoarchitecture-cipher-i.md#init-4)或
[initSync()](arkts-cryptoarchitecture-cipher-i.md#initsync-1)方法中CcmParamsSpec的authTag。

**类型：** DataBlob

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

