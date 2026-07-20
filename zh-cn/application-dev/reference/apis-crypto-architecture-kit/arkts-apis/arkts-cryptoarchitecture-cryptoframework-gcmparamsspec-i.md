# GcmParamsSpec

加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，封装使用GCM AEAD模式进行加密或解密的参数，需要IV、AAD和认证标签。它是[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，用于在对称加解密时作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法的参数。

适用于GCM模式。

> **说明：**  
>  
> 1. 传入[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法前需  
> 要指定其algName属性（来源于父类[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)）。  
> 2. 如果不需要aad或者aad长度为0，构造GcmParamsSpec时可以将aad的data属性设置为空的Uint8Array，  
> 即aad: { data: new Uint8Array() }。

**继承/实现关系：** GcmParamsSpec extends [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)

**起始版本：** 9

<!--Device-cryptoFramework-interface GcmParamsSpec extends ParamsSpec--><!--Device-cryptoFramework-interface GcmParamsSpec extends ParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## aad

```TypeScript
aad: DataBlob
```

指明加解密参数aad，长度为0~INT_MAX字节。

**类型：** DataBlob

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GcmParamsSpec-aad: DataBlob--><!--Device-GcmParamsSpec-aad: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## authTag

```TypeScript
authTag: DataBlob
```

指明加解密参数authTag，长度为16字节。

采用GCM模式加密时，需从[doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal-1)或[doFinalSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinalsync-1)输出的[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)中提取末尾16字节，作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)或[initSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#initsync-1)方法中GcmParamsSpec的authTag。

**类型：** DataBlob

**起始版本：** 9

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

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GcmParamsSpec-iv: DataBlob--><!--Device-GcmParamsSpec-iv: DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

