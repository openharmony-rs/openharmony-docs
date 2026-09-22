# Calendar

```TypeScript
export class Calendar
```

Provides calendar management capabilities, such as calendar name retrieval and date calculation.

**Since:** 7

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## add

```TypeScript
add(field: string, amount: number): void
```

Performs addition or subtraction on the calendar attributes of this **Calendar** object.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Calendar attribute. The value can be any of the following: **year**, **month**, **week_of_year**, **week_of_month**, **date**, **day_of_year**, **day_of_week**, **day_of_week_in_month**, **hour**, **hour_of_day**, **minute**, **second**, **millisecond**. For details about the values, see [get](#get). |
| amount | number | Yes | Addition or subtraction amount. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
  calendar.set(2021, 11, 11, 8, 0, 0); // Set the date and time to 2021.12.11 08:00:00.
  calendar.add('year', 8); // 2021 + 8
  let year: number = calendar.get('year'); // year = 2029
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call Calendar.add failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## compareDays

```TypeScript
compareDays(date: Date): number
```

Compares the current date of this **Calendar** object with the specified date for the difference in the number of days.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | Yes | Date and time. Note: The month starts from **0**. For example, **0** indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Difference in the number of days. A positive number indicates that the calendar date is earlier, and a negative number indicates the opposite. The value is accurate to milliseconds. If the value is less than one day, it is considered as one day. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
  calendar.setTime(5000);
  let date: Date = new Date(6000);
  let diff: number = calendar.compareDays(date); // diff = 1
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call Calendar.compareDays failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## get

```TypeScript
get(field: string): number
```

Obtains the values of the calendar attributes in this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Calendar attributes. The following table lists the supported attribute values. The value can be"era": Era, for example, AD or BC."year": Year."month": Month. Note: The month starts from **0**. For example, **0** indicates January."date": Date."hour": Wall-clock hour."hour_of_day": Hour of day."minute": Minute."second": Second."millisecond": Millisecond."week_of_year": Week of year. Note that the algorithm for calculating the first week of a year varies according to regions. For example, the first seven days in a year are the first week."year_woy": Year used with the week of year field."week_of_month": Week of month."day_of_week_in_month": Day of week in month."day_of_year": Day of year."day_of_week": Day of week."milliseconds_in_day": Milliseconds in day."zone_offset": Fixed time zone offset in milliseconds (excluding DST)."dst_offset": DST offset in milliseconds."dow_local": Localized day of week."extended_year": Extended year, which can be a negative number."julian_day": Julian day."is_leap_month": Whether a month is a leap month. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the calendar attribute. For example, if the year of the internal date of the current **Calendar** object is 1990, **get('year')** returns **1990**. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.set(2021, 10, 1, 8, 0, 0); // Set the date and time to 2021.11.1 08:00:00.
let hourOfDay: number = calendar.get('hour_of_day'); // hourOfDay = 8
```

## getDisplayName

```TypeScript
getDisplayName(locale: string): string
```

Obtains calendar display name in the specified language.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Calendar display name in the specified language. For example, **buddhist** is displayed as **Buddhist Calendar** if the locale is **en-US**. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'buddhist');
let calendarName: string = calendar.getDisplayName('zh'); // calendarName = 'Buddhist'
```

## getFirstDayOfWeek

```TypeScript
getFirstDayOfWeek(): number
```

Obtains the first day of a week for this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | First day of a week. The value **1** indicates Sunday, and the value **7** indicates Saturday. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'gregory');
let firstDayOfWeek: number = calendar.getFirstDayOfWeek(); // firstDayOfWeek = 1
```

## getMinimalDaysInFirstWeek

```TypeScript
getMinimalDaysInFirstWeek(): number
```

Obtains the minimum number of days in the first week for this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum number of days in the first week of a year. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
let minimalDaysInFirstWeek: number = calendar.getMinimalDaysInFirstWeek(); // minimalDaysInFirstWeek = 1
```

## getTimeInMillis

```TypeScript
getTimeInMillis(): number
```

Obtains the timestamp of this **Calendar** object.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Unix timestamp, which indicates the number of milliseconds that have elapsed since the Unix epoch. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.setTime(5000);
let millisecond: number = calendar.getTimeInMillis(); // millisecond = 5000
```

## getTimeZone

```TypeScript
getTimeZone(): string
```

Obtains the time zone ID of this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | Time zone ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.setTimeZone('Asia/Shanghai');
let timezone: string = calendar.getTimeZone(); // timezone = 'Asia/Shanghai'
```

## isWeekend

```TypeScript
isWeekend(date?: Date): boolean
```

Checks whether a given date is a weekend in this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | No | Date and time. Note: The month starts from **0**. For example, **0** indicates January. The default value is current date of the **Calendar** object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the specified date is a weekend, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.set(2021, 11, 11, 8, 0, 0); // Set the time to 2021.12.11 08:00:00.
let isWeekend: boolean = calendar.isWeekend(); // isWeekend = true
let date: Date = new Date(2011, 11, 6, 9, 0, 0); // The date and time is 2011-12-06 09:00:00.
isWeekend = calendar.isWeekend(date); // isWeekend = false
```

## set

```TypeScript
set(year: number, month: number, date:number, hour?: number, minute?: number, second?: number): void
```

Sets the year, month, day, hour, minute, and second for this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| year | number | Yes | Year to set. |
| month | number | Yes | Month to set. Note: The month starts from **0**. For example, **0** indicates January. |
| date | number | Yes | Day to set. |
| hour | number | No | Hour to set. The default value is the current system time. |
| minute | number | No | Minute to set. The default value is the current system time. |
| second | number | No | Second to set. The default value is the current system time. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.set(2021, 10, 1, 8, 0, 0); // Set the date and time to 2021.11.1 08:00:00.
```

## setFirstDayOfWeek

```TypeScript
setFirstDayOfWeek(value: number): void
```

Sets the first day of a week for this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Start day of a week. The value **1** indicates Sunday, and the value **7** indicates Saturday. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.setFirstDayOfWeek(3);
let firstDayOfWeek: number = calendar.getFirstDayOfWeek(); // firstDayOfWeek = 3
```

## setMinimalDaysInFirstWeek

```TypeScript
setMinimalDaysInFirstWeek(value: number): void
```

Sets the minimum number of days in the first week for this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum number of days in the first week of a year. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.setMinimalDaysInFirstWeek(3);
let minimalDaysInFirstWeek: number = calendar.getMinimalDaysInFirstWeek(); // minimalDaysInFirstWeek = 3
```

## setTime

```TypeScript
setTime(date: Date): void
```

Sets the date and time for a **Calendar** object based on the input **Date** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | Yes | Date and time. Note: The month starts from **0**. For example, **0** indicates January. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'gregory');
let date: Date = new Date(2021, 10, 7, 8, 0, 0); // The date and time is 2021.11.07 08:00:00.
calendar.setTime(date);
```

<a id="settime-1"></a>

## setTime

```TypeScript
setTime(time: number): void
```

Sets the date and time for a **Calendar** object based on the input timestamp.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| time | number | Yes | Unix timestamp, which indicates the number of milliseconds that have elapsed since the Unix epoch. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'gregory');
calendar.setTime(10540800000);
```

## setTimeZone

```TypeScript
setTimeZone(timezone: string): void
```

Sets the time zone of this **Calendar** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timezone | string | Yes | Valid time zone ID, for example, Asia/Shanghai. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.setTimeZone('Asia/Shanghai');
```
