# Character

提供Unicode字符属性相关的接口，例如：判断一个字符是否是数字。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Unicode](arkts-localization-i18n-unicode-c.md)

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getType

```TypeScript
getType(ch: string): string
```

获取输入的字符的一般类别值。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getType](arkts-localization-i18n-unicode-c.md#gettype)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 输入字符的一般类别值。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let unicodeType: string = i18n.Unicode.getType('a'); // unicodeType = 'U_LOWERCASE_LETTER'
```

## isDigit

```TypeScript
isDigit(ch: string): boolean
```

判断输入的字符是否是数字。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isDigit](arkts-localization-i18n-unicode-c.md#isdigit)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是数字，false表示输入的字符不是数字。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isDigit: boolean = i18n.Unicode.isDigit('1'); // isDigit = true
```

## isIdeograph

```TypeScript
isIdeograph(ch: string): boolean
```

判断输入的字符是否是表意文字。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isIdeograph](arkts-localization-i18n-unicode-c.md#isideograph)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是表意文字，false表示输入的字符不是表意文字。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isIdeograph: boolean = i18n.Unicode.isIdeograph('a'); // isIdeograph = false
```

## isLetter

```TypeScript
isLetter(ch: string): boolean
```

判断输入的字符是否是字母。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isLetter](arkts-localization-i18n-unicode-c.md#isletter)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是字母，false表示输入的字符不是字母。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isLetter: boolean = i18n.Unicode.isLetter('a'); // isLetter = true
```

## isLowerCase

```TypeScript
isLowerCase(ch: string): boolean
```

判断输入的字符是否是小写字母。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isLowerCase](arkts-localization-i18n-unicode-c.md#islowercase)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是小写字母，false表示输入的字符不是小写字母。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isLowercase: boolean = i18n.Unicode.isLowerCase('a'); // isLowercase = true
```

## isRTL

```TypeScript
isRTL(ch: string): boolean
```

判断输入的字符是否是从右到左语言的字符。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isRTL](arkts-localization-i18n-unicode-c.md#isrtl)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是从右到左语言的字符，false表示输入的字符不是从右到左语言的字符。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isRtl: boolean = i18n.Unicode.isRTL('a'); // isRtl = false
```

## isSpaceChar

```TypeScript
isSpaceChar(ch: string): boolean
```

判断输入的字符是否是空格符。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSpaceChar](arkts-localization-i18n-unicode-c.md#isspacechar)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是空格符，false表示输入的字符不是空格符。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isSpacechar: boolean = i18n.Unicode.isSpaceChar('a'); // isSpacechar = false
```

## isUpperCase

```TypeScript
isUpperCase(ch: string): boolean
```

判断输入的字符是否是大写字母。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isUpperCase](arkts-localization-i18n-unicode-c.md#isuppercase)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是大写字母，false表示输入的字符不是大写字母。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isUppercase: boolean = i18n.Unicode.isUpperCase('a'); // isUppercase = false
```

## isWhitespace

```TypeScript
isWhitespace(ch: string): boolean
```

判断输入的字符是否是空白符。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isWhitespace](arkts-localization-i18n-unicode-c.md#iswhitespace)

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是空白符，false表示输入的字符不是空白符。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isWhitespace: boolean = i18n.Unicode.isWhitespace('a'); // isWhitespace = false
```
