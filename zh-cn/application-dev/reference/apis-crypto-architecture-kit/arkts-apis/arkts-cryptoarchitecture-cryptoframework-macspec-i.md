# MacSpec

消息认证码参数，计算HMAC或CMAC时，需要构建子类对象并作为输入参数。

> **说明：**  
>  
> algName是必选参数，表示消息认证码算法。

**起始版本：** 18

<!--Device-cryptoFramework-interface MacSpec--><!--Device-cryptoFramework-interface MacSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## algName

```TypeScript
algName: string
```

消息认证码算法名。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-MacSpec-algName: string--><!--Device-MacSpec-algName: string-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

