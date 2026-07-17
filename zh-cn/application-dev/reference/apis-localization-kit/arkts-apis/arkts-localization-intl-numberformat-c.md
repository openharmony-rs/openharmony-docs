# NumberFormat

提供标准的数字格式化的能力。

**起始版本：** 6

<!--Device-intl-export class NumberFormat--><!--Device-intl-export class NumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor()
```

使用当前系统区域创建数字格式化对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberFormat-constructor()--><!--Device-NumberFormat-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用系统当前区域ID创建NumberFormat对象
let formatter: intl.NumberFormat = new intl.NumberFormat();

```

## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: NumberOptions)
```

根据指定的区域和配置项创建数字格式化对象。

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberFormat-constructor(locale: string | Array<string>, options?: NumberOptions)--><!--Device-NumberFormat-constructor(locale: string | Array<string>, options?: NumberOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string \| Array<string> | 是 | 区域ID或区域ID数组。输入是区域ID数组时，使用第一个有效的区域ID。 |
| options | [NumberOptions](arkts-localization-intl-numberoptions-i.md) | 否 | 创建数字格式化对象时可设置的配置项。<br>默认值：所有属性都取默认值时的配置项。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用en-GB区域ID创建NumberFormat对象，style设置为decimal，notation设置为scientific
let formatter: intl.NumberFormat = new intl.NumberFormat('en-GB', { style: 'decimal', notation: 'scientific' });

```

## format

```TypeScript
format(num: number): string
```

对数字进行格式化，返回格式化后的数字字符串。

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberFormat-format(num: double): string--><!--Device-NumberFormat-format(num: double): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| num | number | 是 | 数字对象。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的数字字符串。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用区域ID列表创建NumberFormat对象，因为en-GB为合法的区域ID，因此使用en-GB创建NumberFormat对象
let formatter: intl.NumberFormat = new intl.NumberFormat(['en-GB', 'zh'], { style: 'decimal', notation: 'scientific' });
let formattedNumber: string = formatter.format(1223); // formattedNumber = 1.223E3
let options: intl.NumberOptions = {
  roundingPriority: 'lessPrecision',
  maximumFractionDigits: 3,
  maximumSignificantDigits: 3
}
formatter = new intl.NumberFormat('en', options);
let result: string = formatter.format(1.23456); // result = 1.23

```

## formatRange

```TypeScript
formatRange(startRange: number, endRange: number): string
```

对数字范围进行格式化，返回格式化后的数字范围字符串。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NumberFormat-formatRange(startRange: double, endRange: double): string--><!--Device-NumberFormat-formatRange(startRange: double, endRange: double): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startRange | number | 是 | 数字范围的起始值。 |
| endRange | number | 是 | 数字范围的终止值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的数字范围字符串。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let formatter: intl.NumberFormat = new intl.NumberFormat('en-US', { style: 'unit', unit: 'meter' });
let formattedRange: string = formatter.formatRange(0, 3); // formattedRange: 0–3 m

```

## resolvedOptions

```TypeScript
resolvedOptions(): NumberOptions
```

获取创建数字格式化对象时设置的配置项。

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberFormat-resolvedOptions(): NumberOptions--><!--Device-NumberFormat-resolvedOptions(): NumberOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NumberOptions](arkts-localization-intl-numberoptions-i.md) | 创建数字格式化对象时设置的配置项。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let formatter: intl.NumberFormat = new intl.NumberFormat(['en-GB', 'zh'], { style: 'decimal', notation: 'scientific' });
// 获取NumberFormat对象配置项
let options: intl.NumberOptions = formatter.resolvedOptions();
let style: string | undefined = options.style; // style = 'decimal'
let notation: string | undefined = options.notation; // notation = 'scientific'

```

