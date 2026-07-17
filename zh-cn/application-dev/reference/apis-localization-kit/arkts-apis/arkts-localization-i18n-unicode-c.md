# Unicode

提供字符属性相关的能力，包括判断字符是否为空格、数字和字母等。

**起始版本：** 9

<!--Device-i18n-export class Unicode--><!--Device-i18n-export class Unicode-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## detectEncoding

```TypeScript
static detectEncoding(bytes: Uint8Array): EncodingInfo
```

识别输入字节流的编码信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static detectEncoding(bytes: Uint8Array): EncodingInfo--><!--Device-Unicode-static detectEncoding(bytes: Uint8Array): EncodingInfo-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bytes | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 输入字节流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EncodingInfo](arkts-localization-i18n-encodinginfo-i.md) | 编码信息，包含编码名称和置信度。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let uint8Array = new Uint8Array([0xEF, 0xBB, 0xBF, 0xE4, 0xB8, 0xAD]);
let info = i18n.Unicode.detectEncoding(uint8Array); // info.encodingName = 'UTF-8', info.confidence = 100

```

## getType

```TypeScript
static getType(ch: string): string
```

获取输入的字符的一般类别值。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static getType(ch: string): string--><!--Device-Unicode-static getType(ch: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 输入字符的一般类别值。取值包括：<br>U_UNASSIGNED： 表示未分配和非字符代码点对应类别。<br>U_GENERAL_OTHER_TYPES： 与 U_UNASSIGNED 一致。<br>U_UPPERCASE_LETTER： 表示大写字母。<br>U_LOWERCASE_LETTER： 表示小写字母。<br>U_TITLECASE_LETTER： 表示首字母大写。<br>U_MODIFIER_LETTER： 表示字母修饰符。<br>U_OTHER_LETTER： 表示其它字母，不属于大写字母、小写字母、首字母大写或修饰符字母的字母。<br>U_NON_SPACING_MARK： 表示非间距标记，例如重音符号'，变音符号#。<br>U_ENCLOSING_MARK： 表示封闭标记和能围住其它字符的标记，如圆圈、方框等。<br>U_COMBINING_SPACING_MARK： 表示间距标记，例如元音符号[ ]。<br>U_DECIMAL_DIGIT_NUMBER： 表示十进制数字。<br>U_LETTER_NUMBER： 表示字母数字，罗马数字。<br>U_OTHER_NUMBER： 表示其它作为加密符号和记号的数字，非阿拉伯数字的数字表示符，例如@、#、（1）、①等。<br>U_SPACE_SEPARATOR： 表示空白分隔符，如空格符、不间断空格、固定宽度的空白符。<br>U_LINE_SEPARATOR： 表示行分隔符。<br>U_PARAGRAPH_SEPARATOR： 表示段落分隔符。<br>U_CONTROL_CHAR： 表示控制字符。<br>U_FORMAT_CHAR： 表示格式字符。<br>U_PRIVATE_USE_CHAR： 表示私人使用区代码点类别，例如公司 logo。<br>U_SURROGATE： 表示代理项，在UTF-16中用来表示补充字符的方法。<br>U_DASH_PUNCTUATION： 表示短划线标点。<br>U_START_PUNCTUATION： 表示开始标点，如左括号。<br>U_END_PUNCTUATION： 表示结束标点，如右括号。<br>U_INITIAL_PUNCTUATION： 表示前引号，例如左双引号、左单引号。<br>U_FINAL_PUNCTUATION： 表示后引号，例如右双引号、右单引号。<br>U_CONNECTOR_PUNCTUATION： 表示连接符标点。<br>U_OTHER_PUNCTUATION： 表示其他标点。<br>U_MATH_SYMBOL： 表示数学符号。<br>U_CURRENCY_SYMBOL： 表示货币符号。<br>U_MODIFIER_SYMBOL： 表示修饰符号。<br>U_OTHER_SYMBOL： 表示其它符号。<br> 更详细的介绍可以参考Unicode标准。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let unicodeType: string = i18n.Unicode.getType('a'); // unicodeType = 'U_LOWERCASE_LETTER'

```

## isDigit

```TypeScript
static isDigit(ch: string): boolean
```

判断输入的字符是否是数字。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isDigit(ch: string): boolean--><!--Device-Unicode-static isDigit(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是数字，false表示输入的字符不是数字。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isDigit: boolean = i18n.Unicode.isDigit('1'); // isDigit = true

```

## isIdeograph

```TypeScript
static isIdeograph(ch: string): boolean
```

判断输入的字符是否是表意文字。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isIdeograph(ch: string): boolean--><!--Device-Unicode-static isIdeograph(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是表意文字，false表示输入的字符不是表意文字。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isIdeograph: boolean = i18n.Unicode.isIdeograph('a'); // isIdeograph = false

```

## isLetter

```TypeScript
static isLetter(ch: string): boolean
```

判断输入的字符是否是字母。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isLetter(ch: string): boolean--><!--Device-Unicode-static isLetter(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是字母，false表示输入的字符不是字母。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isLetter: boolean = i18n.Unicode.isLetter('a'); // isLetter = true

```

## isLowerCase

```TypeScript
static isLowerCase(ch: string): boolean
```

判断输入的字符是否是小写字母。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isLowerCase(ch: string): boolean--><!--Device-Unicode-static isLowerCase(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是小写字母，false表示输入的字符不是小写字母。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isLowercase: boolean = i18n.Unicode.isLowerCase('a'); // isLowercase = true

```

## isRTL

```TypeScript
static isRTL(ch: string): boolean
```

判断输入的字符是否是从右到左语言的字符。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isRTL(ch: string): boolean--><!--Device-Unicode-static isRTL(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是从右到左语言的字符，false表示输入的字符不是从右到左语言的字符。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isRtl: boolean = i18n.Unicode.isRTL('a'); // isRtl = false

```

## isSpaceChar

```TypeScript
static isSpaceChar(ch: string): boolean
```

判断输入的字符是否是空格符。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isSpaceChar(ch: string): boolean--><!--Device-Unicode-static isSpaceChar(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是空格符，false表示输入的字符不是空格符。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isSpacechar: boolean = i18n.Unicode.isSpaceChar('a'); // isSpacechar = false

```

## isUpperCase

```TypeScript
static isUpperCase(ch: string): boolean
```

判断输入的字符是否是大写字母。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isUpperCase(ch: string): boolean--><!--Device-Unicode-static isUpperCase(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是大写字母，false表示输入的字符不是大写字母。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isUppercase: boolean = i18n.Unicode.isUpperCase('a'); // isUppercase = false

```

## isWhitespace

```TypeScript
static isWhitespace(ch: string): boolean
```

判断输入的字符是否是空白符。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Unicode-static isWhitespace(ch: string): boolean--><!--Device-Unicode-static isWhitespace(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是空白符，false表示输入的字符不是空白符。 |

**示例：**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isWhitespace: boolean = i18n.Unicode.isWhitespace('a'); // isWhitespace = false

```

