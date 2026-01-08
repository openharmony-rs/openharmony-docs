# Int
本模块提供整数基础操作。开发者可以使用本模块的功能，对整数进行处理、转换及相关运算。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## constructor

constructor()

无参构造函数，创建一个值为0的Int实例。

**示例：**

```typescript
const zero = new Int();
console.info(zero); // 输出: 0
```

## constructor

constructor(value: int)

带参构造函数，使用指定的初始值创建Int对象。

**参数：**

| 参数名  | 类型  | 必填 | 说明         |
| ------- | ----- | ---- | :----------- |
| value | int | 是 | 原始整数值。 |

**示例：**

```typescript
const n = new Int(123);
console.info(n); // 输出: 123
```

## valueOf

static valueOf(value: int): Int

将原始int值包装为Int对象。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待包装的原始整数值。 |

**返回值：**

| 类型      | 说明                                  |
| --------- | ------------------------------------- |
| Int | 返回一个包装后的Int实例。。 |

**示例：**

```typescript
const a = Int.valueOf(123);
console.info(a); // 输出：123
```

## equals

equals(other: Any): boolean

判断当前Int实例与other是否“值相等”，当other为Int且值相同时返回true。

**参数：**

| 参数名  | 类型  | 必填 | 说明           |
| ------- | ----- | ---- | -------------- |
| other | Any | 是 | 比较的基准值。 |

**返回值：**

| 类型      | 说明                                  |
| --------- | ------------------------------------- |
| boolean | 是否相等。相等为true，不相等为false。 |

**示例：**

```typescript
const a = new Int(123);
console.info(a.equals(234)); // 输出：false
```

## 属性

| 名称          | 类型 | 只读  |  可选  | 说明               |
| ------------- | :--- | ---- | ----  | :----------------- |
| MIN_VALUE | int  | 是   |  否   | 表示Int类型可表示的最小值为：-2147483648。 |
| MAX_VALUE | int  | 是   |  否   | 表示Int类型可表示的最大值为：2147483647。 |
| BIT_SIZE | byte  | 是   |  否   | 表示Int类型占用的位数为：32。 |
| BYTE_SIZE | byte  | 是   |  否   | 表示Int类型占用的字节数为：4。 |

## toByte

toByte(): byte

返回当前Int实例的数值，转换为byte类型。

**返回值：**

| 类型   | 说明             |
| ------ | ---------------- |
| byte | 转换后的字节值。 |

**示例：**

```typescript
const num = new Int(100);
console.info(num.toByte()); // 输出: 100
```

## byteValue

byteValue(): byte

返回当前Int实例的数值，转换为byte类型。

**返回值：**

| 类型   | 说明             |
| ------ | ---------------- |
| byte | 转换后的字节值。 |

**示例：**

```typescript
const num = new Int(16);
console.info(num.byteValue()); // 输出：16
```

## toShort

toShort(): short

将原始int值转换为short类型。

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
const a = new Int(16);
console.info(a.toShort()); // 输出：16
```

## shortValue

shortValue(): short

将原始int值转换为short类型。

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
const a = new Int(16);
console.info(a.shortValue()); // 输出：16
```

## toInt

toInt(): int

从Int对象中提取出原始的int类型值。

**返回值：**

| 类型  | 说明                    |
| ----- | ----------------------- |
| int | 提取出原始的int类型值。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.toInt()); // 输出：65
```

## intValue

intValue(): int

从Int对象中提取出原始的int类型值。

**返回值：**

| 类型  | 说明                    |
| ----- | ----------------------- |
| int | 提取出原始的int类型值。 |

**示例：**

```typescript
const a = new Int(64);
console.info(a.intValue()); // 输出：64
```

## toLong

toLong(): long

将原始int值转换为long类型。

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| long | 转换后的long类型值。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.toLong()); // 输出：65
```

## longValue

longValue(): long

将原始int值转换为long类型。

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| long | 转换后的long类型值。 |

**示例：**

```typescript
const a = new Int(64);
console.info(a.longValue()); // 输出：64
```

## toFloat

toFloat(): float

将原始int值转换为float类型（32位浮点数）。

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.toFloat()); // 输出：65
```

## floatValue

floatValue(): float

将原始int值转换为float类型（32位浮点数）。

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
const a = new Int(64);
console.info(a.floatValue()); // 输出：6
```

## toDouble

toDouble(): double

将原始int值转换为double类型。

**返回值：**

| 类型     | 说明                       |
| -------- | -------------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.toDouble()); // 输出：65
```

## doubleValue

doubleValue(): double

将原始int值转换为double类型。

**返回值：**

| 类型     | 说明                       |
| -------- | -------------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
const a = new Int(64);
console.info(a.doubleValue()); // 输出：64
```

## toChar

toChar(): char

将原始int值转换为char类型。

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| char | 转换后的char类型值。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.toChar()); // 输出："A"
```

## toByte

static toByte(value: int): byte

将原始int值转换为byte类型。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待转换的原始整数值。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| byte | 转换后的byte类型值。 |

**示例：**

```typescript
console.info(Int.toByte(65)); // 输出：65
```

## toShort

static toShort(value: int): short

将原始int值转换为short类型。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待转换的原始整数值。 |

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
console.info(Int.toShort(64)); // 输出：64
```

## toLong

static toLong(value: int): long

将原始int值转换为long类型。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待转换的原始整数值。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| long | 转换后的long类型值。 |

**示例：**

```typescript
console.info(Int.toLong(65)); // 输出：65
```

## toFloat

static toFloat(value: int): float

将原始int值转换为float类型（32位浮点数）。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待转换的原始整数值。 |

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
console.info(Int.toFloat(65)); // 输出：65
```

## toDouble

static toDouble(value: int): double

将原始int值转换为double类型。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待转换的原始整数值。 |

**返回值：**

| 类型     | 说明                       |
| -------- | -------------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
console.info(Int.toDouble(65)); // 输出：65
```

## toChar

static toChar(value: int): char

将原始int值转换为char类型。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待转换的原始整数值。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| char | 转换后的char类型值。 |

**示例：**

```typescript
console.info(Int.toChar(65)); // 输出："A"
```

## toInt

static toInt(value: int): int

将原始int值转换为int类型。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| value | int | 是 | 待转换的原始整数值。 |

**返回值：**

| 类型  | 说明                    |
| ----- | ----------------------- |
| int | 转换后的int类型值。 |

**示例：**

```typescript
console.info(Int.toInt(65)); // 输出：65
```

## toString

toString(): String

将当前int值转换为十进制字符串。

**返回值：**

| 类型     | 说明               |
| -------- | ------------------ |
| string | 十进制字符串表示。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.toString()); // 输出：65
```

## toString

toString(radix: number): string

将当前int值转换为指定基数（radix）的字符串。

**参数：**

| 参数名  | 类型     | 必填 | 说明       |
| ------- | -------- | ---- | ---------- |
| radix | number | 是 | 进制基数。 |

**返回值：**

| 类型     | 说明                       |
| -------- | -------------------------- |
| string | 按进制转换后的字符串表示。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.toString(10)); // 输出：65
```

## compareTo

compareTo(other: Int): int

比较当前Int与other的数值大小，返回比较结果。

**参数：**

| 参数名  | 类型  | 必填 | 说明                 |
| ------- | ----- | ---- | -------------------- |
| other | int | 是 | 待比较的原始整数值。 |

**返回值：**

| 类型  | 说明                                                       |
| ----- | ---------------------------------------------------------- |
| int | 结果=0说明相等，结果=1当前值更大，结果=-1说明other值更大。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.compareTo(64)); // 输出：1
```

## add

add(other: Int): Int

当前值加other值，返回新Int实例。

**参数：**

| 参数名  | 类型  | 必填 | 说明 |
| ------- | ----- | ---- | ---- |
| other | Int | 是 | 加数。 |

**返回值：**

| 类型  | 说明       |
| ----- | ---------- |
| Int | 相加结果。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.add(10)); // 输出：75
```

## sub

sub(other: Int): Int

当前值减other值，返回新Int实例。

**参数：**

| 参数名  | 类型  | 必填 | 说明   |
| ------- | ----- | ---- | ------ |
| other | Int | 是 | 减数。 |

**返回值：**

| 类型  | 说明       |
| ----- | ---------- |
| Int | 相减结果。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.sub(10)); // 输出：55
```

## mul

mul(other: Int): Int

当前值乘以other值，返回新Int实例。

**参数：**

| 参数名  | 类型  | 必填 | 说明   |
| ------- | ----- | ---- | ------ |
| other | Int | 是 | 乘数。 |

**返回值：**

| 类型  | 说明       |
| ----- | ---------- |
| Int | 相乘结果。 |

**示例：**

```typescript
const a = new Int(6);
console.info(a.mul(5)); // 输出：30
```

## div

div(other: Int): Int

当前值除以other值（整数除法，舍去小数），返回新Int实例。

**参数：**

| 参数名  | 类型  | 必填 | 说明      |
| ------- | ----- | ---- | --------- |
| other | Int | 是 | 不能为0。 |

**返回值：**

| 类型  | 说明       |
| ----- | ---------- |
| Int | 相除结果。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.div(10)); // 输出：6
```

## isLessThan

isLessThan(other: Int): boolean

判断当前值是否小于other值。

**参数：**

| 参数名  | 类型  | 必填 | 说明           |
| ------- | ----- | ---- | -------------- |
| other | Int | 是 | 比较的基准值。 |

**返回值：**

| 类型      | 说明                                         |
| --------- | -------------------------------------------- |
| boolean | 若当前值小于other值为true，否则为false。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.isLessThan(75)); // 输出：true
```

## isLessEqualThan

isLessEqualThan(other: Int): boolean

判断当前值是否小于等于other值。

**参数：**

| 参数名  | 类型  | 必填 | 说明           |
| ------- | ----- | ---- | -------------- |
| other | Int | 是 | 比较的基准值。 |

**返回值：**

| 类型      | 说明                                             |
| --------- | ------------------------------------------------ |
| boolean | 若当前值小于等于other值为true，否则为false。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.isLessEqualThan(65)); // 输出：true
```

## isGreaterThan

isGreaterThan(other: Int): boolean

判断当前值是否大于other值。

**参数：**

| 参数名  | 类型  | 必填 | 说明           |
| ------- | ----- | ---- | -------------- |
| other | Int | 是 | 比较的基准值。 |

**返回值:**

| 类型      | 说明                                         |
| --------- | -------------------------------------------- |
| boolean | 若当前值大于other值为true，否则为false。 |

**示例:**

```typescript
const a = new Int(65);
console.info(a.isGreaterThan(55)); // 输出：true
```

## isGreaterEqualThan

isGreaterThan(other: Int): boolean

判断当前值是否大于等于other值。

**参数:**

| 参数名  | 类型  | 必填 | 说明           |
| ------- | ----- | ---- | -------------- |
| other | Int | 是 | 比较的基准值。 |

**返回值:**

| 类型      | 说明                                             |
| --------- | ------------------------------------------------ |
| boolean | 若当前值大于等于other值为true，否则为false。 |

**示例：**

```typescript
const a = new Int(65);
console.info(a.isGreaterEqualThan(55)); // 输出：true
```
