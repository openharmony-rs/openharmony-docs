# LocaleOptions

Options for initializing the **Locale** object. Since API version 9, the **LocaleOptions** attribute is changed from mandatory to optional.

> **NOTE:** 
> 
> - For details about **calendar**, see Table 1 in [Calendar Setting](../../../internationalization/i18n-calendar.md).

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale#options)

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## calendar

```TypeScript
calendar?: string
```

Calendar parameter. The value can be:

"buddhist", "chinese", "coptic", "dangi", "ethioaa", "ethiopic", "gregory", "hebrew", "indian", "islamic", "islamic-umalqura", "islamic-tbla", "islamic-civil", "islamic-rgsa", "iso8601", "japanese", "persian", "roc", or "islamicc".

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.calendar](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale#calendar)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## caseFirst

```TypeScript
caseFirst?: string
```

Whether case is taken into account for the locale's collation rules. The value can be:

**upper**: Uppercase letters come first.

**lower**: Lowercase letters come first.

**false**: The default collation rules of the locale are used.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.caseFirst](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale#casefirst)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## collation

```TypeScript
collation?: string
```

Collation rules for the locale. The value can be:

**big5han**: Pinyin sorting for Latin letters.

**compat**: compatibility sorting, only for Arabic.

**dict**: dictionary-style sorting, only for Singhalese.

**direct**: binary code point sorting.

**ducet**: sorting according to the Unicode collation element table.

**eor**: sorting according to the European collation rules.

**gb2312**: Pinyin sorting, only for Chinese.

**phonebk**: phone book-style sorting.

**phonetic**: phonetic sorting.

**pinyin**: Pinyin sorting.

**reformed**: reformed sorting, only for Swedish.

**searchjl**: special sorting for Korean initial consonant search.

**stroke**: stroke sorting for Chinese.

**trad**: traditional-style sorting, for example, Spanish.

**unihan**: radical-stroke sorting for Han characters, only for Chinese, Japanese, and Korean.

**zhuyin**: Zhuyin sorting, only for Chinese.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.collation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale#collation)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## hourCycle

```TypeScript
hourCycle?: string
```

Hour cycle. The value can be:

"h11", "h12", "h23", or  "h24".

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.hourCycle](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale#hourcycle)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## numberingSystem

```TypeScript
numberingSystem?: string
```

Numbering system. The value can be:

**adlm**, **ahom**, **arab**, **arabext**, **bali**, **beng**, **bhks**, **brah**, **cakm**, **cham**, **deva**, **diak**, **fullwide**, **gong**, **gonm**, **gujr**, **guru**, **hanidec**, **hmng**, **hmnp**, **java**, **kali**, **khmr**, **knda**, **lana**, **lanatham**, **laoo**, **latn**, **lepc**, **limb**, **mathbold**, **mathdbl**, **mathmono**, **mathsanb**, **mathsans**, **mlym**, **modi**, **mong**, **mroo**, **mtei**, **mymr**, **mymrshan**, **mymrtlng**, **newa**, **nkoo**, **olck**, **orya**, **osma**, **rohg**, **saur**, **segment**, **shrd**, **sind**, **sinh**, **sora**, **sund**, **takr**, **talu**, **tamldec**, **telu**, **thai**, **tibt**, **tirh**, **vaii**, **wara**, or **wcho**.

**Type:** string

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.numberingSystem](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale#numberingsystem)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

## numeric

```TypeScript
numeric?: boolean
```

Whether to treat numeric characters as numbers for sorting. The value true means to treat numeric characters as numbers for sorting, and the value **false** means to treat numeric characters as ordinary characters for sorting. For example, when this parameter is set to **true**, comparing the string **21** with the string **123** is equivalent to comparing the number 21 with the number 123. The default value is **false**.

**Type:** boolean

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.LocaleOptions.numeric](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/Locale#numeric)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n
