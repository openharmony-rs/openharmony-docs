# getDisplayLanguage

## getDisplayLanguage

```TypeScript
export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string
```

获取指定语言的本地化显示文本。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [i18n.System.getDisplayLanguage](arkts-localization-i18n-system-c.md#getdisplaylanguage)

<!--Device-i18n-export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string--><!--Device-i18n-export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | 指定语言。 |
| locale | string | 是 | \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，由语言、脚本、国家地区组成。 |
| sentenceCase | boolean | 否 | true表示按照首字母大写的格式显示文本，false表示按照区域默认的大小写格式显示文本。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 指定语言的本地化显示文本。 |

