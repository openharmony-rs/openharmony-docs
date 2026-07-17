# ParamsSpec

加解密参数，在进行对称加解密时需要构造其子类对象，并将子类对象传入[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)方法。

适用于需要iv等参数的对称加解密模式（对于无iv等参数的模式如ECB模式，无需构造，在[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)中传入null即可）。

> **说明：**  
>  
> iv（Initialization Vector，初始化向量）是用于对称加密模式（如 CBC/CTR/OFB/CFB/GCM/CCM/ChaCha20-Poly1305）中引入随机性或  
> 唯一性的字节序列，保证相同明文在相同密钥下产生不同密文。

> **说明：**  
>  
> 由于[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)的params  
> 参数是ParamsSpec类型（父类），而实际需要传入具体的子类对象（如[IvParamsSpec](arkts-cryptoarchitecture-cryptoframework-ivparamsspec-i.md)），因此在  
> 构造子类对象时应设置其父类ParamsSpec的algName参数，使算法库在init()时知道传入的是哪种子类对象。

**起始版本：** 9

<!--Device-cryptoFramework-interface ParamsSpec--><!--Device-cryptoFramework-interface ParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## algName

```TypeScript
algName: string
```

指明对称加解密参数的算法模式。可选值如下：

- "IvParamsSpec"：适用于CBC|CTR|OFB|CFB模式。  
- "GcmParamsSpec"：适用于GCM模式。  
- "CcmParamsSpec"：适用于CCM模式。  
- "AeadParamsSpec"：适用于AES-GCM，AES-CCM，SM4-GCM和ChaCha20-Poly1305算法。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParamsSpec-algName: string--><!--Device-ParamsSpec-algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

