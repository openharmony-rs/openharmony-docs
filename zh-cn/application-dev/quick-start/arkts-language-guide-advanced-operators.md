---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "讲解位运算符、复合赋值运算符、类型判断操作符、展开与剩余运算符等ArkTS高级运算符的概念与用法，并给出运算符优先级表及ArkTS相关限制说明。"
keywords: [ArkTS, 高级运算符, 位运算符, 复合赋值运算符, 类型判断操作符, 展开运算符, 运算符优先级]
doctype: guide
status: active
---

# 高级运算符
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

在[基本运算符](arkts-language-guide-basic-operators.md)一章中介绍了赋值、算术、比较、逻辑等常用运算符。本章进一步介绍位运算符、复合赋值运算符、类型判断运算符、展开与剩余运算符，以及高级运算符的优先级和结合性。

## 位运算符

位运算符直接操作整数的二进制位，常用于权限标志位管理、数据压缩、加密解密和性能敏感的数学计算。例如，用按位OR组合权限（`READ | WRITE`）、用按位AND检查权限（`flags & READ`）、用按位XOR切换标志（`flags ^ TOGGLE`）。位运算在底层开发和系统编程中广泛使用，日常业务逻辑中较少直接使用。

### 按位与 (&)

按位与运算符对两个整数的每一位执行逻辑与操作，仅当对应位都为1时结果为1。

<!-- @[bitwise_and](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let a: number = 5;   // 二进制0101
let b: number = 3;   // 二进制0011
let bitAndResult: number = a & b;  // 二进制0001，十进制1

// 使用场景：检查标志位
const READ: number = 0b001;
const WRITE: number = 0b010;
const EXECUTE: number = 0b100;

let permission: number = 0b110;  // 可写可执行

let canRead: boolean = (permission & READ) !== 0;
let canWrite: boolean = (permission & WRITE) !== 0;
let canExecute: boolean = (permission & EXECUTE) !== 0;

console.info(`读取: ${canRead}`);      // false
console.info(`写入: ${canWrite}`);     // true
console.info(`执行: ${canExecute}`);   // true

// 清除标志位
permission = permission & ~WRITE;  // 清除写入权限
```

### 按位或 (|)

按位或运算符对两个整数的每一位执行逻辑或操作，只要对应位有1则结果为1。

<!-- @[bitwise_or](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let bitOrA: number = 5;   // 二进制: 0101
let bitOrB: number = 3;   // 二进制: 0011
let bitOrResult: number = bitOrA | bitOrB;  // 二进制: 0111 (十进制: 7)

// 使用场景：设置标志位
const BOLD: number = 0b001;
const ITALIC: number = 0b010;
const UNDERLINE: number = 0b100;

let style: number = 0;
style = style | BOLD | ITALIC;  // 设置加粗和斜体

// 组合多个标志
let fullStyle: number = BOLD | ITALIC | UNDERLINE;  // 0b111
```

### 按位异或 (^)

按位异或运算符对两个整数的每一位执行异或操作，对应位不同时结果为1。

<!-- @[bitwise_xor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let bitXorA: number = 5;   // 二进制: 0101
let bitXorB: number = 3;   // 二进制: 0011
let bitXorResult: number = bitXorA ^ bitXorB;  // 二进制: 0110 (十进制: 6)

// 使用场景：切换标志位
let bitXorFlags: number = 0b101;
bitXorFlags = bitXorFlags ^ 0b001;  // 切换第0位: 0b100
bitXorFlags = bitXorFlags ^ 0b001;  // 再次切换第0位: 0b101

// 简单加密
let data: number = 42;
let key: number = 123;
let encrypted: number = data ^ key;
let decrypted: number = encrypted ^ key;
console.info(`${decrypted === data}`);  // true
```

### 按位非 (~)

按位非运算符对整数的每一位执行取反操作，将0变为1、将1变为0。

<!-- @[bitwise_not](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let bitNotA: number = 5;   // 二进制: 0101
let bitNotResult: number = ~bitNotA;  // 二进制: ...11111010 (十进制: -6)

// 公式: ~x = -(x + 1)
console.info(`${~5}`);   // -6
console.info(`${~(-6)}`); // 5

// 使用场景：清除标志位
const FLAG: number = 0b010;
let bitNotValue: number = 0b111;
bitNotValue = bitNotValue & ~FLAG;  // 清除第1位: 0b101
```

### 左移运算符 (<<)

左移运算符将整数的二进制位向左移动指定位数，相当于乘以2的幂次。

<!-- @[left_shift](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let lshiftA: number = 5;   // 二进制: 0101
let lshiftResult: number = lshiftA << 2;  // 二进制: 010100 (十进制: 20)

// 左移n位相当于乘以2^n
console.info(`${5 << 1}`);  // 10 (5 * 2)
console.info(`${5 << 2}`);  // 20 (5 * 4)
console.info(`${5 << 3}`);  // 40 (5 * 8)

// 使用场景：快速乘法
let base: number = 10;
let doubled: number = base << 1;   // 20
let quadrupled: number = base << 2;  // 40
```

### 右移运算符 (>>)

右移运算符将整数的二进制位向右移动指定位数，相当于除以2的幂次。

<!-- @[right_shift](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let rshiftA: number = 20;  // 二进制010100
let rshiftResult: number = rshiftA >> 2;  // 二进制0101，十进制5

// 右移n位相当于除以2^n（向下取整）
console.info(`${20 >> 1}`);  // 10
console.info(`${20 >> 2}`);  // 5
console.info(`${20 >> 3}`);  // 2

// 负数右移
let neg: number = -20;
console.info(`${neg >> 2}`);  // -5

// 使用场景：快速除法
let total: number = 100;
let half: number = total >> 1;  // 50
let quarter: number = total >> 2;  // 25
```

### 无符号右移运算符 (>>>)

无符号右移运算符将整数二进制位向右移动，左侧补零。与`>>`的区别：`>>`保留符号位（负数左侧补1），`>>>`无论正负左侧都补零。常见用途是通过`>>> 0`将浮点数转换为32位无符号整数。

<!-- @[unsigned_right_shift](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let rshiftA2: number = 20;  // 二进制: 010100
let rshiftResult2: number = rshiftA2 >>> 2;  // 二进制: 0101 (十进制: 5)

// 对正数与 >> 效果相同
console.info(`${20 >> 2}`);   // 5
console.info(`${20 >>> 2}`);  // 5

// 对负数的处理不同
let rshiftNeg: number = -20;  // 二进制: ...11101100
console.info(`${rshiftNeg >> 2}`);    // -5（保留符号位）
console.info(`${rshiftNeg >>> 2}`);   // 1073741819（符号位变成0）

// 使用场景：转换为无符号整数
function toUnsigned(value: number): number {
  return value >>> 0;
}
```

## 复合赋值运算符

复合赋值运算符将运算和赋值合并为一个操作。

### 复合赋值的语法格式

复合赋值运算符将二元运算与赋值合并为单步操作，等价于`x = x op y`的简写。算术类支持`+=`、`-=`、`*=`、`/=`、`%=`、`**=`，位运算类支持`&=`、`|=`、`^=`、`<<=`、`>>=`、`>>>=`，逻辑类支持`??=`、`||=`、`&&=`。

``` TypeScript
variable operator= expression
等价于: variable = variable operator expression
```

<!-- @[compound_assignment_basics](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let compoundA: number = 10;
compoundA += 5;
console.info(`${compoundA}`);  // 15
compoundA -= 3;
console.info(`${compoundA}`);  // 12
compoundA *= 2;
console.info(`${compoundA}`);  // 24
compoundA /= 4;
console.info(`${compoundA}`);  // 6
```

### 位运算复合赋值

位运算复合赋值包括`&=`（按位与赋值）、`|=`（按位或赋值）、`^=`（按位异或赋值）、`<<=`（左移赋值）、`>>=`（右移赋值）、`>>>=`（无符号右移赋值），将位运算结果直接赋值给左操作数。

<!-- @[compound_assignment_bitwise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let compoundFlags: number = 0b1010;

// 按位与赋值
compoundFlags &= 0b1100;  // compoundFlags = compoundFlags & 0b1100 = 0b1000

// 按位或赋值
compoundFlags |= 0b0011;  // compoundFlags = compoundFlags | 0b0011 = 0b1011

// 按位异或赋值
compoundFlags ^= 0b0001;  // compoundFlags = compoundFlags ^ 0b0001 = 0b1010

// 左移赋值
let compoundValue: number = 5;
compoundValue <<= 2;  // compoundValue = compoundValue << 2 = 20

// 右移赋值
compoundValue >>= 1;  // compoundValue = compoundValue >> 1 = 10

// 无符号右移赋值
compoundValue >>>= 1;  // compoundValue = compoundValue >>> 1 = 5
```

### 算术运算复合赋值

算术运算复合赋值包括`+=`、`-=`、`*=`、`/=`、`%=`、`**=`，将算术运算结果直接赋值给左操作数。

<!-- @[compound_assignment_arithmetic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// 加法赋值
let compoundTotal: number = 100;
compoundTotal += 50;
console.info(`${compoundTotal}`);  // 150

// 减法赋值
let balance: number = 1000;
balance -= 200;
console.info(`${balance}`);  // 800

// 乘法赋值
let price: number = 10;
price *= 2;
console.info(`${price}`);  // 20

// 除法赋值
let amount: number = 100;
amount /= 4;
console.info(`${amount}`);  // 25

// 取模赋值
let compoundValue2: number = 17;
compoundValue2 %= 5;
console.info(`${compoundValue2}`);  // 2

// 指数赋值
let compoundBase: number = 2;
compoundBase **= 4;
console.info(`${compoundBase}`);  // 16
```

### 逻辑运算复合赋值

逻辑运算复合赋值包括`??=`（逻辑空赋值）、`||=`（逻辑或赋值）、`&&=`（逻辑与赋值），将逻辑运算与赋值合并，并保留对应逻辑运算符的短路特性——右侧表达式仅在需要赋值时才求值：

- `x ??= y`：仅当`x`为`null`或`undefined`时，才将`y`赋给`x`。
- `x ||= y`：仅当`x`为[falsy值](arkts-language-guide-basic-operators.md#逻辑赋值运算符-)时，才将`y`赋给`x`。
- `x &&= y`：仅当`x`为truthy值时，才将`y`赋给`x`。

<!-- @[logical_operation_compound_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// ??= 仅在左侧为null或undefined时赋值
let logicAssignConfig: string | null = null;
logicAssignConfig ??= 'default';  // "default"

// ||= 仅在左侧为falsy值时赋值
let logicAssignLabel: string = '';
logicAssignLabel ||= 'unnamed';  // "unnamed"

// &&= 仅在左侧为truthy值时赋值
let logicAssignCount: number = 10;
logicAssignCount &&= logicAssignCount * 2;  // 20
```

## 类型判断操作符

类型判断操作符`typeof`和`instanceof`在运行时检查值的实际类型，常用于构成类型守卫，在条件分支中将联合类型收窄为具体类型：

- `typeof value === 'string'`：判断`value`是否为`string`类型（同理可判断`number`、`boolean`等基础类型）。
- `pet instanceof Dog`：判断`pet`是否为`Dog`类的实例。

类型判断与类型守卫的详细用法见[类型](arkts-language-guide-types.md#类型守卫)。

## 展开与剩余运算符

展开运算符（...）将数组元素拆解为独立元素，用于合并、复制和传参；剩余运算符（...）将多个参数收集为数组。

### 数组展开运算符

数组展开运算符（...）将数组元素展开为独立元素，用于复制、合并和传参。

<!-- @[spread_operator_array](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// 展开数组元素
let spreadArr1: number[] = [1, 2, 3];
let spreadArr2: number[] = [4, 5, 6];

// 合并数组
let merged: number[] = [...spreadArr1, ...spreadArr2];
console.info(`${merged.join(', ')}`);  // 1, 2, 3, 4, 5, 6

// 在任意位置插入
let inserted: number[] = [0, ...spreadArr1, 4];
console.info(`${inserted.join(', ')}`);  // 0, 1, 2, 3, 4

// 复制数组
let spreadCopied: number[] = [...spreadArr1];
console.info(`${spreadCopied.join(', ')}`);  // 1, 2, 3

// 作为函数参数：被展开数组应传给剩余参数
function spreadSum(...values: number[]): number {
  let spreadTotal: number = 0;
  for (let value of values) {
    spreadTotal += value;
  }
  return spreadTotal;
}

let numbers: number[] = [1, 2, 3];
let spreadTotal: number = spreadSum(...numbers);  // 6

// 展开与数组方法结合
let spreadMax: number = Math.max(...spreadArr1);  // 3
let min: number = Math.min(...spreadArr2);  // 4
```

### 剩余参数运算符

剩余参数运算符（...）将多个参数收集为数组，用于处理不定数量的参数。

<!-- @[rest_parameters](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// 函数参数中的剩余参数
function sumAll(...numbers: number[]): number {
  let total: number = 0;
  for (const num of numbers) {
    total += num;
  }
  return total;
}

console.info(`${sumAll(1, 2, 3, 4, 5)}`);  // 15

// 与固定参数结合
function greet(greeting: string, ...names: string[]): string {
  return `${greeting}, ${names.join(', ')}!`;
}

console.info(`${greet('Hello', 'Alice', 'Bob', 'Charlie')}`);  // 'Hello, Alice, Bob, Charlie!'

// 数组解构中的剩余元素
let arr: number[] = [1, 2, 3, 4, 5];
// ArkTS不支持解构赋值，需要手动提取
let first: number = arr[0] ?? 0;
let rest: number[] = arr.slice(1);
console.info(`${first}`);  // 1
console.info(`${rest.join(', ')}`);   // 2, 3, 4, 5

// 函数参数收集
function restProcess(first: string, second: string, ...remaining: string[]): void {
  console.info(`First: ${first}`);
  console.info(`Second: ${second}`);
  console.info(`Remaining: ${remaining.join(', ')}`);
}

restProcess('a', 'b', 'c', 'd', 'e');
// First: a
// Second: b
// Remaining: c, d, e
```

## 高级运算符的优先级和结合性

运算符优先级决定不同运算符的求值顺序，结合性决定同级运算符的求值方向（从左到右或从右到左）。下表汇总了ArkTS常见运算符的优先级与结合性，自上而下优先级由高到低。表中涵盖本章介绍的位运算符、类型判断操作符、复合赋值运算符，以及[基本运算符](arkts-language-guide-basic-operators.md)中介绍的常用运算符：

| 优先级 | 运算符 | 说明 | 结合性 |
| ------ | ------ | ---- | ------ |
| 1 | `()` | 括号分组 | — |
| 2 | `.`、`[]`、`?.` | 成员访问、可选链 | 从左到右 |
| 3 | `++`、`--`（后置）、`!`（后置） | 后置递增、后置递减、非空断言 | — |
| 4 | `!`、`~`、`typeof`、`+`、`-`（一元）、`++`、`--`（前置） | 一元运算符 | 从右到左 |
| 5 | `**` | 指数 | 从右到左 |
| 6 | `*`、`/`、`%` | 乘法、除法、取余 | 从左到右 |
| 7 | `+`、`-` | 加法、减法 | 从左到右 |
| 8 | `<<`、`>>`、`>>>` | 位移 | 从左到右 |
| 9 | `<`、`<=`、`>`、`>=`、`instanceof` | 关系比较、`instanceof`类型判断 | 从左到右 |
| 10 | `===`、`!==`、`==`、`!=` | 相等比较 | 从左到右 |
| 11 | `&` | 按位与 | 从左到右 |
| 12 | `^` | 按位异或 | 从左到右 |
| 13 | `\|` | 按位或 | 从左到右 |
| 14 | `&&` | 逻辑与 | 从左到右 |
| 15 | `\|\|`、`??` | 逻辑或、空值合并 | 从左到右 |
| 16 | `?:` | 三元条件 | 从右到左 |
| 17 | `=`、`+=`、`-=`、`*=`、`/=`、`%=`、`**=`、`&=`、`\|=`、`^=`、`<<=`、`>>=`、`>>>=`、`??=`、`\|\|=`、`&&=` | 赋值、复合赋值 | 从右到左 |

同级运算符按结合性确定求值方向，例如`10 - 5 - 2`从左到右计算，等价于`(10 - 5) - 2`。本章新介绍的按位运算符`&`、`^`、`|`位于相等比较与逻辑运算符之间，且优先级依次降低，例如`flags & MASK !== 0`会解析为`flags & (MASK !== 0)`，检查标志位时应写成`(flags & MASK) !== 0`。`??`不能与`&&`、`||`直接混用，必须使用括号分组。复杂表达式建议使用括号明确优先级，避免依赖默认规则导致歧义：

<!-- @[parentheses_for_precedence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

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
