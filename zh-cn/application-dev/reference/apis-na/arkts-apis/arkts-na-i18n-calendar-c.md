# Calendar

提供历法相关的能力，包括历法名称获取和日期计算等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-i18n-export class Calendar--><!--Device-i18n-export class Calendar-End-->

**系统能力：** SystemCapability.Global.I18n

## add

```TypeScript
add(field: string, amount: int): void
```

对日历对象中的表示时间日期的日历属性值进行加减操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-add(field: string, amount: int): void--><!--Device-Calendar-add(field: string, amount: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 指定的日历属性，目前支持的属性值有 year, month, week_of_year, week_of_month, date, day_of_year,  day_of_week, day_of_week_in_month, hour, hour_of_day, minute, second, millisecond。 &lt;br&gt;各取值代表的含义请参考[get](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-calendar-c.md#get)。 |
| amount | int | 是 | 进行加减操作的具体数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## compareDays

```TypeScript
compareDays(date: Date): int
```

比较日历对象当前日期和指定日期相差的天数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-compareDays(date: Date): int--><!--Device-Calendar-compareDays(date: Date): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 相差的天数，正数表示日历时间更早，负数表示指定时间更早。 &lt;br&gt;按毫秒级的精度，不足一天按一天计。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

## get

```TypeScript
get(field: string): int
```

获取日历对象中日历属性的值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-get(field: string): int--><!--Device-Calendar-get(field: string): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 指定的日历属性，取值包括： &lt;br&gt;"era"：纪元，例如公历中的公元前或者公元后。 &lt;br&gt;"year"：年。 &lt;br&gt;"month"：月，从0开始计数，0表示一月。 &lt;br&gt;"date"：日。 &lt;br&gt;"hour"：挂钟小时数。 &lt;br&gt;"hour_of_day"：一天中的第几小时。 &lt;br&gt;"minute"：分。 &lt;br&gt;"second"：秒。 &lt;br&gt;"millisecond"：毫秒。 &lt;br&gt;"week_of_year"：一年中的第几周，按照星期计算周，第一周的归属各地有区别。 &lt;br&gt;"year_woy"：一年中的第几周，按照数值计算周，例如一年中前1~7日属于第一周。 &lt;br&gt;"week_of_month"：一个月中的第几周，按照星期计算周。 &lt;br&gt;"day_of_week_in_month"：一月中的第几周，按照数值计算周，例如1-7日属于第一周。 &lt;br&gt;"day_of_year"：一年中的第几天。 &lt;br&gt;"day_of_week"：一周中的第几天(星期)。 &lt;br&gt;"milliseconds_in_day"：一天中的第几毫秒。 &lt;br&gt;"zone_offset"：以毫秒计时的时区固定偏移量（不含夏令时）。 &lt;br&gt;"dst_offset"：以毫秒计时的夏令时偏移量。 &lt;br&gt;"dow_local"：本地星期。 &lt;br&gt;"extended_year"：扩展的年份数值，支持负数。 &lt;br&gt;"julian_day"：儒略日，与当前时区相关。 &lt;br&gt;"is_leap_month"：返回1表示是闰月，返回0表示不是闰月。 &lt;br&gt; |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 日历属性的值，如当前Calendar对象的内部日期的年份为1990，get('year')返回1990。 |

## getDisplayName

```TypeScript
getDisplayName(locale: string): string
```

获取日历对象名称在指定语言下的翻译。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getDisplayName(locale: string): string--><!--Device-Calendar-getDisplayName(locale: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组 成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 日历对象名称在指定语言下的翻译。如buddhist在en-US上显示的名称为“Buddhist Calendar”。 |

## getFirstDayOfWeek

```TypeScript
getFirstDayOfWeek(): int
```

获取日历对象的周起始日。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getFirstDayOfWeek(): int--><!--Device-Calendar-getFirstDayOfWeek(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 周起始日，1代表周日，7代表周六。 |

## getMinimalDaysInFirstWeek

```TypeScript
getMinimalDaysInFirstWeek(): int
```

获取日历对象一年中第一周的最小天数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getMinimalDaysInFirstWeek(): int--><!--Device-Calendar-getMinimalDaysInFirstWeek(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 一年中第一周的最小天数。 |

## getTimeInMillis

```TypeScript
getTimeInMillis(): long
```

获取当前日历对象的时间戳。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getTimeInMillis(): long--><!--Device-Calendar-getTimeInMillis(): long-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Unix时间戳，表示从1970.1.1 00:00:00 GMT逝去的毫秒数。 |

## getTimeZone

```TypeScript
getTimeZone(): string
```

获取日历对象的时区ID。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-getTimeZone(): string--><!--Device-Calendar-getTimeZone(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示时区ID的字符串。 |

## isWeekend

```TypeScript
isWeekend(date?: Date): boolean
```

判断指定的日期在日历对象中是否为周末。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-isWeekend(date?: Date): boolean--><!--Device-Calendar-isWeekend(date?: Date): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 否 | 时间日期。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 &lt;br&gt;默认值：日历对象的当前日期。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示指定的日期是周末，false表示指定的日期不是周末。 |

## set

```TypeScript
set(year: int, month: int, date:int, hour?: int, minute?: int, second?: int): void
```

设置日历对象的年、月、日、时、分、秒。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-set(year: int, month: int, date:int, hour?: int, minute?: int, second?: int): void--><!--Device-Calendar-set(year: int, month: int, date:int, hour?: int, minute?: int, second?: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| year | int | 是 | 设置的年。 |
| month | int | 是 | 设置的月。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 |
| date | int | 是 | 设置的日。 |
| hour | int | 否 | 设置的小时。默认值：系统时间。 |
| minute | int | 否 | 设置的分钟。默认值：系统时间。 |
| second | int | 否 | 设置的秒。默认值：系统时间。 |

## setFirstDayOfWeek

```TypeScript
setFirstDayOfWeek(value: int): void
```

设置日历对象的周起始日。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setFirstDayOfWeek(value: int): void--><!--Device-Calendar-setFirstDayOfWeek(value: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | 一周的起始日，1代表周日，7代表周六。 |

## setMinimalDaysInFirstWeek

```TypeScript
setMinimalDaysInFirstWeek(value: int): void
```

设置日历对象一年中第一周的最小天数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setMinimalDaysInFirstWeek(value: int): void--><!--Device-Calendar-setMinimalDaysInFirstWeek(value: int): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | 一年中第一周的最小天数。 |

## setTime

```TypeScript
setTime(date: Date): void
```

基于传入的Date对象，设置日历对象内部的时间日期。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setTime(date: Date): void--><!--Device-Calendar-setTime(date: Date): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。 &lt;br&gt;**说明：** &lt;br&gt;月份从0开始计数，0表示一月。 |

## setTime

```TypeScript
setTime(time: double): void
```

基于传入的时间戳，设置日历对象内部的时间日期。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setTime(time: double): void--><!--Device-Calendar-setTime(time: double): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| time | double | 是 | Unix时间戳，表示从1970.1.1 00:00:00 GMT逝去的毫秒数。 |

## setTimeZone

```TypeScript
setTimeZone(timezone: string): void
```

设置日历对象的时区。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Calendar-setTimeZone(timezone: string): void--><!--Device-Calendar-setTimeZone(timezone: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timezone | string | 是 | 合法的时区ID，如“Asia/Shanghai”。 |

