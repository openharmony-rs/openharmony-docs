# PhoneNumberFormatOptions

电话号码格式化时可设置的配置项。

**起始版本：** 8

<!--Device-i18n-export interface PhoneNumberFormatOptions--><!--Device-i18n-export interface PhoneNumberFormatOptions-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## type

```TypeScript
type?: string
```

表示对电话号码格式化的类型，取值包括：'E164', 'INTERNATIONAL', 'NATIONAL', 'RFC3966', 'TYPING'。

-在API version 8版本，type为必填项。

-API version 9版本开始，type为选填项。

-API version 12版本开始支持TYPING，表示对拨号中的电话号码实时格式化。

-API version 23版本开始，TYPING支持实时获取拨号中的电话号码的归属地。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhoneNumberFormatOptions-type?: string--><!--Device-PhoneNumberFormatOptions-type?: string-End-->

**系统能力：** SystemCapability.Global.I18n

