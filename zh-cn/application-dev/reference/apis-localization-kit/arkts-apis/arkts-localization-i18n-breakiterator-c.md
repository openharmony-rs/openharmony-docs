# BreakIterator

提供文本换行相关的能力，包括可换行点的获取、移动和识别等。

**起始版本：** 8

<!--Device-i18n-export class BreakIterator--><!--Device-i18n-export class BreakIterator-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="current"></a>
## current

```TypeScript
current(): number
```

获取换行迭代器在当前处理文本中的位置。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-current(): int--><!--Device-BreakIterator-current(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取换行迭代器在当前处理的文本中的位置。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let currentPos: number = iterator.current(); // currentPos = 0

```

<a id="first"></a>
## first

```TypeScript
first(): number
```

将换行迭代器移动到第一个可换行点。第一个可换行点总是在被处理文本的起始位置。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-first(): int--><!--Device-BreakIterator-first(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 被处理文本的第一个可换行点的偏移量。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let firstPos: number = iterator.first(); // firstPos = 0

```

<a id="following"></a>
## following

```TypeScript
following(offset: number): number
```

将换行迭代器移动到指定位置后面一个可换行点。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-following(offset: int): int--><!--Device-BreakIterator-following(offset: int): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 将换行迭代器移动到文本指定位置的后面一个可换行点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 换行迭代器移动后的位置。若offset所指定位置的下一个可换行点超出了文本的范围，则返回-1。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let pos: number = iterator.following(0); // pos = 6
pos = iterator.following(100); // pos = -1
pos = iterator.current(); // pos = 27

```

<a id="getlinebreaktext"></a>
## getLineBreakText

```TypeScript
getLineBreakText(): string
```

获取BreakIterator对象当前处理的文本。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-getLineBreakText(): string--><!--Device-BreakIterator-getLineBreakText(): string-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | BreakIterator对象正在处理的文本。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let breakText: string = iterator.getLineBreakText(); // breakText = 'Apple is my favorite fruit.'

```

<a id="isboundary"></a>
## isBoundary

```TypeScript
isBoundary(offset: number): boolean
```

判断指定位置是否为可换行点。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-isBoundary(offset: int): boolean--><!--Device-BreakIterator-isBoundary(offset: int): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 文本指定位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示offset指定的文本位置是一个可换行点，false表示offset指定的文本位置不是一个可换行点。<br>返回true时，会将换行迭代器移动到offset指定的位置，否则相当于调用following。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let isBoundary: boolean = iterator.isBoundary(0); // isBoundary = true;
isBoundary = iterator.isBoundary(5); // isBoundary = false;

```

<a id="last"></a>
## last

```TypeScript
last(): number
```

将换行迭代器移动到最后一个可换行点。最后一个可换行点总是在被处理文本末尾的下一个位置。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-last(): int--><!--Device-BreakIterator-last(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 被处理文本的最后一个可换行点的偏移量。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let lastPos: number = iterator.last(); // lastPos = 27

```

<a id="next"></a>
## next

```TypeScript
next(index?: number): number
```

将换行迭代器向后移动index个可换行点。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-next(index?: int): int--><!--Device-BreakIterator-next(index?: int): int-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 否 | 换行迭代器将要移动的可换行点数，取值为整数。<br>正数表示向后移动index个可换行点，负数表示向前移动index个可换行点。<br>默认值：1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 移动index个可换行点后，当前换行迭代器在文本中的位置。<br>若移动index个可换行点后超出了所处理的文本的长度范围，返回-1。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let pos: number = iterator.first(); // pos = 0
pos = iterator.next(); // pos = 6
pos = iterator.next(10); // pos = -1

```

<a id="previous"></a>
## previous

```TypeScript
previous(): number
```

将换行迭代器向前移动一个可换行点。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-previous(): int--><!--Device-BreakIterator-previous(): int-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 移动到前一个可换行点后，当前换行迭代器在文本中的位置。<br>若移动后超出了所处理的文本的长度范围，返回-1。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let pos: number = iterator.first(); // pos = 0
pos = iterator.next(3); // pos = 12
pos = iterator.previous(); // pos = 9

```

<a id="setlinebreaktext"></a>
## setLineBreakText

```TypeScript
setLineBreakText(text: string): void
```

设置BreakIterator对象要处理的文本。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BreakIterator-setLineBreakText(text: string): void--><!--Device-BreakIterator-setLineBreakText(text: string): void-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入文本。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.'); // 设置处理文本

```

