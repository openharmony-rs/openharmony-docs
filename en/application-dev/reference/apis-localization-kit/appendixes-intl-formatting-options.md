# Intl Formatting Options

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d7998796afac7f4d3c17377669b1b456bb50ff5f translatedAt=2026-11-09T06:18:51.896Z pushedAt=2026-11-09T07:35:40.771Z nl=1 -->

## Date and Time Formatting Options

The following tables use 13:04:00 and 00:25:00 on September 17, 2021 and locales **zh-CN** and **en** as examples to illustrate the values and display results of [DateTimeOptions](js-apis-intl.md#datetimeoptionsdeprecated).

**Table 1** Date display format (dateStyle)

| Value   | Description                                    | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| ------ | --------------------------------------- | ------------------------------------------  | ---------------------------------------- |
| full   | Complete date display, including the year, month, day, and week.| Friday, September 17, 2021                          | Friday, September 17, 2021               |
| long   | Long date display, including the year, month, and day.     | September 17, 2021                                | September 17, 2021                       |
| short  | Short date display, including the year, month, and day.     | 2021/9/17                                   | 9/17/21                                  |
| medium | Medium date display, including the year, month, and day.   | September 17, 2021                                | Sep 17, 2021                             |

**Table 2** Time display format (timeStyle)

| Value   | Description | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| ------ | ------------- | -------- | -------- |
| full   | Complete time display, including the time zone and time accurate to seconds. | 13:04:00 China Standard Time | 13:04:00 China Standard Time |
| long   | Long time display, including the time zone expressed in the format of GMT + time zone offset and time accurate to seconds. | GMT+8 13:04:00 | 13:04:00 GMT+8 |
| short  | Short time display, including hour and minute. | 13:04 | 13:04 |
| medium | Medium time display, including hour, minute, and second. | 13:04:00 | 13:04:00 |

**Table 3** Year display format (year)

| Value | Description | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| -------- | --------- | -------- | -------- |
| numeric | Complete year. | 2021 | 2021 |
| 2-digit | Last two digits of the year. | 21 | 21 |

**Table 4** Weekday display format (weekday)

| Value | Description | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| -------- | ------- | -------- | -------- |
| long | Long weekday display. | Friday | Friday |
| short | Short weekday display. | Fri. | Fri |
| narrow | Narrow weekday display. | 5 | F |

**Table 5** Hour cycle format (hourCycle)

| Value | Description            | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 00:25:00 for Locale zh-CN |
| --- | --------------- | -------------------------------------------- | ------------------------------------------- |
| h11 | Hour using 0 to 11 | 1:04 p.m.                                     |  0:25 a.m.                                    |
| h12 | Hour using 0 to 12 | 1:04 p.m.                                     |  12:25 a.m.                                   |
| h23 | Hour using 0 to 23 | 13:04                                        | 00:25                                       |
| h24 | Hour using 0 to 24 | 13:04                                        | 24:25                                       |

> **NOTE**
>
> The preceding table shows the display effect for different values of **hourCycle** when **dateStyle** or **timeStyle** is not set.


**Table 6** Hour cycle format (hourCycle)

| Value | Description            | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 00:25:00 for Locale zh-CN |
| --- | --------------- | -------------------------------------------- | ------------------------------------------- |
| h11 | Hour using 0 to 24 | 13:04                                    |  24:25                                   |
| h12 | Hour using 0 to 12 | 1:04 p.m.                                     |  12:25 a.m.                                   |
| h23 | Hour using 0 to 11 | 1:04                                         |  0:25                                       |
| h24 | Hour using 0 to 23 | 13:04                                        |  0:25                                       |

> **NOTE**
>
> The preceding table shows the display effect for different values of **hourCycle** when **dateStyle** or **timeStyle** is set.

**Table 7** Month format (month)

| Value | Description | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| -------- | --------- | -------- | -------- |
| numeric | Display of the month as a number. | 9 | 9 |
| 2-digit | Display of the month in two digits. | 09 | 09 |
| long | Long month display. | September | September |
| short | Short month display. | 9 | Sep |
| narrow | Narrow month display. | 9 | S |

**Table 8** Localized representation of time zone names (timeZoneName)

| Value  | Description                | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| ----- | ------------------ | -------------------------------------------- | ---------------------------------------- |
| long  | Long time zone name. | China Standard Time                                  | China Standard Time                      |
| short | Short time zone name. | GMT+8                                        | GMT+8                                    |

**Table 9** Era display format (era)

| Value | Description | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| -------- | ------ | -------- | -------- |
| long | Long epoch display. | Anno Domini | Anno Domini |
| short | Short epoch display. | Anno Domini | AD |
| narrow | Narrow epoch display. | Anno Domini | A |

**Table 10** Time period format (dayPeriod)

| Value | Description | 2021-09-17 13:04:00 for Locale zh-CN | 2021-09-17 13:04:00 for Locale en |
| -------- | ------ | -------- | -------- |
| long | Long time period display. | in the afternoon | in the afternoon |
| short | Short time period display. | in the afternoon | in the afternoon |
| narrow | Narrow time period display. | in the afternoon | in the afternoon |

## Number Formatting Options

Number formatting options allow you to set the minimum integer digits, minimum fraction digits, maximum fraction digits, minimum significant digits, maximum significant digits, whether to use grouping, the number representation, the compact display format, the rounding mode, the rounding priority, the rounding increment, and the number display format and numbering system. The number display format includes decimal, percent, currency, and unit. The following table describes the values and display results of some parameters in [NumberOptions](js-apis-intl.md#numberoptions).

The following uses **123000.123** as an example to show the parameter values and corresponding display effects.

**Table 11** Minimum number of integer digits (minimumIntegerDigits)

| Value | Display Effect |
| -------- | -------- |
| 6 | 123,000.123 |
| 7 | 0,123,000.123 |

**Table 12** Minimum number of decimal places (minimumFractionDigits)

| Value | Display Effect |
| -------- | -------- |
| 3 | 123,000.123 |
| 4 | 123,000.1230 |

**Table 13** Maximum number of fraction digits (maximumFractionDigits)

| Value | Display Effect |
| -------- | -------- |
| 3 | 123,000.123 |
| 2 | 123,000.12 |

**Table 14** Minimum number of significant digits (minimumSignificantDigits)

| Value | Display Effect |
| -------- | -------- |
| 9 | 123,000.123 |
| 10 | 123,000.1230 |

**Table 15** Maximum number of significant digits (maximumSignificantDigits)

| Value | Display Effect |
| -------- | -------- |
| 9 | 123,000.123 |
| 8 | 123,000.12 |

**Table 16** Use of grouping for display (useGrouping)

| Value | Display Effect |
| -------- | -------- |
| true | 123,000.123 |
| false | 123000.123 |

**Table 17** Number notation (notation)

| Value | Display Effect |
| -------- | -------- |
| standard | 123,000.123 |
| scientific | 1.230001E5 |
| engineering | 123.000123E3 |
| compact | 123K |

**Table 18** Compact display (compactDisplay)

| Value | Display Effect |
| -------- | -------- |
| short | 123K |
| long | 123 thousand |

## Currency Formatting Options

Using the currency unit USD and the number **-12300** as an example, this section describes the values and display results of some parameters of [NumberOptions](js-apis-intl.md#numberoptions).

**Table 19** Currency signs (currencySign)

| Value | Display Effect |
| -------- | -------- |
| standard | -US$12,300.00 |
| accounting | (US$12,300.00) |

**Table 20** Currency display (currencyDisplay)

| Value | Display Effect |
| -------- | -------- |
| symbol | -US$12,300.00 |
| narrowSymbol | -$12,300.00 |
| code | -USD 12,300.00 |
| name | -12,300.00 US dollars |

## Unit Formatting Options

Using the unit hectare and the number **-12300** as an example, the following describes the values and display results of some [NumberOptions](js-apis-intl.md#numberoptions) parameters.

**Table 21** Unit display (unitDisplay)

| Value | Display Effect |
| -------- | -------- |
| long | -12,300 hectares |
| short | -12,300 ha |
| narrow | -12,300ha |

**Table 22** Unit usage (unitUsage)

| Value | Display Effect |
| -------- | -------- |
| Unspecified | -12,300 ha |
| default | -47.491 sq mi |
| area-land-agricult | -30,393.962 ac |

## Relative Time Formatting Options

Using the relative time "one day ago" with the locale IDs **fr-FR** and **en-GB** as an example, the following describes the values and display results of [RelativeTimeFormatInputOptions](js-apis-intl.md#relativetimeformatinputoptionsdeprecated).

**Table 23** Numeric representation (numeric)

| Value   | Description                                          | Display Effect (fr-FR) | Display Effect (en-GB) |
| ------ | -------------------------------------------- | -------------- | --------------- |
| always | Relative time indicated by a number.                        | il y a 1 jour  | 1 day ago       |
| auto   | Relative time indicated by a phrase or value based on the locale ID. | hier           | yesterday       |

**Table 24** Relative time style (style)

| Value   | Description                  | Display Effect (fr-FR) | Display Effect (en-GB) |
| ------ | -------------------- | -------------- | --------------  |
| long   | Long relative time display.   | il y a 1 jour  | 1 day ago       |
| short  | Short relative time display.   | il y a 1 j     | 1 day ago       |
| narrow | Narrow relative time display. | -1 j           | 1 day ago       |
