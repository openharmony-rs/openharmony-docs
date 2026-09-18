# Locale

Provides APIs for obtaining locale information.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.Locale](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale)

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor()
```

Creates a **Locale** object.

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.Locale.constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// The current locale ID is used by the default constructor.
let locale = new intl.Locale();
// Return the current system locale ID.
let localeID = locale.toString();
```

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a zh-CN locale object.
let locale = new intl.Locale('zh-CN');
let localeID = locale.toString(); // localeID = 'zh-CN'
```

## constructor

```TypeScript
constructor(locale: string, options?: LocaleOptions)
```

Creates a **Locale** object.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.Locale.constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | Locale information, which consists of the language, script, and country/region. |
| options | [LocaleOptions](arkts-localization-intl-localeoptions-i.md) | No | Options for creating the **Locale** object.<br>**Since:** 12 |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// The current locale ID is used by the default constructor.
let locale = new intl.Locale();
// Return the current system locale ID.
let localeID = locale.toString();
```

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a zh-CN locale object.
let locale = new intl.Locale('zh-CN');
let localeID = locale.toString(); // localeID = 'zh-CN'
```

## maximize

```TypeScript
maximize(): Locale
```

Maximizes locale information by supplementing the missing script and country/region information.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.Locale.maximize](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/maximize)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [Locale](arkts-localization-intl-locale-c.md) | **Locale** object with the script and country/region information. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a zh locale object.
let locale = new intl.Locale('zh');
// Supplement the locale object's script and region.
let maximizedLocale = locale.maximize();
let localeID = maximizedLocale.toString(); // localeID = 'zh-Hans-CN'

// Create an en-US locale object.
locale = new intl.Locale('en-US');
// Supplement the locale object's script.
maximizedLocale = locale.maximize();
localeID = maximizedLocale.toString(); // localeID = 'en-Latn-US'
```

## minimize

```TypeScript
minimize(): Locale
```

Minimizes locale information by removing the script and country/region information.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.Locale.minimize](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/minimize)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [Locale](arkts-localization-intl-locale-c.md) | **Locale** object without the script and country/region information. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a zh-Hans-CN locale object.
let locale = new intl.Locale('zh-Hans-CN');
// Remove the locale object's script and region.
let minimizedLocale = locale.minimize();
let localeID = minimizedLocale.toString(); // localeID = 'zh'

// Create an en-US locale object.
locale = new intl.Locale('en-US');
// Remove locale object's region.
minimizedLocale = locale.minimize();
localeID = minimizedLocale.toString(); // localeID = 'en'
```

## toString

```TypeScript
toString(): string
```

Obtains the string that represents a **Locale** object.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.Locale.toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/toString)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | String that represents the **Locale** object. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create an en-GB locale object.
let locale = new intl.Locale('en-GB');
let localeID = locale.toString(); // localeID = 'en-GB'
```

## baseName

```TypeScript
baseName: string
```

Locale information, which consists of the language, script, and country/region, for example, **zh-Hans-CN**.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.baseName](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/baseName)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## calendar

```TypeScript
calendar: string
```

Calendar for the locale. The value can be: The value can be any of the following: **buddhist**, **chinese**, **coptic**, **dangi**, **ethioaa**, **ethiopic**, **gregory**, **hebrew**, **indian**, **islamic**, **islamic-umalqura**, **islamic-tbla**, **islamic-civil**, **islamic-rgsa**, **iso8601**, **japanese**, **persian**, **roc**, or **islamicc**. For details about their meanings, see Table 1 in [Calendar Setting](../../../internationalization/i18n-calendar.md).

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.calendar](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/calendar)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## caseFirst

```TypeScript
caseFirst: string
```

Whether case is taken into account for the locale's collation rules. The value can be: **upper**: Uppercase letters come first. **lower**: Lowercase letters come first. **false**: The default collation rules of the locale are used.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.caseFirst](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/caseFirst)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## collation

```TypeScript
collation: string
```

Collation rules for the locale. The value can be: **big5han**: Pinyin sorting for Latin letters. **compat** : compatibility sorting, only for Arabic. **dict**: dictionary-style sorting, only for Singhalese. **direct**: binary code point sorting. **ducet**: sorting according to the Unicode collation element table. **eor**: sorting according to the European collation rules. **gb2312**: Pinyin sorting, only for Chinese. **phonebk**: phone book-style sorting. **phonetic**: phonetic sorting. **pinyin**: Pinyin sorting. **reformed**: reformed sorting, only for Swedish. **searchjl**: special sorting for Korean initial consonant search. **stroke**: stroke sorting for Chinese. **trad**: traditional-style sorting, for example, Spanish. **unihan**: radical-stroke sorting for Han characters, only for Chinese, Japanese, and Korean. **zhuyin**: Zhuyin sorting, only for Chinese.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.collation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/collation)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## hourCycle

```TypeScript
hourCycle: string
```

Time system for the locale. The value can be:"h11", "h12", "h23", or "h24". For details about their display effects, see [Table 5](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.hourCycle](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/hourCycle)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## language

```TypeScript
language: string
```

Language associated with the locale, for example, **zh**. The value complies with the ISO 639 standard.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.language](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/language)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## numberingSystem

```TypeScript
numberingSystem: string
```

Numbering system for the locale. The value can be: **adlm**, **ahom**, **arab**, **arabext**, **bali**, **beng**, **bhks**, **brah**, **cakm**, **cham**, **deva**, **diak**, **fullwide**, **gong**, **gonm**, **gujr**, **guru**, **hanidec**, **hmng**, **hmnp**, **java**, **kali**, **khmr**, **knda**, **lana**, **lanatham**, **laoo**, **latn**, **lepc**, **limb**, **mathbold**, **mathdbl**, **mathmono**, **mathsanb**, **mathsans**, **mlym**, **modi**, **mong**, **mroo**, **mtei**, **mymr**, **mymrshan**, **mymrtlng**, **newa**, **nkoo**, **olck**, **orya**, **osma**, **rohg**, **saur**, **segment**, **shrd**, **sind**, **sinh**, **sora**, **sund**, **takr**, **talu**, **tamldec**, **telu**, **thai**, **tibt**, **tirh**, **vaii**, **wara**, or **wcho**.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.numberingSystem](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/numberingSystem)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## numeric

```TypeScript
numeric: boolean
```

Whether to use special sorting rules for digits. The value **true** means to use special sorting rules for digits, and the value **false** means the opposite.The default value is **false**.

**Type:** boolean

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.numeric](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/numeric)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## region

```TypeScript
region: string
```

Country/region associated with the locale, for example, **CN**. The value complies with the ISO 3166 standard.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.region](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/region)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## script

```TypeScript
script: string
```

Script type of the language, for example, **Hans**. The value complies with the Unicode ISO 15924 standard.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.script](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/script)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n
