# Collator

提供字符串排序的能力。

**起始版本：** 8

<!--Device-intl-export class Collator--><!--Device-intl-export class Collator-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

<a id="compare"></a>
## compare

```TypeScript
compare(first: string, second: string): number
```

根据配置项的排序规则，比较两个字符串。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Collator-compare(first: string, second: string): int--><!--Device-Collator-compare(first: string, second: string): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | string | 是 | 进行比较的第一个字符串。 |
| second | string | 是 | 进行比较的第二个字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 比较结果。<br>- number为负数时，表示first排序在second之前。<br>- number为0时，表示first与second排序相同。<br>- number为正数，表示first排序在second之后。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用en-GB区域ID创建Collator对象
let collator = new intl.Collator('en-GB');
// 比较first和second的先后顺序
let compareResult = collator.compare('first', 'second'); // compareResult = -1

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

使用当前系统区域创建排序对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Collator-constructor()--><!--Device-Collator-constructor()-End-->

**系统能力：** SystemCapability.Global.I18n

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用系统区域创建Collator对象
let collator = new intl.Collator();

```

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: CollatorOptions)
```

根据指定的区域和配置项创建排序对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Collator-constructor(locale: string | Array<string>, options?: CollatorOptions)--><!--Device-Collator-constructor(locale: string | Array<string>, options?: CollatorOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string \| Array&lt;string&gt; | 是 | 区域ID或区域ID数组。输入是区域ID数组时，使用第一个有效的区域ID。 |
| options | [CollatorOptions](arkts-localization-intl-collatoroptions-i.md) | 否 | 创建排序对象时可设置的配置项。<br>默认值：所有属性都取默认值时的配置项。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// 使用zh-CN区域ID创建Collator对象，localeMatcher设置为lookup，usage设置为sort
let collator = new intl.Collator('zh-CN', {localeMatcher: 'lookup', usage: 'sort'});

```

<a id="resolvedoptions"></a>
## resolvedOptions

```TypeScript
resolvedOptions(): CollatorOptions
```

获取创建排序对象时设置的配置项。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Collator-resolvedOptions(): CollatorOptions--><!--Device-Collator-resolvedOptions(): CollatorOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CollatorOptions](arkts-localization-intl-collatoroptions-i.md) | 返回排序对象的属性。 |

**示例：**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let collator = new intl.Collator('zh-Hans', { usage: 'sort', ignorePunctuation: true });
// 获取Collator对象的配置项
let options = collator.resolvedOptions();
let usage = options.usage; // usage = 'sort'
let ignorePunctuation = options.ignorePunctuation; // ignorePunctuation = true

```

