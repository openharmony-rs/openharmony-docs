# EncodingInfo

编码信息。

**起始版本：** 26.0.0

<!--Device-i18n-export interface EncodingInfo--><!--Device-i18n-export interface EncodingInfo-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## confidence

```TypeScript
confidence: number
```

识别结果的置信度，范围是0-100。值越大，识别结果越可靠。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EncodingInfo-confidence: int--><!--Device-EncodingInfo-confidence: int-End-->

**系统能力：** SystemCapability.Global.I18n

## encodingName

```TypeScript
encodingName: string
```

编码名称，取值包括：UTF-8，UTF-16BE，UTF-16LE，UTF-32BE，UTF-32LE，Shift_JIS，ISO-2022-JP，ISO-2022-CN，ISO-2022-KR，GB18030，Big5，EUC-JP，EUC-KR，ISO-8859-1，ISO-8859-2，ISO-8859-5，ISO-8859-6，ISO-8859-7，ISO-8859-8，ISO-8859-9，windows-1250，windows-1251，windows-1252，windows-1253，windows-1254，windows-1255，windows-1256，KOI8-R，IBM420，IBM424。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EncodingInfo-encodingName: string--><!--Device-EncodingInfo-encodingName: string-End-->

**系统能力：** SystemCapability.Global.I18n

