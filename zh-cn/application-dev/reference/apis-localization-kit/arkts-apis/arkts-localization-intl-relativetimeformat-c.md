# RelativeTimeFormat

提供相对时间格式化的能力。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat)

<!--Device-intl-export class RelativeTimeFormat--><!--Device-intl-export class RelativeTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

创建相对时间格式化对象。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/RelativeTimeFormat)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormat-constructor()--><!--Device-RelativeTimeFormat-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用系统区域创建RelativeTimeFormat对象
let formatter: intl.RelativeTimeFormat = new intl.RelativeTimeFormat();

```

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: RelativeTimeFormatInputOptions)
```

创建相对时间格式化对象。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/RelativeTimeFormat)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormat-constructor(locale: string | Array<string>, options?: RelativeTimeFormatInputOptions)--><!--Device-RelativeTimeFormat-constructor(locale: string | Array<string>, options?: RelativeTimeFormatInputOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string \| Array&lt;string&gt; | 是 | 区域ID或区域ID数组。输入是区域ID数组时，使用第一个有效的区域ID。 |
| options | [RelativeTimeFormatInputOptions](arkts-localization-intl-relativetimeformatinputoptions-i.md) | 否 | 创建相对时间格式化对象时的配置项。<br>默认值：所有属性都取默认值时的配置项。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用zh-CN区域ID创建RelativeTimeFormat对象，localeMatcher设置为lookup，numeric设置为always，style设置为long
let formatter: intl.RelativeTimeFormat = new intl.RelativeTimeFormat('zh-CN', {
  localeMatcher: 'lookup',
  numeric: 'always',
  style: 'long'
});

```

<a id="format"></a>
## format

```TypeScript
format(value: number, unit: string): string
```

对相对时间进行格式化，返回相对时间字符串。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/format)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormat-format(value: double, unit: string): string--><!--Device-RelativeTimeFormat-format(value: double, unit: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 相对时间格式化的数值。 |
| unit | string | 是 | 相对时间格式化的单位，<br>取值包括："year", "quarter", "month", "week", "day", "hour", "minute", "second"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的相对时间。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用zh-CN区域ID创建RelativeTimeFormat对象
let formatter: intl.RelativeTimeFormat = new intl.RelativeTimeFormat('zh-CN');
// 计算zh-CN区域中数字3，单位quarter的本地化表示
let formatResult: string = formatter.format(3, 'quarter'); // formatResult = '3个季度后'

```

<a id="formattoparts"></a>
## formatToParts

```TypeScript
formatToParts(value: number, unit: string): Array<object>
```

对相对时间进行格式化，获取格式化结果中各个部分的对象数组。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/formatToParts)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormat-formatToParts(value: double, unit: string): Array<object>--><!--Device-RelativeTimeFormat-formatToParts(value: double, unit: string): Array<object>-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 相对时间格式化的数值。 |
| unit | string | 是 | 相对时间格式化的单位，<br>取值包括："year", "quarter", "month", "week", "day", "hour", "minute", "second"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;object&gt; | 格式化结果中各个部分的对象数组。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用en区域ID创建RelativeTimeFormat对象，numeric设置为auto
let formatter: intl.RelativeTimeFormat = new intl.RelativeTimeFormat('en', { numeric: 'auto' });
let parts: Array<object> = formatter.formatToParts(10, 'seconds'); // parts = [ {type: 'literal', value: 'in'}, {type: 'integer', value: 10, unit: 'second'}, {type: 'literal', value: 'seconds'} ]

```

<a id="resolvedoptions"></a>
## resolvedOptions

```TypeScript
resolvedOptions(): RelativeTimeFormatResolvedOptions
```

获取相对时间格式化对象的格式化配置项。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/resolvedOptions)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RelativeTimeFormat-resolvedOptions(): RelativeTimeFormatResolvedOptions--><!--Device-RelativeTimeFormat-resolvedOptions(): RelativeTimeFormatResolvedOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RelativeTimeFormatResolvedOptions](arkts-localization-intl-relativetimeformatresolvedoptions-i.md) | 相对时间格式化对象的格式化配置项。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用en-GB区域ID创建RelativeTimeFormat对象
let formatter: intl.RelativeTimeFormat = new intl.RelativeTimeFormat('en-GB', { style: 'short' });
// 获取RelativeTimeFormat对象配置项
let options: intl.RelativeTimeFormatResolvedOptions = formatter.resolvedOptions();
let style: string = options.style; // style = 'short'

```

