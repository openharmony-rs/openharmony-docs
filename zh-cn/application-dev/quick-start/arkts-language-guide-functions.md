---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "讲解ArkTS函数的声明与调用方式，涵盖参数、返回值、函数类型及闭包、箭头函数、重载、高阶函数等特性。"
keywords: [ArkTS, 函数, 参数, 返回值, 闭包, 箭头函数, 函数重载, 高阶函数, 调用签名]
doctype: guide
status: active
---

# 函数
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

ArkTS提供丰富的函数特性，包括参数、返回值、类型定义、重载、高阶函数等。

## 函数的声明与调用

函数通过`function`关键字声明，包含函数名、参数列表、返回类型和函数体，通过函数名加括号调用。函数的作用体现在四个方面：将重复逻辑封装以避免代码冗余、将复杂操作封装以提供清晰接口、将大任务分解为小函数以便管理和测试、隐藏实现细节只暴露必要接口。由此带来的好处是提高复用性（一次编写多处调用）、增强可读性（函数名直观表达功能）、易于维护（修改一处所有调用点生效）、便于测试（独立函数更易单独测试调试）。

### 函数的基本语法结构

ArkTS函数通过`function`关键字声明，支持类型标注的参数和返回值、可选/默认/剩余参数、函数类型、重载和高阶函数等特性。

<!-- @[function_declaration_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 基本函数声明
function add(a: number, b: number): number {
  return a + b;
}

// 函数调用
let result: number = add(1, 2);

// 无返回值函数
function logMessage(message: string): void {
  console.info(`${message}`);
}

logMessage('Hello, ArkTS');

// 简单计算函数
function multiply(x: number, y: number): number {
  return x * y;
}

let product: number = multiply(5, 3);  // 15

// 复杂逻辑函数
function calculateArea(width: number, height: number): number {
  let area: number = width * height;
  return area;
}

let area: number = calculateArea(10, 20);  // 200
```

ArkTS要求函数参数显式标注类型（省略将因隐式`any`编译报错）；返回类型多数场景可推断，但当`return`表达式是对返回类型未标注的函数或方法进行调用时，必须显式标注返回类型（如递归函数）。在上下文类型推断的场景中（如回调函数参数），编译器可根据函数签名自动推断参数类型，此时可省略回调参数的类型标注。返回类型为`void`的函数可省略`return`，或使用`return;`提前退出。

### 函数名与参数命名规范

函数名使用camelCase动词短语（如`calculateTotal`、`validateInput`），应描述"做什么"而非"怎么做"；参数名使用描述性名词，避免缩写和无意义命名。

<!-- @[function_naming_conventions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 函数名：动词或动词短语，camelCase
function calculateTotal() {}
function validateInput() {}
function processData() {}
function fetchUserInfo() {}

// 参数名：名词，camelCase，描述性
function greet(userName: string): string {
  return `Hello, ${userName}`;
}

function calculateDistance(startPoint: Point, endPoint: Point): number {
  return Math.sqrt(
    Math.pow(endPoint.x - startPoint.x, 2) +
    Math.pow(endPoint.y - startPoint.y, 2)
  );
}

interface Point {
  x: number;
  y: number;
}

// 避免无意义命名
// 反例：function f(a, b) {}
// 推荐：function calculateSum(firstValue: number, secondValue: number) {}
```

命名是约定而非编译约束：命名不当仅降低可读性；但注意省略参数类型标注（如`function f(a, b)`）会因隐式`any`直接编译报错。ArkTS中函数和参数用camelCase，类型（如`Point`）用PascalCase。

### 函数的调用方式

函数支持直接调用、嵌套调用和条件调用。嵌套调用在函数内部调用其他函数，函数的返回值也可以直接作为其他调用的实参，适合组合复杂逻辑。

<!-- @[function_invocation_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 直接调用
function sayHello(): void {
  console.info('Hello');
}

sayHello();

// 带参数调用
function invokeGreet(name: string): void {
  console.info(`Hello, ${name}`);
}

invokeGreet('Alice');

// 带返回值调用
function invokeAdd(a: number, b: number): number {
  return a + b;
}

let sum: number = invokeAdd(1, 2);

// 嵌套调用
function double(x: number): number {
  return x * 2;
}

let invokeResult: number = double(double(5));  // 20

// 条件调用
function invokeProcessData(data: string | null): void {
  if (data !== null) {
    processValidData(data);
  }
}

function processValidData(data: string): void {
  console.info(`${data}`);
}
```

嵌套调用的求值顺序为由内向外：`double(double(5))`先求`double(5)`得10，再求`double(10)`得20。嵌套调用要求内层函数的返回类型与外层函数的参数类型匹配，类型不一致会在编译期报错。条件调用将"是否调用"与"调用什么"解耦，是后续可选链调用（`?.()`）的基础模式。

## 函数的参数

函数参数包括形参（声明中的参数名和类型）和实参（调用时传入的值），ArkTS支持可选参数、默认参数和剩余参数。

### 形参和实参的对应关系

形参是函数声明中的参数名，实参是调用时传入的值，按位置一一对应。

<!-- @[parameters_formal_and_actual](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 形参（形式参数）：函数定义时的参数
function addNumbers(a: number, b: number): number {
  return a + b;
}

// 实参（实际参数）：函数调用时传入的值
let paramsResult: number = addNumbers(1, 2);
console.info(`${paramsResult}`); // 3

// 参数数量必须匹配
// addNumbers(1);        // 编译错误：缺少参数
// addNumbers(1, 2, 3);  // 编译错误：参数过多

// 参数类型必须匹配
// addNumbers('1', '2');  // 编译错误：类型不匹配
```

### 可选参数

可选参数使用`?`标记，表示调用时可以省略该参数。在类型层面，可选参数的类型为`T | undefined`——传入时为`T`，省略时为`undefined`。因此函数体内访问可选参数前须检查`!== undefined`，或使用空值合并`??`提供默认值。注意：可选参数必须排在必选参数之后。

<!-- @[optional_parameters](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 可选参数
function paramsGreet(name: string, title?: string): string {
  if (title !== undefined) {
    return `Hello, ${title} ${name}`;
  }
  return `Hello, ${name}`;
}

paramsGreet('Alice');           // "Hello, Alice"
paramsGreet('Alice', 'Dr.');    // "Hello, Dr. Alice"

// 可选参数必须在必需参数之后
function buildMessage(
  content: string,
  prefix?: string,
  suffix?: string
): string {
  let result: string = content;
  // 检查可选参数
  if (prefix !== undefined) {
    result = prefix + result;
  }
  if (suffix !== undefined) {
    result = result + suffix;
  }
  return result;
}

buildMessage('Hello');           // "Hello"
buildMessage('Hello', '[');      // "[Hello"
buildMessage('Hello', '[', ']'); // "[Hello]"
```

### 默认参数

为参数指定默认值，调用时若未传入该参数则使用默认值，可与可选参数混用。

<!-- @[default_parameters](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 默认参数
function paramsGreet2(name: string, greeting: string = 'Hello'): string {
  return `${greeting}, ${name}`;
}

paramsGreet2('Alice');              // "Hello, Alice"
paramsGreet2('Alice', 'Hi');        // "Hi, Alice"

// 默认参数可以与可选参数混用
function createMessage(
  content: string,
  prefix: string = '[INFO]',
  suffix?: string
): string {
  let message: string = `${prefix} ${content}`;
  if (suffix !== undefined) {
    message = message + suffix;
  }
  return message;
}

createMessage('Hello');           // "[INFO] Hello"
createMessage('Hello', '[WARN]'); // "[WARN] Hello"
createMessage('Hello', '[WARN]', '!'); // "[WARN] Hello!"

// 默认值可以是表达式
function createTimer(
  interval: number = 60 * 1000,
  callback: () => void = () => {}
): Timer {
  return {
    interval: interval,
    callback: callback,
    start: () => {}
  };
}

interface Timer {
  interval: number;
  callback: () => void;
  start: () => void;
}

// 默认值使用其他参数
function calculatePrice(
  basePrice: number,
  taxRate: number = 0.1,
  discount: number = basePrice * 0.05
): number {
  return basePrice + basePrice * taxRate - discount;
}

calculatePrice(100);      // 100 + 10 - 5 = 105
calculatePrice(100, 0.2); // 100 + 20 - 5 = 115
```

### 剩余参数（可变参数）

使用`...`语法定义剩余参数，将不定数量的参数收集为数组，实现参数数量可变。函数只能在参数列表末尾定义一个剩余参数。

<!-- @[rest_parameters](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 剩余参数
function restSum(...values: number[]): number {
  let total: number = 0;
  for (let value of values) {
    total += value;
  }
  return total;
}

restSum(1);           // 1
restSum(1, 2);        // 3
restSum(1, 2, 3);     // 6
restSum(1, 2, 3, 4);  // 10

// 剩余参数与普通参数结合
function greetAll(greeting: string, ...names: string[]): string {
  let result: string = '';
  for (let name of names) {
    result += `${greeting}, ${name}\n`;
  }
  return result;
}

greetAll('Hello', 'Alice', 'Bob', 'Charlie');
// Hello, Alice
// Hello, Bob
// Hello, Charlie
```

## 函数的返回值

本节介绍`void`函数、单返回值、多返回值（元组）和可选返回值（`T | undefined`）等不同返回模式。

### 无返回值函数（void类型）

`void`函数不返回值，用于执行操作但不产生结果。

<!-- @[void_type_functions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// void类型函数
function log(message: string): void {
  console.info(`${message}`);
}

function notify(message: string): void {
  alert(message);
}

function alert(message: string): void {
  console.info(`Alert: ${message}`);
}

// void函数可以提前返回
function process(data: string | null): void {
  if (data === null) {
    return;  // 提前退出
  }
  console.info(`${data}`);
}

// void函数可以省略return
function initialize(): void {
  let config: FunctionsConfig = loadConfig();
  setupEnvironment(config);
}

function loadConfig(): FunctionsConfig {
  return { debug: false };
}

function setupEnvironment(config: FunctionsConfig): void {
  console.info('Environment setup');
}

interface FunctionsConfig {
  debug: boolean;
}
```

### 单返回值函数

函数通过`return`返回单个值，返回类型可为基本类型、对象或数组。

<!-- @[return_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 返回基本类型
function typesAdd(a: number, b: number): number {
  return a + b;
}

function concat(a: string, b: string): string {
  return a + b;
}

function isPositive(value: number): boolean {
  return value > 0;
}

// 返回对象
function createConfig(): TypesConfig {
  return {
    apiUrl: 'EXAMPLE_API_URL',
    timeout: 5000,
    retries: 3
  };
}

interface TypesConfig {
  apiUrl: string;
  timeout: number;
  retries: number;
}

// 返回数组
function getNumbers(): number[] {
  return [1, 2, 3, 4, 5];
}

// 返回类实例
function typesCreateUser(id: number): TypesUser {
  let user: TypesUser = new TypesUser();
  user.id = id;
  user.name = 'TypesUser';
  return user;
}

class TypesUser {
  public id: number = 0;
  public name: string = '';
}
```

### 多返回值函数（使用元组承载）

通过数组或元组类型返回多个值，调用方按索引逐个获取各返回项。

<!-- @[multiple_return_values](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 使用数组承载多个返回值
function divideWithRemainder(a: number, b: number): number[] {
  let quotient: number = Math.floor(a / b);
  let remainder: number = a % b;
  return [quotient, remainder];
}

let valsResult: number[] = divideWithRemainder(10, 3);
let quotient: number = valsResult[0];  // 3
let remainder: number = valsResult[1]; // 1

// 使用元组类型
function minMax(arr: number[]): [number, number] {
  let min: number = arr[0];
  let max: number = arr[0];
  
  for (let value of arr) {
    if (value < min) {
      min = value;
    }
    if (value > max) {
      max = value;
    }
  }
  
  return [min, max];
}

let bounds: [number, number] = minMax([1, 5, 3, 9, 2]);
let minVal: number = bounds[0];  // 1
let maxVal: number = bounds[1];  // 9

// 返回结果和状态
function tryParseInt(str: string): [number, boolean] {
  let parsed: number = Number.parseInt(str, 10);
  let success: boolean = !Number.isNaN(parsed);
  return [parsed, success];
}

let parsed: [number, boolean] = tryParseInt('42');
let value: number = parsed[0];     // 42
let success: boolean = parsed[1];  // true

// 返回数据和错误
function fetchData(id: number): [Data | null, Error | null] {
  if (id <= 0) {
    return [null, new Error('Invalid ID')];
  }
  return [{ id: id, content: 'data' }, null];
}

interface Data {
  id: number;
  content: string;
}

let dataResult: [Data | null, Error | null] = fetchData(1);
let data: Data | null = dataResult[0];
let error: Error | null = dataResult[1];
```

### 可选返回值函数（T | undefined类型）

返回类型为`T | undefined`的函数，表示结果可能不存在。

<!-- @[optional_return_values](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
interface OrvUser {
  id: number;
  name: string;
  active: boolean;
}

// 返回可能为undefined
function findUser(id: number): OrvUser | undefined {
  if (id <= 0) {
    return undefined;
  }
  let users: OrvUser[] = [
    { id: 1, name: 'Alice', active: true },
    { id: 2, name: 'Bob', active: false }
  ];
  
  for (let valsUser of users) {
    if (valsUser.id === id) {
      return valsUser;
    }
  }
  return undefined;
}

let orvUser: OrvUser | undefined = findUser(1);
if (orvUser !== undefined) {
  console.info(`${orvUser.name}`);
} // Alice

// 查找函数
function findFirst(arr: number[], predicate: (n: number) => boolean): number | undefined {
  for (let value of arr) {
    if (predicate(value)) {
      return value;
    }
  }
  return undefined;
}

let first: number | undefined = findFirst([1, 2, 3, 4], (n: number): boolean => n > 2);
console.info(`${first}`); // 3

// 获取元素
function getElement(arr: string[], index: number): string | undefined {
  if (index < 0 || index >= arr.length) {
    return undefined;
  }
  return arr[index];
}

let element: string | undefined = getElement(['a', 'b', 'c'], 1);
console.info(`${element}`); // 'b'

// 返回null或值
function getConfigValue(key: string): string | null {
  let config: Map<string, string> = new Map<string, string>();
  config.set('apiUrl', 'EXAMPLE_API_URL');
  config.set('timeout', '5000');
  
  let value: string | undefined = config.get(key);
  if (value !== undefined) {
    return value;
  }
  return null;
}
```

## 递归函数

递归函数是在函数体内调用自身的函数，适合处理可分解为同构子问题的问题，如阶乘、斐波那契数列、树结构遍历等。递归函数必须包含基线条件（终止条件）：满足基线条件时直接返回结果、不再递归；缺少基线条件或基线条件不可达会导致无限递归，引发调用栈溢出。

<!-- @[recursive_factorial](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 阶乘：n! = n * (n-1)!
function factorial(n: number): number {
  if (n <= 1) {
    return 1;  // 基线条件：终止递归
  }
  return n * factorial(n - 1);  // 递归调用
}

console.info(`${factorial(5)}`);  // 120

// 斐波那契数列：fib(n) = fib(n-1) + fib(n-2)
function fibonacci(n: number): number {
  if (n <= 1) {
    return n;  // 基线条件
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}

console.info(`${fibonacci(10)}`);  // 55
```

### 尾递归

尾递归指递归调用是函数体中的最后一个操作，其返回值直接作为当前函数的返回值，不再有后续计算。普通递归（如`n * factorial(n - 1)`）在递归调用返回后还需执行乘法，外层调用的栈帧需要保留，调用栈随递归深度增长；尾递归将中间结果通过参数传递给下一次调用，当前调用没有未完成的计算。部分语言和编译器支持尾调用优化，将尾递归转换为循环执行，从而避免栈溢出；递归深度较大时，也可以直接改写为循环实现。

<!-- @[tail_vs_normal_recursion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 普通递归：递归调用返回后还需执行乘法，调用栈随深度增长
function factorialNormal(n: number): number {
  if (n <= 1) {
    return 1;
  }
  return n * factorialNormal(n - 1);
}

// 尾递归：累积结果通过acc参数传递，递归调用是最后一个操作
function factorialTail(n: number, acc: number = 1): number {
  if (n <= 1) {
    return acc;
  }
  return factorialTail(n - 1, n * acc);
}

console.info(`${factorialNormal(5)}`);  // 120
console.info(`${factorialTail(5)}`);    // 120
```

## 箭头函数与函数类型

函数在ArkTS中是一等公民：既可以通过`function`关键字声明具名函数，也可以通过箭头函数（lambda表达式）定义匿名函数。函数拥有独立的类型，使用`(param1: paramType1, param2: paramType2, ...) => returnType`描述参数与返回值签名，可作为变量、参数和属性的类型；函数可以赋值给变量、作为参数传递或作为返回值返回，支持函数式编程范式。

### 箭头函数（lambda）的定义

箭头函数（lambda表达式）是定义函数的简洁语法：括号内为参数列表及可选的返回类型标注，后跟`=>`和函数体。函数体为单表达式时，可以省略花括号和`return`。箭头函数常与函数类型标注配合使用。

<!-- @[arrow_function_body_forms](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 块体形式：花括号内显式return
let addFn: (a: number, b: number) => number = (a: number, b: number): number => {
  return a + b;
};

// 表达式体形式：单表达式省略花括号和return
let doubleFn: (value: number) => number = (value: number): number => value * 2;
```

### 函数类型的定义与匹配规则

函数类型赋值时需要满足函数的子类型规则，即参数类型逆变（父类型），返回值类型协变（子类型）。

<!-- @[ts_function_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Functions.ts) -->

``` TypeScript
// 函数类型定义
type MathOperation = (a: number, b: number) => number;

let add: MathOperation = (a: number, b: number): number => {
  return a + b;
};

let subtract: MathOperation = (a: number, b: number): number => {
  return a - b;
};

let multiply: MathOperation = (a: number, b: number): number => {
  return a * b;
};

// 函数类型必须匹配参数和返回值
type GreetingFunction = (name: string) => string;

let greet: GreetingFunction = (name: string): string => {
  return `Hello, ${name}`;
};

// 不匹配的类型会编译错误
let invalid: MathOperation = (a: string) => a; // 编译错误
```

### 函数类型作为参数

将函数作为参数（回调函数）传递，可实现自定义的比较器、过滤器、事件处理器等灵活逻辑。

<!-- @[functions_as_parameters](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 函数作为参数
type MathOperation = (a: number, b: number) => number;
function addNumbersOp(a: number, b: number): number {
  return a + b;
}
function subtractNumbers(a: number, b: number): number {
  return a - b;
}
function multiplyNumbersOp(a: number, b: number): number {
  return a * b;
}
function calculate(a: number, b: number, operation: MathOperation): number {
  return operation(a, b);
}

let paramsSum: number = calculate(10, 5, addNumbersOp);       // 15
let diff: number = calculate(10, 5, subtractNumbers); // 5
let prod: number = calculate(10, 5, multiplyNumbersOp); // 50
console.info(`${paramsSum}, ${diff}, ${prod}`); // 15, 5, 50

// 回调函数
function paramsProcessData(
  data: string[],
  processor: (item: string) => string
): string[] {
  let result: string[] = [];
  for (let item of data) {
    result.push(processor(item));
  }
  return result;
}

let processed: string[] = paramsProcessData(
  ['hello', 'world'],
  (s: string): string => s.toUpperCase()
);
console.info(`${processed[0]}, ${processed[1]}`); // 'HELLO, WORLD'

// 条件判断函数
function filterNumbers(
  numbers: number[],
  predicate: (n: number) => boolean
): number[] {
  let result: number[] = [];
  for (let num of numbers) {
    if (predicate(num)) {
      result.push(num);
    }
  }
  return result;
}

let evens: number[] = filterNumbers([1, 2, 3, 4, 5, 6], (n: number): boolean => n % 2 === 0);
console.info(`${evens.join(', ')}`); // 2, 4, 6
```

### 函数类型作为返回值

函数可以作为返回值，用于创建闭包（捕获外层变量）、工厂函数（按参数生成不同行为）和延迟执行的策略模式。

<!-- @[functions_returning_functions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
type RetMathOperation = (a: number, b: number) => number;

// 返回函数
function getOperation(type: string): RetMathOperation {
  switch (type) {
    case 'add':
      return (a: number, b: number): number => a + b;
    case 'subtract':
      return (a: number, b: number): number => a - b;
    case 'multiply':
      return (a: number, b: number): number => a * b;
    default:
      return (a: number, b: number): number => 0;
  }
}

let frfOperation: RetMathOperation = getOperation('add');
let functionsResult: number = frfOperation(5, 3);
console.info(`${functionsResult}`); // 8

// 创建器函数
function createMultiplier(factor: number): (n: number) => number {
  return (n: number): number => n * factor;
}

let functionsDouble: (n: number) => number = createMultiplier(2);
let triple: (n: number) => number = createMultiplier(3);

console.info(`${functionsDouble(5)}`); // 10
console.info(`${triple(5)}`); // 15

// 创建比较器
function createComparator(ascending: boolean): (a: number, b: number) => number {
  if (ascending) {
    return (a: number, b: number): number => a - b;
  }
  return (a: number, b: number): number => b - a;
}

let ascComparator: (a: number, b: number) => number = createComparator(true);
let descComparator: (a: number, b: number) => number = createComparator(false);
```

### 类型别名简化函数类型

用`type`为复杂函数类型起别名，简化签名书写。

<!-- @[function_type_aliases](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 使用类型别名
type MyCallback = (result: string) => void;
type Predicate = (value: number) => boolean;
type Transformer = (input: string) => string;
type Comparator = (a: number, b: number) => number;

// 简化复杂函数类型
type EventHandler = (event: MyEvent) => void;

interface MyEvent {
  type: string;
  data: string | number | boolean;
}

function addEventListener(handler: EventHandler): void {
  // 注册事件处理器
}
```

## 闭包

闭包是函数与其词法环境的组合。ArkTS不使用局部函数声明来构造闭包，但局部箭头函数仍然可以捕获外层作用域中的变量和参数。

### 闭包的形成

内层箭头函数捕获外层作用域的变量，即使外层函数已返回，捕获的变量仍保留状态。

<!-- @[closure_counter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
function createCounter(): () => number {
  let count: number = 0;

  let increment: () => number = (): number => {
    count++;
    return count;
  };

  return increment;
}

let counter: () => number = createCounter();
console.info(`${counter()}`);  // 1
console.info(`${counter()}`);  // 2
console.info(`${counter()}`);  // 3
```
在上例中，`increment`捕获了`createCounter`中的`count`。即使`createCounter`已经返回，`counter`仍然可以继续读取并更新这个状态。

### 捕获外层参数

闭包可捕获外层函数的参数，返回的函数持续引用该参数并据此处理后续调用。

<!-- @[closure_multiplier](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
function multiplierCreateMultiplier(factor: number): (value: number) => number {
  let multiply: (value: number) => number = (value: number): number => {
    return value * factor;
  };

  return multiply;
}

let multiplierDouble: (value: number) => number = multiplierCreateMultiplier(2);
console.info(`${multiplierDouble(5)}`);  // 10
```
闭包适合保存少量配置或状态。若状态较多、生命周期复杂，优先使用类来表达。

### 箭头函数中的this

箭头函数不绑定自己的`this`，而是捕获外层作用域的`this`，适合在类方法中作回调。

<!-- @[arrow_function_this_binding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
class BindingTimer {
  private seconds: number = 0;

  start(): void {
    mySetInterval((): void => {
      this.seconds++;
      console.info(`${this.seconds.toString()}`);
    }, 1000);
  }
}

// 示意桩：同步模拟异步定时调用，实际开发中请使用系统或第三方异步定时接口
function mySetInterval(callback: () => void, ms: number): void {
  callback();
}
```
独立函数体内不应依赖`this`；需要实例状态时，使用类方法或显式参数传递。

## 函数的重载

函数重载允许同一函数名根据不同参数类型或数量提供多个调用签名，编译器根据传入参数自动匹配对应的签名。重载解决的问题是：当函数需要对不同类型执行相似但类型不同的操作时，避免使用`any`丢失类型安全。注意：实现签名对外不可见，调用方只能使用已声明的重载签名。当参数类型不同但逻辑相同时，优先使用联合类型而非重载。

### 函数重载的声明方式

函数重载先写多个签名（仅参数和返回值类型），最后用一个实现签名覆盖。

<!-- @[function_overloading](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 重载签名
function overloadGreet(name: string): string;
function overloadGreet(name: string, age: number): string;
function overloadGreet(name: string, age?: number): string {
  if (age !== undefined) {
    return `Hello, ${name} (${age} years old)`;
  }
  return `Hello, ${name}`;
}

overloadGreet('Alice');        // "Hello, Alice"
overloadGreet('Alice', 25);    // "Hello, Alice (25 years old)"

// 不同参数类型的重载
function overloadProcess(value: number): string;
function overloadProcess(value: string): number;
function overloadProcess(value: number | string): number | string {
  if (typeof value === 'number') {
    return `Number: ${value}`;
  }
  return value.length;
}

overloadProcess(42);     // "Number: 42"
overloadProcess('text'); // 4

// 多参数重载
function overloadCreatePoint(x: number): OverloadPoint;
function overloadCreatePoint(x: number, y: number): OverloadPoint;
function overloadCreatePoint(x: number, y?: number): OverloadPoint {
  return {
    x: x,
    y: y !== undefined ? y : 0
  };
}

interface OverloadPoint {
  x: number;
  y: number;
}

let point1: OverloadPoint = overloadCreatePoint(10);
console.info(`${JSON.stringify(point1)}`);  // '{"x":10,"y":0}'
let point2: OverloadPoint = overloadCreatePoint(10, 20);
console.info(`${JSON.stringify(point2)}`);  // '{"x":10,"y":20}'
```

### 重载签名与实现签名的匹配

通过多个签名声明同一函数的不同调用形式，实现签名必须兼容所有重载签名。

<!-- @[overload_signatures](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 实现签名必须兼容所有重载签名
interface NumberValue {
  value: number;
}

interface StringValue {
  value: string;
}

type NumericOrTextValue = NumberValue | StringValue;

function sigGetValue(obj: NumberValue): number;
function sigGetValue(obj: StringValue): string;
function sigGetValue(obj: NumericOrTextValue): number | string {
  return obj.value;
}

// 重载顺序：更具体的类型先声明
function sigConvert(value: string): number;
function sigConvert(value: number): string;
function sigConvert(value: string | number): string | number {
  if (typeof value === 'string') {
    return Number.parseInt(value, 10);
  }
  return value.toString();
}

// 重载与联合类型
function sigFormat(input: string): string;
function sigFormat(input: number): string;
function sigFormat(input: string | number): string {
  if (typeof input === 'string') {
    return input.toUpperCase();
  }
  return input.toFixed(2);
}
```

### 函数重载的类型约束

重载签名之间必须类型兼容，实现签名需统一处理所有情况，调用方只能按已声明的签名调用。优先使用联合类型而非重载。

<!-- @[overload_type_constraints](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
interface OverloadData {
  id: number;
  type: string;
  name?: string;
}

// 重载签名必须类型兼容，实现签名统一处理所有情况
function getData(id: number): OverloadData;
function getData(name: string): OverloadData;
function getData(idOrName: number | string): OverloadData {
  if (typeof idOrName === 'number') {
    return { id: idOrName, type: 'numeric' };
  }
  return { id: 0, type: 'named', name: idOrName };
}

let otcData1: OverloadData = getData(1);
let otcData2: OverloadData = getData('test');
console.info(`${otcData1.id}, ${otcData2.type}`); // '1, named'

// 返回类型不同的重载
function parseInput(input: string): number;
function parseInput(input: string, format: string): Date;
function parseInput(input: string, format?: string): number | Date {
  if (format !== undefined) {
    return new Date(input);
  }
  return Number.parseInt(input, 10);
}

let parsedNum: number = parseInput('42');
let parsedDate: Date = parseInput('2024-01-01', 'date');
console.info(`${parsedNum}`); // 42
```

## 泛型函数

泛型函数在函数名后使用`<T>`声明类型参数，并在参数类型和返回值类型中使用该类型参数，使同一份函数体在保留类型检查的前提下适用于多种类型。调用泛型函数时可以显式指定类型参数，也可以由编译器根据实参自动推断。

<!-- @[generic_function_signature](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 泛型函数签名：T为类型参数，调用时确定具体类型
function firstOrDefault<T>(values: T[], defaultValue: T): T {
  if (values.length > 0) {
    return values[0];
  }
  return defaultValue;
}

let firstNum: number = firstOrDefault<number>([1, 2, 3], 0);  // 显式指定类型参数
let firstStr: string = firstOrDefault(['a', 'b'], 'none');    // 根据实参推断T为string
```

泛型的详细介绍（类型约束、泛型接口、泛型类等），请阅读[泛型](arkts-language-guide-generics.md)。

## 高阶函数

高阶函数是接受函数作为参数或返回函数的函数，常用于抽象遍历、过滤、映射等集合操作。

### 高阶函数的定义

高阶函数接受函数作为参数或返回函数作为结果，可将遍历、过滤、映射等集合操作抽象为可复用的通用逻辑。

<!-- @[higher_order_functions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 接受函数作为参数
function applyOperation(
  a: number,
  b: number,
  operation: (x: number, y: number) => number
): number {
  return operation(a, b);
}

applyOperation(5, 3, (x, y) => x + y);  // 8
applyOperation(5, 3, (x, y) => x * y);  // 15

// 返回函数
function createGreeter(greeting: string): (name: string) => string {
  return (name: string): string => `${greeting}, ${name}`;
}

let functionsSayHello: (name: string) => string = createGreeter('Hello');
let sayHi: (name: string) => string = createGreeter('Hi');

functionsSayHello('Alice');  // "Hello, Alice"
sayHi('Bob');       // "Hi, Bob"

// 既接受又返回函数
function compose<T, U, V>(
  f: (x: U) => V,
  g: (x: T) => U
): (x: T) => V {
  return (x: T): V => f(g(x));
}

let functionsDouble2 = (n: number): number => n * 2;
let addOne = (n: number): number => n + 1;

let doubleThenAddOne = compose(addOne, functionsDouble2);
doubleThenAddOne(5);  // 11
```

### 常用高阶函数（map、filter、reduce）

`map`对每个元素变换生成新数组，`filter`按条件筛选元素，`reduce`将数组归约为单个值。

<!-- @[array_higher_order_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// map：映射每个元素
let orderNumbers: number[] = [1, 2, 3, 4, 5];

let orderDoubled: number[] = orderNumbers.map((n: number): number => n * 2);
console.info(`${orderDoubled.join(', ')}`);  // 2, 4, 6, 8, 10

let squared: number[] = orderNumbers.map((n: number): number => n * n);
console.info(`${squared.join(', ')}`);  // 1, 4, 9, 16, 25

let strings: string[] = orderNumbers.map((n: number): string => `Item ${n}`);
console.info(`${strings.join(', ')}`);  // 'Item 1, Item 2, Item 3, Item 4, Item 5'

// filter：过滤元素
let orderEvens: number[] = orderNumbers.filter((n: number): boolean => n % 2 === 0);
console.info(`${orderEvens.join(', ')}`);  // 2, 4

let greaterThan3: number[] = orderNumbers.filter((n: number): boolean => n > 3);
console.info(`${greaterThan3.join(', ')}`);  // 4, 5

// reduce：归约数组
let orderSum: number = orderNumbers.reduce(
  (acc: number, n: number): number => acc + n,
  0
);
console.info(`${orderSum}`);  // 15

let orderProduct: number = orderNumbers.reduce(
  (acc: number, n: number): number => acc * n,
  1
);
console.info(`${orderProduct}`);  // 120

let orderMax: number = orderNumbers.reduce(
  (acc: number, n: number): number => acc > n ? acc : n,
  orderNumbers[0]
);
console.info(`${orderMax}`);  // 5

// 组合使用
let orderResult: number[] = orderNumbers
  .filter((n: number): boolean => n % 2 === 0)
  .map((n: number): number => n * 2);
console.info(`${orderResult.join(', ')}`);  // 4, 8
```

### 自定义高阶函数的实现

封装通用的遍历、过滤逻辑为高阶函数，通过回调参数实现灵活扩展。

<!-- @[custom_array_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
// 自定义map
function customMap<T, R>(arr: T[], mapper: (item: T) => R): R[] {
  let result: R[] = [];
  for (let item of arr) {
    result.push(mapper(item));
  }
  return result;
}

// 自定义filter
function customFilter<T>(arr: T[], predicate: (item: T) => boolean): T[] {
  let result: T[] = [];
  for (let item of arr) {
    if (predicate(item)) {
      result.push(item);
    }
  }
  return result;
}

// 自定义reduce
function customReduce<T, R>(
  arr: T[],
  reducer: (acc: R, item: T) => R,
  initial: R
): R {
  let accumulator: R = initial;
  for (let item of arr) {
    accumulator = reducer(accumulator, item);
  }
  return accumulator;
}

// 自定义forEach
function customForEach<T>(arr: T[], consumer: (item: T) => void): void {
  for (let item of arr) {
    consumer(item);
  }
}

// 自定义find
function customFind<T>(arr: T[], predicate: (item: T) => boolean): T | undefined {
  for (let item of arr) {
    if (predicate(item)) {
      return item;
    }
  }
  return undefined;
}
```

## 函数的可选链调用

可选链调用（?.()）在函数可能为`undefined`时安全调用，避免运行时错误。

### 函数的可选调用语法（func?.()）

`func?.()`在`func`不为`undefined`时才执行调用，否则返回`undefined`。

<!-- @[ts_optional_chaining_function_call](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Functions.ts) -->

``` TypeScript
// 可选调用函数
let callback: (() => void) | null = null;

callback?.();  // 不执行（callback为null）

callback = () => console.info(`Called`);
callback?.();  // 执行，输出 "Called"

// 方法可选调用
let service: Service | null = null;

service?.processData?.();  // 不执行

interface Service {
  processData?: () => void;
}

service = { processData: () => console.info(`Processing`) };
service?.processData?.();  // 执行

// 回调可选调用
function triggerEvent(callback?: () => void): void {
  callback?.();  // 安全调用
}

triggerEvent();  // 无回调，不执行
triggerEvent(() => console.info(`Event triggered`));  // 执行回调

// 对象方法可选调用
let handler: { onClick?: () => void } | null = null;

handler?.onClick?.();  // 不执行

handler = { onClick: () => console.info(`Clicked`) };
handler?.onClick?.();  // 执行
```

### 可选链调用的使用场景

可选链调用用于回调可能未注册、事件处理器可能未绑定的场景。

<!-- @[ts_optional_chaining_use_cases](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Functions.ts) -->

``` TypeScript
// 事件处理器
interface EventEmitter {
  emit?: (event: string) => void;
}

let emitter: EventEmitter | null = getEmitter();

function trigger(event: string): void {
  emitter?.emit?.(event);
}

function getEmitter(): EventEmitter | null {
  return null;
}

// 配置回调
interface Config {
  onSuccess?: (data: string) => void;
  onError?: (error: Error) => void;
}

function processWithCallbacks(config: Config): void {
  let result: string = 'data';
  config.onSuccess?.(result);

  // 或错误情况
  let error: Error = new Error('Failed');
  config.onError?.(error);
}

// 可选链式调用
interface Chain {
  next?: Chain;
  execute?: () => void;
}

let chain: Chain | null = { next: { execute: () => console.info(`Executed`) } };

chain?.next?.execute?.();  // 执行

// API响应处理
interface APIResponseData {
  items?: string[];
}

interface APIResponse {
  data?: APIResponseData;
  callback?: () => void;
}

let response: APIResponse | null = null;

response?.callback?.();  // 不执行
response?.data?.items?.forEach?.(item => console.info(`${item}`));
```

## void返回类型的赋值兼容性

`void`返回类型的函数类型有一个特殊规则：返回值为`void`的函数类型可接受返回任意值的函数实现。返回值会被忽略。此设计允许返回值的函数（如`push`返回`number`）用于期望`void`回调的场景。

<!-- @[void_return_compatibility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Functions.ets) -->

``` TypeScript
type VcCallback = () => void;

// 返回number的函数可赋给void返回类型
let vcCb: VcCallback = (): number => {
  console.info('side effect');
  return 42;
};

vcCb(); // 打印side effect，返回值42被忽略
```

此规则仅适用于返回值类型为`void`时，不适用于其他返回类型。常用于事件处理、回调注册等不需要返回值的场景。
