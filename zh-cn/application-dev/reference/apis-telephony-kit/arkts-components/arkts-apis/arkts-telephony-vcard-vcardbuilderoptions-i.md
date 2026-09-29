# VCardBuilderOptions

```TypeScript
export interface VCardBuilderOptions
```

VCard版本和编码信息。

**起始版本：** 23

<!--Device-vcard-export interface VCardBuilderOptions--><!--Device-vcard-export interface VCardBuilderOptions-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { vcard } from '@kit.TelephonyKit';
```

## cardType

```TypeScript
cardType?: VCardType
```

VCard版本类型 (默认值为VERSION_21)。

**类型：** [VCardType](arkts-telephony-vcard-vcardtype-e.md)

**起始版本：** 23

<!--Device-VCardBuilderOptions-cardType?: VCardType--><!--Device-VCardBuilderOptions-cardType?: VCardType-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## charset

```TypeScript
charset?: string
```

VCard编码类型（默认值为'UTF-8'）。

**类型：** string

**起始版本：** 23

<!--Device-VCardBuilderOptions-charset?: string--><!--Device-VCardBuilderOptions-charset?: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService
