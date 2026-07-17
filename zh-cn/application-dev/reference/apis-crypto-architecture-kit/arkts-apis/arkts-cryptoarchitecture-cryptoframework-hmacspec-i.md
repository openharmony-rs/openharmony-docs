# HmacSpec

消息认证码参数[MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md)的子类，作为HMAC计算的输入。

> **说明：**  
>  
> mdName是必选参数，表示HMAC摘要算法。

**继承/实现关系：** HmacSpec extends [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md)

**起始版本：** 18

<!--Device-cryptoFramework-interface HmacSpec extends MacSpec--><!--Device-cryptoFramework-interface HmacSpec extends MacSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## mdName

```TypeScript
mdName: string
```

摘要算法名。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HmacSpec-mdName: string--><!--Device-HmacSpec-mdName: string-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

