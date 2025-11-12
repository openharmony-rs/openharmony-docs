# Byte

本模块提供Byte基础操作。开发者可以使用本模块的功能，对字节数据进行处理、转换及相关操作。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## constructor

constructor()

无参构造函数，创建一个初始值为0的Byte对象。

**示例：**

```typescript
const b = new Byte();
console.info(b); // 输出：0
```

## constructor

constructor(value: byte)

带参构造函数，使用指定的初始值创建Byte对象。

**参数：**

| 参数名 | 类型 | 必填 | 说明                                 |
| ------ | ---- | ---- | :----------------------------------- |
| value  | byte | 是   | 原始字节值（需在-128 ~ 127范围内）。 |

**示例：**

```typescript
const b = new Byte(64 as byte);
console.info(b); // 输出：64
```

## valueOf

static valueOf(value: byte): Byte

将原始byte值包装为Byte对象。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待包装的原始字节值。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| Byte | 包装后的Byte实例。 |

**示例：**

```typescript
const b = Byte.valueOf(64 as byte);
console.info(b); // 输出：64
```

## 属性

| 名称          | 类型 | 只读  |  可选  | 说明               |
| ------------- | :--- | ---- | ----  | :----------------- |
| MIN_VALUE | byte  | 否   |  否   | 表示Byte类型可表示的最小值：-128。 |
| MAX_VALUE | byte  | 否   |  否   | 表示Byte类型可表示的最大值：127。 |
| BIT_SIZE | byte  | 否   |  否   | 表示Byte类型占用8bit位。 |
| BYTE_SIZE | byte  | 否   |  否   | 表示Byte类型占用1字节。 |

## toByte

toByte(): byte

返回当前Byte实例的数值，转换为byte类型。

**返回值：**

| 类型 | 说明             |
| ---- | ---------------- |
| byte | 转换后的字节值。 |

**示例：**

```typescript
const b = new Byte(16);
console.info(b.toByte()); // 输出：16
```

## byteValue

byteValue(): byte

返回当前Byte实例的数值，转换为byte类型。

**返回值：**

| 类型 | 说明             |
| ---- | ---------------- |
| byte | 转换后的字节值。 |

**示例：**

```typescript
const b = new Byte(16);
console.info(b.byteValue()); // 输出：16
```

## toShort

toShort(): short

将原始byte值转换为short类型。

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.toShort()); // 输出：64
```

## shortValue

shortValue(): short

将原始byte值转换为short类型。

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.shortValue()); // 输出：64
```

## toInt

toInt(): int

将原始byte值转换为int类型。

**返回值：**

| 类型 | 说明                |
| ---- | ------------------- |
| int  | 转换后的int类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.toInt()); // 输出：64
```

## intValue

intValue(): int

将原始byte值转换为int类型。

**返回值：**

| 类型 | 说明                |
| ---- | ------------------- |
| int  | 转换后的int类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.intValue()); // 输出：64
```

## toLong

toLong(): long

将原始byte值转换为long类型。

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| long | 转换后的long类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.toLong()); // 输出：64
```

## longValue

longValue(): long

将原始byte值转换为long类型。

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| long | 转换后的long类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.longValue()); // 输出：64
```

## toFloat

toFloat(): float

将原始byte值转换为float类型（32位浮点数）。

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.toFloat()); // 输出：64
```

## floatValue

floatValue(): float

将原始byte值转换为float类型（32位浮点数）。

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.floatValue()); // 输出：64
```

## toDouble

toDouble(): double

将原始byte值转换为double类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.toDouble()); // 输出：64
```

## doubleValue

doubleValue(): double

将原始byte值转换为double类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
const b = new Byte(64);
console.info(b.doubleValue()); // 输出：64
```

## toChar

toChar(): char

将原始byte值转换为char类型。

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| char | 转换后的char类型值。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.toChar()); // 输出："A"
```

## toShort

static toShort(value: byte): short

将原始byte值转换为short类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待转换的原始字节值。 |

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| short | 转换后的short类型值。 |

**示例：**

```typescript
console.info(Byte.toShort(64)); // 输出：64
```

## toInt

static toInt(value: byte): int

将原始byte值转换为int类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待转换的原始字节值。 |

**返回值：**

| 类型 | 说明                |
| ---- | ------------------- |
| int  | 转换后的int类型值。 |

**示例：**

```typescript
console.info(Byte.toInt(64)); // 输出：64
```

## toLong

static toLong(value: byte): long

将原始byte值转换为long类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待转换的原始字节值。 |

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| long | 转换后的long类型值。 |

**示例：**

```typescript
console.info(Byte.toLong(64)); // 输出：64
```

## toFloat

static toFloat(value: byte): float

将原始byte值转换为float类型（32位浮点数）。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待转换的原始字节值。 |

**返回值：**

| 类型  | 说明                  |
| ----- | --------------------- |
| float | 转换后的float类型值。 |

**示例：**

```typescript
console.info(Byte.toFloat(64)); // 输出：64
```

## toDouble

static toDouble(value: byte): double

将原始byte值转换为double类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待转换的原始字节值。 |

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| double | 转换后的double类型值。 |

**示例：**

```typescript
console.info(Byte.toDouble(64)); // 输出：64
```

## toChar

static toChar(value: byte): char

将原始byte值转换为char类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待转换的原始字节值。 |

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| char | 转换后的char类型值。 |

**示例：**

```typescript
console.info(Byte.toChar(65)); // 输出："A"
```

## toByte

static toByte(value: byte): byte

将原始byte值转换为char类型。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| value  | byte | 是   | 待转换的原始字节值。 |

**返回值：**

| 类型 | 说明                 |
| ---- | -------------------- |
| byte | 转换后的byte类型值。 |

**示例：**

```typescript
console.info(Byte.toByte(64)); // 输出：64
```

## compareTo

compareTo(other: Byte): int

比较当前Byte与other的数值大小，返回比较结果。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| ------ | ---- | ---- | -------------------- |
| other  | byte | 是   | 待比较的原始字节值。 |

**返回值：**

| 类型 | 说明                                          |
| ---- | --------------------------------------------- |
| int  | 结果>0说明当前值更大，结果<0说明other值更大。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.compareTo(64)); // 输出：1
```

## toString

toString(): String

将当前Byte值转换为十进制字符串。

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| string | 十进制字符串表示。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.toString()); // 输出：65
```

## toString

toString(radix: number): string

将当前Byte值转换为指定基数（radix）的字符串。

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| radix  | number | 是   | 进制基数。 |

**返回值：**

| 类型   | 说明                       |
| ------ | -------------------------- |
| string | 按进制转换后的字符串表示。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.toString(10)); // 输出：65
```

## equals

equals(other: Any): boolean

判断当前Byte对象与other是否“值相等”，仅当other为Byte实例且值相同时返回true。

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| other  | Any  | 是   | 比较的基准值。 |

**返回值：**

| 类型    | 说明                        |
| ------- | --------------------------- |
| boolean | 相等为true，不相等为false。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.equals(10)); // 输出：false
```

## add

add(other: Byte): Byte

当前值加other值，返回新Byte实例。

**参数：**

| 参数名 | 类型 | 必填 | 说明   |
| ------ | ---- | ---- | ------ |
| other  | Byte | 是   | 加数。 |

**返回值：**

| 类型 | 说明       |
| ---- | ---------- |
| Byte | 相加结果。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.add(10)); // 输出：75
```

## sub

sub(other: Byte): Byte

当前值减other值，返回新Byte实例。

**参数：**

| 参数名 | 类型 | 必填 | 说明   |
| ------ | ---- | ---- | ------ |
| other  | Byte | 是   | 减数。 |

**返回值：**

| 类型 | 说明       |
| ---- | ---------- |
| Byte | 相减结果。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.sub(10)); // 输出：55
```

## mul

mul(other: Byte): Byte

当前值乘以other值，返回新Byte实例。

**参数：**

| 参数名 | 类型 | 必填 | 说明   |
| ------ | ---- | ---- | ------ |
| other  | Byte | 是   | 乘数。 |

**返回值：**

| 类型 | 说明       |
| ---- | ---------- |
| Byte | 相乘结果。 |

**示例：**

```typescript
const b = new Byte(6);
console.info(b.mul(5)); // 输出：30
```

## div

div(other: Byte): Byte

当前值除以other值（整数除法，舍去小数），返回新Byte实例。

**参数：**

| 参数名 | 类型 | 必填 | 说明      |
| ------ | ---- | ---- | --------- |
| other  | Byte | 是   | 不能为0。 |

**返回值：**

| 类型 | 说明       |
| ---- | ---------- |
| Byte | 相除结果。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.div(10)); // 输出：6
```

## isLessThan

isLessThan(other: Byte): boolean

判断当前值是否小于other值。

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| other  | Byte | 是   | 比较的基准值。 |

**返回值：**

| 类型    | 说明                                     |
| ------- | ---------------------------------------- |
| boolean | 若当前值小于other值为true，否则为false。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.isLessThan(75)); // 输出：true
```

## isLessEqualThan

isLessEqualThan(other: Byte): boolean

判断当前值是否小于等于other值。

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| other  | Byte | 是   | 比较的基准值。 |

**返回值：**

| 类型    | 说明                                         |
| ------- | -------------------------------------------- |
| boolean | 若当前值小于等于other值为true，否则为false。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.isLessEqualThan(65)); // 输出：true
```

## isGreaterThan

isGreaterThan(other: Byte): boolean

判断当前值是否大于other值。

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| other  | Byte | 是   | 比较的基准值。 |

**返回值：**

| 类型    | 说明                                     |
| ------- | ---------------------------------------- |
| boolean | 若当前值大于other值为true，否则为false。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.isGreaterThan(55)); // 输出：true
```

## isGreaterEqualThan

isGreaterThan(other: Byte): boolean

判断当前值是否大于等于other值。

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| other  | Byte | 是   | 比较的基准值。 |

**返回值：**

| 类型    | 说明                                         |
| ------- | -------------------------------------------- |
| boolean | 若当前值大于等于other值为true，否则为false。 |

**示例：**

```typescript
const b = new Byte(65);
console.info(b.isGreaterEqualThan(55)); // 输出：True
```