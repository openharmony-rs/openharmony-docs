# IvParamsSpec

加解密参数[ParamsSpec](arkts-cryptoarchitecture-paramsspec-i.md)的子类，用于在对称加解密时作为
[init()](arkts-cryptoarchitecture-cipher-i.md#init-4)方法的参数。

适用于CBC、CTR、OFB、CFB这些需要iv作为参数的加解密模式。

> **说明：**
>
> 传入[init()](arkts-cryptoarchitecture-cipher-i.md#init-4)方法前需要
> 指定其algName属性（来源于父类[ParamsSpec](arkts-cryptoarchitecture-paramsspec-i.md)）。

**继承/实现关系：** IvParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-paramsspec-i.md)

**起始版本：** 9

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## iv

```TypeScript
iv: DataBlob
```

加密和解密参数iv。常见取值如下：

- AES的CBC|CTR|OFB|CFB模式：iv长度为16字节。
- 3DES的CBC|OFB|CFB模式：iv长度为8字节。
- SM4<sup>10+</sup>的CBC|CTR|OFB|CFB模式：iv长度为16字节。

**类型：** DataBlob

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

