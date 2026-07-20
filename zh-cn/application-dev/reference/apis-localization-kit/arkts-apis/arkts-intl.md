# @ohos.intl

本模块提供基础的应用国际化能力，包括时间日期格式化、数字格式化、排序等，相关接口在ECMA 402标准中定义。

[国际化-I18n](arkts-i18n.md)提供其他非ECMA 402定义的国际化接口，与本模块共同使用可提供完整的国际化支持能力。

> **说明：**  
>  
> - 本模块接口基于[CLDR](https://cldr.unicode.org)国际化数据库实现，随着CLDR标准的迭代演进，接口处理结果可能会相应调整。例如数字格式化接口，其返回值仅适用于界面展示场景，开发者请勿对返回格式进行  
> 硬编码或假设性判断，否则可能导致版本兼容问题。其中，API version 12 对应[CLDR 42](https://cldr.unicode.org/downloads/cldr-42)版本，具体数据变更详情可查阅  
> [CLDR官方文档](https://cldr.unicode.org/)。  
>  
> - 从API version 11开始，本模块部分接口支持在ArkTS卡片中使用。  
>  
> - 从API version 12开始，本模块全接口支持在原子化服务中使用。

**起始版本：** 6

<!--Device-unnamed-declare namespace intl--><!--Device-unnamed-declare namespace intl-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Collator](arkts-localization-intl-collator-c.md) | 提供字符串排序的能力。 |
| [DateTimeFormat](arkts-localization-intl-datetimeformat-c.md) | 提供日期格式化的能力。 |
| [Locale](arkts-localization-intl-locale-c.md) | 区域信息 |
| [NumberFormat](arkts-localization-intl-numberformat-c.md) | 提供标准的数字格式化的能力。 |
| [PluralRules](arkts-localization-intl-pluralrules-c.md) | 提供获取单复数类型的能力。 |
| [RelativeTimeFormat](arkts-localization-intl-relativetimeformat-c.md) | 提供相对时间格式化的能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CollatorOptions](arkts-localization-intl-collatoroptions-i.md) | 创建排序对象时可设置的配置项。  从API version 9开始，CollatorOptions中的属性改为可选。 |
| [DateTimeOptions](arkts-localization-intl-datetimeoptions-i.md) | 时间日期格式化时可设置的配置项。从API version 9开始，DateTimeOptions的属性由必填改为可选。 |
| [LocaleOptions](arkts-localization-intl-localeoptions-i.md) | > 从API version 6开始支持，从API version 20开始废弃，以calendar为例，  > 区域初始化配置项。从API version 9开始，LocaleOptions属性由必填改为可选。 |
| [NumberOptions](arkts-localization-intl-numberoptions-i.md) | 创建数字格式化对象时可设置的配置项。从API version 9开始，NumberOptions的属性由必填改为可选。 |
| [PluralRulesOptions](arkts-localization-intl-pluralrulesoptions-i.md) | 创建单复数对象时可设置的配置项。从API version 9开始，PluralRulesOptions的属性由必填改为可选。 |
| [RelativeTimeFormatInputOptions](arkts-localization-intl-relativetimeformatinputoptions-i.md) | 创建相对时间格式化对象时可设置的配置项。  从API version 9开始，RelativeTimeFormatInputOptions中的属性改为可选。 |
| [RelativeTimeFormatResolvedOptions](arkts-localization-intl-relativetimeformatresolvedoptions-i.md) | 相对时间格式化对象的格式化配置项。 |

