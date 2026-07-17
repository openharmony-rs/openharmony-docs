# LocaleItem（系统接口）

语言或国家地区的组合信息。

**起始版本：** 10

<!--Device-i18n-export interface LocaleItem--><!--Device-i18n-export interface LocaleItem-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## displayName

```TypeScript
displayName: string
```

id在SystemLocaleManager的指定区域下的表示。

**类型：** string

**起始版本：** 10

<!--Device-LocaleItem-displayName: string--><!--Device-LocaleItem-displayName: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: string
```

语言代码或国家地区代码，如"zh"、"CN"。

**类型：** string

**起始版本：** 10

<!--Device-LocaleItem-id: string--><!--Device-LocaleItem-id: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## localName

```TypeScript
localName?: string
```

id的本地名称。只有在表示语言相关信息时才存在该选项。

**类型：** string

**起始版本：** 10

<!--Device-LocaleItem-localName?: string--><!--Device-LocaleItem-localName?: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## suggestionType

```TypeScript
suggestionType: SuggestionType
```

语言或国家地区推荐类型。

**类型：** SuggestionType

**起始版本：** 10

<!--Device-LocaleItem-suggestionType: SuggestionType--><!--Device-LocaleItem-suggestionType: SuggestionType-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

