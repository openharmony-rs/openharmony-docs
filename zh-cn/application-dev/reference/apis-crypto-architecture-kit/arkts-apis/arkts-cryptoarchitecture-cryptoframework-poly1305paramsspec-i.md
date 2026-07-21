# Poly1305ParamsSpec

加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，封装使用ChaCha20-Poly1305 AEAD模式进行加密或解密的参数，需要nonce、AAD和认证标签。它是[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，用于在对称加解密时作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法的参数。

适用于[ChaCha20-Poly1305](../../../security/CryptoArchitectureKit/crypto-sym-encrypt-decrypt-spec.md#chacha20)。

> **说明：**  
>  
> 传入[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法前需要  
> 指定其algName属性（来源于父类[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)）。  
>  
> 在ChaCha20-Poly1305加密时，需从  
> [doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal-1)或  
> [doFinalSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinalsync)输出的  
> [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)末尾提取16字节，作为解密时  
> [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)或  
> [initSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#initsync)方法的参数  
> [Poly1305ParamsSpec](arkts-cryptoarchitecture-cryptoframework-poly1305paramsspec-i.md)中的authTag。

**继承/实现关系：** Poly1305ParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 22

<!--Device-cryptoFramework-interface Poly1305ParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface Poly1305ParamsSpec extends ParamsSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## aad

```TypeScript
aad: DataBlob
```

指明加解密参数aad。

**类型：** DataBlob

**起始版本：** 22

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

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Poly1305ParamsSpec-iv: DataBlob--><!--Device-Poly1305ParamsSpec-iv: DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

