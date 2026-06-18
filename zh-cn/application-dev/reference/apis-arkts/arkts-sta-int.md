# Int
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供`Int`装箱类型及`int`相关转换、比较、格式化和算术接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。

## Int

export final class Int extends Integral implements Comparable\<Int>

`int`值的装箱类型。`Int`实例保存一个`int`值，并提供基础类型转换、字符串转换、比较和算术方法。继承自[Integral](arkts-sta-numeric.md#integral)。

**系统能力：** SystemCapability.Utils.Lang

### 静态常量

以下表格列出该类型提供的公开静态常量。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 常量 | 类型 | 说明 |
| :--- | :--- | :--- |
| MIN_VALUE | int | 最小`int`值，值为`-2147483648`。 |
| MAX_VALUE | int | 最大`int`值，值为`2147483647`。 |
| BIT_SIZE | byte | `int`位数，值为`32`。 |
| BYTE_SIZE | byte | `int`字节数，值为`4`。 |

**示例：**

```ts
console.info(Int.MIN_VALUE); // -2147483648
console.info(Int.MAX_VALUE); // 2147483647
console.info(Int.BIT_SIZE);  // 32
console.info(Int.BYTE_SIZE); // 4
```

### constructor

public constructor()

创建值为`0`的`Int`实例。

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```ts
const zero = new Int();
console.info(zero); // 0
```

### constructor

public constructor(value: int)

按指定`int`值创建`Int`实例。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 初始`int`值。 |

**示例：**

```ts
const n = new Int(123);
console.info(n); // 123
```

### toByte

public override toByte(): byte

将当前`Int`实例保存的值转换为`byte`并返回。当值超出`byte`范围时，截断低8位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | 转换后的`byte`值。 |

**示例：**

```ts
console.info(new Int(100).toByte()); // 100
// 超出byte范围，截断低8位
console.info(new Int(300).toByte()); // 44
```

### toShort

public override toShort(): short

将当前`Int`实例保存的值转换为`short`并返回。当值超出`short`范围时，截断低16位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | 转换后的`short`值。 |

**示例：**

```ts
console.info(new Int(16).toShort()); // 16
// 超出short范围，截断低16位
console.info(new Int(40000).toShort()); // -25536
```

### toInt

public override toInt(): int

返回当前`Int`实例保存的`int`值。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 当前实例保存的`int`值。 |

**示例：**

```ts
const a = new Int(65);
console.info(a.toInt()); // 65
```

### toLong

public override toLong(): long

将当前`Int`实例保存的值转换为`long`并返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 转换后的`long`值。 |

**示例：**

```ts
const a = new Int(65);
console.info(a.toLong()); // 65
```

### toFloat

public override toFloat(): float

将当前`Int`实例保存的值转换为`float`并返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 转换后的`float`值。 |

**示例：**

```ts
console.info(new Int(65).toFloat()); // 65
console.info(new Int(-65).toFloat()); // -65
// 超出Float.MAX_SAFE_INTEGER（即2²⁴-1），可能会丢失精度
console.info(new Int(16777217).toFloat()); // 16777216
```

### toDouble

public override toDouble(): double

将当前`Int`实例保存的值转换为`double`并返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 转换后的`double`值。 |

**示例：**

```ts
const a = new Int(65);
console.info(a.toDouble()); // 65
const b = new Int(-65);
console.info(b.toDouble()); // -65
```

### toChar

public toChar(): char

将当前`Int`实例保存的数值转换为对应编码点的`char`。传入无效编码点（负数或超出Unicode有效范围）时行为未定义。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| char | 转换后的`char`值。 |

**示例：**

```ts
const a = new Int(65);
console.info(a.toChar()); // "A"
// 中文字符
const b = new Int(0x4E2D);
console.info(b.toChar()); // "中"
// 无效编码点（负数），行为未定义，应避免使用
const c = new Int(-1);
console.info(c.toChar()); // 结果未定义
// 无效编码点（超出Unicode上限0x10FFFF），行为未定义，应避免使用
const d = new Int(0x110000);
console.info(d.toChar()); // 结果未定义
```

### toByte

public static native toByte(value: int): byte

将传入的`int`值转换为`byte`。当值超出`byte`范围时，截断低8位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 待转换的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | 转换后的`byte`值。 |

**示例：**

```ts
console.info(Int.toByte(65)); // 65
// 超出byte范围，截断低8位
console.info(Int.toByte(300)); // 44
```

### toShort

public static native toShort(value: int): short

将传入的`int`值转换为`short`。当值超出`short`范围时，截断低16位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 待转换的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | 转换后的`short`值。 |

**示例：**

```ts
console.info(Int.toShort(64)); // 64
// 超出short范围，截断低16位
console.info(Int.toShort(40000)); // -25536
```

### toLong

public static native toLong(value: int): long

将传入的`int`值转换为`long`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 待转换的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 转换后的`long`值。 |

**示例：**

```ts
console.info(Int.toLong(65)); // 65
```

### toFloat

public static native toFloat(value: int): float

将传入的`int`值转换为`float`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 待转换的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 转换后的`float`值。 |

**示例：**

```ts
console.info(Int.toFloat(65)); // 65
console.info(Int.toFloat(-65)); // -65
// 超出Float.MAX_SAFE_INTEGER（即2²⁴-1），可能会丢失精度
console.info(Int.toFloat(16777217)); // 16777216
```

### toDouble

public static native toDouble(value: int): double

将传入的`int`值转换为`double`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 待转换的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 转换后的`double`值。 |

**示例：**

```ts
console.info(Int.toDouble(65)); // 65
console.info(Int.toDouble(-65)); // -65
```

### toChar

public static native toChar(value: int): char

将传入的`int`值转换为对应编码点的`char`。传入无效编码点（负数或超出Unicode有效范围）时行为未定义。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 待转换的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| char | 转换后的`char`值。 |

**示例：**

```ts
console.info(Int.toChar(65)); // "A"
// 中文字符
console.info(Int.toChar(0x4E2D)); // "中"
// 无效编码点（负数），行为未定义，应避免使用
console.info(Int.toChar(-1)); // 结果未定义
// 无效编码点（超出Unicode上限0x10FFFF），行为未定义，应避免使用
console.info(Int.toChar(0x110000)); // 结果未定义
```

### toInt

public static toInt(value: int): int

返回传入的`int`值。该方法用于和其他数值装箱类型的静态转换接口保持一致。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 待返回的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 原始`int`值。 |

**示例：**

```ts
// 用于泛型场景下统一调用静态转换接口
const result: int = Int.toInt(65);
console.info(result); // 65
```

### compareTo

public override compareTo(other: Int): int

比较当前`Int`实例与`other`的大小。当前值更小时返回`-1`，相等时返回`0`，更大时返回`1`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 参与比较的另一个`Int`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 比较结果。 |

**示例：**

```ts
const a = new Int(65);
// 65大于64
console.info(a.compareTo(new Int(64))); // 1
// 相等
console.info(a.compareTo(new Int(65))); // 0
// 65小于66
console.info(a.compareTo(new Int(66))); // -1
```

### toString

public static toString(v: int): string

将传入的`int`值转换为十进制字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | int | 是 | 待转换的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 十进制字符串。 |

**示例：**

```ts
console.info(Int.toString(65)); // "65"
```

### toString

public override toString(): String

将当前`Int`实例保存的值转换为十进制字符串。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 十进制字符串。 |

**示例：**

```ts
const a = new Int(65);
console.info(a.toString()); // "65"
```

### toString

public toString(radix: int): string

按指定进制将当前`Int`实例保存的值转换为字符串。`radix`的有效范围为`2`到`36`。

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
const value = new Int(255);
console.info(value.toString(2));  // "11111111"
console.info(value.toString(8));  // "377"
console.info(value.toString(16)); // "ff"
```

### equals

equals(other: Any): boolean

判断`other`是否与当前`Int`实例保存相同的`int`值。`other`为`Int`实例或`int`原始值且值相同时返回`true`，否则返回`false`。

**系统能力：** SystemCapability.Utils.Lang

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
const left = new Int(10);
const right = new Int(10);
console.info(left.equals(right)); // true
// 值不同返回false
console.info(left.equals(new Int(20))); // false
// 非数值类型返回false
console.info(left.equals("10" as Any)); // false
```

### toLocaleString

public toLocaleString(locales?: Intl.LocalesArgument, options?: Intl.NumberFormatOptions): String

按指定区域设置和数字格式选项格式化当前`Int`值。

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
const value = new Int(1234);
console.info(value.toLocaleString("en-US")); // "1,234"
```

### toLocaleString

public override toLocaleString(locales?: Intl.LocalesArgument, options?: object): String

按指定区域设置格式化当前`Int`值。若`options`不是`Intl.NumberFormatOptions`实例，则忽略该参数。

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
const value = new Int(1234);
const options: Intl.NumberFormatOptions = { style: 'currency', currency: 'CNY' };
console.info(value.toLocaleString("en-US", options)); // "CN¥1,234.00"
```

### add

public add(other: Int): Int

返回当前值与`other`相加后的新`Int`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 加法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Int | 相加后的新实例。 |

**示例：**

```ts
console.info(new Int(6).add(new Int(4))); // 10
// 溢出：Int.MAX_VALUE + 1超出int范围，结果回绕为负数
console.info(new Int(Int.MAX_VALUE).add(new Int(1))); // -2147483648
```

### sub

public sub(other: Int): Int

返回当前值减去`other`后的新`Int`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 减法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Int | 相减后的新实例。 |

**示例：**

```ts
console.info(new Int(6).sub(new Int(4))); // 2
// 溢出：Int.MIN_VALUE - 1超出int范围，结果回绕为正数
console.info(new Int(Int.MIN_VALUE).sub(new Int(1))); // 2147483647
```

### mul

public mul(other: Int): Int

返回当前值与`other`相乘后的新`Int`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 乘法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Int | 相乘后的新实例。 |

**示例：**

```ts
console.info(new Int(6).mul(new Int(4))); // 24
// 溢出：Int.MAX_VALUE * 2超出int范围，结果回绕
console.info(new Int(Int.MAX_VALUE).mul(new Int(2))); // -2
```

### div

public div(other: Int): Int

返回当前值除以`other`后的新`Int`实例。`other`为`0`时抛出异常。当结果超出`int`范围时发生溢出，例如`Int.MIN_VALUE`除以`-1`时结果仍为`Int.MIN_VALUE`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 除法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Int | 相除后的新实例。 |

**示例：**

```ts
console.info(new Int(8).div(new Int(4))); // 2
// 溢出：Int.MIN_VALUE / -1应为2147483648，超出int范围，结果仍为Int.MIN_VALUE
console.info(new Int(Int.MIN_VALUE).div(new Int(-1))); // -2147483648
// 除零抛出异常
try {
  new Int(8).div(new Int(0));
} catch (e) {
  console.info(e instanceof ArithmeticError); // true
}
```

### isLessThan

public isLessThan(other: Int): boolean

判断当前值是否小于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 参与比较的另一个`Int`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否小于`other`。`true`表示当前值小于`other`，`false`表示当前值不小于`other`。 |

**示例：**

```ts
console.info(new Int(3).isLessThan(new Int(4))); // true
console.info(new Int(4).isLessThan(new Int(4))); // false
```

### isLessEqualThan

public isLessEqualThan(other: Int): boolean

判断当前值是否小于或等于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 参与比较的另一个`Int`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否小于或等于`other`。`true`表示当前值小于或等于`other`，`false`表示当前值大于`other`。 |

**示例：**

```ts
// 3小于4
console.info(new Int(3).isLessEqualThan(new Int(4))); // true
// 4等于4
console.info(new Int(4).isLessEqualThan(new Int(4))); // true
```

### isGreaterThan

public isGreaterThan(other: Int): boolean

判断当前值是否大于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 参与比较的另一个`Int`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否大于`other`。`true`表示当前值大于`other`，`false`表示当前值不大于`other`。 |

**示例：**

```ts
console.info(new Int(5).isGreaterThan(new Int(4))); // true
console.info(new Int(4).isGreaterThan(new Int(4))); // false
```

### isGreaterEqualThan

public isGreaterEqualThan(other: Int): boolean

判断当前值是否大于或等于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Int | 是 | 参与比较的另一个`Int`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否大于或等于`other`。`true`表示当前值大于或等于`other`，`false`表示当前值小于`other`。 |

**示例：**

```ts
// 5大于4
console.info(new Int(5).isGreaterEqualThan(new Int(4))); // true
// 5等于5
console.info(new Int(5).isGreaterEqualThan(new Int(5))); // true
```

### parseInt

public static native parseInt(s: String, r: int): int

按指定进制解析字符串并返回`int`值。`r`应在`2`到`36`之间；传入`0`时按十进制处理。解析结果超出`int`范围时抛出`FormatError`。

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
| int | 解析得到的`int`值。 |

**示例：**

```ts
// 十六进制解析
console.info(Int.parseInt("2a", 16)); // 42
// 二进制解析
console.info(Int.parseInt("1010", 2)); // 10
// 八进制解析
console.info(Int.parseInt("77", 8)); // 63
// 传入0时始终按十进制处理（标准JS中传入0时，若字符串以"0x"开头会自动按十六进制解析）
console.info(Int.parseInt("0x2a", 0)); // 0（按十进制解析，遇'x'停止，仅解析出前缀"0"）
// 结果超出int范围时抛出FormatError
try {
  Int.parseInt("2147483648", 10);
} catch (e) {
  console.info(e instanceof FormatError); // true
}
```
