# Boolean

本模块提供布尔值基础操作。开发者可以使用本模块的功能，进行布尔值的处理、转换及相关操作。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## constructor

constructor(value: boolean)

带参构造函数，使用指定的初始值创建Boolean对象。

**参数：**

| 参数名 | 类型    | 必填 | 说明                        |
| :----- | :------ | :--- | :-------------------------- |
| value  | boolean | 是   | 原始布尔值（true或false）。 |

**示例：**

```typescript
const bool1 = new Boolean(true);
console.info(bool1); // 输出：true
const bool2 = new Boolean(false);
console.info(bool2); // 输出：false
```

## constructor

constructor(value: byte / short / int / long / bigint)

从整数类型（byte/short/int/long/bigint）创建Boolean对象，非零值转换为true，零值转换为false。

**参数：**

| 参数名 | 类型                       | 必填 | 说明         |
| :----- | :------------------------- | :--- | :----------- |
| value  | byte/short/int/long/bigint | 是   | 整数类型值。 |

**示例：**

```typescript
const bool3 = new Boolean(127 as byte); 
const bool4 = new Boolean(0 as int);    
const bool5 = new Boolean(BigInt(100));
console.info(bool3, bool4, bool5); // 输出：true, false, true
```

## constructor

constructor(value: char)

从字符类型（char）创建Boolean对象，非空字符（\u0000）转换为true，空字符转换为false。

**参数：**

| 参数名 | 类型 | 必填 | 说明                               |
| :----- | :--- | :--- | :--------------------------------- |
| value  | char | 是   | 字符类型值（如 c'A'、c'\u0000'）。 |

**示例：**

```typescript
const bool6 = new Boolean(c'A');       
const bool7 = new Boolean(c'\u0000');  
console.info(bool6, bool7); // 输出：true, false
```

## constructor

constructor(value: float / number)

从浮点数类型（float/number）创建Boolean对象，非零且非NaN值转换为true，零或NaN转换为false。

**参数：**

| 参数名 | 类型         | 必填 | 说明           |
| :----- | :----------- | :--- | :------------- |
| value  | float/number | 是   | 浮点数类型值。 |

**示例：**

```typescript
const bool8 = new Boolean(3.14 as float); 
const bool9 = new Boolean(0.0);           
const bool10 = new Boolean(NaN);          
console.info(bool8, bool9, bool10); // 输出：true, false, false
```

## constructor

constructor(value: string) 

从字符串类型（string）创建Boolean对象，非空字符串转换为true，空字符串（''）转换为false。

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| :----- | :----- | :--- | :--------- |
| value  | string | 是   | 字符串值。 |

**示例：**

```typescript
const bool1 = new Boolean("arkts"); 
const bool2 = new Boolean("");      
console.info(bool1, bool2); // 输出：true, false
```

## constructor

constructor(value: Any = undefined)

从任意类型（Any）或默认undefined创建Boolean对象。

**参数：**

| 参数名 | 类型 | 必填 | 说明                            |
| :----- | :--- | :--- | :------------------------------ |
| value  | Any  | 否   | 若value为null或undefined，创建一个值为false的Boolean对象；<br>若value为Boolean实例，则返回其原始值；<br>若value为其他包装类实例（Number/Char/Float 等），先取原始值，再按对应类型规则转换；<br>若value为String实例，且为非空字符串，则返回true；<br>若value为任意其他Object实例，则返回true；<br>其他情况创建一个值为false的Boolean对象。 |

**示例：**

```typescript
const bool1 = new Boolean(null);       
const bool2 = new Boolean(undefined);  
const numObj = new Number(10);          
const bool3 = new Boolean(numObj);     
console.info(bool1, bool2, bool3); 
// 输出：false, false, true
```

## 属性

| 名称          | 类型 | 只读  |  可选  | 说明               |
| ------------- | :--- | ---- | ----  | :----------------- |
| TRUE | Boolean  | 是   |  否   | 表示真布尔值的静态实例。 |
| FALSE | Boolean  | 是   |  否   | 表示假布尔值的静态实例。 |

## Boolean.$_invoke

$_invoke(): boolean

创建默认值为false的原始布尔值。

**返回值：**

| 类型    | 说明            |
| :------ | :-------------- |
| boolean | 默认返回false。 |

**示例：**

```typescript
const defaultBool = Boolean.$_invoke();
console.info(defaultBool); // 输出：false
```

## Boolean.$_invoke\<T>

$_invoke\<T>(value: T): boolean

将任意类型值 value 转换为对应的布尔值。

**参数：**

| 参数名 | 类型 | 必填 | 说明                 |
| :----- | :--- | :--- | :------------------- |
| value  | T    | 是   | 待转换的任意类型值。 |

**返回值：**

| 类型    | 说明                |
| :------ | :------------------ |
| boolean | value对应的布尔值。 |

**示例：**

```typescript
const bool1 = Boolean.$_invoke("test");  
const bool2 = Boolean.$_invoke(1); 
const bool3 = Boolean.$_invoke(undefined);  
const bool4 = Boolean.$_invoke(null);   
console.info(bool1, bool2, bool3, bool4); // 输出：true, true, false, false
```

## toBoolean

static toBoolean(value: boolean): boolean

直接返回输入的原始布尔值。

**参数：**

| 参数名 | 类型    | 必填 | 说明         |
| :----- | :------ | :--- | :----------- |
| value  | boolean | 是   | 原始布尔值。 |

**返回值：**

| 类型    | 说明              |
| :------ | :---------------- |
| boolean | 输入的value本身。 |

**示例：**

```typescript
const bool1 = Boolean.toBoolean(true);
console.info(bool1); // 输出：true
```

## toBoolean

toBoolean(): boolean

直接返回当前实例的布尔值。

**返回值：**

| 类型    | 说明             |
| :------ | :--------------- |
| boolean | 前实例的布尔值。 |

**示例：**

```typescript
const boo = new Boolean(true);
console.info(boo.toBoolean()); // 输出：true
```

## valueOf

static valueOf(b: boolean): Boolean

返回与原始布尔值b对应的Boolean单例实例。

**参数：**

| 参数名 | 类型    | 必填 | 说明         |
| :----- | :------ | :--- | :----------- |
| b      | boolean | 是   | 原始布尔值。 |

**返回值：**

| 类型    | 说明                                                 |
| :------ | :--------------------------------------------------- |
| Boolean | 若b为true，返回Boolean.TRUE；否则返回Boolean.FALSE。 |

**示例：**

```typescript
const bool1 = Boolean.valueOf(true);
const bool2 = Boolean.valueOf(false);
console.info(bool1);  // 输出：true
console.info(bool2); // 输出：false
```

## valueOf

valueOf(): boolean

获取原始布尔值。

**返回值：**

| 类型    | 说明                   |
| :------ | :--------------------- |
| boolean | 当前对象的原始布尔值。 |

**示例：**

```typescript
const bool = new Boolean(null);
console.info(bool.valueOf()); // 输出：false
```

## equals

equals(other: Any): boolean

判断当前Boolean对象与other是否“值相等”，仅当other为Boolean实例且值相同时返回true。

**参数：**

| 参数名 | 类型 | 必填 | 说明                   |
| :----- | :--- | :--- | :--------------------- |
| other  | Any  | 是   | 待比较的任意类型对象。 |

**返回值：**

| 类型    | 说明                                                         |
| :------ | :----------------------------------------------------------- |
| boolean | 若other是Boolean实例且值与当前对象相同则为true不相同则为false。 |

**示例：**

```typescript
const bool1 = new Boolean(true);
const bool2 = new Boolean(true);
const bool3 = new Boolean(false);
const s = "true"; // 原始布尔值

console.info(bool1.equals(bool2)); // 输出：true（同类型且值相等）
console.info(bool1.equals(bool3)); // 输出：false（值不相等）
console.info(bool1.equals(s));  // 输出：false（类型不同，rawTrue 非 Boolean 实例）
```

## toString

toString(): String

将当前Boolean对象转换为字符串表示，true对应"true"，false对应"false"。

**返回值：**

| 类型   | 说明                    |
| :----- | :---------------------- |
| String | 字符串"true"或"false"。 |

**示例：**

```typescript
const bool1 = new Boolean(true);
const bool2 = new Boolean(false);
console.info(bool1.toString()); // 输出：true
console.info(bool2.toString()); // 输出：false
```

## compareTo

compareTo(other: Boolean): int

按“false < true”的规则比较两个Boolean对象。

**参数**：

| 参数名 | 类型    | 必填 | 说明                  |
| :----- | :------ | :--- | :-------------------- |
| other  | Boolean | 是   | 待比较的Boolean实例。 |

**返回值：**

| 类型 | 说明                                                         |
| :--- | :----------------------------------------------------------- |
| int  | 若当前对象为true且other为false则返回1；若当前对象为false且other为true则返回-1；若两者值相等则返回0。 |

**示例：**

```typescript
const bool1 = Boolean.TRUE;
const bool2 = Boolean.FALSE;

console.info(bool1.compareTo(bool2)); // 输出：1（true > false）
console.info(bool2.compareTo(bool1)); // 输出：-1（false < true）
console.info(bool1.compareTo(bool1)); // 输出：0（值相等）
```

## isTrue

isTrue(): boolean

判断当前Boolean对象的值是否为true。

**返回值：**

| 类型    | 说明                                            |
| :------ | :---------------------------------------------- |
| boolean | 若当前实例的值为true则返回true；否则返回false。 |

**示例：**

```typescript
const bool1 = new Boolean(1);
console.info(bool1.isTrue()); // 输出：true
```

## isFalse

isFlase(): boolean

判断当前Boolean对象的值是否为false。

**返回值：**

| 类型    | 说明                                           |
| :------ | :--------------------------------------------- |
| boolean | 若当前实例值为false则返回true；否则返回false。 |

**示例：**

```typescript
const bool1 = new Boolean(0);
console.info(bool1.isFalse()); // 输出：true
```

## negate

negate(): Boolean

对当前Boolean对象的值进行逻辑非（NOT）运算，返回新的Boolean实例。

**返回值：**

| 类型    | 说明                                                      |
| :------ | :-------------------------------------------------------- |
| Boolean | 若当前值为true则返回Boolean.FALSE；否则返回Boolean.TRUE。 |

**示例：**

```typescript
const bool1 = Boolean.TRUE;
const negated = bool1.negate();
console.info(negated); // 输出：false
```

## and

and(other: Boolean): Boolean

对当前Boolean对象与other进行逻辑与（AND）运算，返回新的Boolean实例（规则：同真为真，否则为假）。

**参数：**

| 参数名 | 类型    | 必填 | 说明                          |
| :----- | :------ | :--- | :---------------------------- |
| other  | Boolean | 是   | 参与运算的另一个Boolean实例。 |

**返回值：**

| 类型    | 说明                        |
| :------ | :-------------------------- |
| Boolean | 运算结果对应的Boolean实例。 |

**示例：**

```typescript
const a = Boolean.TRUE;
const b = Boolean.FALSE;
console.info(a.and(b)); // 输出：false（true && false = false）
console.info(a.and(a)); // 输出：true（true && true = true）
```

## or

or(other: Boolean):Boolean

对当前Boolean对象与other进行逻辑或（OR）运算，返回新的Boolean实例（规则：同假为假，否则为真）。

**参数：**

| 参数名 | 类型    | 必填 | 说明                          |
| :----- | :------ | :--- | :---------------------------- |
| other  | Boolean | 是   | 参与运算的另一个Boolean实例。 |

**返回值：**

| 类型    | 说明                        |
| :------ | :-------------------------- |
| Boolean | 运算结果对应的Boolean实例。 |

**示例：**

```typescript
const a = Boolean.TRUE;
const b = Boolean.FALSE;
console.info(a.or(b)); // 输出：true（true || false = true）
console.info(b.or(b)); // 输出：false（false || false = false）
```

## xor

xor(other: Boolean): Boolean

对当前Boolean对象与other进行逻辑异或（XOR）运算，返回新的Boolean实例（规则：值不同为真，值相同为假）。

**参数：**

| 参数名 | 类型    | 必填 | 说明                          |
| :----- | :------ | :--- | :---------------------------- |
| other  | Boolean | 是   | 参与运算的另一个Boolean实例。 |

**返回值：**

| 类型    | 说明                        |
| :------ | :-------------------------- |
| Boolean | 运算结果对应的Boolean实例。 |

**示例：**

```typescript
const a = Boolean.TRUE;
const b = Boolean.FALSE;
console.info(a.xor(b)); // 输出：true（值不同）
console.info(a.xor(a)); // 输出：false（值相同）
```