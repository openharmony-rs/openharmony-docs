---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍ArkTS的基础知识，涵盖常量与变量、注释、分号、类型声明与标注、类型推断及作用域等核心概念。"
keywords: [ArkTS, 基础知识, const, let, 类型标注, 类型推断, 作用域]
doctype: guide
status: active
---

# 基础知识
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

ArkTS是基于TypeScript的扩展语言，专为OpenHarmony应用开发设计。本章介绍ArkTS的基础知识，包括常量与变量、注释、分号、类型、作用域等核心概念。

## 常量与变量

ArkTS使用`const`声明不可重新赋值的常量、`let`声明可重新赋值的变量。选择准则：默认使用`const`，仅在需要重新赋值时改用`let`，这遵循最小权限原则——不打算修改的数据不应被意外写入。`const`保证变量绑定不变，但对象类型的`const`仅锁定引用，对象内部属性仍可修改（如`const arr = []; arr.push(1)`合法）。

### 声明

ArkTS使用`let`和`const`声明变量与常量。

<!-- @[variable_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let count: number = 10;
let name: string = 'ArkTS';
let isActive: boolean = true;

// 可重新赋值
let message: string = 'Hello';
message = 'Hello, ArkTS';
```

与`let`不同，`const`声明的绑定不可重新赋值，但对于引用类型，对象内部属性仍可修改。

<!-- @[ts_const_reassignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Basics.ts) -->

``` TypeScript
const MAX_SIZE: number = 100;
const APP_NAME: string = 'MyApp';

// 常量必须初始化
const value: number = 10;  // 正确

// 引用类型：引用不变，内容可修改
const numbers: number[] = [1, 2, 3];
numbers.push(4);           // 合法
numbers = [5, 6];          // 编译错误
```

### 命名

标识符由字母、数字、下划线和`$`组成，不能以数字开头，不能使用[保留关键字](#保留关键字)。变量、类、常量等各场景的命名约定详见[ArkTS编程规范](arkts-coding-style-guide.md#命名)。

<!-- @[ts_illegal_naming](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Basics.ts) -->

``` TypeScript
// 合法命名
let validName: number = 1;
let _private: number = 2;
let $special: number = 3;
let camelCase: number = 4;

// 非法命名
let 123start: number = 1;    // 数字开头
let my-var: number = 2;      // 包含连字符
let class: number = 3;       // 保留关键字
```

### 保留关键字

以下关键字在ArkTS中具有特殊语义，不能用作标识符名称。

| 类别 | 关键字 |
| --- | --- |
| 控制流 | `break` `case` `catch` `continue` `default` `do` `else` `finally` `for` `if` `of` `return` `switch` `throw` `try` `while` |
| 声明 | `class` `const` `declare` `enum` `export` `extends` `function` `import` `interface` `let` `type` `var` |
| 修饰符与访问器 | `abstract` `get` `private` `protected` `public` `readonly` `set` `static` |
| 运算符与操作 | `delete` `in` `instanceof` `new` `super` `this` `typeof` `void` |
| 值 | `false` `null` `true` |
| 其他 | `as` `async` `await` `debugger` `implements` `package` `with` `yield` |

### 打印

`console`提供多种输出方式：`console.info`输出一般信息，`console.warn`输出警告，`console.error`输出错误，`console.log`输出日志。`console.info`是`console.log`的别名，两者行为一致。

推荐使用`console.info`属于编码风格建议而非语言限制，目的是与`console.warn`、`console.error`等按级别命名的方法保持一致，让日志意图更清晰。开发调试时可用模板字面量拼接变量值，或用`JSON.stringify`输出对象。

<!-- @[variable_output](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let outputName: string = 'ArkTS';
const version: number = 1.0;

console.info(`${outputName}`);              // 'ArkTS'
console.info(`${version}`);      // 1
console.info(`Name: ${outputName}`);   // 'Name: ArkTS'
console.info(`Version: ${version}, Name: ${outputName}`);  // 'Version: 1, Name: ArkTS'
console.warn(`Version: ${version}, Name: ${outputName}`);  // 'Version: 1, Name: ArkTS'
console.error('Invalid input');        // 'Invalid input'
```

调试时建议根据信息级别选择对应方法，并用模板字符串或`JSON.stringify`格式化复杂对象输出。

## 注释

ArkTS支持单行注释（//）和多行注释（/* */），用于解释代码意图。

### 单行注释

单行注释使用//开始，用于简短说明或临时禁用代码。

<!-- @[single_line_comment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let commentCount: number = 10;  // 单行注释
```

### 多行注释

多行注释使用/* */包裹，用于详细说明或大段代码注释。

<!-- @[multi_line_comment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
/*
 * 多行注释
 * 可以跨越多行
 */
function calculate(): number {
  return 100;
}
```

### 文档注释

文档注释使用/** */包裹，用于生成API文档和类型提示。

<!-- @[documentation_comment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
/**
 * 计算两个数的和
 * @param a 第一个数
 * @param b 第二个数
 * @returns 两数之和
 */
function add(a: number, b: number): number {
  return a + b;
}
```

## 分号

每条语句末尾推荐使用分号结束，提高代码一致性和可读性。多条语句写在同一行时，分号是必须的。

<!-- @[semicolon_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let x: number = 10;
let y: number = 20;

// 同一行多个语句需要分号
let a: number = 1; let b: number = 2;

// 语句块末尾的分号可选
function greet(): void {
  console.info('Hello');
}
```

## 类型

ArkTS提供`number`、`boolean`、`string`等基础数据类型，约束值的范围和操作。各数据类型的详细介绍见[类型系统](arkts-language-guide-types.md)；数组见[集合](arkts-language-guide-collection-types.md)，枚举见[枚举](arkts-language-guide-enums.md)。

### 类型声明

类型声明通过类型标注在编译期约束变量、参数和返回值的类型，使编译器能在运行前发现类型不匹配的错误（如将`string`赋给`number`变量），而非等到运行时才暴露。除下文介绍的类型标注（`: type`）外，ArkTS还支持类型别名（`type Name = ...`）和接口声明（`interface`）两种形式，详见[类型系统](arkts-language-guide-types.md)和[接口](arkts-language-guide-interfaces.md)。

### 类型标注

通过类型标注（`: type`）为变量、参数和返回值标注类型。

<!-- @[type_annotation_examples](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// 变量类型
let annotExAge: number = 0;

// 函数参数和返回值类型
function annotExGreet(name: string): string {
  return `Hello, ${name}`;
}

// 类属性类型
class User {
  public id: number = 0;
  public name: string = '';
}
```

公共API和复杂类型（联合、泛型）应显式标注，简单局部变量可依赖类型推断（详见[类型推断](#类型推断)）。

### 类型推断

类型推断是编译器根据上下文自动推导变量或表达式的类型，无需开发者显式标注。ArkTS在大多数场景下支持类型推断，合理使用可减少冗余标注。

变量赋值时，编译器根据右侧值推断左侧类型。

<!-- @[type_inference_variables](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let tiCount = 10;        // 推断为number
let tiMessage = 'hello'; // 推断为string
let tiItems = [1, 2, 3]; // 推断为number[]
```

`const`声明的变量推断为字面量类型，`let`声明的变量推断为宽泛类型。

<!-- @[type_inference_const_let](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
const tiPi = 3.14;   // 推断为3.14（字面量类型）
let tiRatio = 3.14;  // 推断为number（宽泛类型）
```

当多个候选类型存在时，编译器从中选择最通用的类型。数组包含多种类型的元素（如数值与`null`混用）时，ArkTS会将数组字面量自动推断为所有元素类型的联合数组（如`(number | null)[]`），无需显式标注。

<!-- @[type_inference_best_common](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let tiMixed = [0, 1, null]; // 自动推断为(number | null)[]，无需显式标注
let tiNames: string[] = ['Alice', 'Bob'];      // 推断为string[]
```

如果数组中某个元素的类型无法推导（如未标注类型的对象字面量），类型推断会失败，需要开发者显式标注数组类型，或对元素进行类型断言后再放入数组。

## 作用域规则

作用域决定变量的可见性和生命周期。ArkTS不支持`var`声明变量，变量声明统一使用`let`和`const`，两者均具有块级作用域；函数的参数以及在函数内部声明的变量和嵌套函数，在函数外部不可访问，由此构成函数作用域。

### let/const声明（块级作用域）

`let`和`const`声明的变量具有块级作用域，声明前不可访问，且不允许在同一作用域内重复声明。

<!-- @[let_const_block_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
function blockScope(): void {
  let bsA: number = 10;
  const bsB: number = 20;
  if (true) {
    let bsA: number = 30; // 内层作用域的独立变量，不影响外层
    console.info(`${bsA}`); // 30
    console.info(`${bsB}`); // 20，可访问外层
  }
  console.info(`${bsA}`); // 10
}
```

### 嵌套作用域

内层作用域可访问外层变量，反之不行。`let`/`const`在嵌套块中可遮蔽外层同名变量。

<!-- @[nested_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let nsOuter: string = 'outer';

function nestedScope(): void {
  let nsInner: number = 100;
  console.info(`${nsOuter}`); // 可访问外层

  if (true) {
    let nsInner: number = 200; // 遮蔽外层nsInner
    console.info(`${nsInner}`); // 200
  }
  console.info(`${nsInner}`); // 100
}
```
