# 静态ArkTS语言介绍

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @fanglou-->
<!--Designer: @fanglou-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本教程将指导开发者了解静态ArkTS的核心功能、语法和最佳实践，助力开发者使用ArkTS高效构建高性能的移动应用。

## 基本知识

### 声明

ArkTS通过声明引入变量、常量、类型和函数。

**变量声明**

使用关键字`let`声明的变量可以在程序执行期间具有不同的值。


``` TypeScript
let hi: string = 'hello';
hi = 'hello, world';
```

**常量声明**

使用关键字`const`声明的常量为只读类型，只能被赋值一次。


``` TypeScript
const hello: string = 'hello';
```

对常量重新赋值会造成编译时错误。

**自动类型推断**

如果变量或常量的声明包含初始值，开发者无需显式指定类型，因为ArkTS规范已列举了所有允许自动推断类型的场景。

以下示例中，两条声明语句都是有效的，两个变量都是`string`类型：


``` TypeScript
let hi1: string = 'hello';
let hi2 = 'hello, world';
```

### 类型

ArkTS是静态类型语言，每个声明实体和表达式的类型在编译时已知。类型可由开发者显式指定，也可由编译器自动推断。

ArkTS的类型分为**预定义类型**和**用户定义类型**：

| 预定义类型 | 用户定义类型 |
| ---------- | ------------ |
| `byte`、`short`、`int`、`long`、`float`、`double`、`number` | 类类型 |
| `boolean`、`char` | 接口类型 |
| `string`、`bigint` | 元组类型 |
| `Any`、`Object`、`never`、`void`、`undefined`、`null` | 联合类型 |
| `Array<T>`或`T[]`、`FixedArray<T>`、`ValueArray<T>` | 函数类型、枚举类型、类型参数、字符串字面量类型 |

> **说明：**
>
> `number`是`double`的别名。

**值类型和引用类型**

值类型包括整数类型（`byte`、`short`、`int`、`long`）、浮点类型（`float`、`double`/`number`）、`boolean`类型和`char`类型。值类型的值不与其他值共享状态。

引用类型包括类、接口、数组、元组、函数、联合类型等。多个引用可以指向同一对象，修改引用会影响原始数据。

**类型别名**

某些预定义类型具有别名以提高TS兼容性，推荐使用主要名称：

| 主要名称 | 别名 |
| -------- | ---- |
| `bigint` | `BigInt` |
| `boolean` | `Boolean` |
| `byte` | `Byte` |
| `char` | `Char` |
| `double` | `Double` |
| `float` | `Float` |
| `int` | `Int` |
| `long` | `Long` |
| `number` | `Number` |
| `Object` | `object` |
| `short` | `Short` |
| `string` | `String` |

**数值类型**

数值类型包括整数类型和浮点类型。数值类型层级关系如下：

`byte` < `short` < `int` < `long` < `float` < `double`

其中`byte`是最小类型，`double`是最大类型。在表达式中，较小类型的值会自动向较大类型转换（宽化转换）。`number`是`double`的别名。

数值类型是类类型，都是`Object`的子类型，可以在需要类名的地方使用。

**整数类型**

| 类型 | 取值范围 |
| ---- | -------- |
| `byte` | 有符号8位整数（-128到127） |
| `short` | 有符号16位整数（-32768到32767） |
| `int` | 有符号32位整数（-2147483648到2147483647） |
| `long` | 有符号64位整数 |

整数字面量包括以下类别：

* 十进制整数，由数字序列组成。例如：`0`、`117`、`-345`。
* 十六进制整数，以0x（或0X）开头。例如：`0x1123`、`-0xF1A7`。
* 八进制整数，以0o（或0O）开头。例如：`0o777`。
* 二进制整数，以0b（或0B）开头。例如：`0b11`、`-0b11`。

``` TypeScript
let a: byte = 127;
let b: short = 32000;
let c: int = 100000;
let d: long = 100000000000;
let e: int = 0x1F;
let f: int = 0o77;
let g: int = 0b11;
```

如果二元整数运算中有一个操作数为`long`类型，则另一个较小的类型会宽化为`long`，运算结果为`long`类型。否则，任何非`int`类型的操作数会宽化为`int`，运算结果为`int`类型。

``` TypeScript
let x: int = 10 + 20;
let y: long = 10 + 20;
```

**浮点类型**

| 类型 | 取值范围 |
| ---- | -------- |
| `float` | IEEE 754 32位浮点数 |
| `double`、`number` | IEEE 754 64位浮点数 |

浮点数字面量包括以下部分：

* 十进制整数，支持正负号前缀（前缀为"+"或"-"），默认为正。
* 小数点（"."）。
* 小数部分（由十进制数字字符串表示）。
* 指数部分，以"e"或"E"开头，后跟有符号或无符号整数。

``` TypeScript
let n1 = 3.14;
let n2: double = 3.141592;
let n3: float = 0.5f;
let n4 = 1e2;

function factorial(n: double): double {
  if (n <= 1) {
    return 1;
  }
  return n * (n - 1);
}
factorial(n1)
factorial(n2)
factorial(n3)
factorial(n4)
```

如果二元运算中至少有一个操作数为浮点类型，则运算为浮点运算。若有一个操作数为`double`类型，结果为`double`类型；若均为`float`类型，结果为`float`类型。

**`char`类型**

`char`类型表示单个字符，是值类型。`char` 字面量使用前缀 `c` 加单引号的形式，如 `c'a'` 表示字符 `a` 的 `char` 类型值，`c'\n'` 表示换行字符。

``` TypeScript
let ch: char = c'a';
let ch2: char = c'\n';
```

**`bigint`类型**

`bigint`类型不属于数值类型层级，可表示任意大的整数。`bigint`与数值类型之间不会发生隐式转换，需要使用标准库的`BigInt`类方法来创建`bigint`值。

``` TypeScript
let bigInt: bigint = 999999999999999999999999999999999999999999999999999999999999n;
console.info('bigInt:', bigInt.toString());

let b1: bigint = new BigInt(5)
let b2: bigint = 123n;
```

**`boolean`类型**

`boolean`类型由`true`和`false`两个逻辑值组成。

通常在条件语句中使用`boolean`类型的变量：


``` TypeScript
let isDone: boolean = false;

// ...

if (isDone) {
  console.info('Done!');
}
```

**`string`类型**

`string`类型代表字符序列，可以使用转义字符来表示字符。

字符串字面量由单引号（'）或双引号（"）之间括起来的零个或多个字符组成。字符串字面量还有一种特殊形式，是用反向单引号（\`）括起来的模板字面量。


``` TypeScript
let s1 = 'Hello, world!\n';
let s2 = 'this is a string';
let a = 'Success';
let s3 = `The result is ${a}`;
```

**`void`和`undefined`类型**

类型`void`和`undefined`实际上是同一类型，具有唯一值`undefined`，两个名称可互换使用。

`void`通常用作函数返回类型，表示函数不返回值或只包含不带表达式的`return`语句：

``` TypeScript
function f0(): void {
    // 无return语句
}
function f1(): void {
    return  // return不带表达式
}
function f2(): void {
    return undefined  // OK
}
```

`void`和`undefined`都可以用于泛型类型参数：

``` TypeScript
class Class<T> {
  // ...
}
let instance1: Class<void>;
let instance2: Class<undefined>;
```

**`null`类型**

推荐使用`undefined`代替`null`，因为编译器对`undefined`的处理性能更优（`undefined`是单值类型，运行时开销更低），而`null`主要为TS兼容性保留。

**`Object`类型**

`Object`类型是除`undefined`、`null`、`Any`、类型参数以及包含类型参数的联合类型之外所有类型的超类型。`Object`是`Any`的子类型，这意味着 `Any` 是所有类型的超类型（包括 `Object`），而 `Object` 是除 nullish 类型（`undefined`、`null`、`Any`）和类型参数之外所有类型的超类型。两者属于不同层次的类型层级。所有`Object`的子类型都继承了`Object`类的方法。`object`是`Object`的别名。

数值类型、`boolean`、`char`、`string`、`bigint`都是类类型，都是`Object`的子类型，可以直接赋给`Object`类型的变量：

``` TypeScript
let o1: Object = 'Alice';
let o2: Object = ['a', 'b'];
let o3: Object = 1;
```
 
**`array`类型**

`array`类型，即数组，是由可赋值给数组声明中指定的元素类型的数据组成的对象。

数组可由数组复合字面量赋值。数组复合字面量是用方括号括起来的零个或多个表达式列表，每个表达式为数组中的一个元素。数组的长度由数组中元素的个数确定。数组中第一个元素的索引为0。

以下示例将创建包含三个元素的数组：


``` TypeScript
let names: string[] = ['Alice', 'Bob', 'Carol'];
```

**`enum`类型**

`enum`类型，即枚举类型，是用户定义的值类型，由预先定义的一组命名值组成，其中命名值又称为枚举常量。

使用枚举常量时必须以枚举类型名称为前缀。


``` TypeScript
enum ColorSet { Red, Green, Blue }
let c: ColorSet = ColorSet.Red;
```

常量表达式用于显式设置枚举常量的值。


``` TypeScript
enum ColorSet { White = 0xFF, Grey = 0x7F, Black = 0x00 }
let c: ColorSet = ColorSet.Black;
```

**枚举基类型**

每个枚举都有一个*枚举基类型*（enumeration base type）。基类型可以显式指定或从初始化表达式推断：

- 如果至少一个成员没有初始化表达式，推断基类型为`int`，所有初始化表达式的类型必须可赋值给`int`。
- 如果所有初始化表达式的类型都可赋值给`int`，推断基类型为`int`。
- 如果所有初始化表达式的类型都可赋值给`string`，推断基类型为`string`。


``` TypeScript
enum E1 { A, B }     // OK, 基类型为 int
enum E2 { A = 5, B } // OK, 基类型为 int

enum E3 { A, B = "hello" }     // 编译错误：无法推断基类型
enum E4 { A = 5, B = "hello" } // 编译错误：无法推断基类型
```

枚举基类型可以显式指定为任意数值类型或`string`类型：

``` TypeScript
enum DoubleEnum: double { A = 0.0, B = 1, C = 3.14159 }
enum ByteEnum: byte { A = 0, B = 1, C = 3 }
enum LongEnum: long { A = 0, B = 1, C = 3 }
```

> **说明：** 
>
> 如果基类型为非整数类型（如`double`或`string`），则所有成员必须显式初始化，不支持自动递增。


``` TypeScript
enum Wrong1: double { A, B, C }   // 编译错误：非整数基类型必须显式初始化
enum Wrong2: string { A, B }      // 编译错误：非整数基类型必须显式初始化
enum StringEnum: string { A = "a", B = "b" } // OK
```

**联合类型（Union Type）**

`Union`类型，即联合类型，是由多个类型组合成的引用类型。联合类型包含了变量可能的所有类型。


``` TypeScript
class Cat {
  public name: string = 'cat';
  // ...
}

class Dog {
  public name: string = 'dog';
  // ...
}

class Frog {
  public name: string = 'frog';
  // ...
}

type Animal = Cat | Dog | Frog | int | string | null | undefined;
// Cat、Dog、Frog是一些类型（类或接口）

let animal: Animal = new Cat();
animal = new Frog();
animal = 42;
animal = 'dog';
animal = undefined;
// 可以将类型为联合类型的变量赋值为任何组成类型的有效值
```
 
可以使用不同机制获取联合类型中的特定类型值。

示例：


``` TypeScript
class Cat { sleep () {}; meow () {} }
class Dog { sleep () {}; bark () {} }
class Frog { sleep () {}; leap () {} }

type Animal = Cat | Dog | Frog;

function foo(animal: Animal) {
  if (animal instanceof Frog) {  // 判断animal是否是Frog类型
    animal.leap();  // animal在这里是Frog类型
  }
  animal.sleep(); // Animal具有sleep方法
}
```

**类型别名（Type Aliases）**

`Aliases`类型为匿名类型（如数组、函数、对象字面量或联合类型）提供名称，或为已定义的类型提供替代名称。


``` TypeScript

// 函数类型
type Handler = (s: string, no: int) => string;
const repeatString: Handler = (str, times) => {
  return str.repeat(times);
};
console.info(repeatString('abc', 3)); // 'abcabcabc'
// ...
// 泛型函数类型
type Predicate<T> = (x: T) => boolean;
const isEven: Predicate<int> = (num) => num % 2 === 0;

// 可为空的对象类型
type NullableObject = Object | null;

class Cat {
}

let animalData: NullableObject = new Cat();
let emptyData: NullableObject = null;
```

### 运算符

**赋值运算符**

赋值运算符`=`，使用方式如`x=y`。

复合赋值运算符将赋值与运算符组合在一起，例如：`a += b` 等价于 `a = a + b`，

其中的 `+=` 即为复合赋值运算符

复合赋值运算符包括：`+=`、`-=`、`*=`、`/=`、`%=`、`<<=`、`>>=`、`>>>=`、`&=`、`|=`、`^=`。

**比较运算符**

| 运算符| 说明                                                 |
| -------- | ------------------------------------------------------------ |
| `===`    | 如果两个操作数严格相等，则返回true。 |
| `!==`    | 如果两个操作数严格不相等，则返回true。 |
| `==`     | 如果两个操作数相等，则返回true。 |
| `!=`     | 如果两个操作数不相等，则返回true。    |
| `>`      | 如果左操作数大于右操作数，则返回true。 |
| `>=`     | 如果左操作数大于或等于右操作数，则返回true。 |
| `<`      | 如果左操作数小于右操作数，则返回true。    |
| `<=`     | 如果左操作数小于或等于右操作数，则返回true。 |

`===`与`==`的区别：对`null`和`undefined`的比较结果不同。

``` TypeScript
console.info(String(null == undefined)); // true
console.info(String(null === undefined)); // false
```


**算术运算符**

一元运算符包括：`-`、`+`、`--`、`++`。

二元运算符列举如下：

| 运算符| 说明             |
| -------- | ------------------------ |
| `+`      | 加法                |
| `-`      | 减法             |
| `*`      | 乘法          |
| `/`      | 除法                |
| `%`      | 除法后余数|

**位运算符**

| 运算符 | 说明                                                 |
| --------- | ------------------------------------------------------------ |
| `a & b`   | 按位与：如果两个操作数的对应位都为1，则将这个位设置为1，否则设置为0。|
| `a \| b`  | 按位或：如果两个操作数的相应位中至少有一个为1，则将这个位设置为1，否则设置为0。|
| `a ^ b`   | 按位异或：如果两个操作数的对应位不同，则将这个位设置为1，否则设置为0。|
| `~ a`     | 按位非：反转操作数的位。               |
| `a << b`  | 左移：将a的二进制表示向左移b位。|
| `a >> b`  | 算术右移：将a的二进制表示向右移b位，带符号扩展。|
| `a >>> b` | 逻辑右移：将a的二进制表示向右移b位，左边补0。|

**逻辑运算符**

| 运算符  | 说明|
| ---------- | ----------- |
| `a && b`   | 逻辑与 |
| `a \|\| b` | 逻辑或 |
| `! a`      | 逻辑非 |

**`instanceof`运算符**

`instanceof`运算符用于在运行时检查一个对象是否是指定类或其子类的实例。

示例如下：

```typescript
obj instanceof className;
```

返回值类型为`boolean`。

如果`obj`是`className`类或其子类的实例，则返回值为`true`；否则，返回值为`false`。

示例：


``` TypeScript
class Person {}
const person = new Person();
if ((person instanceof Person)) {
  console.info('true'); // true
}

class Animal {}
class Bird extends Animal {}
const bird = new Bird();
if (bird instanceof Animal) {
  console.info('true'); // true
}
```

### 语句

**`if`语句**

`if`语句用于需要根据逻辑条件执行不同语句的场景。当逻辑条件为真时，执行对应的一组语句，否则执行另一组语句（如果有的话）。

`else`部分也可以包含`if`语句。

`if`语句如下所示：

```typescript
if (condition1) {
  // 语句1
} else if (condition2) {
  // 语句2
} else {
  // else语句
}
```

条件表达式期望`boolean`类型。虽然ArkTS允许部分非`boolean`类型值作为条件（会进行隐式转换），但推荐始终使用显式`boolean`表达式以保持代码的静态类型清晰性。示例：推荐使用`if (s1.length != 0)`而非 `if (s1)`。


``` TypeScript
let s1 = 'Hello';
if (s1) {
  console.info(s1); // 打印"Hello"
}

let s2 = 'World';
if (s2.length != 0) {
  console.info(s2); // 打印"World"
}
```

**`switch`语句**

使用`switch`语句执行与`switch`表达式值匹配的代码块。

`switch`语句如下所示：


``` TypeScript
switch (expression) {
  case label1: // 如果label1匹配，则执行
    // ...
    // 语句1
    // ...
    break; // 可省略
  case label2:
  case label3: // 如果label2或label3匹配，则执行
    // ...
    // 语句23
    // ...
    break; // 可省略
  default:
  // 默认语句
}
```

如果`switch`表达式的值等于某个label的值，则执行相应的语句。

如果没有任何一个label值与表达式值相匹配，并且`switch`具有`default`子句，那么程序会执行`default`子句对应的代码块。

`break`语句（可选的）允许跳出`switch`语句并继续执行`switch`语句之后的语句。

如果没有`break`语句，则执行`switch`中的下一个label对应的代码块。

**条件表达式**

条件表达式根据第一个表达式的布尔值来返回其他两个表达式之一的结果。

示例如下：

```typescript
condition ? expression1 : expression2;
```

如果`condition`的值为真值（转换后为`true`的值），则使用`expression1`作为该表达式的结果；否则，使用`expression2`作为该表达式的结果。

示例：


``` TypeScript
let message = Math.random() > 0.5 ? 'Valid' : 'Failed';
```

`condition`如果是非bool值则会进行隐式转换。

示例：


``` TypeScript
console.info('a' ? 'true' : 'false'); // true
console.info('' ? 'true' : 'false'); // false
console.info(1 ? 'true' : 'false'); // true
console.info(0 ? 'true' : 'false'); // false
console.info(null ? 'true' : 'false'); // false
console.info(undefined ? 'true' : 'false'); // false
```

**`for`语句**

`for`语句会被重复执行，直到循环退出语句值为`false`。

`for`语句如下所示：

```typescript
for ([init]; [condition]; [update]) {
  statements;
}
```

`for`语句的执行流程如下：

1.  执行`init`表达式（如有）。此表达式通常初始化一个或多个循环计数器。

2. 计算`condition`。如果它为真值（转换后为`true`的值），则执行循环主体的语句。如果它为假值（转换后为`false`的值），则`for`循环终止。

3. 执行循环主体的语句。

4. 如果有`update`表达式，则执行该表达式。

5. 返回步骤2。

示例：


``` TypeScript
let sum = 0;
for (let i = 0; i < 10; i += 2) {
  sum += i;
}
```

**`for-of`语句**

使用`for-of`语句可遍历数组、Set、Map、字符串等可迭代的类型。示例如下：

```typescript
for (forVar of IterableExpression) {
  // 处理forVar。
}
```

示例：


``` TypeScript
for (let ch of 'a string object') {
  console.info(ch);
  // ...
}
```

**`while`语句**

只要`condition`为真值（转换后为`true`的值），`while`语句就会执行`statements`语句。示例如下：

```typescript
while (condition) {
  statements;
}
```

示例：


``` TypeScript
let n = 0;
let x = 0;
while (n < 3) {
  n++;
  x += n;
}
```

**`do-while`语句**

如果`condition`的值为真值（转换后为`true`的值），那么`statements`语句会重复执行。示例如下：

```typescript
do {
  statements;
} while (condition)
```

示例：


``` TypeScript
let i = 0;
do {
  i += 1;
} while (i < 10)
```

**`break`语句**

使用`break`语句可以终止循环语句或`switch`。

示例：


``` TypeScript
let x = 0;
while (true) {
  x++;
  if (x > 5) {
    break;
  }
}
```

如果`break`语句后带有标识符，则将控制流转移到该标识符所包含的语句块之外。

示例：


``` TypeScript
let x = 1;
label: while (true) {
  switch (x) {
    case 1:
      // statements
      break label; // 中断while语句
  }
}
```

**`continue`语句**

`continue`语句会停止当前循环迭代的执行，并将控制传递给下一次迭代。

示例：


``` TypeScript
let sum = 0;
for (let x = 0; x < 100; x++) {
  if (x % 2 == 0) {
    continue;
  }
  sum += x;
}
```
 
**`throw`和`try`语句**

`throw`语句用于抛出异常或错误：


``` TypeScript
throw new Error('this error')
```

`try`语句用于捕获和处理异常或错误：


``` TypeScript
try {
  // ...
} catch (e) {
  // 异常处理
  // ...
}
```

下面的示例中`throw`和`try`语句用于处理除数为0的错误：


``` TypeScript
class ZeroDivisor extends Error {}

function divide (a: double, b: double): double {
  if (b == 0) {
    throw new ZeroDivisor();
  }
  return a / b;
}

function process(a: double, b: double) {
  try {
    let res = divide(a, b);
    console.info('result: ' + res);
  } catch (x) {
    console.error('some error');
  }
}
```

支持`finally`语句：


``` TypeScript
function processData(s: string) {
  let error: Error | null = null;

  try {
    console.info('Data processed: ' + s);
    // ...
    // 可能发生异常的语句
    // ...
  } catch (e) {
    error = e as Error;
    // ...
    // 异常处理
    // ...
  } finally {
    // 无论是否发生异常都会执行的代码
    if (error != null) {
      console.error(`Error caught: input='${s}', message='${error.message}'`);
    }
  }
}
```

## 函数

### 函数声明

函数声明引入一个函数，包含其名称、参数列表、返回类型和函数体。

以下示例是一个简单的函数和它的语法语义说明：

1.参数类型标注：`x: string, y: string`显式声明参数类型为字符串类型。

2.返回值类型：`: string`指定函数返回值为字符串类型。


``` TypeScript
function add(x: string, y: string): string {
  let z: string = `${x} ${y}`;
  return z;
}
```

在函数声明中，必须为每个参数标记类型。如果参数为可选参数，那么允许在调用函数时省略该参数。函数的最后一个参数可以是rest参数。

### 可选参数

可选参数的格式可为`name?: Type`。


``` TypeScript
function hello(name?: string) {
  if (name == undefined) {
    console.info('Hello!');
  } else {
    console.info(`Hello, ${name}!`);
  }
}
```

可选参数的另一种形式为设置的参数默认值。如果在函数调用中这个参数被省略了，则会使用此参数的默认值作为实参。


``` TypeScript
function multiply(n: int, coeff: int = 2): int {
  return n * coeff;
}
  // ...
  multiply(2);  // 返回2*2
  multiply(2, 3); // 返回2*3
```

### rest参数

函数的最后一个参数可以是rest参数，格式为`...restName: Type[]`。rest参数允许函数接收一个不定长数组，用于处理不定数量的参数输入。


``` TypeScript
function sum(...numbers: int[]): int {
  let res = 0;
  for (let n of numbers) {
    res += n;
  }
  return res;
}
  // ...
  sum(); // 返回0
  sum(1, 2, 3); // 返回6
```

### 返回类型

如果可以从函数体内推断出函数返回类型，则可在函数声明中省略标注返回类型。


``` TypeScript
// 显式指定返回类型
function foo(): string { return 'foo'; }

// 推断返回类型为string
function goo() { return 'goo'; }
```

不需要返回值的函数的返回类型可以显式指定为`void`或省略标注。这类函数不需要返回语句。

以下示例中两种函数声明方式都是有效的：


``` TypeScript
function hi1() { console.info('hi'); }
function hi2(): void { console.info('hi'); }
```

### 函数的作用域

函数中定义的变量和其他实例仅可以在函数内部访问，不能从外部访问。

如果函数中定义的变量与外部作用域中已有实例同名，则函数内的局部变量定义将覆盖外部定义。


``` TypeScript
let outerVar = 'I am outer ';

function func() {
  let outerVar = 'I am inside';
  console.info(outerVar); // 输出: I am inside
}
  // ...
  func();
```

### 函数调用

调用函数以执行其函数体，实参值会赋值给函数的形参。

如果函数定义如下：


``` TypeScript
function join(x: string, y: string): string {
  let z: string = `${x} ${y}`;
  return z;
}
let x = join('hello', 'world');
console.info(x); // 输出: hello world
```

### 函数类型

函数类型通常用于定义回调函数：


``` TypeScript
type trigFunc = (x: double) => double // 这是一个函数类型

function doAction(f: trigFunc) {
  f(3.141592653589); // 调用函数
}

doAction(Math.sin); // 将函数作为参数传入
```

### 箭头函数（又名Lambda函数）

函数可以定义为箭头函数，例如：


``` TypeScript
let sum = (x: int, y: int): int => {
  return x + y;
}
```

箭头函数的返回类型可以省略，此时返回类型从函数体推断。

表达式可以指定为箭头函数，使表达更简短，因此以下两种表达方式是等价的：


``` TypeScript
let sum1 = (x: int, y: int) => { return x + y; }
let sum2 = (x: int, y: int) => x + y;
```

### 闭包

闭包是由函数及声明该函数的环境组合而成的。该环境包含了这个闭包创建时作用域内的任何局部变量。

在下例中，`f`函数返回了一个闭包，它捕获了`count`变量，每次调用`z`，`count`的值会被保留并递增。


``` TypeScript
function f(): () => int {
  let count = 0;
  let g = (): int => { count++; return count; };
  return g;
}
  // ...
  let z = f();
  z(); // 返回：1
  z(); // 返回：2
```

### 函数重载

重载允许通过同一名称调用多个具有不同签名的函数。在同一声明作用域中声明两个或多个同名函数时，它们隐式重载。调用时，根据实参类型确定具体调用的函数。

``` TypeScript
function foo(p: int) {}
function foo(p: string) {}

foo(5)   // 调用 foo(p: int)
foo("5") // 调用 foo(p: string)
```

不允许重载函数有相同的参数列表，否则将导致编译错误。

## 类

类声明引入一个新类型，并定义其字段、方法和构造函数。

在以下示例中，定义了`Person`类，该类具有字段`name`和`surname`、构造函数和方法`fullName`：


``` TypeScript
class Person {
  public name: string = '';
  public surname: string = '';
  constructor (n: string, sn: string) {
    this.name = n;
    this.surname = sn;
  }
  fullName(): string {
    return this.name + ' ' + this.surname;
  }
}
```

定义类后，可以使用关键字`new`创建实例：


``` TypeScript
let p = new Person('John', 'Smith');
console.info(p.fullName());
```

或者，可以使用对象字面量创建实例：


``` TypeScript
class Point {
  public x: int = 0;
  public y: int = 0;
}
let p: Point = {x: 42, y: 42};
```

### 字段

字段是直接在类中声明的某种类型的变量。

类可以具有实例字段或者静态字段。

**实例字段**

实例字段存在于类的每个实例上。每个实例都有自己的实例字段集合。

要访问实例字段，需要使用类的实例。


``` TypeScript
class Person1 {
  public name: string = '';
  public age: int = 0;
  constructor(n: string, a: int) {
    this.name = n;
    this.age = a;
  }

  getName(): string {
    return this.name;
  }
}
  // ...
  let p1 = new Person1('Alice', 25);
  p1.name; // Alice
  let p2 = new Person1('Bob', 28);
  p2.getName(); // Bob
```

**静态字段**

使用关键字`static`将字段声明为静态。静态字段属于类本身，类的所有实例共享一个静态字段。

要访问静态字段，需要使用类名：


``` TypeScript
class Person2 {
  public static numberOfPersons = 0;
  constructor() {
    // ...
    Person2.numberOfPersons++;
    // ...
  }
}

Person2.numberOfPersons;
```

**字段初始化**

为了减少运行时错误并提升执行性能，ArkTS要求所有字段在声明时或构造函数中显式初始化，与标准TS的`strictPropertyInitialization`模式相同。

字段初始化有两种合法方式：  

1. 声明时初始化：`public name: string = ''`  

2. 构造函数中初始化：

   ```typescript
   class C {
     field: int;
     constructor(p: int) {
       this.field = p;
     }
   }
   ```

两种方式均满足ArkTS的字段初始化要求。仅当字段既无声明时初始值又无构造函数赋值时，才会导致编译错误。

以下代码在ArkTS中不合法。

```typescript
class Person {
  name: string; // undefined
  
  setName(n: string): void {
    this.name = n;
  }
  
  getName(): string {
    // 开发者使用"string"作为返回类型，这隐藏了name可能为"undefined"的事实。
    // 更合适的做法是将返回类型标注为"string | undefined"，以告诉开发者这个API所有可能的返回值。
    return this.name;
  }
}

let jack = new Person();
// 假设代码中没有对name赋值，即没有调用"jack.setName('Jack')"
jack.getName().length; // 运行时异常：name is undefined
```

正确的ArkTS写法如下。


``` TypeScript
class Person3 {
  public name: string = '';

  setName(n: string): void {
    this.name = n;
  }

  // 类型为'string'，不可能为"null"或者"undefined"
  getName(): string {
    return this.name;
  }
}


let jack = new Person3();
// 假设代码中没有对name赋值，即没有调用"jack.setName('Jack')"
jack.getName().length; // 0, 没有运行时异常
```

接下来的代码示例展示了当`name`的值可能为`undefined`时，如何正确编写代码。

```typescript
class Person {
  name?: string; // 可能为`undefined`

  setName(n: string): void {
    this.name = n;
  }

  // 编译时错误：name可以是"undefined"，所以这个API的返回值类型不能仅定义为string类型
  getNameWrong(): string {
    return this.name;
  }

  getName(): string | undefined { // 返回类型匹配name的类型
    return this.name;
  }
}

let jack = new Person();
// 假设代码中没有对name赋值，即没有调用"jack.setName('Jack')"

// 编译时错误：编译器认为下一行代码有可能会访问undefined的属性，报错
jack.getName().length;  // 编译失败

jack.getName()?.length; // 编译成功，没有运行时错误
```

**getter和setter**

setter和getter可用于提供对类属性的受控访问。

在以下示例中，setter用于禁止将`_age`属性设置为无效值：


``` TypeScript
class Person4 {
  public name: string = '';
  private _age: int = 0;
  get age(): int { return this._age; }
  set age(x: int) {
    if (x < 0) {
      throw Error('Invalid age argument');
    }
    this._age = x;
  }
}
  // ...
  let p = new Person4();
  p.age; // 输出0
  p.age = -42; // 设置无效age值会抛出错误
```

在类中可以定义getter或者setter。

### 方法

方法属于类。类可以定义实例方法或者静态方法。静态方法属于类本身，只能访问静态字段。而实例方法既可以访问静态字段，也可以访问实例字段，包括类的私有字段。

**实例方法**

以下示例说明了实例方法的工作原理。

`calculateArea`方法计算矩形面积：


``` TypeScript
class RectangleSize {
  private height: int = 0;
  private width: int = 0;
  constructor(height: int, width: int) {
    this.height = height;
    this.width = width;
  }
  calculateArea(): int {
    return this.height * this.width;
  }
}
```

必须通过类的实例调用实例方法：


``` TypeScript
let square = new RectangleSize(10, 10);
square.calculateArea(); // 输出：100
```

**静态方法**

使用关键字 `static` 声明静态方法。静态方法属于类，只能访问静态字段。

静态方法定义了类作为一个整体的公共行为。

必须通过类名调用静态方法：


``` TypeScript
class C2 {
  public static staticMethod(): string {
    return 'this is a static method.';
  }
}
  // ...
  console.info(C2.staticMethod());
```

**继承**

一个类可以继承另一个类（称为基类），并使用以下语法实现多个接口：

```typescript
class [extends BaseClassName] [implements listOfInterfaces] {
  // ...
}
```

继承类继承基类的字段和方法，但不继承构造函数。继承类可以新增定义字段和方法，也可以覆盖其基类定义的方法。

基类也称为“父类”或“超类”。继承类也称为“派生类”或“子类”。

示例：


``` TypeScript
class Person5 {
  public name: string = '';
  public _age = 0;
  get age(): int {
    return this._age;
  }
}
class Employee extends Person5 {
  public salary: int = 0;
  calculateTaxes(): double {
    return this.salary * 0.42;
  }
}
```

包含`implements`子句的类必须实现列出的接口中定义的所有方法，但使用默认实现定义的方法除外。


``` TypeScript
interface DateInterface {
  now(): string;
}
class MyDate implements DateInterface {
  now(): string {
    // 在此实现
    return 'now';
  }
}
```

**父类访问**

关键字`super`可用于访问父类的方法和构造函数。在实现子类功能时，可以通过该关键字从父类中获取所需接口：


``` TypeScript
class RectangleSize {
  protected height: int = 0;
  protected width: int = 0;

  constructor (h: int, w: int) {
    this.height = h;
    this.width = w;
  }

  draw() {
    /* 绘制边界 */
  }
}
class FilledRectangle extends RectangleSize {
  public color = '';
  constructor (h: int, w: int, c: string) {
    super(h, w); // 父类构造函数的调用
    this.color = c;
  }

  draw() {
    super.draw(); // 父类方法的调用
    // 填充矩形
  }
}
```

**方法重写**

子类可以重写其父类中定义的方法的实现。重写的方法必须具有与原始方法相同的参数类型和相同或派生的返回类型。


``` TypeScript
class RectangleSize {
  // ...
  area(): int {
    // 实现
    return 0;
  }
}
class Square extends RectangleSize {
  private side: int = 0;
  area(): int {
    return this.side * this.side;
  }
}
```

**方法重载**

类或接口中的两个或多个同名方法，如果同为`static`或同为实例方法，则隐式重载。调用时根据实参类型确定具体调用的方法。


``` TypeScript
class C {
  foo(p: int) {}
  foo(p: string) {}
}

let c = new C()
c.foo(5)   // 调用 foo(p: int)
c.foo("5") // 调用 foo(p: string)
```

不允许重载方法有相同的参数列表，否则将导致编译错误。

### 构造函数

类声明可以包含用于初始化对象状态的构造函数。

构造函数定义如下：

```typescript
constructor ([parameters]) {
  // ...
}
```

如果未定义构造函数，则会自动创建具有空参数列表的默认构造函数，例如：


``` TypeScript
class Point {
  public x: int = 0;
  public y: int = 0;
}
let p = new Point();
```

在这种情况下，默认构造函数使用字段类型的默认值初始化实例中的字段。

**派生类的构造函数**

构造函数函数体的第一条语句可以使用关键字`super`来显式调用直接父类的构造函数。


``` TypeScript
class RectangleSize {
  constructor(width: int, height: int) {
    // ...
  }
}
class Square extends RectangleSize {
  constructor(side: int) {
    super(side, side);
  }
}
```

**构造函数重载**

同一类中的两个或多个无名构造函数隐式重载。调用时根据实参类型确定具体调用的构造函数：

``` TypeScript
class BigFloat {
  constructor(n: double) {
    // body1
  }
  constructor(s: string) {
    // body2
  }
}

new BigFloat(1)       // 使用第一个构造函数
new BigFloat("3.14")  // 使用第二个构造函数
```

不允许重载构造函数有相同的参数列表，否则将导致编译错误。

### 可见性修饰符

类的方法和属性都可以使用可见性修饰符。

可见性修饰符包括：`private`、`protected`和`public`。默认可见性为`public`。

**Public（公有）**

`public`修饰的类成员（字段、方法、构造函数）在程序的任何可访问该类的地方都是可见的。

**Private（私有）**

`private`修饰的成员不能在声明该成员的类之外访问，例如：

```typescript
class C {
  public x: string = '';
  private y: string = '';
  set_y (new_y: string) {
    this.y = new_y; // OK，因为y在类本身中可以访问
  }
}
let c = new C();
c.x = 'a'; // OK，该字段是公有的
c.y = 'b'; // 编译时错误：'y'不可见
```

**Protected（受保护）**

`protected`修饰符的作用与`private`修饰符非常相似，不同点是`protected`修饰的成员允许在派生类中访问，例如：

```typescript
class Base {
  protected x: string = '';
  private y: string = '';
}
class Derived extends Base {
  foo() {
    this.x = 'a'; // OK，访问受保护成员
    this.y = 'b'; // 编译时错误，'y'不可见，因为它是私有的
  }
}
```

### 对象字面量

对象字面量是一个表达式，可用于创建类实例并提供一些初始值。它在某些情况下更方便，可以用来代替`new`表达式。

对象字面量的表示方式是：封闭在花括号对({})中的'属性名：值'的列表。


``` TypeScript
class C {
  public n: int = 0;
  public s: string = '';
}

let c: C = {n: 42, s: 'foo'};
```

ArkTS是静态类型语言，如上述示例所示，对象字面量只能在可以推导出该字面量类型的上下文中使用。其他正确的例子如下所示：


``` TypeScript
class C1 {
  public n: int = 0;
  public s: string = '';
}

function foo(c1: C1) {}

let c1: C1;

c1 = {n: 42, s: 'foo'};  // 使用变量的类型
foo({n: 42, s: 'foo'}); // 使用参数的类型

function bar(): C1 {
  return {n: 42, s: 'foo'}; // 使用返回类型
}
```

也可以在数组元素类型或类字段类型中使用：


``` TypeScript
class C {
  public n: int = 0;
  public s: string = '';
}
let cc: C[] = [{n: 1, s: 'a'}, {n: 2, s: 'b'}];
```

**`Record`类型的对象字面量**

泛型`Record<K, V>`用于将类型（键类型）的属性映射到另一个类型（值类型）。常用对象字面量来初始化该类型的值：


``` TypeScript
let map: Record<string, int> = {
  'John': 25,
  'Mary': 21;
};
  // ...
  map['John']; // 25
```

类型`K`可以是字符串类型或数值类型(不包括bigint)，而`V`可以是任何类型。


``` TypeScript
interface PersonInfo {
  age: int;
  salary: int;
}
let map: Record<string, PersonInfo> = {
  'John': { age: 25, salary: 10},
  'Mary': { age: 21, salary: 20}
}
```

### 抽象类 

带有`abstract`修饰符的类称为抽象类。抽象类可用于表示一组更具体的概念所共有的概念。

尝试创建抽象类的实例会导致编译错误：

```typescript
abstract class X {
  field: int;
  constructor(p: int) {
    this.field = p; 
  }
}

let x = new X(666)  // 编译时错误：不能创建抽象类的具体实例
```

抽象类的子类可以是抽象类也可以是非抽象类。抽象父类的非抽象子类可以实例化。因此，执行抽象类的构造函数和该类非静态字段的字段初始化器：


``` TypeScript
abstract class Base {
  private field: int;
  constructor(p: int) {
    this.field = p;
  }
}

class Derived extends Base {
  constructor(p: int) {
    super(p);
  }
}

let x = new Derived(666);
```

**抽象方法**

带有`abstract`修饰符的方法称为抽象方法，抽象方法可以被声明但不能被实现。

只有抽象类内才能有抽象方法，如果非抽象类具有抽象方法，则会发生编译时错误：

```typescript
class Y {
  abstract method(p: string)  // 编译时错误：抽象方法只能在抽象类内
}
```

## 接口

接口声明引入新类型。接口是定义代码协定的常见方式。

任何类的实例，只要实现了特定接口，即可通过该接口实现多态。

接口通常包含属性和方法的声明。

示例：


``` TypeScript
interface Style {
  color: string; // 属性
}
interface AreaSize {
  calculateAreaSize(): int; // 方法的声明
  someMethod(): void;     // 方法的声明
}
```

实现接口的类示例：


``` TypeScript
// 接口：
interface AreaSize {
  calculateAreaSize(): int; // 方法的声明
  someMethod(): void;     // 方法的声明
}

// 实现：
class RectangleSize implements AreaSize {
  private width: int = 0;
  private height: int = 0;
  someMethod(): void {
    console.info('someMethod called');
  }
  calculateAreaSize(): int {
    this.someMethod(); // 调用另一个方法并返回结果
    return this.width * this.height;
  }
}
```

### 接口属性

接口属性可以是字段、getter、setter或getter和setter组合的形式。

属性字段只是getter/setter对的便捷写法。以下表达方式是等价的：


``` TypeScript
interface Style {
  color: string;
}
```


``` TypeScript
interface Style {
  get color(): string;
  set color(x: string);
}
```

实现接口的类也可以使用以下两种方式：


``` TypeScript
interface Style {
  color: string;
}

class StyledRectangle implements Style {
  public color: string = '';
}
```


``` TypeScript
interface Style {
  color: string;
}

class StyledRectangle implements Style {
  private _color: string = '';
  get color(): string { return this._color; }
  set color(x: string) { this._color = x; }
}
```
 
### 接口继承

接口可以继承其他接口，示例如下：


``` TypeScript
interface Style {
  color: string;
}

interface ExtendedStyle extends Style {
  width: int;
}
```

继承接口包含被继承接口的所有属性和方法，还可以添加自己的属性和方法。


### 抽象类和接口

抽象类与接口都无法实例化。抽象类是类的抽象，抽象类用来捕捉子类的通用特性，接口是行为的抽象。在ArkTS语法中抽象类与接口的区别如下：

* 一个类只能继承一个抽象类，而一个类可以实现一个或多个接口；
  ```typescript
  // Bird类继承Animal抽象类并实现多个接口CanFly、CanSwim
  class Bird extends Animal implements CanFly, CanSwim {
    // ...  
  }
  ```
* 接口中不能含有静态代码块以及静态方法，而抽象类可以有静态代码块和静态方法；
  ```typescript
  interface MyInterface {
      // 错误：接口中不能包含静态成员
      static staticMethod(): void;

      // 错误：接口中不能包含静态代码块
      static { console.info('static'); };
  }

  abstract class MyAbstractClass {
      // 正确：抽象类可以有静态方法
      static staticMethod(): void { console.info('static'); }

      // 正确：抽象类可以有静态代码块
      static { console.info('static initialization block'); }
  }
  ```
* 抽象类里面可以有方法的实现，但是接口没有方法的实现，是完全抽象的；
  ```typescript
  abstract class MyAbstractClass {
    // 正确：抽象类里面可以有方法的实现
    func(): void { console.info('func'); }
  }
  interface MyInterface {
    // 错误：接口没有方法的实现，是完全抽象的
    func(): void { console.info('func'); }
  }
  ```
* 抽象类可以有构造函数，而接口不能有构造函数。
  ```typescript
  abstract class MyAbstractClass {
    constructor(){}  // 正确：抽象类可以有构造函数
  }
  // interface MyInterface {
  //   constructor(); // 错误：接口中不能有构造函数
  // }
  ```

## 泛型类型和函数

泛型类型和函数使代码能够以类型安全的方式操作多种数据类型，而无需为每种类型编写重复的逻辑。

### 泛型类和接口

类和接口可以定义为泛型，将参数添加到类型定义中。如以下示例中的类型参数`Element`：


``` TypeScript
class CustomStack<Element> {
  public push(e: Element):void {
    // ...
  }
}
```

要使用类型CustomStack，必须为每个类型参数指定类型实参：


``` TypeScript
let s = new CustomStack<string>();
s.push('hello');
```

编译器在使用泛型类型和函数时会确保类型安全。参见以下示例：

```typescript
let s = new CustomStack<string>();
s.push(55); // 将会产生编译时错误
```

### 泛型约束

泛型类型的类型参数可以被限制只能取某些特定的值。例如，`MyHashMap<Key, Value>`这个类中的`Key`类型参数必须具有`hash`方法。


``` TypeScript
interface Hashable {
  hash(): int;
}
class MyHashMap<Key extends Hashable, Value> {
  public set(k: Key, v: Value) {
    let h = k.hash();
    // ...
  }
}
```

在上面的例子中，`Key`类型扩展了`Hashable`，`Hashable`接口的所有方法都可以为key调用。

### 泛型函数

使用泛型函数可编写更通用的代码。比如返回数组最后一个元素的函数：


``` TypeScript
function last(x: int[]): int {
  return x[x.length - 1];
}
  // ...
  last([1, 2, 3]); // 3
```

如果需要为任何数组定义相同的函数，使用类型参数将该函数定义为泛型：


``` TypeScript
function last1<T>(x: T[]): T {
  return x[x.length - 1];
}
```

现在，该函数可以与任何数组一起使用。

在函数调用中，类型实参可以显式或隐式设置：

```typescript
// 显式设置的类型实参
let res1: string = last<string>(['aa', 'bb']);
let res2: int = last<int>([1, 2, 3]);

// 隐式设置的类型实参
// 编译器根据调用参数的类型来确定类型实参
let res3: int = last([1, 2, 3]);
```

### 泛型默认值

泛型类型的类型参数可以设置默认值，这样无需指定实际类型实参，直接使用泛型类型名称即可。以下示例展示了类和函数的这一特性。


``` TypeScript
class SomeType {}
interface Interface <T1 = SomeType> { }
class Base <T2 = SomeType> { }
class Derived1 extends Base implements Interface { }
// Derived1在语义上等价于Derived2
class Derived2 extends Base<SomeType> implements Interface<SomeType> { }

function foo<T = int>(): void {
  // ...
}
foo();
// 此函数在语义上等价于下面的调用
foo<int>();
```

## 空安全

默认情况下，ArkTS中的所有类型都不允许为空，这类似于TypeScript的(`strictNullChecks`)模式，但规则更严格。

在下面的示例中，所有行都会导致编译时错误：

```typescript
let x: int = null;    // 编译时错误
let y: string = null;    // 编译时错误
let z: int[] = null;  // 编译时错误
```

可以为空值的变量定义为联合类型`T | null`。


``` TypeScript
let x: int | null = null;
x = 1;    // ok
x = null; // ok
if (x != null) {
  // ...
}
```

### 非空断言运算符

后缀运算符`!`可用于断言其操作数为非空。

当应用于可空类型的值时，编译时类型会变为非空类型。例如，类型从`T | null`变为`T`：

```typescript
class A {
  value: int = 0;
}

function foo(a: A | null) {
  a.value;   // 编译时错误：无法访问可空值的属性
  a!.value;  // 编译通过，如果运行时a的值非空，可以访问到a的属性；如果运行时a的值为空，则发生运行时异常
}
```

### 空值合并运算符

空值合并二元运算符`??`用于检查左侧表达式的求值是否等于`null`或者`undefined`。如果是，则表达式的结果为右侧表达式；否则，结果为左侧表达式。

换句话说，`a ?? b`等价于三元运算符`(a != null && a != undefined) ? a : b`。

在以下示例中，`getNick`方法返回已设置的昵称。如果未设置，则返回空字符串。


``` TypeScript
class Person {
  // ...
  public nick: string | null = null;
  getNick(): string {
    return this.nick ?? '';
  }
}
```

### 可选链

访问对象属性时，如果属性是`undefined`或`null`，可选链运算符返回`undefined`。


``` TypeScript
class Person {
  public nick: string | null = null;
  public spouse?: Person;

  setSpouse(spouse: Person): void {
    this.spouse = spouse;
  }

  getSpouseNick(): string | null | undefined {
    return this.spouse?.nick;
  }

  constructor(nick: string) {
    this.nick = nick;
    this.spouse = undefined;
  }
}
```

> **说明**：
>
>`getSpouseNick`的返回类型必须为`string | null | undefined`，因为该方法在某些情况下会返回`null`或`undefined`。
>
> 可选链可以任意长，可以包含任意数量的`?.`运算符。
>
> 在以下示例中，如果`Person`实例的`spouse`属性不为空，并且`spouse`的`nick`属性也不为空时，输出`spouse.nick`。否则，输出`undefined`。


``` TypeScript
class Person {
  public nick: string | null = null;
  public spouse?: Person;

  constructor(nick: string) {
    this.nick = nick;
    this.spouse = undefined;
  }
}

let p: Person = new Person('Alice');
p.spouse?.nick; // undefined
```

## 模块

程序可划分为多组编译单元或模块。

每个模块都有其自己的作用域，即在模块中创建的任何声明（变量、函数、类等）在该模块之外都不可见，除非它们被显式导出。

与此相对，必须首先将另一个模块导出的变量、函数、类、接口等导入到当前模块中。

### 导出

可以使用关键字`export`导出顶层的声明。

未导出的声明名称被视为私有名称，只能在声明该名称的模块中使用。


``` TypeScript
export class Point {
  public x: int = 0;
  public y: int = 0;
  constructor(x: int, y: int) {
    this.x = x;
    this.y = y;
  }
}
export let origin: Point = new Point(0, 0);
export function Distance(p1: Point, p2: Point): double {
  return Math.sqrt((p2.x - p1.x) * (p2.x - p1.x) + (p2.y - p1.y) * (p2.y - p1.y));
}
```
**导出默认导出的对象**

``` TypeScript
export class Demo {
  constructor() {}
}
export default new Demo();
```

### 导入

**静态导入**

导入声明用于导入从其他模块导出的实体，并在当前模块中提供其绑定。导入声明由两部分组成：

* 导入路径，用于指定导入的模块；
* 导入绑定，用于定义导入的模块中的可用实体集和使用形式（限定或不限定使用）。

导入绑定可以有几种形式。

假设模块的路径为“./utils”，并且导出了实体“X”和“Y”。

导入绑定`* as A`表示绑定名称“A”，通过`A.name`可访问从导入路径指定的模块导出的所有实体：


``` TypeScript
import * as Utils from './utils';
// ...
Utils.X // 表示来自Utils的X
Utils.Y // 表示来自Utils的Y
```

导入绑定`{ ident1, ..., identN }`表示将导出的实体与指定名称绑定，该名称可以用作简单名称：


``` TypeScript
import { X, Y } from './utils';
// ...
X // 表示来自utils的X
Y // 表示来自utils的Y
```

如果标识符列表定义了`ident as alias`，则实体`ident`将绑定在名称`alias`下：

```typescript
import { X as Z, Y } from './utils';
Z // 表示来自Utils的X
Y // 表示来自Utils的Y
X // 编译时错误：'X'不可见
```


### 顶层语句

顶层语句是指在模块最外层编写的语句，不被任何函数、类或块级作用域包裹。这些语句包括变量声明、函数声明和表达式。

## 关键字

### this

关键字`this`只能在类的实例方法中使用。

**示例**


``` TypeScript
class A {
  private count: string = 'a';
  m(i: string): void {
    this.count = i;
  }
}
```

使用限制：

* 不支持`this`类型。
* 不支持在函数和类的静态方法中使用`this`。

**示例**

```typescript
class A {
  n: int = 0;
  f1(arg1: this) {} // 编译时错误，不支持this类型
  static f2(arg1: int) {
    this.n = arg1;  // 编译时错误，不支持在类的静态方法中使用this
  }
}

function foo(arg1: int) {
  this.n = i;       // 编译时错误，不支持在函数中使用this
}
```

关键字`this`的指向:

* 调用实例方法的对象
* 正在构造的对象

## 注解

注解（Annotation）是一种语言特性，它通过添加元数据来改变应用声明的语义。

注解的声明和使用如下所示：

**示例：**


``` TypeScript
// 注解的声明：
@interface ClassAuthor {
  authorName: string;
}

// 注解的使用：
@ClassAuthor({authorName: "Bob"})
class MyClass {
  // ...
}
```

- 使用@interface声明注解。
- 注解`ClassAuthor`需要将元信息添加到类声明中。
- 注解必须放置在声明之前。
- 注解可以包含上述示例中所示的参数。

对于要使用的注解，其名称必须以符号`@`（例如：@MyAnno）为前缀。符号`@`和名称之间不允许有空格和行分隔符。
```typescript
ClassAuthor({authorName: "Bob"}) // 编译错误：注解需要'@'为前缀
@ ClassAuthor({authorName: "Bob"}) // 编译错误：符号`@`和名称之间不允许有空格和行分隔符
```
如果在使用位置无法访问注解名称，则会发生编译错误。

注解声明可以导出并在其他文件中使用。

多个注解可以应用于同一个声明（注解间的先后顺序不影响使用）。

``` TypeScript
@MyAnno()
@ClassAuthor({authorName: "John Smith"})
class MyClass1 {
  // ...
}
```

### 用户自定义注解

**用户自定义注解的声明**
`用户自定义注解`的定义与`interface`的定义类似，其中的`interface`关键字以符号`@`为前缀。<br>
注解字段仅限于下面列举的类型：
* double
* boolean
* string
* 枚举
* 以上类型的数组
>**说明：**
>
> - 如果使用其他类型用作注解字段的类型，则会发生编译错误。
> - 注解字段类型不支持bigint。

注解字段的默认值必须使用常量表达式来指定。<br>常量表达式的场景如下所示：
* 数字字面量
* 布尔字面量
* 字符串字面量
* 枚举值（需要在编译时确定值）
* 以上常量组成的数组
>**说明：**
>
> 如果枚举值不能在编译时确定，会编译报错。
```typescript
// a.ts
export enum X {
  x = foo(); // x不是编译时能确定的常量
}

// b.ets
import {X} from './a';

@interface Position {
  data: double = X.x; // 编译错误：注解字段的默认值必须使用常量表达式
}
```
注解必须定义在顶层作用域（top-level），否则会出现编译报错。<br>
注解的名称不能与注解定义所在作用域内可见的其他实体名称相同，否则会出现编译报错。<br>
注解不支持类型TypeScript中的合并，否则会出现编译报错。
```typescript
namespace ns {
  @interface MetaInfo { // 编译错误：注解必须定义在顶层作用域
    // ...
  }
}

@interface Position {
  // ...
}

class Position { // 编译错误：注解的名称不能与注解定义所在作用域内可见的其他实体名称相同
  // ...
}

@interface ClassAuthor {
  name: string;
}

@interface ClassAuthor { // 编译错误：注解的名称不能与注解定义所在作用域内可见的其他实体名称相同
  data: string;
}
```
注解不是类型，把注解当类型使用时会出现编译报错（例如：对注解使用类型别名）。
```typescript
@interface Position {}
type Pos = Position; // 编译错误：注解不是类型
```
注解不支持在类的getter和setter方法中添加，若添加注解会编译报错。
```typescript
@interface ClassAuthor {
  authorName: string;
}

@ClassAuthor({authorName: 'John Smith'})
class MyClass {
  private _name: string = 'Bob';

  @ClassAuthor({authorName: 'John Smith'}) // 编译错误：注解不支持在类的getter和setter方法添加
    return this._name;
  }

  @ClassAuthor({authorName: 'John Smith'}) // 编译错误：注解不支持在类的getter和setter方法添加
    this._name = authorName;
  }
}
```

**用户自定义注解的使用**
注解声明示例如下：


``` TypeScript
@interface ClassPreamble {
  authorName: string;
  revision: double = 1;
}
@interface MyAnno {}
```

当前仅允许对`class declarations`和`method declarations`使用注解，对类和方法可以同时使用同一个注解。<br>注解用法示例如下：


``` TypeScript
@ClassPreamble({authorName: "John", revision: 2})
class C1 {
  // ...
}


@ClassPreamble({authorName: "Bob"}) // revision的默认值为1
class C2 {
  // ...
}

@MyAnno() // 对类和方法可以同时使用同一个注解
class C3 {
  @MyAnno()
  foo() {}
  @MyAnno()
  static bar() {}
}
```

注解中的字段顺序不影响使用。


``` TypeScript
@ClassPreamble1({authorName: "John", revision: 2})
// ...
// 等价于:
@ClassPreamble1({revision: 2, authorName: "John"})
```

使用注解时，必须给所有没有默认值的字段赋值，否则会发生编译错误。
>**说明：**
>
> 赋值应当与注解声明的类型一致，所赋的值与注解字段默认值的要求一样，只能使用常量表达式。
```typescript
@ClassPreamble() // 编译错误：authorName字段未定义
class C1 {
  // ...
}
```
如果注解中定义了数组类型的字段，则使用数组字面量来设置该字段的值。


``` TypeScript
@interface ClassPreamble2 {
  authorName: string;
  revision: double = 1;
  reviewers: string[];
}

@ClassPreamble2(;
{
  authorName: "Alice",
  reviewers: ["Bob", "Clara"];
}
)
class C0 {
  // ...
}
```

如果不需要定义注解字段，可以省略注解名称后的括号。


``` TypeScript
@MyAnno;
class C4 {
  // ...
}
```


**导入和导出注解**
注解也可以被导入导出。针对导出，当前仅支持在定义时的导出，即`export @interface`的形式。<br>
**示例：**


``` TypeScript
export @interface MyAnno1 {}
```

针对导入，当前仅支持`import {}`和`import * as`两种方式。<br>
**示例：**


``` TypeScript
// MyAnno.ets
export @interface MyAnno2 {}
export @interface ClassAuthor2 {}
```


``` TypeScript
// Annotation.ets
import { MyAnno2 } from './MyAnno';
import * as ns from './MyAnno';
// ...
@MyAnno2;
@ns.ClassAuthor2;
class C {
  // ...
}
```

- 不允许在import中对注解进行重命名。
```typescript
import { MyAnno as Anno } from './a'; // 编译错误：不允许在import中对注解进行重命名
```
不允许对注解使用任何其他形式的 import/export，这会导致编译报错。
- 由于注解不是类型，因此禁止使用`type`符号进行导入和导出。
```typescript
import type { MyAnno } from './a'; // 编译错误：注解不允许使用'type'符号进行导入和导出
```

- 如果仅从模块导入注解，则不会触发模块的副作用。

``` TypeScript
// MyAnno.ets
export @interface Anno {}

export @interface ClassAuthor1 {}

console.info('hello');
```




``` TypeScript
// Annotation.ets
import { MyAnno2 } from './MyAnno';
import * as ns from './MyAnno';
// 仅引用了Anno注解，不会导致MyAnno.ets的console.info执行
class X {
  // ...
}
```

**.d.ets文件中的注解**
注解可以出现在.d.ets文件中。

可以在.d.ets文件中用环境声明（ambient declaration）来声明注解。
```typescript
ambientAnnotationDeclaration:
  'declare' userDefinedAnnotationDeclaration;
  ;
```

**示例：**


``` TypeScript
// NameAnno.d.ets
export declare @interface ClassAuthor3 {}
```

上述声明中：
- 不会引入新的注解定义，而是提供注解的类型信息。
- 注解需定义在其他源代码文件中。
- 注解的环境声明和实现需要完全一致，包括字段的类型和默认值。


``` TypeScript
// NameAnno.d.ets
export declare @interface NameAnno{name: string = ""}
```



``` TypeScript
// MyAnno.ets
export @interface NameAnno{name: string = ""} // ok
```


环境声明的注解和class类似，也可以被import使用。


``` TypeScript
// NameAnno.d.ets
export declare @interface MyAnno {}
```



``` TypeScript
// ImportMyAnno.ets
import { MyAnno } from './NameAnno';

@MyAnno;
class C {
  // ...
}
```


**编译器自动生成的.d.ets文件**<br>
当编译器根据ets代码自动生成.d.ets文件时，存在以下2种情况。

1. 当注解定义被导出时，源代码中的注解定义会在.d.ets文件中保留。

   
   ``` TypeScript
   // MyAnno.ets
   export @interface ClassAuthor5 {}
   
   @interface MethodAnno { // 没导出
     data: double;
   }
   ```
   
   
   ``` TypeScript
   // NameAnno.d.ets
   export declare @interface ClassAuthor3 {}
   ```

2. 当下面所有条件成立时，源代码中实体的注解实例会在.d.ets文件中保留。<br>
  2.1 注解的定义被导出（import的注解也算作被导出）。<br>
  2.2 如果实体是类，则类被导出。<br>
  2.3 如果实体是方法，则类被导出，并且方法不是私有方法。
   
   ``` TypeScript
   // MyAnno.ets
   import { ClassAuthor4 } from './Author';
   
   export @interface MethodAnno4 {
     data: double = 0;
   }
   
   @ClassAuthor4;
   class MyClass {
     @MethodAnno4({data: 123})
     foo() {}
   
     @MethodAnno4({data: 456})
     private bar() {}
   }
   ```


  
    ``` TypeScript
    // NameAnno.d.ets 编译器生成的声明文件
    import { ClassAuthor4 } from './Author';
    
    export declare @interface MethodAnno4 {
      data: double = 0;
    }
    
    @ClassAuthor4;
    export declare class MyClass {
      @MethodAnno4({data: 123})
      foo(): void;
    
      bar; // 私有方法不保留注解
    }
    ```
  

**开发者生成的.d.ets文件**<br>
开发者生成的.d.ets文件中的注解信息不会自动应用到实现的源代码中。<br>
**示例：**


``` TypeScript
// NameAnno.d.ets 开发者生成的声明文件
@interface ClassAuthor6 {}

@ClassAuthor6 // 声明文件中有注解
class C {
  // ...
}
```



``` TypeScript
// MyAnno.ets 开发者对声明文件实现的源代码
@interface ClassAuthor6 {}

// 实现文件中没有注解
class C {
  // ...
}
```

在最终编译产物中，class C没有注解。

**重复注解和继承**

同一个实体不能重复使用同一注解，否则会导致编译错误。
```typescript
@MyAnno({name: "123", value: 456})
@MyAnno({name: "321", value: 654}) // 编译错误：不允许重复注释
class C {
  // ...
}
```
子类不会继承基类的注解，也不会继承基类方法的注解。

**注解和抽象类、抽象方法**

不支持对抽象类或抽象方法使用注解，否则将导致编译错误。
```typescript
@MyAnno // 编译错误：不允许在抽象类和抽象方法上使用注解
abstract class C {
  @MyAnno;
  abstract foo(): void; // 编译错误：不允许在抽象类和抽象方法上使用注解
}
```

### 源码态注解

源码态注解为一类特殊形式的注解。源码态注解的生命周期只在编译期，不会影响编译产物。

开发者可以通过使用ArkTS提供的[Retention](../reference/apis-arkts/js-apis-arkts-lang.md#retention24)接口来构造自定义源码态注解。源码态注解有更广的使用范围，支持在以下声明上使用：
- 类
- 类成员（除构造函数外）
- 变量声明
- 接口
- 接口成员
- 注解
- 函数
- 命名空间
- 类型别名
- 枚举

源码态注解的声明和使用示例如下所示：

**示例：**


```ts
import { Retention, RetentionPolicy } from '@kit.ArkTS';

// 构造用户自定义源码态注解
@Retention({policy: RetentionPolicy.SOURCE})
@interface SourceAnnotation {}
// 源码态注解可以在类和类成员上使用
@SourceAnnotation;
class C {
  @SourceAnnotation;
  private name_: string = '';
  @SourceAnnotation;
  get name(): string {
    return this.name_;
  }
}
// 源码态注解可以在变量声明上使用
@SourceAnnotation;
let a = 1;
// 源码态注解可以在接口和接口成员上使用
@SourceAnnotation;
interface I {
  @SourceAnnotation;
  foo(): void;
}
// 源码态注解可以在注解上使用
@SourceAnnotation;
@interface Anno {}
// 源码态注解可以在函数上使用
@SourceAnnotation;
function func () {}
// 源码态注解可以在命名空间上使用
@SourceAnnotation;
namespace ns {}
// 源码态注解可以在类型别名上使用
@SourceAnnotation;
type A = double;
// 源码态注解可以在枚举上使用
@SourceAnnotation;
enum ColorSet { RED, GREEN, BLUE }
```
