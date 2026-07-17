# ECField

指定椭圆曲线的域类型。当前只支持Fp域。

**起始版本：** 10

<!--Device-cryptoFramework-interface ECField--><!--Device-cryptoFramework-interface ECField-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## fieldType

```TypeScript
fieldType: string
```

指定椭圆曲线域的类型，当前只支持"Fp"。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECField-fieldType: string--><!--Device-ECField-fieldType: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

