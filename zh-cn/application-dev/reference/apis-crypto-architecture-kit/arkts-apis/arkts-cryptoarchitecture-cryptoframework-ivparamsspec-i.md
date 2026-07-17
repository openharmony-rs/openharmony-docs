# IvParamsSpec

加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，用于在对称加解密时作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)方法的参数。

适用于CBC、CTR、OFB、CFB这些需要iv作为参数的加解密模式。

> **说明：**  
>  
> 传入[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)方法前需要  
> 指定其algName属性（来源于父类[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)）。

**继承/实现关系：** IvParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 9

<!--Device-cryptoFramework-interface IvParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface IvParamsSpec extends ParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IvParamsSpec-iv: DataBlob--><!--Device-IvParamsSpec-iv: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

