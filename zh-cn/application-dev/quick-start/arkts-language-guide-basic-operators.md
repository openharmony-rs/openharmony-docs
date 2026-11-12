---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "讲解ArkTS的赋值、算术、比较、逻辑、三元条件等基本运算符的用法与运算符优先级规则。"
keywords: [ArkTS, 基本运算符, 赋值运算符, 算术运算符, 比较运算符, 逻辑运算符, 三元条件运算符, 运算符优先级]
doctype: guide
status: active
---

# 基本运算符
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

ArkTS提供丰富的运算符用于数据运算、逻辑判断和赋值操作。

## 赋值运算符

赋值运算符（=）将右侧的值赋给左侧的变量，支持链式赋值和复合赋值（+=、-=等）。

### 简单赋值 (=)

使用`=`将右侧的值赋给左侧的变量。赋值是引用语义——对对象类型的变量赋值后，新旧变量指向同一对象，修改其中一个会影响另一个。

<!-- @[basic_variable_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let value: number = 10;
let name: string = 'Alice';
let active: boolean = true;

// 重新赋值
value = 20;
name = 'Bob';
```

### 赋值表达式的返回值

赋值表达式本身返回被赋的值，语法上支持链式赋值`a = b = 10`，但**不建议使用**，建议分开赋值以提高可读性。

<!-- @[chain_vs_separate_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let a: number;
let b: number;

// 反例：链式赋值
a = b = 10;

// 推荐：分开赋值
a = 10;
b = 10;
```

### 对象赋值

将对象赋值给变量传递的是引用而非副本——新旧变量指向同一对象，修改其中一个的属性会影响另一个。如需独立副本，须手动实现深拷贝。

<!-- @[object_property_and_reference_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
class Point {
  public x: number = 0;
  public y: number = 0;
}

let point: Point = new Point();
point.x = 10;       // 属性赋值
point.y = 20;

let another: Point = point;  // 引用赋值
another.x = 30;    // point.x也变为30
```

## 算术运算符

算术运算符包括加（+）、减（-）、乘（*）、除（/）、取余（%）以及递增递减（++/--）。

### 加法运算符 (+)

加法运算符执行数值相加或字符串拼接，返回相加或拼接结果。

<!-- @[addition_and_string_concatenation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let addA: number = 10;
let addB: number = 5;

let sum: number = addA + addB;    // 15

// 字符串拼接
let greeting: string = 'Hello' + ' World';
let message: string = 'Count: ' + 10;
```

### 减法运算符 (-)

减法运算符（`-`）计算两个数值操作数的差值，操作数必须为`number`类型。与支持字符串拼接的`+`不同，`-`、`*`、`/`、`%`及一元负号不允许`number`与`string`等跨类型运算。

<!-- @[subtraction_and_negative_number](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let numberA: number = 10;
let numberB: number = 5;

let diff: number = numberA - numberB;   // 5
let negative: number = -10; // 负数表示
```

### 乘法运算符 (*)

乘法运算符（`*`）计算两个数值操作数的乘积。操作数必须为`number`类型，ArkTS不支持字符串重复（如Python的`'ab' * 3`），字符串重复需使用`repeat()`方法。

<!-- @[multiplication_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let mulA: number = 10;
let mulB: number = 5;

let product: number = mulA * mulB;  // 50

// 面积计算
let width: number = 5;
let height: number = 10;
let area: number = width * height;  // 50
```

### 除法运算符 (/)

除法运算符（/）计算两数商值，结果始终为浮点数。

<!-- @[division_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let divA: number = 10;
let divB: number = 4;

let quotient: number = divA / divB;  // 2.5

// 整数除法
let intDivision: number = Math.floor(10 / 4);  // 2

// 除以零
let zeroDiv: number = 10 / 0;   // Infinity
let negZeroDiv: number = -10 / 0;  // -Infinity
let zeroByZero: number = 0 / 0;  // NaN
```

### 取余运算符 (%)

取余运算符返回除法的余数，用于循环、周期计算。

<!-- @[modulo_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let modA: number = 10;
let modB: number = 3;

let remainder: number = modA % modB;  // 1

// 判断奇偶
let isEven: boolean = (modA % 2) === 0;
let isOdd: boolean = (modA % 2) !== 0;
```

### 一元负号运算符 (-)

一元负号（-）将数值取反，正变负、负变正。

<!-- @[unary_negation_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let negA: number = 5;
let negNegative: number = -negA;  // -5

let negB: number = -10;
let positive: number = -negB;  // 10
```

### 指数运算符 (**)

指数运算符计算幂次，返回底数的指数次幂。

<!-- @[exponentiation_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let base: number = 2;
let exponent: number = 3;

let power: number = base ** exponent;  // 8 (2^3)

let square: number = 5 ** 2;   // 25
let cube: number = 3 ** 3;     // 27
```

## 复合赋值运算符

复合赋值运算符合并运算和赋值，简化代码编写。

<!-- @[compound_assignment_operators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// 加法赋值
let total: number = 100;
total += 50;  // 150

// 字符串拼接赋值
let compoundMessage: string = 'Hello';
compoundMessage += ' World';  // 'Hello World'

// 减法赋值
let balance: number = 1000;
balance -= 200;  // 800

// 乘法赋值
let price: number = 10;
price *= 2;  // 20

// 除法赋值
let amount: number = 100;
amount /= 4;  // 25

// 取模赋值
let compoundValue: number = 17;
compoundValue %= 5;  // 2

// 指数赋值
let compoundBase: number = 2;
compoundBase **= 4;  // 16
```

### 逻辑赋值运算符 (??=、||=、&&=)

逻辑赋值运算符（??=、||=、&&=）将逻辑运算与赋值合并，语义与对应的`??`、`||`、`&&`一致，并保留其短路特性——右侧表达式仅在需要赋值时才会求值。其求值沿袭JavaScript的truthy/falsy概念：`false`、`0`、`-0`、`NaN`、`''`（空字符串）、`null`、`undefined`在布尔上下文中被视为falsy值，其余值均为truthy值，后文的逻辑运算符与空值合并运算符同样以此为基础。

- `a ??= b`：仅当`a`为`null`或`undefined`时，才将`b`赋给`a`。
- `a ||= b`：仅当`a`为falsy值时，才将`b`赋给`a`。
- `a &&= b`：仅当`a`为truthy值时，才将`b`赋给`a`。

<!-- @[logical_assignment_operators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// ??= 仅在左侧为null或undefined时赋值
let configValue: string | null = null;
configValue ??= 'default';  // "default"（原值为null，执行赋值）

let timeout: number | null = 0;
timeout ??= 3000;  // 0（0是有效值，不执行赋值）

// ||= 仅在左侧为falsy值时赋值
let label: string = '';
label ||= 'unnamed';  // "unnamed"（''是falsy值，执行赋值）

// &&= 仅在左侧为truthy值时赋值
let logicalCount: number = 10;
logicalCount &&= logicalCount * 2;  // 20（10是truthy值，执行赋值）

// 短路特性：左侧条件不满足时，右侧表达式不会执行
let cache: string | null = 'cached';
function loadFromDisk(): string {
  console.info('执行磁盘读取');
  return 'loaded';
}
cache ??= loadFromDisk();  // "cached"（不为null，loadFromDisk不执行）
```

## 比较运算符

比较运算符判断值的关系，返回布尔结果。

### 等于运算符 (===)

严格相等（===）在值和类型都相同时返回`true`。

<!-- @[strict_equality_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// 数值比较
let eqA: number = 5;
let eqB: number = 5;
console.info(`${eqA === eqB}`);     // true

// 不同值
let eqNum1: number = 5;
let eqNum2: number = 10;
console.info(`${eqNum1 === eqNum2}`); // false

// 对象比较引用
class EqPoint {
  public x: number;
  public y: number;
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

let p1: EqPoint = new EqPoint(1, 2);
let p2: EqPoint = new EqPoint(1, 2);
console.info(`${p1 === p2}`);  // false（不同对象）

// NaN不等于自身
let nan1: number = 0 / 0;  // 浮点计算产生NaN
let nan2: number = 0 / 0;  // 浮点计算产生NaN
console.info(`${nan1 === nan2}`);        // false
console.info(`${Number.isNaN(nan1)}`);   // true
```

`NaN`不等于任何值（包括自身），`NaN === NaN`恒为`false`，因此不能用`===`判断浮点计算结果是否为`NaN`，应使用`Number.isNaN`判断。

ArkTS还支持松散相等（==）。由于静态类型检查限制了不同类型值之间的比较，`==`与`===`的差异主要体现在对`null`与`undefined`的处理上：`==`将两者视为相等，`===`则严格区分。若无特殊需要，建议使用更严谨的`===`：

<!-- @[loose_equality_not_recommended](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// == 将null与undefined视为相等
let inputValue: string | null = null;
let missing: string | undefined = undefined;

console.info(`${inputValue == null}`);     // true
console.info(`${missing == null}`);        // true（undefined == null为true）
console.info(`${inputValue == missing}`);  // true

// === 严格区分null与undefined
console.info(`${inputValue === null}`);  // true
console.info(`${missing === null}`);     // false（undefined !== null）
```

推荐使用严格相等：

<!-- @[strict_equality_preferred](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let eqValue: string | null = null;
let eqCount: number = 0;
// 推荐：使用严格相等
if (eqValue === null) { }
if (eqCount === 0) { }
```

### 不等于运算符 (!==)

严格不等（!==）在值或类型不同时返回`true`。与之对应的松散不等（!=）同样不建议使用，推荐统一使用`!==`。

<!-- @[strict_inequality_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let neA: number = 5;
let neB: number = 3;
console.info(`${neA !== neB}`);     // true

let neNum1: number = 5;
let neNum2: number = 10;
console.info(`${neNum1 !== neNum2}`); // true
```

### 大于运算符 (>)

大于运算符（>）在左侧值大于右侧时返回`true`。

<!-- @[greater_than_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let gtA: number = 10;
let gtB: number = 5;

console.info(`${gtA > gtB}`);   // true
console.info(`${gtB > gtA}`);   // false
console.info(`${gtA > gtA}`);   // false

// 字符串比较Unicode码点
console.info(`${'b' > 'a'}`);     // true
console.info(`${'abc' > 'abb'}`); // true
```

### 小于运算符 (<)

小于运算符（<）在左侧值小于右侧时返回`true`。

<!-- @[less_than_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let ltA: number = 10;
let ltB: number = 5;

console.info(`${ltA < ltB}`);   // false
console.info(`${ltB < ltA}`);   // true
console.info(`${ltA < ltA}`);   // false
```

### 大于等于运算符 (>=)

大于等于（>=）在左侧值大于或等于右侧时返回`true`。

<!-- @[greater_than_or_equal_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let gteA: number = 10;
let gteB: number = 5;
let gteC: number = 10;

console.info(`${gteA >= gteB}`);  // true
console.info(`${gteA >= gteC}`);  // true
console.info(`${gteB >= gteA}`);  // false
```

### 小于等于运算符 (<=)

小于等于（<=）在左侧值小于或等于右侧时返回`true`。

<!-- @[less_than_or_equal_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let lteA: number = 10;
let lteB: number = 5;
let lteC: number = 10;

console.info(`${lteA <= lteB}`);  // false
console.info(`${lteA <= lteC}`);  // true
console.info(`${lteB <= lteA}`);  // true
```

## 三元条件运算符

三元条件运算符根据条件表达式的布尔值，从两个值中选择一个作为结果。它是`if-else`的简洁写法，适用于简单的条件赋值场景。

``` TypeScript
条件表达式 ? 真值 : 假值
```

<!-- @[ternary_conditional_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let age: number = 20;
let status: string = age >= 18 ? 'adult' : 'minor';

let score: number = 85;
let result: string = score >= 60 ? 'pass' : 'fail';

// 嵌套三元运算符
let grade: string = 
  score >= 90 ? 'A' :
  score >= 80 ? 'B' :
  score >= 70 ? 'C' :
  score >= 60 ? 'D' : 'F';

// 函数返回
function getStatus(code: number): string {
  return code === 200 ? 'OK' : 'Error';
}

// 条件赋值
let isAdmin: boolean = true;
let role: string = isAdmin ? 'admin' : 'user';
```

## 空值合并运算符

空值合并运算符（??）提供默认值，仅当左侧为`null`或`undefined`时才返回右侧的值。

`??`与逻辑或`||`的区别在于对[falsy值](#逻辑赋值运算符-)的处理：`||`在左侧为任何falsy值时都会返回右侧，`0`、`''`、`false`等有效值会被误替换；`??`仅在左侧为`null`或`undefined`（falsy值的子集）时才返回右侧，能够保留其余有效值。

<!-- @[nullish_coalescing_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let coalesceValue: string | null = null;
let coalesceResult: string = coalesceValue ?? 'default';
console.info(`${coalesceResult}`);  // 'default'

let value2: string = 'hello';
let result2: string = value2 ?? 'default';  // "hello"

// 与 || 的区别
let count: number = 0;
let text: string = '';
let flag: boolean = false;

// || 替换falsy值
let withOr1: number = count || 10;     // 10（0是falsy）
let withOr2: string = text || 'default'; // 'default'

// ?? 只替换null/undefined
let withNullCoalesce1: number = count ?? 10;      // 0（保留0）
let withNullCoalesce2: string = text ?? 'default'; // ''（保留空字符串）

// 链式空值合并
let primary: string | null = null;
let secondary: string | null = null;
let fallback: string = 'default';

let result3: string = primary ?? secondary ?? fallback;
console.info(`${result3}`);  // 'default'
```

## 逻辑运算符

逻辑运算符包括非（!）、与（&&）、或（||），对布尔值做逻辑运算并支持短路。

### 逻辑非运算符 (!)

逻辑非（!）将`true`变`false`、`false`变`true`。

<!-- @[logical_not_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let isA: boolean = true;
let isB: boolean = false;

console.info(`${!isA}`);  // false
console.info(`${!isB}`);  // true

// 双重否定转换为布尔值
let notValue: number = 5;
console.info(`${!!notValue}`);  // true（等同于Boolean(notValue)）
```

### 逻辑与运算符 (&&)

逻辑与（&&）两侧均为`true`才返回`true`，左侧为`false`时短路跳过右侧。

<!-- @[logical_and_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let andA: boolean = true;
let andB: boolean = true;
let andC: boolean = false;

console.info(`${andA && andB}`);  // true
console.info(`${andA && andC}`);  // false

// 真值表
// true && true   → true
// true && false  → false
// false && true  → false
// false && false → false

// 条件检查
let andAge: number = 25;
let hasLicense: boolean = true;
let hasInsurance: boolean = true;

let canDrive: boolean = andAge >= 18 && hasLicense && hasInsurance;
```

### 逻辑或运算符 (||)

逻辑或（||）任一侧为`true`即返回`true`，左侧为`true`时短路跳过右侧。

<!-- @[logical_or_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let orA: boolean = true;
let orB: boolean = false;
let orC: boolean = false;

console.info(`${orA || orB}`);  // true
console.info(`${orB || orC}`);  // false

// 真值表
// true || true   → true
// true || false  → true
// false || true  → true
// false || false → false

// 任一条件满足
let orRole: string = 'admin';
let hasPermission: boolean = true;

let canAccess: boolean = orRole === 'admin' || hasPermission;
```

### 短路求值

逻辑与（&&）和逻辑或（||）在左侧已能决定结果时跳过右侧执行。

<!-- @[short_circuit_evaluation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// && 短路：左边为false，右边不执行
function expensiveCheck(): boolean {
  console.info('执行复杂检查');
  return true;
}

let enabled: boolean = false;
let circuitResult: boolean = enabled && expensiveCheck();  // 不执行expensiveCheck

// || 短路：左边为true，右边不执行
function fallbackValue(): string {
  console.info('使用默认值');
  return 'default';
}

let circuitPrimary: string = 'primary';
let circuitValue: string = circuitPrimary || fallbackValue();  // "primary"，不执行fallbackValue

// ?? 短路：左边不为null/undefined，右边不执行
function expensiveDefault(): string {
  console.info('执行昂贵默认值计算');
  return 'default';
}

let provided: string = 'text';
let circuitResult2: string = provided ?? expensiveDefault();  // 不执行expensiveDefault
```

## 运算符的优先级和结合性

运算符优先级决定不同运算符的求值顺序，结合性决定同级运算符的求值方向（从左到右或从右到左）。本章所介绍运算符的优先级与结合性如下表所示，自上而下优先级由高到低：

| 优先级 | 运算符 | 说明 | 结合性 |
| ------ | ------ | ---- | ------ |
| 1 | `()` | 括号分组 | — |
| 2 | `?.` | 可选链 | 从左到右 |
| 3 | `++`、`--`（后置）、`!`（后置） | 后置递增、后置递减、非空断言 | — |
| 4 | `!`、`+`、`-`（一元）、`++`、`--`（前置） | 一元运算符 | 从右到左 |
| 5 | `**` | 指数 | 从右到左 |
| 6 | `*`、`/`、`%` | 乘法、除法、取余 | 从左到右 |
| 7 | `+`、`-` | 加法、减法 | 从左到右 |
| 8 | `<`、`<=`、`>`、`>=` | 关系比较 | 从左到右 |
| 9 | `===`、`!==`、`==`、`!=` | 相等比较 | 从左到右 |
| 10 | `&&` | 逻辑与 | 从左到右 |
| 11 | `\|\|`、`??` | 逻辑或、空值合并 | 从左到右 |
| 12 | `?:` | 三元条件 | 从右到左 |
| 13 | `=`、`+=`、`-=`、`*=`、`/=`、`%=`、`**=`、`??=`、`\|\|=`、`&&=` | 赋值、复合赋值 | 从右到左 |

位运算符、位移运算符等高级运算符的优先级与结合性，见[高级运算符](arkts-language-guide-advanced-operators.md#高级运算符的优先级和结合性)。

`??`不能与`&&`、`||`直接混用，必须使用括号分组。实际编码中建议用括号显式标注运算优先级，避免依赖默认规则导致歧义：

<!-- @[parentheses_for_precedence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let precA: number = 5;
let precB: number = 3;
let precC: number = 10;
let precD: number = 2;
let precInput: string | null = 'hello';
// 使用括号明确优先级
let precResult: number = (precA + precB) * (precC - precD);
let valid: boolean = (precA > precB) && (precC < precD);
let precValue: string = (precInput ?? 'default') + ' suffix';
```

## 递增递减运算符

递增（++）和递减（--）对数值加1或减1，前置先变后用、后置先用后变。

<!-- @[increment_decrement_operators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let decrCount: number = 5;

// 前置递增：先增加，再使用
let preInc: number = ++decrCount;  // decrCount=6, preInc=6

// 后置递增：先使用，再增加
let postInc: number = decrCount++; // decrCount=7, postInc=6

// 前置递减
let preDec: number = --decrCount;  // decrCount=6, preDec=6

// 后置递减
let postDec: number = decrCount--; // decrCount=5, postDec=6
```

## 可选链运算符

可选链运算符（?.）在变量或其属性可能为`null`/`undefined`时安全访问，避免运行时错误。

<!-- @[optional_chaining_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// 变量为数组或null，都能正常访问
function printScores(scores: number[] | null) {
  // 安全访问属性：scores为null时返回undefined
  let scoreCount: number | undefined = scores?.length;
  console.info(`分数数量: ${scoreCount}`);
  
  // 安全调用方法：scores为null时返回undefined
  let hasPass: boolean | undefined = scores?.includes(60);
  console.info(`是否有及格: ${hasPass}`);
  
  // 结合空值合并提供默认值
  let safeCount: number = scores?.length ?? 0;
  console.info(`安全获取数量: ${safeCount}`);
}

// 测试 null 情况
printScores(null);  // 输出: 分数数量: undefined, 是否有及格: undefined, 安全获取数量: 0

// 测试数组情况
printScores([80, 95]);  // 输出: 分数数量: 2, 是否有及格: false, 安全获取数量: 2
```

## 非空断言运算符

非空断言运算符（!）用在可为空的值之后，向编译器断言该值不为`null`或`undefined`，随后可直接访问其属性或调用方法。它与可选链`?.`相对：`?.`在值为空时安全返回`undefined`，`!`则假定值非空，若值实际为空，会在运行时抛出异常。仅在能确保非空时使用，否则优先使用`?.`或`??`。

<!-- @[non_null_assertion_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
function getValue(): string | null {
  return 'Alice';
}

let nickname: string | null = getValue();
console.info(nickname!.toUpperCase());  // 'ALICE'（断言非空后直接调用）
```
