# Util

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [I18NUtil](arkts-localization-i18n-i18nutil-c.md)

<!--Device-i18n-export interface Util--><!--Device-i18n-export interface Util-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## unitConvert

```TypeScript
unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string
```

将fromUnit的单位转换为toUnit的单位，并根据区域与风格进行格式化。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [unitConvert](arkts-localization-i18n-i18nutil-c.md#unitconvert)

<!--Device-Util-unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: double, locale: string, style?: string): string--><!--Device-Util-unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: double, locale: string, style?: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromUnit | [UnitInfo](arkts-localization-i18n-unitinfo-i.md) | 是 | 要被转换的单位。 |
| toUnit | [UnitInfo](arkts-localization-i18n-unitinfo-i.md) | 是 | 要转换为的单位。 |
| value | number | 是 | 要被转换的单位的数量值。 |
| locale | string | 是 | 格式化时使用的区域ID，如：zh-Hans-CN。 |
| style | string | 否 | 格式化使用的风格，取值包括：'long', 'short', 'narrow'。默认值：short。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 按照toUnit的单位格式化后，得到的字符串。 |

