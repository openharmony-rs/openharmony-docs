# Character

提供Unicode字符属性相关的接口，例如：判断一个字符是否是数字。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Unicode](arkts-localization-i18n-unicode-c.md)

<!--Device-i18n-export class Character--><!--Device-i18n-export class Character-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

<a id="gettype"></a>
## getType

```TypeScript
getType(ch: string): string
```

获取输入的字符的一般类别值。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getType](arkts-localization-i18n-unicode-c.md#gettype-1)

<!--Device-Character-getType(ch: string): string--><!--Device-Character-getType(ch: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 输入字符的一般类别值。 |

<a id="isdigit"></a>
## isDigit

```TypeScript
isDigit(ch: string): boolean
```

判断输入的字符是否是数字。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isDigit](arkts-localization-i18n-unicode-c.md#isdigit-1)

<!--Device-Character-isDigit(ch: string): boolean--><!--Device-Character-isDigit(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是数字，false表示输入的字符不是数字。 |

<a id="isideograph"></a>
## isIdeograph

```TypeScript
isIdeograph(ch: string): boolean
```

判断输入的字符是否是表意文字。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isIdeograph](arkts-localization-i18n-unicode-c.md#isideograph-1)

<!--Device-Character-isIdeograph(ch: string): boolean--><!--Device-Character-isIdeograph(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是表意文字，false表示输入的字符不是表意文字。 |

<a id="isletter"></a>
## isLetter

```TypeScript
isLetter(ch: string): boolean
```

判断输入的字符是否是字母。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isLetter](arkts-localization-i18n-unicode-c.md#isletter-1)

<!--Device-Character-isLetter(ch: string): boolean--><!--Device-Character-isLetter(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是字母，false表示输入的字符不是字母。 |

<a id="islowercase"></a>
## isLowerCase

```TypeScript
isLowerCase(ch: string): boolean
```

判断输入的字符是否是小写字母。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isLowerCase](arkts-localization-i18n-unicode-c.md#islowercase-1)

<!--Device-Character-isLowerCase(ch: string): boolean--><!--Device-Character-isLowerCase(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是小写字母，false表示输入的字符不是小写字母。 |

<a id="isrtl"></a>
## isRTL

```TypeScript
isRTL(ch: string): boolean
```

判断输入的字符是否是从右到左语言的字符。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isRTL](arkts-localization-i18n-unicode-c.md#isrtl-1)

<!--Device-Character-isRTL(ch: string): boolean--><!--Device-Character-isRTL(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是从右到左语言的字符，false表示输入的字符不是从右到左语言的字符。 |

<a id="isspacechar"></a>
## isSpaceChar

```TypeScript
isSpaceChar(ch: string): boolean
```

判断输入的字符是否是空格符。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSpaceChar](arkts-localization-i18n-unicode-c.md#isspacechar-1)

<!--Device-Character-isSpaceChar(ch: string): boolean--><!--Device-Character-isSpaceChar(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是空格符，false表示输入的字符不是空格符。 |

<a id="isuppercase"></a>
## isUpperCase

```TypeScript
isUpperCase(ch: string): boolean
```

判断输入的字符是否是大写字母。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isUpperCase](arkts-localization-i18n-unicode-c.md#isuppercase-1)

<!--Device-Character-isUpperCase(ch: string): boolean--><!--Device-Character-isUpperCase(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是大写字母，false表示输入的字符不是大写字母。 |

<a id="iswhitespace"></a>
## isWhitespace

```TypeScript
isWhitespace(ch: string): boolean
```

判断输入的字符是否是空白符。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isWhitespace](arkts-localization-i18n-unicode-c.md#iswhitespace-1)

<!--Device-Character-isWhitespace(ch: string): boolean--><!--Device-Character-isWhitespace(ch: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ch | string | 是 | 输入的字符。如果输入的是字符串，则只判断首字符的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示输入的字符是空白符，false表示输入的字符不是空白符。 |

