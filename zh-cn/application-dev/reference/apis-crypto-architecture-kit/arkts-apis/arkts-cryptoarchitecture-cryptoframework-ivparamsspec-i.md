# IvParamsSpec

加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md#ParamsSpec)的子类，用于在对称加解密时作为
[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)方法的参数。

适用于CBC、CTR、OFB、CFB这些需要iv作为参数的加解密模式。

> **说明：**
>
> 传入[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)方法前需要指定其
> algName属性（来源于父类[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md#ParamsSpec)）。

**继承/实现关系：** IvParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md#ParamsSpec)

**起始版本：** 9

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## iv

```TypeScript
iv: DataBlob
```

指明加解密参数iv。常见取值如下：

- AES的CBC|CTR|OFB|CFB模式：iv长度为16字节。
- 3DES的CBC|OFB|CFB模式：iv长度为8字节。
- SM4<sup>10+</sup>的CBC|CTR|OFB|CFB模式：iv长度为16字节。

**类型：** DataBlob

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

