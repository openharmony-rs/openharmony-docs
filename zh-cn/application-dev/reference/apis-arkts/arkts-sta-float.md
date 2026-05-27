# Float
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供`Float`装箱类型及`float`相关转换、比较、格式化、判断、算术和位转换接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## Float

export final class Float extends Floating implements Comparable\<Float>

`float`值的装箱类型。`Float`实例保存一个`float`值，并提供浮点数相关的转换、比较和算术方法。继承自[Floating](arkts-sta-numeric.md#floating)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 静态常量

以下表格列出该类型提供的公开静态常量。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 常量 | 类型 | 说明 |
| :--- | :--- | :--- |
| MIN_VALUE | float | 最小正`float`值。 |
| MAX_VALUE | float | 最大`float`值。 |
| MAX_SAFE_INTEGER | float | `float`可安全表示的最大整数。 |
| BIT_SIZE | byte | `float`位数，值为`32`。 |
| BYTE_SIZE | byte | `float`字节数，值为`4`。 |
| NaN | float | 非数字值。 |
| POSITIVE_INFINITY | float | 正无穷。 |
| NEGATIVE_INFINITY | float | 负无穷。 |
| PRECISION | byte | 有效精度位数。 |
| DELTA | float | 两个`float`值进行近似比较时使用的最小差值。 |
| EPSILON | float | 与`DELTA`相同。 |

**示例：**

```ts
console.info(Float.MIN_VALUE);        // 1e-45
console.info(Float.MAX_VALUE);        // 3.4028235e+38
console.info(Float.MAX_SAFE_INTEGER); // 16777215
console.info(Float.BIT_SIZE);         // 32
console.info(Float.BYTE_SIZE);        // 4
console.info(Float.isNaN(Float.NaN)); // true
console.info(Float.POSITIVE_INFINITY); // Infinity
console.info(Float.NEGATIVE_INFINITY); // -Infinity
console.info(Float.PRECISION);         // 24
console.info(Float.DELTA);             // 1.1920929e-7
console.info(Float.EPSILON);           // 1.1920929e-7
```

### constructor

public constructor()

创建值为`0.0f`的`Float`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
const value = new Float();
console.info(value); // 0
```

### constructor

public constructor(value: float)

按指定`float`值创建`Float`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | float | 是 | 初始`float`值。 |

**示例：**

```ts
const value = new Float(1.5f);
console.info(value); // 1.5
```

### constructor

public constructor(value: double)

按指定`double`值创建`Float`实例，构造时会转换为`float`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | double | 是 | 初始`double`值，构造时会转换为`float`。 |

**示例：**

```ts
const value = new Float(1.5);
console.info(value); // 1.5
```

### toByte

public override toByte(): byte

将当前`Float`实例保存的值转换为`byte`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | 转换后的`byte`值。 |

**示例：**

```ts
console.info(new Float(44.5f).toByte()); // 44
// 先转int得300，再截断低8位
console.info(new Float(300.5f).toByte()); // 44
```

### toShort

public override toShort(): short

将当前`Float`实例保存的值转换为`short`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | 转换后的`short`值。 |

**示例：**

```ts
console.info(new Float(600.5f).toShort()); // 600
// 先转int得37700，再截断低16位
console.info(new Float(37700.5f).toShort()); // -27836
```

### toInt

public override toInt(): int

将当前`Float`实例保存的值转换为`int`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 转换后的`int`值。 |

**示例：**

```ts
console.info(new Float(12.9f).toInt()); // 12
// 超出int范围，截断为Int.MAX_VALUE
console.info(new Float(2147483648.0f).toInt()); // 2147483647
```

### toLong

public override toLong(): long

将当前`Float`实例保存的值转换为`long`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 转换后的`long`值。 |

**示例：**

```ts
console.info(new Float(12.9f).toLong()); // 12
// 超出long范围，截断为Long.MAX_VALUE
console.info(new Float(9223372036854775808.0f).toLong()); // 9223372036854775807
```

### toFloat

public override toFloat(): float

返回当前`Float`实例保存的`float`值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 当前实例保存的`float`值。 |

**示例：**

```ts
const value = new Float(1.5f);
console.info(value.toFloat()); // 1.5
```

### toDouble

public override toDouble(): double

将当前`Float`实例保存的值转换为`double`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 转换后的`double`值。 |

**示例：**

```ts
const value = new Float(1.5f);
console.info(value.toDouble()); // 1.5
```

### toByte

public static native toByte(value: float): byte

将传入的`float`值转换为`byte`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | float | 是 | 待转换的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | 转换后的`byte`值。 |

**示例：**

```ts
console.info(Float.toByte(44.5f)); // 44
// 先转int得600，再截断低8位
console.info(Float.toByte(600.123f)); // 88
```

### toShort

public static native toShort(value: float): short

将传入的`float`值转换为`short`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | float | 是 | 待转换的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | 转换后的`short`值。 |

**示例：**

```ts
console.info(Float.toShort(600.123f)); // 600
// 先转int得40000，再截断低16位
console.info(Float.toShort(40000.123f)); // -25536
```

### toInt

public static native toInt(value: float): int

将传入的`float`值转换为`int`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | float | 是 | 待转换的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 转换后的`int`值。 |

**示例：**

```ts
console.info(Float.toInt(12.5f)); // 12
// 超出int范围，截断为Int.MAX_VALUE
console.info(Float.toInt(2147483648.0f)); // 2147483647
```

### toLong

public static native toLong(value: float): long

将传入的`float`值转换为`long`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | float | 是 | 待转换的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 转换后的`long`值。 |

**示例：**

```ts
console.info(Float.toLong(12.5f)); // 12
// 超出long范围，截断为Long.MAX_VALUE
console.info(Float.toLong(9223372036854775808.0f)); // 9223372036854775807
```

### toFloat

public static toFloat(value: float): float

返回传入的`float`值。该方法用于和其他数值装箱类型的静态转换接口保持一致。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | float | 是 | 待返回的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 原始`float`值。 |

**示例：**

```ts
const result: float = Float.toFloat(1.5f);
console.info(result); // 1.5
```

### toDouble

public static native toDouble(value: float): double

将传入的`float`值转换为`double`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | float | 是 | 待转换的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 转换后的`double`值。 |

**示例：**

```ts
const result: double = Float.toDouble(1.5f);
console.info(result); // 1.5
```

### compareTo

public override compareTo(other: Float): int

比较当前`Float`实例与`other`。两个值差值小于`Float.EPSILON`时视为相等；当前值更小时返回`-1`，相等时返回`0`，更大或当前值为`NaN`时返回`1`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 参与比较的另一个`Float`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 比较结果。 |

**示例：**

```ts
const left = new Float(1.0f);
const right = new Float(2.0f);
console.info(left.compareTo(right)); // -1
// 差值小于EPSILON视为相等
console.info(new Float(1.0f).compareTo(new Float(1.0f))); // 0
// NaN时返回1
console.info(new Float(Float.NaN).compareTo(new Float(1.0f))); // 1
```

### toString

public static native toString(f: float, r: int): String

按指定进制将`float`值转换为字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| f | float | 是 | 待转换的`float`值。 |
| r | int | 是 | 字符串表示使用的进制。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 字符串表示。 |

**示例：**

```ts
const text = Float.toString(15.5f, 16);
console.info(text); // "f.8"
```

### toString

public static toString(f: float): String

按十进制将`float`值转换为字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| f | float | 是 | 待转换的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 十进制字符串。 |

**示例：**

```ts
const text = Float.toString(15.5f);
console.info(text); // "15.5"
```

### toString

public toString(r: int): String

按指定进制将当前`Float`实例保存的值转换为字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| r | int | 是 | 字符串表示使用的进制。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 字符串表示。 |

**示例：**

```ts
const value = new Float(15.5f);
console.info(value.toString(8)); // "17.4"
```

### toString

public override toString(): String

按十进制将当前`Float`实例保存的值转换为字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 十进制字符串。 |

**示例：**

```ts
const value = new Float(15.5f);
console.info(value.toString()); // "15.5"
```

### toLocaleString

public toLocaleString(locales?: Intl.LocalesArgument, options?: Intl.NumberFormatOptions): String

按指定区域设置和数字格式选项格式化当前`Float`值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | [Intl.LocalesArgument](arkts-sta-intl.md#localesargument) | 否 | BCP 47语言标签或标签数组。 |
| options | [Intl.NumberFormatOptions](arkts-sta-intl.md#numberformatoptions) | 否 | 数字格式化选项。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 格式化后的字符串。 |

**示例：**

```ts
const value = new Float(1234.5f);
console.info(value.toLocaleString("en-US")); // "1,234.5"
```

### toLocaleString

public override toLocaleString(locales?: Intl.LocalesArgument, options?: object): String

按指定区域设置格式化当前`Float`值。若`options`不是`Intl.NumberFormatOptions`实例，则忽略该参数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | [Intl.LocalesArgument](arkts-sta-intl.md#localesargument) | 否 | BCP 47语言标签或标签数组。 |
| options | object | 否 | 可选格式化对象。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| String | 格式化后的字符串。 |

**示例：**

```ts
const value = new Float(1234.5f);
const options: Intl.NumberFormatOptions = { style: 'currency', currency: 'CNY' };
console.info(value.toLocaleString("en-US", options)); // "CN¥1,234.50"
```

### compare

public static compare(lhs: float, rhs: float): boolean

判断两个`float`值的差值是否不大于`Float.DELTA`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| lhs | float | 是 | 左操作数。 |
| rhs | float | 是 | 右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断两值差值是否不大于`Float.DELTA`。`true`表示差值不大于`Float.DELTA`，`false`表示差值大于`Float.DELTA`。 |

**示例：**

```ts
console.info(Float.compare(1.0f, 1.0f)); // true
// 差值不大于DELTA
console.info(Float.compare(1.0f, 1.0f + Float.DELTA)); // true
// 差值超过DELTA
console.info(Float.compare(1.0f, 1.0f + Float.DELTA * 2.0f)); // false
```

### equals

public equals(other: Any): boolean

判断`other`是否也是`Float`实例且保存相同的`float`值。

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
const left = new Float(1.5f);
const right = new Float(1.5f);
console.info(left.equals(right)); // true
```

### isNaN

public static isNaN(v: float): boolean

判断传入的`float`值是否为`NaN`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | float | 是 | 待检测的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。`true`表示为`NaN`，`false`表示不为`NaN`。 |

**示例：**

```ts
console.info(Float.isNaN(Float.NaN)); // true
```

### isNaN

public isNaN(): boolean

判断当前`Float`实例保存的值是否为`NaN`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为`NaN`。`true`表示为`NaN`，`false`表示不为`NaN`。 |

**示例：**

```ts
const value = new Float(Float.NaN);
console.info(value.isNaN()); // true
```

### isFinite

public static isFinite(v: float): boolean

判断传入的`float`值是否为有限值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | float | 是 | 待检测的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。`true`表示为有限值，`false`表示不为有限值。 |

**示例：**

```ts
console.info(Float.isFinite(1.0f)); // true
console.info(Float.isFinite(Float.POSITIVE_INFINITY)); // false
console.info(Float.isFinite(Float.NaN)); // false
```

### isFinite

public isFinite(): boolean

判断当前`Float`实例保存的值是否为有限值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为有限值。`true`表示为有限值，`false`表示不为有限值。 |

**示例：**

```ts
const value = new Float(1.0f);
console.info(value.isFinite()); // true
```

### isInteger

public static isInteger(v: float): boolean

判断传入的`float`值是否可视为整数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | float | 是 | 待检测的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否可视为整数。`true`表示可视为整数，`false`表示不可视为整数。 |

**示例：**

```ts
console.info(Float.isInteger(2.0f)); // true
console.info(Float.isInteger(2.5f)); // false
```

### isInteger

public isInteger(): boolean

判断当前`Float`实例保存的值是否可视为整数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否可视为整数。`true`表示可视为整数，`false`表示不可视为整数。 |

**示例：**

```ts
const value = new Float(2.0f);
console.info(value.isInteger()); // true
```

### isSafeInteger

public static isSafeInteger(v: float): boolean

判断传入的`float`值是否为安全整数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| v | float | 是 | 待检测的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为安全整数。`true`表示为安全整数，`false`表示不为安全整数。 |

**示例：**

```ts
console.info(Float.isSafeInteger(2.0f)); // true
console.info(Float.isSafeInteger(16777217f)); // false
```

### isSafeInteger

public isSafeInteger(): boolean

判断当前`Float`实例保存的值是否为安全整数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否为安全整数。`true`表示为安全整数，`false`表示不为安全整数。 |

**示例：**

```ts
console.info(new Float(2.0f).isSafeInteger()); // true
console.info(new Float(16777217f).isSafeInteger()); // false
```

### add

public add(other: Float): Float

返回当前值与`other`相加后的新`Float`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 加法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Float | 相加后的新实例。 |

**示例：**

```ts
const result = new Float(1.5f).add(new Float(2.0f));
console.info(result); // 3.5
```

### sub

public sub(other: Float): Float

返回当前值减去`other`后的新`Float`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 减法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Float | 相减后的新实例。 |

**示例：**

```ts
const result = new Float(3.5f).sub(new Float(2.0f));
console.info(result); // 1.5
```

### mul

public mul(other: Float): Float

返回当前值与`other`相乘后的新`Float`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 乘法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Float | 相乘后的新实例。 |

**示例：**

```ts
const result = new Float(3.0f).mul(new Float(2.0f));
console.info(result); // 6
```

### div

public div(other: Float): Float

返回当前值除以`other`后的新`Float`实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 除法右操作数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Float | 相除后的新实例。 |

**示例：**

```ts
const result = new Float(6.0f).div(new Float(2.0f));
console.info(result); // 3
```

### isLessThan

public isLessThan(other: Float): boolean

判断当前值是否小于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 参与比较的另一个`Float`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否小于`other`。`true`表示当前值小于`other`，`false`表示当前值不小于`other`。 |

**示例：**

```ts
console.info(new Float(1.0f).isLessThan(new Float(2.0f))); // true
console.info(new Float(2.0f).isLessThan(new Float(2.0f))); // false
```

### isLessEqualThan

public isLessEqualThan(other: Float): boolean

判断当前值是否小于或等于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 参与比较的另一个`Float`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否小于或等于`other`。`true`表示当前值小于或等于`other`，`false`表示当前值大于`other`。 |

**示例：**

```ts
// 1.0小于2.0
console.info(new Float(1.0f).isLessEqualThan(new Float(2.0f))); // true
// 2.0等于2.0
console.info(new Float(2.0f).isLessEqualThan(new Float(2.0f))); // true
```

### isGreaterThan

public isGreaterThan(other: Float): boolean

判断当前值是否大于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 参与比较的另一个`Float`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否大于`other`。`true`表示当前值大于`other`，`false`表示当前值不大于`other`。 |

**示例：**

```ts
console.info(new Float(3.0f).isGreaterThan(new Float(2.0f))); // true
console.info(new Float(3.0f).isGreaterThan(new Float(3.0f))); // false
```

### isGreaterEqualThan

public isGreaterEqualThan(other: Float): boolean

判断当前值是否大于或等于`other`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| other | Float | 是 | 参与比较的另一个`Float`实例。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断当前值是否大于或等于`other`。`true`表示当前值大于或等于`other`，`false`表示当前值小于`other`。 |

**示例：**

```ts
// 3.0大于2.0
console.info(new Float(3.0f).isGreaterEqualThan(new Float(2.0f))); // true
// 3.0等于3.0
console.info(new Float(3.0f).isGreaterEqualThan(new Float(3.0f))); // true
```

### bitCastFromInt

public static native bitCastFromInt(bits: int): float

将32位整数位模式解释为对应的IEEE-754标准的`float`值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| bits | int | 是 | 待转换的32位整数位模式。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 转换后的`float`值。 |

**示例：**

```ts
// 将int的二进制位模式直接解释为IEEE-754 float
// 0x00000000: 符号位0, 指数0, 尾数0 → 0.0
console.info(Float.bitCastFromInt(0x00000000)); // 0
// 0x3F800000: 符号位0, 指数127, 尾数0 → 1.0
console.info(Float.bitCastFromInt(0x3F800000)); // 1
// 0x40A00000: 符号位0, 指数129, 尾数0x200000 → 5.0
console.info(Float.bitCastFromInt(0x40A00000)); // 5
```

### bitCastToInt

public static native bitCastToInt(val: float): int

将`float`值的IEEE-754位模式转换为32位整数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | float | 是 | 待转换的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 转换后的32位整数。 |

**示例：**

```ts
// 将float的IEEE-754位模式转换为int
// 0.0的二进制: 符号位0, 指数0, 尾数0 → 0x00000000
console.info(Float.bitCastToInt(0.0f)); // 0
// 1.0的二进制: 符号位0, 指数127, 尾数0 → 0x3F800000
console.info(Float.bitCastToInt(1.0f)); // 1065353216
// 5.0的二进制: 符号位0, 指数129, 尾数0x200000 → 0x40A00000
console.info(Float.bitCastToInt(5.0f)); // 1084227584
```
