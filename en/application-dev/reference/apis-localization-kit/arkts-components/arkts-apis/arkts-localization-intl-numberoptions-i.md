# NumberOptions

Options for creating the **NumberFormat** object. Since API version 9, the **NumberOptions** attribute is changed from mandatory to optional.

**Since:** 6

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## compactDisplay

```TypeScript
compactDisplay?: string
```

Compact display format. The value can be **long** or **short**.

The default value is **short**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 18](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## currency

```TypeScript
currency?: string
```

Currency unit. The value must comply with the [ISO-4217 standard](https://www.iso.org/iso-4217-currency-codes.html), for example, EUR, CNY, and USD.

From API version 12, a three-digit number is supported, for example, **978**, **156**, or **840**.

This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## currencyDisplay

```TypeScript
currencyDisplay?: string
```

Currency display mode. The value can be **symbol**, **narrowSymbol**, **code**, or **name**.

The default value is **symbol**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 20](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## currencySign

```TypeScript
currencySign?: string
```

Currency unit symbol. The value can be **standard** or **accounting**.

The default value is **standard**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 19](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## locale

```TypeScript
locale?: string
```

Valid locale ID, for example, **zh-Hans-CN**.

The default value is the current system locale.

This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## localeMatcher

```TypeScript
localeMatcher?: string
```

Locale matching algorithm. The value can be **lookup** or **best fit**.

The default value is **best fit**.

This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## maximumFractionDigits

```TypeScript
maximumFractionDigits?: number
```

Maximum number of digits in the fraction part of a number. The value ranges from **1** to **21**.

The default value is **3**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 13](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## maximumSignificantDigits

```TypeScript
maximumSignificantDigits?: number
```

Maximum number of the least significant digits. The value ranges from **1** to **21**.

The default value is **21**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 15](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## minimumFractionDigits

```TypeScript
minimumFractionDigits?: number
```

Minimum number of digits in the fraction part of a number. The value ranges from **0** to **20**.

The default value is **0**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 12](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## minimumIntegerDigits

```TypeScript
minimumIntegerDigits?: number
```

Minimum number of digits allowed in the integer part of a number. The value ranges from **1** to **21**.

The default value is **1**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 11](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## minimumSignificantDigits

```TypeScript
minimumSignificantDigits?: number
```

Minimum number of the least significant digits. The value ranges from **1** to **21**.

The default value is **1**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 14](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## notation

```TypeScript
notation?: string
```

Number notation. The value can be **standard**, **scientific**, **engineering**, or **compact**.

The default value is **standard**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 17](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## numberingSystem

```TypeScript
numberingSystem?: string
```

Numbering system. The value can be:

**adlm**, **ahom**, **arab**, **arabext**, **bali**, **beng**, **bhks**, **brah**, **cakm**, **cham**, **deva**, **diak**, **fullwide**, **gong**, **gonm**, **gujr**, **guru**, **hanidec**, **hmng**, **hmnp**, **java**, **kali**, **khmr**, **knda**, **lana**, **lanatham**, **laoo**, **latn**, **lepc**, **limb**, **mathbold**, **mathdbl**, **mathmono**, **mathsanb**, **mathsans**, **mlym**, **modi**, **mong**, **mroo**, **mtei**, **mymr**, **mymrshan**, **mymrtlng**, **newa**, **nkoo**, **olck**, **orya**, **osma**, **rohg**, **saur**, **segment**, **shrd**, **sind**, **sinh**, **sora**, **sund**, **takr**, **talu**, **tamldec**, **telu**, **thai**, **tibt**, **tirh**, **vaii**, **wara**, or **wcho**.

The default value is the default numbering system of the locale.

This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## roundingIncrement

```TypeScript
roundingIncrement?: number
```

Rounding increment. The value can be **1**, **2**, **5**, **10**, **20**, **25**, **50**, **100**, **200**, **250**, **500**, **1000**, **2000**, **2500**, or **5000**.

The default value is **1**.

This API can be used in atomic services since API version 18.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

## roundingMode

```TypeScript
roundingMode?: string
```

Rounding mode. The value can be:

- **ceil**: rounding up.  
- **floor**: rounding down.  
- **expand**: rounding away from 0.  
- **trunc**: rounding toward 0.  
- **halfCeil**: half-rounding up; that is, rounding up when the decimal number is greater than or equal to half  
of the increment, and rounding down otherwise.  
- **halfFloor**: half-rounding down; that is, rounding up when the decimal number is greater than half of the  
increment, and rounding down otherwise.  
- **halfExpand**: half-rounding away from 0; that is, rounding away from 0 when the decimal number is greater  
than or equal to half of the increment, and rounding toward 0 otherwise.  
- **halfTrunc**: half-rounding toward 0; that is, rounding away from 0 when the decimal number is greater than  
half of the increment, and rounding toward 0 otherwise.  
- "halfEven": half-rounding to the nearest even number; that is, rounding away from 0 when the decimal number is  
greater than half of the increment, rounding toward 0 when the decimal number is less than half of the increment, and rounding to the nearest even number when the decimal number is exactly half of the increment.

The default value is **halfExpand**.

This API can be used in atomic services since API version 18.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

## roundingPriority

```TypeScript
roundingPriority?: string
```

Rounding priority used when both the maximum number of fraction digits and the maximum number of valid digits are set. The value can be **auto**, **morePrecision**, or **lessPrecision**. The value **morePrecision** indicates that the maximum number of fraction digits is used. The value **lessPrecision** indicates that the maximum number of valid digits is used.

The default value is **auto**.

This API can be used in atomic services since API version 18.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

## signDisplay

```TypeScript
signDisplay?: string
```

Number sign display format. The value can be:

- "auto": automatically determines whether to display the plus or minus sign.  
- "never": do not display the plus or minus sign.  
- "always": always displays the plus or minus sign.  
- "exceptZero": displays the plus or minus sign for all values except 0.

Default value: **"auto"**

This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## style

```TypeScript
style?: string
```

Number display format. The value can be **decimal**, **currency**, **percent**, or **unit**.

The default value is **decimal**.

This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## unit

```TypeScript
unit?: string
```

Unit name, for example, **meter**, **inch**, or **hectare**.

The combination units supported since API version 18 are as follows: beat-per-minute, body-weight-per-second, breath-per-minute, foot-per-hour, jump-rope-per-minute, meter-per-hour, milliliter-per-minute-per-kilogram, rotation-per-minute, step-per-minute, and stroke-per-minute.

This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## unitDisplay

```TypeScript
unitDisplay?: string
```

Display format of units. The value can be **long**, **short**, or **narrow**.

The default value is **short**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 21](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## unitUsage

```TypeScript
unitUsage?: string
```

Application scenario of units. The value can be any of the following: **default**, **area-land-agricult**, **area- land-commercl**, **area-land-residntl**, **length-person**, **length-person-small**, **length-rainfall**, ** length-road**, **length-road-small**, **length-snowfall**, **length-vehicle**, **length-visiblty**, **length- visiblty-small**, **length-person-informal**, **length-person-small-informal**, **length-road-informal**, **speed -road-travel**, **speed-wind**, **temperature-person**, **temperature-weather**, **volume-vehicle-fuel**, ** elapsed-time-second**, **size-file-byte**, or **size-shortfile-byte**.

The default value is **default**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 22](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## useGrouping

```TypeScript
useGrouping?: boolean
```

Whether to enable grouping for display. The value **true** means to enable grouping for display, and the value **false** means the opposite.

The default value is **true**.

This API can be used in atomic services since API version 12.

For details about their display effects, see [Table 16](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** boolean

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n
