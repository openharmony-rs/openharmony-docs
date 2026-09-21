# HuksOptions

```TypeScript
export interface HuksOptions
```

调用接口使用的options。

**起始版本：** 8

**系统能力：** SystemCapability.Security.Huks.Core

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## inData

```TypeScript
inData?: Uint8Array
```

标签。

**类型：** Uint8Array

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## properties

```TypeScript
properties?: Array<HuksParam>
```

标签。

**类型：** Array&lt;[HuksParam](arkts-universalkeystore-huks-huksparam-i.md)&gt;

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Huks.Core
