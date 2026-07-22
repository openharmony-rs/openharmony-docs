# Calendar

提供历法相关的能力，包括历法名称获取和日期计算等。

**起始版本：** 7

<!--Device-i18n-export class Calendar--><!--Device-i18n-export class Calendar-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## add

```TypeScript
add(field: string, amount: number): void
```

对日历对象中的表示时间日期的日历属性值进行加减操作。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-add(field: string, amount: int): void--><!--Device-Calendar-add(field: string, amount: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 指定的日历属性，目前支持的属性值有 year, month, week_of_year, week_of_month, date, day_of_year, day_of_week, day_of_week_in_month, hour, hour_of_day, minute, second, millisecond。<br>各取值代表的含义请参考[get](arkts-localization-i18n-calendar-c.md#get)。 |
| amount | number | 是 | 进行加减操作的具体数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
  calendar.set(2021, 11, 11, 8, 0, 0); // 设置时间日期为2021.12.11 08:00:00
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

比较日历对象当前日期和指定日期相差的天数。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-compareDays(date: Date): int--><!--Device-Calendar-compareDays(date: Date): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。<br>**说明：**<br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 相差的天数，正数表示日历时间更早，负数表示指定时间更早。<br>按毫秒级的精度，不足一天按一天计。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

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

获取日历对象中日历属性的值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-get(field: string): int--><!--Device-Calendar-get(field: string): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 指定的日历属性，取值包括：<br>"era"：纪元，例如公历中的公元前或者公元后。<br>"year"：年。<br>"month"：月，从0开始计数，0表示一月。<br>"date"：日。<br>"hour"：挂钟小时数。<br>"hour_of_day"：一天中的第几小时。<br>"minute"：分。<br>"second"：秒。<br>"millisecond"：毫秒。<br>"week_of_year"：一年中的第几周，按照星期计算周，第一周的归属各地有区别。<br>"year_woy"：一年中的第几周，按照数值计算周，例如一年中前1~7日属于第一周。<br>"week_of_month"：一个月中的第几周，按照星期计算周。<br>"day_of_week_in_month"：一月中的第几周，按照数值计算周，例如1-7日属于第一周。<br>"day_of_year"：一年中的第几天。<br>"day_of_week"：一周中的第几天(星期)。<br>"milliseconds_in_day"：一天中的第几毫秒。<br>"zone_offset"：以毫秒计时的时区固定偏移量（不含夏令时）。<br>"dst_offset"：以毫秒计时的夏令时偏移量。<br>"dow_local"：本地星期。<br>"extended_year"：扩展的年份数值，支持负数。<br>"julian_day"：儒略日，与当前时区相关。<br>"is_leap_month"：返回1表示是闰月，返回0表示不是闰月。<br> |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 日历属性的值，如当前Calendar对象的内部日期的年份为1990，get('year')返回1990。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.set(2021, 10, 1, 8, 0, 0); // 设置时间日期为2021.11.1 08:00:00
let hourOfDay: number = calendar.get('hour_of_day'); // hourOfDay = 8

```

## getDisplayName

```TypeScript
getDisplayName(locale: string): string
```

获取日历对象名称在指定语言下的翻译。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getDisplayName(locale: string): string--><!--Device-Calendar-getDisplayName(locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 日历对象名称在指定语言下的翻译。如buddhist在en-US上显示的名称为“Buddhist Calendar”。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'buddhist');
let calendarName: string = calendar.getDisplayName('zh'); // calendarName = '佛历'

```

## getFirstDayOfWeek

```TypeScript
getFirstDayOfWeek(): number
```

获取日历对象的周起始日。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getFirstDayOfWeek(): int--><!--Device-Calendar-getFirstDayOfWeek(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 周起始日，1代表周日，7代表周六。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'gregory');
let firstDayOfWeek: number = calendar.getFirstDayOfWeek(); // firstDayOfWeek = 1

```

## getMinimalDaysInFirstWeek

```TypeScript
getMinimalDaysInFirstWeek(): number
```

获取日历对象一年中第一周的最小天数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getMinimalDaysInFirstWeek(): int--><!--Device-Calendar-getMinimalDaysInFirstWeek(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 一年中第一周的最小天数。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
let minimalDaysInFirstWeek: number = calendar.getMinimalDaysInFirstWeek(); // minimalDaysInFirstWeek = 1

```

## getTimeInMillis

```TypeScript
getTimeInMillis(): number
```

获取当前日历对象的时间戳。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getTimeInMillis(): long--><!--Device-Calendar-getTimeInMillis(): long-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Unix时间戳，表示从1970.1.1 00:00:00 GMT逝去的毫秒数。 |

**示例：**

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

获取日历对象的时区ID。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getTimeZone(): string--><!--Device-Calendar-getTimeZone(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示时区ID的字符串。 |

**示例：**

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

判断指定的日期在日历对象中是否为周末。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-isWeekend(date?: Date): boolean--><!--Device-Calendar-isWeekend(date?: Date): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 否 | 时间日期。<br>**说明：**<br>月份从0开始计数，0表示一月。<br>默认值：日历对象的当前日期。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示指定的日期是周末，false表示指定的日期不是周末。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.set(2021, 11, 11, 8, 0, 0); // 设置时间为2021.12.11 08:00:00
let isWeekend: boolean = calendar.isWeekend(); // isWeekend = true
let date: Date = new Date(2011, 11, 6, 9, 0, 0); // 时间日期为2011.12.06 09:00:00
isWeekend = calendar.isWeekend(date); // isWeekend = false

```

## set

```TypeScript
set(year: number, month: number, date:number, hour?: number, minute?: number, second?: number): void
```

设置日历对象的年、月、日、时、分、秒。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-set(year: int, month: int, date:int, hour?: int, minute?: int, second?: int): void--><!--Device-Calendar-set(year: int, month: int, date:int, hour?: int, minute?: int, second?: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| year | number | 是 | 设置的年。 |
| month | number | 是 | 设置的月。<br>**说明：**<br>月份从0开始计数，0表示一月。 |
| date | number | 是 | 设置的日。 |
| hour | number | 否 | 设置的小时。默认值：系统时间。 |
| minute | number | 否 | 设置的分钟。默认值：系统时间。 |
| second | number | 否 | 设置的秒。默认值：系统时间。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.set(2021, 10, 1, 8, 0, 0); // 设置时间日期为2021.11.1 08:00:00

```

## setFirstDayOfWeek

```TypeScript
setFirstDayOfWeek(value: number): void
```

设置日历对象的周起始日。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setFirstDayOfWeek(value: int): void--><!--Device-Calendar-setFirstDayOfWeek(value: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 一周的起始日，1代表周日，7代表周六。 |

**示例：**

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

设置日历对象一年中第一周的最小天数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setMinimalDaysInFirstWeek(value: int): void--><!--Device-Calendar-setMinimalDaysInFirstWeek(value: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 一年中第一周的最小天数。 |

**示例：**

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

基于传入的Date对象，设置日历对象内部的时间日期。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setTime(date: Date): void--><!--Device-Calendar-setTime(date: Date): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。<br>**说明：**<br>月份从0开始计数，0表示一月。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'gregory');
let date: Date = new Date(2021, 10, 7, 8, 0, 0); // 时间日期为2021.11.07 08:00:00
calendar.setTime(date);

```

## setTime

```TypeScript
setTime(time: number): void
```

基于传入的时间戳，设置日历对象内部的时间日期。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setTime(time: double): void--><!--Device-Calendar-setTime(time: double): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| time | number | 是 | Unix时间戳，表示从1970.1.1 00:00:00 GMT逝去的毫秒数。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('en-US', 'gregory');
calendar.setTime(10540800000);

```

## setTimeZone

```TypeScript
setTimeZone(timezone: string): void
```

设置日历对象的时区。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setTimeZone(timezone: string): void--><!--Device-Calendar-setTimeZone(timezone: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timezone | string | 是 | 合法的时区ID，如“Asia/Shanghai”。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans');
calendar.setTimeZone('Asia/Shanghai');

```

