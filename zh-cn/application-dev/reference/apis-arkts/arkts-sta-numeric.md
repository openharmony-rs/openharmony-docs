# Numeric
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供数值装箱类型的抽象基类。`Numeric`定义通用数值转换接口，`Integral`和`Floating`分别作为整数与浮点装箱类型的基类。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## Numeric

export abstract class Numeric extends Object

所有数值装箱类型的抽象基类。开发者通常通过`Byte`、`Short`、`Int`、`Long`、`Float`或`Double`实例使用这些转换接口。继承自[Object](arkts-sta-object.md#object-2)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### toByte

public abstract toByte(): byte

将当前数值转换为`byte`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| byte | 转换后的`byte`值。 |

**示例：**

```ts
const value: Numeric = new Int(300);
const result: byte = value.toByte();
// 300超出byte范围，截断低8位得44
console.info(result); // 44
```

### toInt

public abstract toInt(): int

将当前数值转换为`int`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 转换后的`int`值。 |

**示例：**

```ts
const value: Numeric = new Long(2147483648);
const result: int = value.toInt();
// 2147483648超出int范围，截断低32位得-2147483648
console.info(result); // -2147483648
```

### toShort

public abstract toShort(): short

将当前数值转换为`short`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| short | 转换后的`short`值。 |

**示例：**

```ts
const value: Numeric = new Int(100000);
const result: short = value.toShort();
// 100000超出short范围，截断低16位得-31072
console.info(result); // -31072
```

### toLong

public abstract toLong(): long

将当前数值转换为`long`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| long | 转换后的`long`值。 |

**示例：**

```ts
const value: Numeric = new Int(100000);
const result: long = value.toLong();
console.info(result); // 100000
```

### toFloat

public abstract toFloat(): float

将当前数值转换为`float`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| float | 转换后的`float`值。 |

**示例：**

```ts
const value: Numeric = new Long(123456789);
const result: float = value.toFloat();
// 123456789超出Float.MAX_SAFE_INTEGER，丢失精度
console.info(result); // 123456792
```

### toDouble

public abstract toDouble(): double

将当前数值转换为`double`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| double | 转换后的`double`值。 |

**示例：**

```ts
const value: Numeric = new Long(9223372036854775807);
const result: double = value.toDouble();
// 超出Double.MAX_SAFE_INTEGER，丢失精度
console.info(result); // 9223372036854776000
```

## Integral

export abstract class Integral extends Numeric

所有整数装箱类型的抽象基类，例如`Byte`、`Short`、`Int`和`Long`。继承自[Numeric](#numeric-1)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
const value = new Int(12);
console.info(value instanceof Integral); // true
```

## Floating

export abstract class Floating extends Numeric

所有浮点装箱类型的抽象基类，例如`Float`和`Double`。继承自[Numeric](#numeric-1)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
const value = new Float(1.5f);
console.info(value instanceof Floating); // true
```
