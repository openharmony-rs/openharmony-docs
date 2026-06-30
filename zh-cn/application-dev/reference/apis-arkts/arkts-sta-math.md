# Math
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供数学常量和常用数学函数。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。

## Math

export class Math

数学工具类，全部成员为静态成员。

**系统能力：** SystemCapability.Utils.Lang

### 常量

以下表格列出本模块提供的公开常量。

**系统能力：** SystemCapability.Utils.Lang

| 常量 | 类型 | 说明 |
| :--- | :--- | :--- |
| PI | double | 圆周率。 |
| E | double | 自然常数。 |
| LN10 | double | 10的自然对数。 |
| LN2 | double | 2的自然对数。 |
| LOG2E | double | 以2为底的`E`对数。 |
| LOG10E | double | 以10为底的`E`对数。 |
| SQRT1_2 | double | `1/2`的平方根。 |
| SQRT2 | double | 2的平方根。 |

**示例：**

```ts
console.info(Math.PI);     // 3.141592653589793
console.info(Math.E);      // 2.718281828459045
console.info(Math.LN10);   // 2.302585092994046
console.info(Math.LN2);    // 0.6931471805599453
console.info(Math.LOG2E);  // 1.4426950408889634
console.info(Math.LOG10E); // 0.4342944819032518
console.info(Math.SQRT1_2);// 0.7071067811865476
console.info(Math.SQRT2);  // 1.4142135623730951
```

### abs

abs(x: byte): byte

返回`byte`值的绝对值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | byte | 是 | 要计算绝对值的`byte`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | `x`的绝对值。 |

**示例：**

```ts
const value: byte = -127;
console.info(Math.abs(value)); // 127
// byte最小值-128的绝对值128溢出byte范围，结果仍为-128
console.info(Math.abs(-128 as byte)); // -128
```

### abs

abs(x: short): short

返回`short`值的绝对值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | short | 是 | 要计算绝对值的`short`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | `x`的绝对值。 |

**示例：**

```ts
const value: short = -1000;
console.info(Math.abs(value)); // 1000
// short最小值-32768的绝对值32768溢出short范围，结果仍为-32768
console.info(Math.abs(-32768 as short)); // -32768
```

### abs

abs(x: int): int

返回`int`值的绝对值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | int | 是 | 要计算绝对值的`int`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | `x`的绝对值。 |

**示例：**

```ts
const value: int = -100000;
console.info(Math.abs(value)); // 100000
// int最小值-2147483648的绝对值2147483648溢出int范围，结果仍为-2147483648
console.info(Math.abs(-2147483648)); // -2147483648
```

### abs

abs(x: long): long

返回`long`值的绝对值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | long | 是 | 要计算绝对值的`long`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | `x`的绝对值。 |

**示例：**

```ts
const value: long = -9223372036854775807;
console.info(Math.abs(value)); // 9223372036854775807
// long最小值-9223372036854775808的绝对值溢出long范围，结果仍为-9223372036854775808
console.info(Math.abs(-9223372036854775808)); // -9223372036854775808
```

### abs

abs(x: float): float

返回`float`值的绝对值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | 要计算绝对值的`float`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | `x`的绝对值。 |

**示例：**

```ts
const value: float = -3.5f;
console.info(Math.abs(value)); // 3.5
```

### abs

abs(x: double): double

返回`double`值的绝对值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | 要计算绝对值的`double`值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | `x`的绝对值。 |

**示例：**

```ts
const value: double = -3.5;
console.info(Math.abs(value)); // 3.5
```

### acos

acos(x: double): double

返回`double`值的反余弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.acos(1.0)); // 0
```

### acos

acos(x: float): float

返回`float`值的反余弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.acos(value)); // 0
```

### acosh

acosh(x: double): double

返回`double`值的反双曲余弦值，输入值通常应大于或等于`1`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.acosh(1.0)); // 0
```

### acosh

acosh(x: float): float

返回`float`值的反双曲余弦值，输入值通常应大于或等于`1`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.acosh(value)); // 0
```

### asin

asin(x: double): double

返回`double`值的反正弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.asin(0.0)); // 0
```

### asin

asin(x: float): float

返回`float`值的反正弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 0.0f;
console.info(Math.asin(value)); // 0
```

### asinh

asinh(x: double): double

返回`double`值的反双曲正弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.asinh(1.0)); // 0.8813736
```

### asinh

asinh(x: float): float

返回`float`值的反双曲正弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.asinh(value)); // 0.8813736
```

### atan

atan(x: double): double

返回`double`值的反正切值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.atan(1.0)); // 0.7853982
```

### atan

atan(x: float): float

返回`float`值的反正切值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.atan(value)); // 0.7853982
```

### atan2

atan2(y: double, x: double): double

返回点`(x, y)`相对正x轴的角度。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| y | double | 是 | y参数。 |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.atan2(1.0, 1.0)); // 0.7853982
```

### atan2

atan2(y: float, x: float): float

返回`float`参数对应点`(x, y)`相对正x轴的角度。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| y | float | 是 | y参数。 |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const y: float = 1.0f;
const x: float = 1.0f;
console.info(Math.atan2(y, x)); // 0.7853982
```

### atanh

atanh(x: double): double

返回`double`值的反双曲正切值，输入值通常应在`-1`到`1`之间。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.atanh(0.5)); // 0.54930616
```

### atanh

atanh(x: float): float

返回`float`值的反双曲正切值，输入值通常应在`-1`到`1`之间。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 0.5f;
console.info(Math.atanh(value)); // 0.54930616
```

### cbrt

cbrt(x: double): double

返回`double`值的立方根。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.cbrt(8.0)); // 2
```

### cbrt

cbrt(x: float): float

返回`float`值的立方根。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 8.0f;
console.info(Math.cbrt(value)); // 2
```

### ceil

ceil(x: double): double

返回大于或等于`x`的最小整数值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.ceil(1.2));  // 2
console.info(Math.ceil(-1.2)); // -1
```

### ceilPow2

ceilPow2(n: int): int

返回不小于`n`的最小2的幂。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| n | int | 是 | n参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 返回值。 |

**示例：**

```ts
console.info(Math.ceilPow2(7)); // 8
```

### clz32

clz32(x: Int): Int

返回`Int`值转换为32位整数后的前导零个数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | Int | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Int | 返回值。 |

**示例：**

```ts
console.info(Math.clz32(1)); // 31
```

### clz32

clz32(value: double): double

返回`double`值转换为32位整数后的前导零个数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | double | 是 | value参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.clz32(1.0)); // 31
```

### cos

cos(x: double): double

返回`x`弧度的余弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.cos(0.0)); // 1
```

### cosh

cosh(x: double): double

返回`double`值的双曲余弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.cosh(0.0)); // 1
```

### cosh

cosh(x: float): float

返回`float`值的双曲余弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 0.0f;
console.info(Math.cosh(value)); // 1
```

### exp

exp(x: float): float

返回`E`的`x`次幂。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.exp(value)); // 2.7182817
```

### exp

exp(x: double): double

返回`E`的`x`次幂。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.exp(1.0)); // 2.7182817
```

### expm1

expm1(x: float): float

返回`exp(x) - 1`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.expm1(value)); // 1.7182817
```

### expm1

expm1(x: double): double

返回`exp(x) - 1`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.expm1(1.0)); // 1.7182817
```

### floor

floor(x: double): double

返回小于或等于`x`的最大整数值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.floor(1.8));  // 1
console.info(Math.floor(-1.8)); // -2
```

### fround

fround(x: double): double

按单精度浮点语义转换后返回数值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
// 1.337无法精确表示为float，fround展示精度差异
console.info(Math.fround(1.337)); // 1.3370000123977661
```

### hypot

hypot(...values: double[]): double

返回所有参数平方和的平方根。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| values | double[] | 否 | values参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.hypot(3.0, 4.0)); // 5
```

### imul

imul(a: double, b: double): double

按32位整数乘法计算结果。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| a | double | 是 | a参数。 |
| b | double | 是 | b参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.imul(3.0, 4.0)); // 12
```

### log

log(x: float): float

返回自然对数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.log(value)); // 0
```

### log

log(x: double): double

返回自然对数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.log(Math.E)); // 1
```

### log10

log10(x: double): double

返回以10为底的对数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.log10(100.0)); // 2
```

### log10

log10(x: float): float

返回以10为底的对数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 100.0f;
console.info(Math.log10(value)); // 2
```

### log1p

log1p(x: double): double

返回`log(1 + x)`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.log1p(1.0)); // 0.6931472
```

### log1p

log1p(x: float): float

返回`log(1 + x)`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.log1p(value)); // 0.6931472
```

### log2

log2(x: double): double

返回以2为底的对数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.log2(8.0)); // 3
```

### log2

log2(x: float): float

返回以2为底的对数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 8.0f;
console.info(Math.log2(value)); // 3
```

### max

max(): double

无参数时返回负无穷。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.max()); // -Infinity
```

### max

max(val: double): double

返回单个参数本身。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | double | 是 | val参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.max(2.0)); // 2
```

### max

max(val1: double, val2: double): double

返回两个参数中的较大值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val1 | double | 是 | val1参数。 |
| val2 | double | 是 | val2参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.max(1.0, 2.0)); // 2
```

### max

max(...values: double[]): double

返回多个参数中的最大值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| values | double[] | 否 | values参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.max(1.0, 2.0, 3.0)); // 3
```

### min

min(): double

无参数时返回正无穷。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.min()); // Infinity
```

### min

min(val: double): double

返回单个参数本身。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | double | 是 | val参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.min(2.0)); // 2
```

### min

min(val1: double, val2: double): double

返回两个参数中的较小值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val1 | double | 是 | val1参数。 |
| val2 | double | 是 | val2参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.min(1.0, 2.0)); // 1
```

### min

min(...values: double[]): double

返回多个参数中的最小值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| values | double[] | 否 | values参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.min(1.0, 2.0, 3.0)); // 1
```

### pow

pow(u: double, v: double): double

返回`u`的`v`次幂。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| u | double | 是 | u参数。 |
| v | double | 是 | v参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.pow(2.0, 3.0)); // 8
```

### random

random(): double

返回`[0, 1)`范围内的伪随机数。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
const value = Math.random();
console.info(value >= 0.0 && value < 1.0); // true
```

### round

round(x: double): double

返回四舍五入到最接近整数后的值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.round(1.5)); // 2
console.info(Math.round(2.5)); // 3
console.info(Math.round(1.4)); // 1
```

### sign

sign(x: double): double

返回数值符号：正数返回`1`，负数返回`-1`，`0`返回`0`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.sign(3.0));  // 1
console.info(Math.sign(-3.0)); // -1
console.info(Math.sign(0.0));  // 0
```

### sin

sin(x: double): double

返回`x`弧度的正弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.sin(0.0)); // 0
```

### sinh

sinh(x: double): double

返回`double`值的双曲正弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.sinh(0.0)); // 0
```

### sinh

sinh(x: float): float

返回`float`值的双曲正弦值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 1.0f;
console.info(Math.sinh(value)); // 1.1752012
```

### sqrt

sqrt(x: double): double

返回平方根。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.sqrt(9.0)); // 3
```

### tan

tan(x: double): double

返回`x`弧度的正切值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.tan(0.0)); // 0
```

### tanh

tanh(x: double): double

返回`double`值的双曲正切值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.tanh(0.0)); // 0
```

### tanh

tanh(x: float): float

返回`float`值的双曲正切值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | float | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 返回值。 |

**示例：**

```ts
const value: float = 0.0f;
console.info(Math.tanh(value)); // 0
```

### trunc

trunc(x: double): double

返回去除小数部分后的值。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | double | 是 | x参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 返回值。 |

**示例：**

```ts
console.info(Math.trunc(1.8));  // 1
console.info(Math.trunc(-1.8)); // -1
```
