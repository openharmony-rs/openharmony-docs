# BigIntToLocaleStringOptions

## Modules to Import

```TypeScript
```

## compactDisplay

```TypeScript
compactDisplay?: string
```

used only when notation is "compact"

**Type:** string

## currency

```TypeScript
currency?: string
```

The currency to use in currency formatting. Possible values are the ISO 4217 currency codes, such as "USD" for the US dollar, "EUR" for the euro, or "CNY" for the Chinese RMB — see the Current currency & funds code list. There is no default value; if the style is "currency", the currency property must be provided. It is only used when [[Style]] has the value "currency".

**Type:** string

## currencyDisplay

```TypeScript
currencyDisplay?: string
```

How to display the currency in currency formatting. It is only used when [[Style]] has the value "currency". The default is "symbol".

"symbol" to use a localized currency symbol such as €,

"code" to use the ISO currency code,

"name" to use a localized currency name such as "dollar"

**Type:** string

## localeMatcher

```TypeScript
localeMatcher?: string
```

The locale matching algorithm to use.The default is "best fit". For information about this option, see the Locale_negotiation Intl page.

**Type:** string

## maximumFractionDigits

```TypeScript
maximumFractionDigits?: 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20
```

The maximum number of fraction digits to use. Possible values are from 0 to 20; the default for plain number formatting is the larger of minimumFractionDigits and 3; the default for currency formatting is the larger of minimumFractionDigits and the number of minor unit digits provided by the html ISO 4217 currency codes list (2 if the list doesn't provide that information); the default for percent formatting is the larger of minimumFractionDigits and 0.

**Type:** 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 10 &#124; 11 &#124; 12 &#124; 13 &#124; 14 &#124; 15 &#124; 16 &#124; 17 &#124; 18 &#124; 19 &#124; 20

## maximumSignificantDigits

```TypeScript
maximumSignificantDigits?: 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21
```

The maximum number of significant digits to use. Possible values are from 1 to 21; the default is 21.

**Type:** 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 10 &#124; 11 &#124; 12 &#124; 13 &#124; 14 &#124; 15 &#124; 16 &#124; 17 &#124; 18 &#124; 19 &#124; 20 &#124; 21

## minimumFractionDigits

```TypeScript
minimumFractionDigits?: 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20
```

The minimum number of fraction digits to use. Possible values are from 0 to 20; the default for plain number and percent formatting is 0; the default for currency formatting is the number of minor unit digits provided by the html ISO 4217 currency codes list (2 if the list doesn't provide that information).

**Type:** 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 10 &#124; 11 &#124; 12 &#124; 13 &#124; 14 &#124; 15 &#124; 16 &#124; 17 &#124; 18 &#124; 19 &#124; 20

## minimumIntegerDigits

```TypeScript
minimumIntegerDigits?: 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21
```

The minimum number of integer digits to use. Possible values are from 1 to 21; the default is 1.

**Type:** 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 10 &#124; 11 &#124; 12 &#124; 13 &#124; 14 &#124; 15 &#124; 16 &#124; 17 &#124; 18 &#124; 19 &#124; 20 &#124; 21

## minimumSignificantDigits

```TypeScript
minimumSignificantDigits?: 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21
```

The minimum number of significant digits to use. Possible values are from 1 to 21; the default is 1.

**Type:** 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 10 &#124; 11 &#124; 12 &#124; 13 &#124; 14 &#124; 15 &#124; 16 &#124; 17 &#124; 18 &#124; 19 &#124; 20 &#124; 21

## notation

```TypeScript
notation?: string
```

The formatting that should be displayed for the number, the defaults is "standard"

"standard" plain number formatting

"scientific" return the order-of-magnitude for formatted number.

"engineering" return the exponent of ten when divisible by three

"compact" string representing exponent, defaults is using the "short" form

**Type:** string

## numberingSystem

```TypeScript
numberingSystem?: string
```

**Type:** string

## style

```TypeScript
style?: string
```

The formatting style to use , the default is "decimal".

**Type:** string

## unit

```TypeScript
unit?: string
```

The unit to use in unit formatting, Possible values are core unit identifiers, defined in UTS #35, Part 2, Section 6. A subset of units from the full list was selected for use in ECMAScript. Pairs of simple units can be concatenated with "-per-" to make a compound unit. There is no default value; if the style is "unit", the unit property must be provided.

**Type:** string

## unitDisplay

```TypeScript
unitDisplay?: string
```

The unit formatting style to use in unit formatting, the defaults is "short".

**Type:** string

## useGrouping

```TypeScript
useGrouping?: boolean
```

Whether to use grouping separators, such as thousands separators or thousand/lakh/crore separators. The default is true.

**Type:** boolean
