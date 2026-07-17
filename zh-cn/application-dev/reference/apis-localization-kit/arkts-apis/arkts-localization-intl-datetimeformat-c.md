# DateTimeFormat

提供日期格式化的能力。

**起始版本：** 6

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)

<!--Device-intl-export class DateTimeFormat--><!--Device-intl-export class DateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor()
```

创建时间日期格式化对象。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-DateTimeFormat-constructor()--><!--Device-DateTimeFormat-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用系统当前区域ID创建DateTimeFormat对象
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat();

```

## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: DateTimeOptions)
```

创建时间日期格式化对象。

**起始版本：** 6

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-DateTimeFormat-constructor(locale: string | Array<string>, options?: DateTimeOptions)--><!--Device-DateTimeFormat-constructor(locale: string | Array<string>, options?: DateTimeOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string \| Array<string> | 是 | 区域ID或区域ID数组。输入是区域ID数组时，使用第一个有效的区域ID。 |
| options | [DateTimeOptions](arkts-localization-intl-datetimeoptions-i.md) | 否 | 创建时间日期格式化对象时可设置的配置项。<br>若所有选项均未设置时，year、month、day三个属性的默认值为numeric。<br>默认值：所有属性都取默认值时的配置项。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用zh-CN区域ID创建DateTimeFormat对象，日期风格为full，时间风格为medium
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('zh-CN', { dateStyle: 'full', timeStyle: 'medium' });

// 使用区域ID列表创建DateTimeFormat对象，因为ban为非法区域ID，因此使用zh区域ID创建DateTimeFormat对象
formatter = new intl.DateTimeFormat(['ban', 'zh'], { dateStyle: 'full', timeStyle: 'medium' });

```

## format

```TypeScript
format(date: Date): string
```

对时间日期进行格式化，返回格式化后的时间日期字符串。

**起始版本：** 6

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/format)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-DateTimeFormat-format(date: Date): string--><!--Device-DateTimeFormat-format(date: Date): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。<br>**说明：**<br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的时间日期字符串。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let date: Date = new Date(2021, 11, 17, 3, 24, 0); // 时间日期为2021.12.17 03:24:00
// 使用en-GB区域ID创建DateTimeFormat对象
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('en-GB');
let formattedDate: string = formatter.format(date); // formattedDate "17/12/2021"

// 使用en-GB区域ID创建DateTimeFormat对象，dateStyle设置为full，timeStyle设置为medium
formatter = new intl.DateTimeFormat('en-GB', { dateStyle: 'full', timeStyle: 'medium' });
formattedDate = formatter.format(date); // formattedDate "Friday, 17 December 2021, 03:24:00"

```

## formatRange

```TypeScript
formatRange(startDate: Date, endDate: Date): string
```

对时间日期段进行格式化，返回格式化后的时间日期段字符串。

**起始版本：** 6

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/formatRange)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-DateTimeFormat-formatRange(startDate: Date, endDate: Date): string--><!--Device-DateTimeFormat-formatRange(startDate: Date, endDate: Date): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startDate | Date | 是 | 时间日期的开始。<br>**说明：**<br>月份从0开始计数，0表示一月。 |
| endDate | Date | 是 | 时间日期的结束。<br>**说明：**<br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的时间日期段字符串。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let startDate: Date = new Date(2021, 11, 17, 3, 24, 0); // 时间日期为2021.12.17 03:24:00
let endDate: Date = new Date(2021, 11, 18, 3, 24, 0);
// 使用en-GB区域ID创建DateTimeFormat对象
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('en-GB');
let formattedDateRange: string = formatter.formatRange(startDate, endDate); // formattedDateRange = '17/12/2021 - 18/12/2021'

```

## resolvedOptions

```TypeScript
resolvedOptions(): DateTimeOptions
```

获取创建时间日期格式化对象时设置的配置项。

**起始版本：** 6

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/resolvedOptions)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-DateTimeFormat-resolvedOptions(): DateTimeOptions--><!--Device-DateTimeFormat-resolvedOptions(): DateTimeOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DateTimeOptions](arkts-localization-intl-datetimeoptions-i.md) | 时间日期格式化对象设置的配置项。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('en-GB', { dateStyle: 'full', timeStyle: 'medium' });
// 返回DateTimeFormat对象的配置项
let options: intl.DateTimeOptions = formatter.resolvedOptions();
let dateStyle: string | undefined = options.dateStyle; // dateStyle = 'full'
let timeStyle: string | undefined = options.timeStyle; // timeStyle = 'medium'

```

