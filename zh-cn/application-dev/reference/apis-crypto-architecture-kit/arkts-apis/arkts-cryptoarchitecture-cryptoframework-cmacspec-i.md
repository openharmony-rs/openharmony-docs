# CmacSpec

消息认证码参数[MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md)的子类，作为CMAC计算的输入。
> **说明：**  
>  
> cipherName是必选参数，表示CMAC使用的对称密码算法。

**继承/实现关系：** CmacSpec extends [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md)

**起始版本：** 18

<!--Device-cryptoFramework-interface CmacSpec extends MacSpec--><!--Device-cryptoFramework-interface CmacSpec extends MacSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## cipherName

```TypeScript
cipherName: string
```

CMAC使用的对称密码算法名。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CmacSpec-cipherName: string--><!--Device-CmacSpec-cipherName: string-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

