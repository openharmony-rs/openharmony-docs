# Char

本模块提供字符基础操作。开发者可以使用本模块的功能，对字符进行处理、转换及相关操作。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## constructor

constructor()

无参构造函数，创建一个值为空字符（\u0000）的Char对象。

**示例：**

```typescript
const c = new Char();
console.info(c); // 输出：" "
```

## constructor

constructor(value: char)

带参构造函数，使用指定的初始值创建Char对象。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | :----------- |
| value  | char | 是   | 原始字符值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c); // 输出："A"
```

## valueOf

static valueOf(value: char): Char

将原始char值包装为Char对象。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待包装的原始字符值。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| Char | 包装后的Char实例。 |

**示例：**

```typescript
const c = Char.valueOf(c'A');
console.info(c); // 输出："A"
```

## equals

equals(other: Any): boolean

判断当前Char对象与other是否“值相等”，仅当other为Char实例且值相同时返回true。

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| other  | Any  | 是   | 待比较的对象。 |

**返回值：**

| 类型    | 说明                                  |
| ------- | ------------------------------------- |
| boolean | 是否相等。相等为true，不相等为false。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.equals(66)); // 输出：false
```

## toString

toString(): String

将当前Char值转换为十进制字符串。

**返回值：**

| 类型   | 说明         |
| ------ | ------------ |
| String | 字符串表示。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toString()); // 输出：A
```

## compare

compare(lhs: Char, rhs: Char): boolean

比较当前lhs与rhs的原始值大小是否相等，返回比较结果。

**参数：**

| 参数名 | 类型 | 必填 | 说明                |
| ------ | ---- | ---- | ------------------- |
| lhs    | Char | 是   | 待比较的原始值1。   |
| rhs    | Char | 是   | 是待比较的原始值2。 |

**返回值：**

| 类型    | 说明                                    |
| ------- | --------------------------------------- |
| boolean | 当lhs==rhs时，结果为true，否则为false。 |

**示例：**

```typescript
const lhs = new Char(c'A');
const rhs = new Char(c'A');
console.info(Char.compare(lhs, rhs)); // 输出：ture
```

## compareTo

compareTo(other: Char): int

比较当前Char与other的数值大小，返回比较结果。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| other  | Char | 是   | 待比较的原始字符值。 |

**返回值：**

| 类型 | 说明                                          |
| ---- | --------------------------------------------- |
| int  | 结果>0说明当前值更大，结果<0说明other值更大，结果=0说明两者相等。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.compareTo(c'A')); // 输出：0
```

## 属性

| 名称          | 类型 | 只读  |  可选  | 说明               |
| ------------- | :--- | ---- | ----  | :----------------- |
| CHAR_BIT_SIZE | int  | 是   |  否   | 表示字符的位大小为16。 |
| MAX_CODE_POINT | number  | 是   |  否   | 表示Unicode标准中最大的有效代码点值为0x10FFFF。 |
| HIGH_SURROGATE_MIN | char  | 是   |  否   | 表示UTF-16编码中高代理项的最小字符值为c'\uD800'。 |
| HIGH_SURROGATE_MAX | char  | 是   |  否   | 表示UTF-16编码中高代理项的最大字符值为c'\uDBFF'。 |
| LOW_SURROGATE_MIN | char  | 是   |  否   | 表示UTF-16编码中低代理项的最小字符值为c'\uDC00'。 |
| LOW_SURROGATE_MAX | char  | 是   |  否   | 表示UTF-16编码中低代理项的最大字符值为c'\uDFFF'。 |
| MIN_VALUE | char  | 是   |  否   | 表示字符类型的最小值为c'\u0000'。 |
| MAX_VALUE | char  | 是   |  否   | 表示字符类型的最大值为c'\uFFFF'。 |

## toByte

toByte(): byte

返回当前Char实例的数值，转换为byte类型。

**返回值：**

| 类型 | 说明             |
| ---- | ---------------- |
| byte | 转换后的字节值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toByte()); // 输出：65
```

## toShort

toShort(): short

将原始Char值转换为short类型。

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toShort()); // 输出：65
```

## toInt

toInt(): int

将原始Char值转换为int类型。

**返回值：**

| 类型 | 说明                |
| ---- | ------------------- |
| int  | 转换后的int类型值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toInt()); // 输出：65
```

## toLong

toLong(): long

将原始Char值转换为long类型。

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| long | 转换后的long类型值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toLong()); // 输出：65
```

## toFloat

toFloat(): float

将原始Char值转换为float类型（32位浮点数）。

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toFloat()); // 输出：65
```

## toDouble

toDouble(): double

将原始Char值转换为double类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toDouble()); // 输出：65
```

## toChar

toChar(): char

将原始Char值转换为char类型。

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| char | 转换后的char类型值。 |

**示例：**

```typescript
const c = new Char(c'A');
console.info(c.toChar()); // 输出："A"
```

## toByte

static toByte(value: char): byte

将原始Char值转换为byte类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待转换的原始字符值。 |

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| byte | 转换后的byte类型值。 |

**示例：**

```typescript
console.info(Char.toByte(c'A')); // 输出：65
```

## toShort

static toShort(value: char): short

将原始byte值转换为short类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待转换的原始字符值。 |

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
console.info(Char.toShort(c'A')); // 输出：65
```

## toInt

static toInt(value: char): int

将原始char值转换为int类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待转换的原始字符值。 |

**返回值：**

| 类型 | 说明                |
| ---- | ------------------- |
| int  | 转换后的int类型值。 |

**示例：**

```typescript
console.info(Char.toInt(c'A')); // 输出：65
```

## toLong

static toLong(value: char): long

将原始char值转换为long类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待转换的原始字符值。 |

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| long | 转换后的long类型值。 |

**示例：**

```typescript
console.info(Char.toLong(c'A')); // 输出：65
```

## toFloat

static toFloat(value: char): float

将原始char值转换为float类型（32位浮点数）。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待转换的原始字符值。 |

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
console.info(Char.toFloat(c'A')); // 输出：65
```

## toDouble

static toDouble(value: char): double

将原始char值转换为double类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待转换的原始字符值。 |

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
console.info(Char.toDouble(c'A')); // 输出：65
```

## toChar

static toChar(value: char): char

将原始char值转换为char类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | char | 是   | 待转换的原始字符值。 |

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| char | 转换后的char类型值。 |

**示例：**

```typescript
console.info(Char.toChar(c'A')); // 输出：A
```

## isInBasicMultilingualPlane

static isInBasicMultilingualPlane(value: char): boolean

判断字符是否属于Unicode标准中的基本多文种平面（BMP）。

**参数：**

| 参数名 | 类型 | 必填 |
| ------ | ---- | ---- |
| value  | char | 是   |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 若字符的整数值小于65536，且它的值<0xD800或者它的值>0xDFFF，则返回true，否则返回false。 |

**示例：**

```typescript
// 判断一个字符是否位于Unicode的基本多文种平面(BMP)内
console.info(Char.isInBasicMultilingualPlane(c'A')); // 输出：true
console.info(Char.isInBasicMultilingualPlane(c'\uD83D')); // 输出：false
```

## isInBasicMultilingualPlane

static isInBasicMultilingualPlane(value: UTF_16_CodePoint): boolean

判断UTF-16代码点是否属于基本多文种平面（BMP）。

**参数：**

| 参数名 | 类型             | 必填 | 说明                 |
| ------ | ---------------- | ---- | -------------------- |
| value  | UTF_16_CodePoint | 是   | 待判断的UTF-16代码点。 |

**返回值：**

| 类型    | 说明                                 |
| ------- | ------------------------------------ |
| boolean | 若属于BMP则返回true，否则返回false。 |

**示例：**

```typescript
console.info(Char.isInBasicMultilingualPlane(0x1F600 as UTF_16_CodePoint)); // 输出：false
```

## isInBasicMultilingualPlane

isInBasicMultilingualPlane(): boolean

判断字符或代码点是否属于基本多文种平面（BMP）。

**返回值：**

| 类型    | 说明                                 |
| ------- | ------------------------------------ |
| boolean | 若属于BMP则返回true，否则返回false。 |

**示例：**

```typescript
const c = new Char(c'A')
console.info(c.isInBasicMultilingualPlane());  // 输出：true
```

## isValidCodePoint

static isValidCodePoint(codePoint: UTF_16_CodePoint): boolean

判断UTF-16代码点是否合法（范围0~0x10FFFF，且非代理码点）。

**参数：**

| 参数名    | 类型             | 必填 | 说明                 |
| --------- | ---------------- | ---- | -------------------- |
| codePoint | UTF_16_CodePoint | 是   | 待判断的UTF-16代码点。 |

**返回值：**

| 类型    | 说明                   |
| ------- | ---------------------- |
| boolean | 合法则true，否则false. |

**示例：**

```typescript
console.info(Char.isValidCodePoint(65 as UTF_16_CodePoint)); // 输出：true
console.info(Char.isValidCodePoint(0xD83D as UTF_16_CodePoint)); // 输出：false
```

## codeUnitsToEncode

static codeUnitsToEncode(value: UTF_16_CodePoint): int

计算编码指定UTF-16代码点所需的代码单元数（BMP代码点需1个，非BMP代码点需2个代理对）。

**参数：**

| 参数名 | 类型             | 必填 | 说明                 |
| ------ | ---------------- | ---- | -------------------- |
| value  | UTF_16_CodePoint | 是   | 待编码的UTF-16代码点。 |

**返回值：**

| 类型 | 说明                   |
| ---- | ---------------------- |
| int  | 代码单元数（1 或 2）。 |

**示例：**

```typescript
// BMP 代码点（1 个代码单元）
console.info(Char.codeUnitsToEncode(97 as UTF_16_CodePoint)); // 输出：1（a 的代码点）
// 非 BMP 代码点（2 个代码单元）
console.info(Char.codeUnitsToEncode(0x1F600 as UTF_16_CodePoint)); // 输出：2（笑脸 emoji 代码点）
```

## isHighSurrogate

static isHighSurrogate(value: char): boolean 

判断字符是否为高代理。高代理是UTF-16编码中代理对的第一个组成部分，用于表示BMP之外的Unicode字符。它的数值范围是U+D800到U+DBFF。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                          |
| ------- | ----------------------------- |
| boolean | 是对应代理则true，否则false。 |

**示例：**

```typescript
const highSurrogate = c'\uD83D';
console.info(Char.isHighSurrogate(highSurrogate)); // 输出：true
```

## isLowSurrogate

static isLowSurrogate(value: char): boolean

判断字符是否为低代理。低代理是UTF-16编码中用于表示基本多文种平面之外的Unicode字符的第二个码元。它总是与高代理成对出现。它的数值范围是U+DC00到U+DFFF。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                          |
| ------- | ----------------------------- |
| boolean | 是对应代理则true，否则false。 |

**示例：**

```typescript
const lowSurrogate = c'\uDE00';
console.info(Char.isLowSurrogate(lowSurrogate));   // 输出：true
```

## getHighSurrogate

static getHighSurrogate(value: UTF_16_CodePoint): char 

将非BMP代码点拆分为对应的高代理。

**参数：**

| 参数名 | 类型             | 必填 | 说明                |
| ------ | ---------------- | ---- | ------------------- |
| value  | UTF_16_CodePoint | 是   | 非BMP的UTF-16代码点。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| char | 对应的高代理字符。 |

**示例：**

```typescript
const emojiCodePoint = 0x1F600 as UTF_16_CodePoint; // 笑脸 emoji 代码点
const high = Char.getHighSurrogate(emojiCodePoint); // 高代理：\uD83D
console.info( high === c'\uD83D'); // 输出：true
```

## getLowSurrogate

static getLowSurrogate(value: UTF_16_CodePoint): char

将非BMP代码点拆分为对应的低代理。

**参数：**

| 参数名 | 类型             | 必填 | 说明                |
| ------ | ---------------- | ---- | ------------------- |
| value  | UTF_16_CodePoint | 是   | 非BMP的UTF-16代码点。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| char | 对应的低代理字符。 |

**示例：**

```typescript
const emojiCodePoint = 0x1F600 as UTF_16_CodePoint; // 笑脸 emoji 代码点
const low = Char.getLowSurrogate(emojiCodePoint);   // 低代理：\uDE00
console.info(low === c'\uDE00'); // 输出：true
```

## isPartOfSurrogatePair

static isPartOfSurrogatePair(value: char): boolean

判断字符是否为代理对的一部分（高代理或低代理）。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| boolean | 是代理则true，否则false。 |

**示例：**

```typescript
console.info(Char.isPartOfSurrogatePair(c'\uD83D')); // 输出：true（高代理）
console.info(Char.isPartOfSurrogatePair(c'A'));     // 输出：false（普通字符）
```

## isPartOfSurrogatePair

isPartOfSurrogatePair(): boolean

判断字符是否为代理对的一部分（高代理或低代理）。

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| boolean | 是代理则true，否则false。 |

**示例：**

```typescript
console.info(c'\uD83D'.isPartOfSurrogatePair());; // 输出：true（高代理）
console.info(c'A'.isPartOfSurrogatePair());     // 输出：false（普通字符）
```

## charsToCodePoint

static charsToCodePoint(highValue: char, lowValue: char): UTF_16_CodePoint

将高代理和低代理组合转换为完整的UTF-16代码点（需确保输入为合法代理对）。

**参数：**

| 参数名    | 类型 | 必填 | 说明           |
| --------- | ---- | ---- | -------------- |
| highValue | char | 是   | 高代理字符。   |
| lowValue  | char | 是   | 是低代理字符。 |

**返回值：**

| 类型             | 说明               |
| ---------------- | ------------------ |
| UTF_16_CodePoint | 组合后的完整代码点。 |

**示例:**

```typescript
const high = c'\uD83D';
const low = c'\uDE00';
const codePoint = Char.charsToCodePoint(high, low);
console.info(codePoint === 0x1F600); // 输出：true
```

## isBinDigit

static isBinDigit(value: char): boolean

判断传入的字符是否为二进制数字（0/1）。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为二进制数字。判断结果是否为二进制数字。true表示是十六进制数字，false表示不是二进制数字。 |

**示例：**

```typescript
console.info(Char.isBinDigit(c'1')); // 输出：true
```

## isBinDigit

isBinDigit(): boolean

判断字符是否为二进制数字（0/1）。

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为二进制数字。判断结果是否为二进制数字。true表示是十六进制数字，false表示不是二进制数字。 |

**示例:**

```typescript
const c = new Char(c'1')
console.info(c.isBinDigit()); // 输出：true
```

## isDecDigit

static isDecDigit(value: char): boolean

判断传入字符是否为十进制数字（0~9）。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为十进制数字。判断结果是否为十进制数字。true表示是十六进制数字，false表示不是十进制数字。 |

**示例：**

```typescript
console.info(Char.isDecDigit(c'1')); // 输出：true
```

## isDecDigit

isDecDigit(): boolean

判断字符是否为十进制数字（0~9）。

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为十进制数字。判断结果是否为十进制数字。true表示是十六进制数字，false表示不是十进制数字。 |

**示例:**

```typescript
const c = new Char(c'1')
console.info(c.isDecDigit()); // 输出：true
```

## isHexDigit

static isHexDigit(value: char): boolean

判断传入字符是否为十六进制数字（0~9/a~f/A~F）。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为十六进制数字。true表示是十六进制数字，false表示不是十六进制数字。 |

**示例：**

```typescript
console.info(Char.isHexDigit(c'A')); // 输出：true
```

## isHexDigit

isHexDigit(): boolean

判断字符是否为十六进制数字（0~9/a~f/A~F）。

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为十六进制数字。true表示是十六进制数字，false表示不是十六进制数字。 |

**示例：**

```typescript
const c = new Char(c'A')
console.info(c.isHexDigit()); // 输出：true
```

## isLetter

static isLetter(value: char): boolean

判断传入字符是否为字母（A~Z/a~z）。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                                                    |
| ------- | ------------------------------------------------------- |
| boolean | 判断结果是否为字母。true表示是字母，false表示不是字母。 |

**示例：**

```typescript
console.info(Char.isLetter(c'A')); // 输出：true
```

## isLetter

isLetter(): boolean

判断字符是否为字母（A~Z/a~z）。

**返回值：**

| 类型    | 说明                                                    |
| ------- | ------------------------------------------------------- |
| boolean | 判断结果是否为字母。true表示是字母，false表示不是字母。 |

**示例：**

```typescript
const c = new Char(c'A')
console.info(c.isLetter()); // 输出：true
```

## isUpperCase

static isUpperCase(value: char): boolean

判断传入字符是否为大写字母。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为大写字母。true表示是大写字母，false表示不是大写字母。 |

**示例：**

```typescript
console.info(Char.isUpperCase(c'A')); // 输出：true
```

## isUpperCase

isUpperCase(): boolean

判断字符是否为大写字母。

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为大写字母。true表示是大写字母，false表示不是大写字母。 |

**示例：**

```typescript
const c = new Char(c'A')
console.info(c.isUpperCase()); // 输出：true
```

## isLowerCase

static isLowerCase(value: char): boolean

判断传入字符是否为小写字母。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为小写字母。true表示是小写字母，false表示不是小写字母。 |

**示例：**

```typescript
console.info(Char.isLowerCase(c'a')); // 输出：true
```

## isLowerCase

isLowerCase(): boolean

判断字符是否为小写字母。

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 判断结果是否为小写字母。true表示是小写字母，false表示不是小写字母。 |

**示例：**

```typescript
const c = new Char(c'a')
console.info(c.isLowerCase()); // 输出：true
```

## toUpperCase

static toUpperCase(value: char): Char 

将传入字符转换为大写（若为小写字母则转换，否则保持原字符）。不管是否发生转换，不会修改原Char，会生成新实例。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型 | 说明           |
| ---- | -------------- |
| Char | 转换后的字符。 |

**示例：**

```typescript
console.info(Char.toUpperCase(c'a')); // 输出：A
```

## toUpperCase

toUpperCase(): Char 

将字符转换为大写（若为小写字母则转换，否则保持原字符）。

**返回值：**

| 类型 | 说明           |
| ---- | -------------- |
| Char | 转换后的字符。 |

**示例：**

```typescript
const c = new Char(c'a')
console.info(c.toUpperCase()); // 输出：A
```

## toLowerCase

static toLowerCase(value: char): Char 

将传入字符转换为小写（若为大写字母则转换，否则保持原字符）。不管是否发生转换，不会修改原Char，会生成新实例。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型 | 说明           |
| ---- | -------------- |
| Char | 转换后的字符。 |

**示例：**

```typescript
console.info(Char.toLowerCase(c'A')); // 输出：a
```

## toLowerCase

toLowerCase(): Char 

将字符转换为小写（若为大写字母则转换，否则保持原字符）。

**返回值：**

| 类型 | 说明           |
| ---- | -------------- |
| Char | 转换后的字符。 |

**示例：**

```typescript
const c = new Char(c'A')
console.info(c.toLowerCase()); // 输出："a"
```

## isWhiteSpace

static isWhiteSpace(value: char): boolean

判断传入字符是否为空白字符（空格 / 制表符 / 换行等）。

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| value  | char | 是   | 原始char值。 |

**返回值：**

| 类型    | 说明                                                      |
| ------- | --------------------------------------------------------- |
| boolean | 判断是否为空白字符。true表示空白字符，false表示非空字符。 |

**示例：**

```typescript
console.info(Char.isWhiteSpace(c' '));   //输出：true
console.info(Char.isWhiteSpace(c'\t'));  //输出：true
```

## isWhiteSpace

toLowerCase(): boolean

判断字符是否为空白字符（空格 / 制表符 / 换行等）。

**返回值：**

| 类型    | 说明                                                      |
| ------- | --------------------------------------------------------- |
| boolean | 判断是否为空白字符。true表示空白字符，false表示非空字符。 |

**示例：**

```typescript
console.info(c' '.isWhiteSpace()); // 输出：true
```