# Transliterator

提供文本音译相关的能力，包括音译支持范围获取和文本音译等。

**起始版本：** 9

<!--Device-i18n-export class Transliterator--><!--Device-i18n-export class Transliterator-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getAvailableIDs

```TypeScript
static getAvailableIDs(): string[]
```

获取音译支持的转换ID列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Transliterator-static getAvailableIDs(): string[]--><!--Device-Transliterator-static getAvailableIDs(): string[]-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 音译支持的转换ID列表。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// 共支持742个ID。每一个ID由短横线分隔的两部分组成，格式为 source-destination。例如ids = ['Han-Latin','Latin-ASCII', 'Amharic-Latin/BGN','Accents-Any', ...]，Han-Latin表示汉语转为拉丁文，Amharic-Latin表示阿姆哈拉语转为拉丁文。
// 更多使用信息可以参考ISO-15924。
let ids: string[] = i18n.Transliterator.getAvailableIDs();

```

## getInstance

```TypeScript
static getInstance(id: string): Transliterator
```

创建指定转换ID的音译对象。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Transliterator-static getInstance(id: string): Transliterator--><!--Device-Transliterator-static getInstance(id: string): Transliterator-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 音译支持的转换ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Transliterator](arkts-localization-i18n-transliterator-c.md) | 音译对象。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let transliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn');

```

## transform

```TypeScript
transform(text: string): string
```

将输入文本从源格式转换为目标格式。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Transliterator-transform(text: string): string--><!--Device-Transliterator-transform(text: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换后的文本。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let transliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn');
let wordArray: string[] = ['中国', '德国', '美国', '法国']
for (let i = 0; i < wordArray.length; i++) {
  let transliterateLatn: string =
    transliterator.transform(wordArray[i]); // transliterateLatn依次为：'zhōng guó', 'dé guó', 'měi guó', 'fǎ guó'
}

// 汉语音译去声调
transliterator = i18n.Transliterator.getInstance('Any-Latn;Latin-Ascii');
let transliterateAscii: string = transliterator.transform('中国'); // transliterateAscii = 'zhong guo'

// 汉语姓氏读音
transliterator = i18n.Transliterator.getInstance('Han-Latin/Names');
let transliterateNames: string = transliterator.transform('单老师'); // transliterateNames = 'shàn lǎo shī'
transliterateNames = transliterator.transform('长孙无忌'); // transliterateNames = 'zhǎng sūn wú jì'

```

