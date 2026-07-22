# HuksReturnResult

调用接口返回的result。

**起始版本：** 9

<!--Device-huks-export interface HuksReturnResult--><!--Device-huks-export interface HuksReturnResult-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## certChains

```TypeScript
certChains?: Array<string>
```

表示证书链数据。默认为undefined。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksReturnResult-certChains?: Array<string>--><!--Device-HuksReturnResult-certChains?: Array<string>-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## outData

```TypeScript
outData?: Uint8Array
```

表示[initSession](arkts-universalkeystore-huks-initsession-f.md#initsession)操作之后获取到的challenge信息。默认为undefined。

**类型：** Uint8Array

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksReturnResult-outData?: Uint8Array--><!--Device-HuksReturnResult-outData?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## properties

```TypeScript
properties?: Array<HuksParam>
```

表示[initSession](arkts-universalkeystore-huks-initsession-f.md#initsession)操作之后获取到的challenge信息。默认为undefined。

**类型：** Array&lt;HuksParam&gt;

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksReturnResult-properties?: Array<HuksParam>--><!--Device-HuksReturnResult-properties?: Array<HuksParam>-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## sharedSecret

```TypeScript
sharedSecret?: Uint8Array
```

定义共享密钥。

**类型：** Uint8Array

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-HuksReturnResult-sharedSecret?: Uint8Array--><!--Device-HuksReturnResult-sharedSecret?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Huks.Core

