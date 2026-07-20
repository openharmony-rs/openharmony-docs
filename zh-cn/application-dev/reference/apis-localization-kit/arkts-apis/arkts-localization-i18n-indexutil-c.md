# IndexUtil

提供索引相关的能力，包括区域索引列表和文本索引值获取。

**起始版本：** 8

<!--Device-i18n-export class IndexUtil--><!--Device-i18n-export class IndexUtil-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="addlocale"></a>
## addLocale

```TypeScript
addLocale(locale: string): void
```

在当前区域的索引列表中，添加新区域的索引列表，形成复合列表。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IndexUtil-addLocale(locale: string): void--><!--Device-IndexUtil-addLocale(locale: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | [表示区域ID的字符串](docroot://internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
indexUtil.addLocale('en-US');

```

<a id="getindex"></a>
## getIndex

```TypeScript
getIndex(text: string): string
```

获取输入文本对应的索引值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IndexUtil-getIndex(text: string): string--><!--Device-IndexUtil-getIndex(text: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 输入文本对应的索引值。无合适索引时返回空字符串。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
let index: string = indexUtil.getIndex('hi'); // index = 'H'

```

<a id="getindexlist"></a>
## getIndexList

```TypeScript
getIndexList(): Array<string>
```

获取当前区域的索引列表。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IndexUtil-getIndexList(): Array<string>--><!--Device-IndexUtil-getIndexList(): Array<string>-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 当前区域的索引列表。第一个元素和最后一个元素为“...”。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
// indexList = [ '...', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
// 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', '...' ]
let indexList: Array<string> = indexUtil.getIndexList();

```

