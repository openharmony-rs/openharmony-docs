# ISO8601DateTimeFormatOptions

符合ISO 8601标准的日期格式化对象创建时的配置项。

**起始版本：** 26.0.0

<!--Device-i18n-export interface ISO8601DateTimeFormatOptions--><!--Device-i18n-export interface ISO8601DateTimeFormatOptions-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## dateFormat

```TypeScript
dateFormat?: 'calendar' | 'ordinal' | 'week'
```

日期格式。取值包括：

**calendar**：日期模式为**YYYY-MM-DD**。

**ordinal**：日期模式为**YYYY-DDD**。

**week**：日期模式为**YYYY-Www-D**。

默认值：**calendar**。模式中字符含义参考[日期字段符号表](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table)。

**类型：** 'calendar' \| 'ordinal' \| 'week'

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ISO8601DateTimeFormatOptions-dateFormat?: 'calendar' | 'ordinal' | 'week'--><!--Device-ISO8601DateTimeFormatOptions-dateFormat?: 'calendar' | 'ordinal' | 'week'-End-->

**系统能力：** SystemCapability.Global.I18n

## displayTimeZone

```TypeScript
displayTimeZone?: boolean
```

是否显示时区，true表示显示时区，false表示不显示时区。默认值：true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ISO8601DateTimeFormatOptions-displayTimeZone?: boolean--><!--Device-ISO8601DateTimeFormatOptions-displayTimeZone?: boolean-End-->

**系统能力：** SystemCapability.Global.I18n

## separatorStyle

```TypeScript
separatorStyle?: 'extended' | 'basic'
```

分隔符风格。取值包括：

**extended**：显示日期和时间分隔符。

**basic**：不显示日期和时间分隔符。

默认值：**extended**。

**类型：** 'extended' \| 'basic'

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ISO8601DateTimeFormatOptions-separatorStyle?: 'extended' | 'basic'--><!--Device-ISO8601DateTimeFormatOptions-separatorStyle?: 'extended' | 'basic'-End-->

**系统能力：** SystemCapability.Global.I18n

## timePrecision

```TypeScript
timePrecision?: 'dateOnly' | 'hours' | 'minutes' | 'seconds' | 'milliSeconds'
```

时间精度。取值包括：

**dateOnly**：只显示日期。

**hours**：显示小时。

**minutes**：显示时分。

**seconds**：显示时分秒。

**milliSeconds**：显示时分秒毫秒。

默认值：**seconds**。

**类型：** 'dateOnly' \| 'hours' \| 'minutes' \| 'seconds' \| 'milliSeconds'

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ISO8601DateTimeFormatOptions-timePrecision?: 'dateOnly' | 'hours' | 'minutes' | 'seconds' | 'milliSeconds'--><!--Device-ISO8601DateTimeFormatOptions-timePrecision?: 'dateOnly' | 'hours' | 'minutes' | 'seconds' | 'milliSeconds'-End-->

**系统能力：** SystemCapability.Global.I18n

## timeZone

```TypeScript
timeZone?: TimeZone
```

时区。默认值：**UTC**。

**类型：** TimeZone

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ISO8601DateTimeFormatOptions-timeZone?: TimeZone--><!--Device-ISO8601DateTimeFormatOptions-timeZone?: TimeZone-End-->

**系统能力：** SystemCapability.Global.I18n

