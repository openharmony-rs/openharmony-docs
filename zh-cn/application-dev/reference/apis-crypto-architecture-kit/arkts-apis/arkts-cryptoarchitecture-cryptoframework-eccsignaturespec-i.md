# EccSignatureSpec

包含（r、s）的ECC/SM2签名数据的对象。
> **说明：**  
>  
> r和s的长度各为256位。

**起始版本：** 20

<!--Device-cryptoFramework-interface EccSignatureSpec--><!--Device-cryptoFramework-interface EccSignatureSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## r

```TypeScript
r: bigint
```

r分量。

**类型：** bigint

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-EccSignatureSpec-r: bigint--><!--Device-EccSignatureSpec-r: bigint-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

## s

```TypeScript
s: bigint
```

s分量。

**类型：** bigint

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-EccSignatureSpec-s: bigint--><!--Device-EccSignatureSpec-s: bigint-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

