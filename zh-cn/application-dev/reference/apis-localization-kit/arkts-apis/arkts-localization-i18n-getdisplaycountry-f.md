# getDisplayCountry

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getDisplayCountry

```TypeScript
export function getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string
```

获取指定国家的本地化名称。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getDisplayCountry](arkts-localization-i18n-system-c.md#getdisplaycountry-1)

<!--Device-i18n-export function getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string--><!--Device-i18n-export function getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| country | string | 是 | 指定国家。 |
| locale | string | 是 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |
| sentenceCase | boolean | 否 | true表示按照首字母大写的格式显示文本，false表示按照区域默认的大小写格式显示文本。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 指定国家的本地化显示文本。 |

