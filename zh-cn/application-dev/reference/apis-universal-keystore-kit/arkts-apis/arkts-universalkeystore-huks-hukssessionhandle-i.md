# HuksSessionHandle

HUKS handle结构体。

**起始版本：** 9

<!--Device-huks-export interface HuksSessionHandle--><!--Device-huks-export interface HuksSessionHandle-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## challenge

```TypeScript
challenge?: Uint8Array
```

表示[initSession](arkts-universalkeystore-huks-initsession-f.md#initsession)操作之后获取到的challenge信息。默认为undefined。

**类型：** Uint8Array

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksSessionHandle-challenge?: Uint8Array--><!--Device-HuksSessionHandle-challenge?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## handle

```TypeScript
handle: number
```

表示无符号整数类型的handle值。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksSessionHandle-handle: number--><!--Device-HuksSessionHandle-handle: number-End-->

**系统能力：** SystemCapability.Security.Huks.Core

