# Long
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供`Long`装箱类型及`long`相关转换、比较、格式化和算术接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。

## Long

export final class Long extends Integral implements Comparable\<Long>

`long`值的装箱类型。`Long`实例保存一个`long`值，并提供基础类型转换、字符串转换、比较和算术方法。继承自[Integral](arkts-sta-numeric.md#integral)。

**系统能力：** SystemCapability.Utils.Lang

### 静态常量

以下表格列出该类型提供的公开静态常量。

**系统能力：** SystemCapability.Utils.Lang

| 常量 | 类型 | 说明 |
| :--- | :--- | :--- |
| MIN_VALUE | long | 最小`long`值，值为`-9223372036854775808`。 |
| MAX_VALUE | long | 最大`long`值，值为`9223372036854775807`。 |
| BIT_SIZE | byte | `long`位数，值为`64`。 |
| BYTE_SIZE | byte | `long`字节数，值为`8`。 |

**示例：**

```ts
console.info(Long.MIN_VALUE); // -9223372036854775808
console.info(Long.MAX_VALUE); // 9223372036854775807
console.info(Long.BIT_SIZE);  // 64
console.info(Long.BYTE_SIZE); // 8
```

### constructor

public constructor()

创建值为`0`的`Long`实例。

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```ts
const value = new Long();
console.info(value); // 0
```

### constructor

public constructor(value: long)

按指定`long`值创建`Long`实例。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 初始`long`值。 |

**示例：**

```ts
const value = new Long(42);
console.info(value); // 42
```

### toByte

public override toByte(): byte

将当前`Long`实例保存的值转换为`byte`并返回。当值超出`byte`范围时，截断低8位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | 转换后的`byte`值。 |

**示例：**

```ts
console.info(new Long(12).toByte()); // 12
// 超出byte范围，截断低8位
console.info(new Long(300).toByte()); // 44
```

### toShort

public override toShort(): short

将当前`Long`实例保存的值转换为`short`并返回。当值超出`short`范围时，截断低16位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | 转换后的`short`值。 |

**示例：**

```ts
console.info(new Long(123).toShort()); // 123
// 超出short范围，截断低16位
console.info(new Long(40000).toShort()); // -25536
```

### toInt

public override toInt(): int

将当前`Long`实例保存的值转换为`int`并返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 转换后的`int`值。 |

**示例：**

```ts
console.info(new Long(1234).toInt()); // 1234
// 超出int范围，截断低32位
console.info(new Long(2147483648).toInt()); // -2147483648
```

### toLong

public override toLong(): long

返回当前`Long`实例保存的`long`值。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 当前实例保存的`long`值。 |

**示例：**

```ts
const value = new Long(1234);
const result: long = value.toLong();
console.info(result); // 1234
```

### toFloat

public override toFloat(): float

将当前`Long`实例保存的值转换为`float`并返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 转换后的`float`值。 |

**示例：**

```ts
console.info(new Long(7).toFloat()); // 7
// 超出Float.MAX_SAFE_INTEGER（即2²⁴-1），可能会丢失精度
console.info(new Long(16777217).toFloat()); // 16777216
```

### toDouble

public override toDouble(): double

将当前`Long`实例保存的值转换为`double`并返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 转换后的`double`值。 |

**示例：**

```ts
console.info(new Long(7).toDouble()); // 7
// 超出Double.MAX_SAFE_INTEGER（即2⁵³-1），可能会丢失精度
console.info(new Long(9007199254740993).toDouble()); // 9007199254740992
```

### toChar

public toChar(): char

将当前`Long`实例保存的数值转换为对应编码点的`char`。传入无效编码点（负数或超出Unicode有效范围0~0x10FFFF）时行为未定义。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| char | 转换后的`char`值。 |

**示例：**

```ts
const value = new Long(65);
const result: char = value.toChar();
console.info(result); // "A"
```

### toByte

public static native toByte(value: long): byte

将传入的`long`值转换为`byte`。当值超出`byte`范围时，截断低8位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 待转换的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | 转换后的`byte`值。 |

**示例：**

```ts
console.info(Long.toByte(8)); // 8
// 超出byte范围，截断低8位
console.info(Long.toByte(300)); // 44
```

### toShort

public static native toShort(value: long): short

将传入的`long`值转换为`short`。当值超出`short`范围时，截断低16位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 待转换的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | 转换后的`short`值。 |

**示例：**

```ts
console.info(Long.toShort(1024)); // 1024
// 超出short范围，截断低16位
console.info(Long.toShort(40000)); // -25536
```

### toInt

public static native toInt(value: long): int

将传入的`long`值转换为`int`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 待转换的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 转换后的`int`值。 |

**示例：**

```ts
console.info(Long.toInt(1024)); // 1024
// 超出int范围，截断低32位
console.info(Long.toInt(2147483648)); // -2147483648
```

### toFloat

public static native toFloat(value: long): float

将传入的`long`值转换为`float`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 待转换的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 转换后的`float`值。 |

**示例：**

```ts
console.info(Long.toFloat(9)); // 9
// 超出Float.MAX_SAFE_INTEGER（即2²⁴-1），可能会丢失精度
console.info(Long.toFloat(16777217)); // 16777216
```

### toDouble

public static native toDouble(value: long): double

将传入的`long`值转换为`double`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 待转换的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 转换后的`double`值。 |

**示例：**

```ts
console.info(Long.toDouble(9)); // 9
// 超出Double.MAX_SAFE_INTEGER（即2⁵³-1），可能会丢失精度
console.info(Long.toDouble(9007199254740993)); // 9007199254740992
```

### toChar

public static native toChar(value: long): char

将传入的`long`值转换为对应编码点的`char`。传入无效编码点（负数或超出Unicode有效范围0~0x10FFFF）时行为未定义。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 待转换的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| char | 转换后的`char`值。 |

**示例：**

```ts
const result: char = Long.toChar(65);
console.info(result); // "A"
```

### toLong

public static toLong(value: long): long

返回传入的`long`值。该方法用于和其他数值装箱类型的静态转换接口保持一致。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | long | 是 | 待返回的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 原始`long`值。 |

**示例：**

```ts
const result: long = Long.toLong(256);
console.info(result); // 256
```

### compareTo

public override compareTo(other: Long): int

比较当前`Long`实例与`other`的大小。当前值更小时返回`-1`，相等时返回`0`，更大时返回`1`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 参与比较的另一个`Long`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 比较结果。 |

**示例：**

```ts
const a = new Long(3);
// 3小于5
console.info(a.compareTo(new Long(5))); // -1
// 相等
console.info(a.compareTo(new Long(3))); // 0
// 3大于1
console.info(a.compareTo(new Long(1))); // 1
```

### toString

public static toString(v: long): string

将传入的`long`值转换为十进制字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | long | 是 | 待转换的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 十进制字符串。 |

**示例：**

```ts
const text: string = Long.toString(123);
console.info(text); // "123"
```

### toString

public override toString(): String

将当前`Long`实例保存的值转换为十进制字符串。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 十进制字符串。 |

**示例：**

```ts
const value = new Long(123);
console.info(value.toString()); // "123"
```

### toString

public toString(radix: int): string

按指定进制将当前`Long`实例保存的值转换为字符串。`radix`的有效范围为`2`到`36`，超出范围会抛出`RangeError`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| radix | int | 是 | 字符串表示使用的进制。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 指定进制下的字符串。 |

**示例：**

```ts
const value = new Long(255);
console.info(value.toString(16)); // "ff"
```

### equals

public equals(other: Any): boolean

判断`other`是否也是`Long`实例且保存相同的`long`值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Any | 是 | 待比较的对象。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否相等。`true`表示相等，`false`表示不相等。 |

**示例：**

```ts
const left = new Long(10);
const right = new Long(10);
console.info(left.equals(right)); // true
```

### toLocaleString

public toLocaleString(locales?: Intl.LocalesArgument, options?: Intl.NumberFormatOptions): String

按指定区域设置和数字格式选项格式化当前`Long`值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | Intl.LocalesArgument | 否 | BCP 47语言标签或标签数组。 |
| options | Intl.NumberFormatOptions | 否 | 数字格式化选项。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 格式化后的字符串。 |

**示例：**

```ts
const value = new Long(1234);
console.info(new Long(1234).toLocaleString("en-US")); // "1,234"
```

### toLocaleString

public override toLocaleString(locales?: Intl.LocalesArgument, options?: object): String

按指定区域设置格式化当前`Long`值。若`options`不是`Intl.NumberFormatOptions`实例，则忽略该参数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | Intl.LocalesArgument | 否 | BCP 47语言标签或标签数组。 |
| options | object | 否 | 可选格式化对象。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 格式化后的字符串。 |

**示例：**

```ts
const value = new Long(1234);
const options: Intl.NumberFormatOptions = { style: 'currency', currency: 'CNY' };
console.info(value.toLocaleString("en-US", options)); // "CN¥1,234.00"
```

### add

public add(other: Long): Long

返回当前值与`other`相加后的新`Long`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 加法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Long | 相加后的新实例。 |

**示例：**

```ts
console.info(new Long(6).add(new Long(4))); // 10
// 溢出：Long.MAX_VALUE + 1超出long范围，结果回绕为负数
console.info(new Long(Long.MAX_VALUE).add(new Long(1))); // -9223372036854775808
```

### sub

public sub(other: Long): Long

返回当前值减去`other`后的新`Long`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 减法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Long | 相减后的新实例。 |

**示例：**

```ts
console.info(new Long(6).sub(new Long(4))); // 2
// 溢出：Long.MIN_VALUE - 1超出long范围，结果回绕为正数
console.info(new Long(Long.MIN_VALUE).sub(new Long(1))); // 9223372036854775807
```

### mul

public mul(other: Long): Long

返回当前值与`other`相乘后的新`Long`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 乘法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Long | 相乘后的新实例。 |

**示例：**

```ts
console.info(new Long(6).mul(new Long(4))); // 24
// 溢出：Long.MAX_VALUE * 2超出long范围，结果回绕
console.info(new Long(Long.MAX_VALUE).mul(new Long(2))); // -2
```

### div

public div(other: Long): Long

返回当前值除以`other`后的新`Long`实例。`other`为`0`时抛出异常。当结果超出`long`范围时发生溢出，例如`Long.MIN_VALUE`除以`-1`时结果仍为`Long.MIN_VALUE`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 除法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Long | 相除后的新实例。 |

**示例：**

```ts
console.info(new Long(8).div(new Long(4))); // 2
// 溢出：Long.MIN_VALUE / -1应为正值，超出long范围，结果仍为Long.MIN_VALUE
console.info(new Long(Long.MIN_VALUE).div(new Long(-1))); // -9223372036854775808
// 除零抛出异常
try {
  new Long(8).div(new Long(0));
} catch (e) {
  console.info(e instanceof ArithmeticError); // true
}
```

### isLessThan

public isLessThan(other: Long): boolean

判断当前值是否小于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 参与比较的另一个`Long`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否小于`other`。`true`表示当前值小于`other`，`false`表示当前值不小于`other`。 |

**示例：**

```ts
console.info(new Long(3).isLessThan(new Long(4))); // true
console.info(new Long(4).isLessThan(new Long(4))); // false
```

### isLessEqualThan

public isLessEqualThan(other: Long): boolean

判断当前值是否小于或等于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 参与比较的另一个`Long`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否小于或等于`other`。`true`表示当前值小于或等于`other`，`false`表示当前值大于`other`。 |

**示例：**

```ts
// 3小于4
console.info(new Long(3).isLessEqualThan(new Long(4))); // true
// 4等于4
console.info(new Long(4).isLessEqualThan(new Long(4))); // true
```

### isGreaterThan

public isGreaterThan(other: Long): boolean

判断当前值是否大于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 参与比较的另一个`Long`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否大于`other`。`true`表示当前值大于`other`，`false`表示当前值不大于`other`。 |

**示例：**

```ts
console.info(new Long(5).isGreaterThan(new Long(4))); // true
console.info(new Long(4).isGreaterThan(new Long(4))); // false
```

### isGreaterEqualThan

public isGreaterEqualThan(other: Long): boolean

判断当前值是否大于或等于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Long | 是 | 参与比较的另一个`Long`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否大于或等于`other`。`true`表示当前值大于或等于`other`，`false`表示当前值小于`other`。 |

**示例：**

```ts
// 5大于4
console.info(new Long(5).isGreaterEqualThan(new Long(4))); // true
// 5等于5
console.info(new Long(5).isGreaterEqualThan(new Long(5))); // true
```

### parseInt

public static native parseInt(s: String, r: int): long

按指定进制解析字符串并返回`long`值。`r`应在`2`到`36`之间；传入`0`时按十进制处理。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| s | String | 是 | 待解析的字符串。 |
| r | int | 是 | 解析使用的进制。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 解析得到的`long`值。 |

**示例：**

```ts
const result: long = Long.parseInt("ff", 16);
console.info(result); // 255
```
