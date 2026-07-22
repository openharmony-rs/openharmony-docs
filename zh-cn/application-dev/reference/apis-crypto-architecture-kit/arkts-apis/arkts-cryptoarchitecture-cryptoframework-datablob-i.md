# DataBlob

二进制数据的封装接口，核心字段data为Uint8Array类型。
> **说明：**  
>  
> Uint8Array类型数据表示8位无符号整数的数组。

**起始版本：** 9

<!--Device-cryptoFramework-interface DataBlob--><!--Device-cryptoFramework-interface DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## data

```TypeScript
data: Uint8Array
```

数据。

**类型：** Uint8Array

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataBlob-data: Uint8Array--><!--Device-DataBlob-data: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework

