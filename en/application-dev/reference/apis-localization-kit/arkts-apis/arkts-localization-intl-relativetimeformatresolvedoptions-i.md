# RelativeTimeFormatResolvedOptions

Represents the formatting options for the **RelativeTimeFormat** object.

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.ResolvedRelativeTimeFormatOptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/resolvedOptions#return_value)

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## locale

```TypeScript
locale: string
```

Locale ID, including the language, script, and region.

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.ResolvedRelativeTimeFormatOptions.locale](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/resolvedOptions#locale)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## numberingSystem

```TypeScript
numberingSystem: string
```

Numbering system. The value can be:

**adlm**, **ahom**, **arab**, **arabext**, **bali**, **beng**, **bhks**, **brah**, **cakm**, **cham**, **deva**, **diak**, **fullwide**, **gong**, **gonm**, **gujr**, **guru**, **hanidec**, **hmng**, **hmnp**, **java**, **kali**, **khmr**, **knda**, **lana**, **lanatham**, **laoo**, **latn**, **lepc**, **limb**, **mathbold**, **mathdbl**, **mathmono**, **mathsanb**, **mathsans**, **mlym**, **modi**, **mong**, **mroo**, **mtei**, **mymr**, **mymrshan**, **mymrtlng**, **newa**, **nkoo**, **olck**, **orya**, **osma**, **rohg**, **saur**, **segment**, **shrd**, **sind**, **sinh**, **sora**, **sund**, **takr**, **talu**, **tamldec**, **telu**, **thai**, **tibt**, **tirh**, **vaii**, **wara**, or **wcho**.

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.ResolvedRelativeTimeFormatOptions.numberingSystem](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/resolvedOptions#numberingsystem)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## numeric

```TypeScript
numeric: string
```

Format of the output result. It determines whether numeric values are used to represent relative dates or times in the formatting result. The value can be **always** or **auto**.

For details about their display effects, see [Table 23](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.ResolvedRelativeTimeFormatOptions.numeric](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/resolvedOptions#numeric)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## style

```TypeScript
style: string
```

Length of an internationalized message. The value can be **long**, **short**, or **narrow**.

For details about their display effects, see [Table 24](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.ResolvedRelativeTimeFormatOptions.style](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/resolvedOptions#style)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n
