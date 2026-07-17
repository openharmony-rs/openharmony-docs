# ECFieldFp

指定椭圆曲线的素数域。是[ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md)的子类。

**继承/实现关系：** ECFieldFp extends [ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md)

**起始版本：** 10

<!--Device-cryptoFramework-interface ECFieldFp extends ECField--><!--Device-cryptoFramework-interface ECFieldFp extends ECField-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## p

```TypeScript
p: bigint
```

指定素数p的值。

**类型：** bigint

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ECFieldFp-p: bigint--><!--Device-ECFieldFp-p: bigint-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

