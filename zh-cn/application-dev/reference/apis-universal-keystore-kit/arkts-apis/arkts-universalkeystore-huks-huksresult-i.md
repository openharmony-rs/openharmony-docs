# HuksResult

调用接口返回的result。
> **说明：**  
>  
> - 从API version 8开始，从API version 9开始废弃，建议使用[HuksReturnResult<sup>9+</sup>](arkts-universalkeystore-huks-huksreturnresult-i.md)替代。  
>  
> - errorCode的具体信息，请参考[HUKS错误码](../../../reference/apis-universal-keystore-kit/errorcode-huks.md)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)

<!--Device-huks-export interface HuksResult--><!--Device-huks-export interface HuksResult-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## certChains

```TypeScript
certChains?: Array<string>
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**类型：** Array&lt;string&gt;

**起始版本：** 8

**废弃版本：** 9

<!--Device-HuksResult-certChains?: Array<string>--><!--Device-HuksResult-certChains?: Array<string>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## errorCode

```TypeScript
errorCode: number
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

<!--Device-HuksResult-errorCode: number--><!--Device-HuksResult-errorCode: number-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## outData

```TypeScript
outData?: Uint8Array
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**类型：** Uint8Array

**起始版本：** 8

**废弃版本：** 9

<!--Device-HuksResult-outData?: Uint8Array--><!--Device-HuksResult-outData?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## properties

```TypeScript
properties?: Array<HuksParam>
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**类型：** Array&lt;HuksParam&gt;

**起始版本：** 8

**废弃版本：** 9

<!--Device-HuksResult-properties?: Array<HuksParam>--><!--Device-HuksResult-properties?: Array<HuksParam>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

