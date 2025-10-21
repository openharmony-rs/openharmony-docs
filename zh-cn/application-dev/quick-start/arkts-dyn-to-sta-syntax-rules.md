# ArkTS-Sta语法迁移规则

ArkTS-Sta在引入了静态类型系统、增强的并发能力的同时，也引入了与ArkTS-Dyn在语法和语义上的一部分差异。本文罗列了所有在ArkTS-Sta中被限制的ArkTS-Dyn特性，并提供了重构代码的建议。

## 限定关键字

**规则：** `arkts-invalid-identifier`

**规则解释：**

ArkTS-Sta中不能使用关键字或保留字作为变量、函数或类型的名称。

**变更原因：**

ArkTS-Sta严格定义了关键字和保留字，代码中不能将其用作变量、函数或类型的名称。

以下关键字不能用作变量或函数的名称：
```
abstract else internal static as enum launch switch async export let super await extends native this break false new throw case final null true class for override try const function package undefined constructor if private while continue implements protected default import public do interface return boolean double number Boolean Double Number byte float object Byte Float Object bigint int short Bigint Int Short char long string Char Long String void Intl
```
以下关键字不能用作类型的名称：
```
Awaited NoInfer Pick ConstructorParameters NonNullable ReturnType Exclude Omit ThisParameterType Extract OmitThisParameter ThisType InstanceType Parameters Capitalize Uncapitalize Lowercase Uppercase ArrayBufferTypes Function Proxy AsyncGenerator Generator ProxyHandler AsyncGeneratorFunction GeneratorFunction Symbol AsyncIterable IArguments TemplateStringsArray AsyncIterableIterator IteratorYieldResult TypedPropertyDescriptor AsyncIterator NewableFunction CallableFunction PropertyDescriptor Intl
```

**适配建议：**

请将用到关键字或保留字的变量、函数或类型重命名。

**示例：**

**ArkTS-Dyn**
```typescript
let as: number = 1;
const abstract: string = "abstract";
```

**ArkTS-Sta**
```typescript
let a = 1;
const abstract1: string = "abstract";
```

## 数值类型语义变化

**规则：** `arkts-numeric-semantic`

**规则解释：**

在ArkTS-Sta中，整型数字字面量默认是int类型，以提高执行效率。

**变更原因：**

在ArkTS-Dyn中只有一个数字基础类型number，不区分整型字面量或是浮点型字面量。

在ArkTS-Sta中，整型数字字面量默认是int类型，以提高执行效率。

**适配建议：**

在表达式中，若涉及除法操作或其他数值类型推导为number的情况，需将整型字面量显式修改为浮点型字面量，避免类型错误。

**示例：**

- 场景1，适用于直接给变量赋值的情况。如果该变量未曾作为number类型使用，则将传值的变量链上的声明都改为int，字面量保留为整型。否则，变量声明为number，字面量仍保留为整型。

- 场景2，对于字面量参与表达式给变量赋值的情况，需根据表达式具体情况处理。如果表达式中包含除法运算，则应将字面量转换为浮点类型，变量类型为number。用户自定义函数（async函数除外）直接赋值时，仅返回number类型，无需修改。SDK API可能返回int类型，但按第二节返回值场景处理，但由于SDK已处理，此规则无需再执行。

- 场景3，对于变量或常量被导出的情况，应将其声明为number类型。其他模块默认将变量视为number类型使用，如果将其更改为int类型，可能会导致调用该变量或常量的模块出现编译错误。

- 场景4，所有整型字面量在包含除法的表达式中，应修改为浮点数字面量。无论变量是数组、tuple还是其他容器中的一个值，表达式所赋值的变量都应保留为number类型。
   ```typescript
   // 公共代码
   function foo(a:number): number {
     return a - 1;
   }
   // ArkTS-Dyn
   let a = 1;
   let b = a;
   let c = 2;
   let d = 3;
   let e = foo(1); // foo的返回值为number，这里foo是开发者自定义函数，不是SDK函数。e要声明为number，因为类型推导会把e推导为number，所以不用改
   let f:number = 1; // f虽然被声明为number，但是上下文中一直作为int使用，那么应该将f的类型修改为int
   export let g:number = 1; // g被export，需要保留为number

   c = 1/2; // 变量c的赋值表达式里有除法，c需要声明为number类型，且表达式中的整型字面量也要修改为浮点型字面量
   d = 1.0; // 变量d又被赋值了浮点字面量，所以需要声明为number类型

   // ArkTS-Sta
   let a:int = 1;
   let b:int = a;
   let c:number = 2;
   let d:number = 3;
   let e:number = foo(1);
   let f:int = 1;
   export let g:number = 1;

   c = 1.0/2.0;
   d = 1.0;
   ```

- 场景5，tuple的情况。<br>
   - 不要改number类型，一律保留。
   - 赋值的情况，如果是整型字面量，不需要修改；如果表达式包含整型字面量和除法操作，需将整型字面量修改为浮点数字面量。
   ```typescript
   // ArkTS-Dyn
   let a : [number, number, boolean] = [1, 1, true];
   a = [2, 2, false];
   a = [2/3, 3/4, false];

   // ArkTS-Sta
   let a : [number, number, boolean] = [1, 1, true];
   a = [2, 2, false];
   a = [2.0/3.0, 3.0/4.0, false]; // 将整型字面量修改成浮点型字面量，否则结果和ArkTS-Dyn不一致
   ```

- 场景6，Array的情况。<br>
   - 不要更改number类型，一律保留。
   - 赋值的情况，如果是整型字面量，则不需要修改。但是如果是包含整型字面量和除法操作的表达式，则需要将整型字面量修改为浮点数字面量。
   ```typescript
   // ArkTS-Dyn
   let arr:number[] = [1, 2, 3];
   arr = [2, 3, 4];
   arr[0] = 2/3;
   arr = [1/3, 2/3, 4];

   // ArkTS-Sta
   let arr:number[] = [1, 2, 3];
   arr = [2, 3, 4];
   arr[0] = 2.0/3.0;
   arr = [1.0/3.0, 2.0/3.0, 4];
   ```

- 场景7，Array及相关操作符的使用情况。
   ```typescript
   // ArkTS-Dyn
   let arr:Array<number> = [1, 2, 3, 4];
   let arr2:Array<number> = arr??[0];
   let arr3:Array<number> = [1, 2, 3, 4];

   // ArkTS-Sta
   // 在ArkTS-Sta中，字面量数组的类型会根据上下文推导。例如，下面的例子中，arr被赋值的字面量数组[1, 2, 3, 4]
   // 因为arr的声明为Array<number>，所以字面量数组推导为number数组，并可以赋值给arr。
   // 数组字面量[1, 2, 3, 4]被赋值给arr3，因为arr3的声明为Array<int>，所以该字面量数组被推导为int数组，并可以被赋值给arr3
   // 当上下文无法推导时，根据数组元素类型进行推导。例如，arr??[0]中的[0]被推导为int数组，这样在将值赋给arr2时会导致错误，因为arr是number数组
   // arr??[0]的类型是Array<number> | Array<int>的联合类型，与arr2的声明类型不符，因此会导致编译错误，需要将0改为0.0
   let arr:Array<number> = [1, 2, 3, 4];
   let arr2:Array<number> = arr??[0.0]; // 将数组中的整型字面量修改为浮点型字面量
   let arr3:Array<int> = [1, 2, 3, 4];

   // 同理三元运算符的情况
   // ArkTS-Dyn
   let b:boolean = true;
   let arr:number[] = [1, 2, 3];
   let arr1:number[] = b? arr : [0, 1, 2];

   //ArkTS-Sta
   let b:boolean = true;
   let arr:number[] = [1, 2, 3];
   let arr1:number[] = b? arr : [0.0, 1.0, 2.0];
   let arr2:int[] = [1, 2, 3];
   ```

- 场景8，Enum中的整型字面量无需修复。
   ```typescript
   enum A {
     A1 = 1,
     A2 = 2,
     A3 = 3
   } // 都不要修复成浮点型字面量
   ```

- 场景9，字面量中的整型字面量，不论是ArkTS-Dyn还是ArkTS-Sta，字面量在赋值时，变量的类型决定了数字字面量的修改方式。此外，SDK API的number类型转换为int已在上一章示例中展示，本章将展示开发者自定义的类型（如class或interface）。
   ```typescript
   // 场景9.1类型属性不需要修改number to int的情况
   // 公共代码
   interface A {
     a : number;
     b : number;
   }
   // ArkTS-Dyn用户自定义类型
   let x:A = {
     a : 1,
     b : 2
   }

   let y:A = {
     a : 1,
     b : 1.1
   }

   let z:A = {
     a : 1,
     b : 2/3
   }

   // ArkTS-Sta用户自定义类型
   // 不用修改
   let x:A = {
     a : 1,
     b : 2
   }
   // 不用修改
   let y:A = {
     a : 1,
     b : 1.1
   }

   let z:A = {
     a : 1,
     b : 2.0/3 //需要修改
   }

   // 场景9.2类型属性仍保留为number，但是需要作为int使用，需要调用toInt
   // 公共代码
   interface A {
     a : number;
     b : number;
     c : number;
   }
   let arr:Array<number> = [1, 2, 3, 4, 5]

   // ArkTS-Dyn用户自定义类型
   let x:A = {
     a : 1.1, // a被赋值为浮点字面量，所以，属性a类型认为number
     b : 2/3, // b被含除法操作的表达式赋值，所以b还需要作为number使用，且表达式的整型字面量需要改为浮点型字面量
     c : 3
   }
   arr[x.a];
   arr[x.b];
   x.c/2; // c参与除法操作，所以仍要为number

   // 如果该属性被用作索引或其他需要整数的情况（如SDK的入参），且该属性没有在其他地方被用作数字（例如参与除法操作或被浮点数字面量赋值），则应将属性类型修改为整数。
   // ArkTS-Sta用户自定义类型
   let x:A = {
     a : 1.1,
     b : 2.0/3,
     c : 3
   }

   arr[x.a.toInt()]; // Array的index必须是整数
   arr[x.b.toInt()];
   x.c/2;
   ```

- 场景10，async函数、方法和lambda表达式必须返回Promise\<T>类型的值。如果函数体返回T，编译器会自动推导返回值为Promise\<T>。因此，当async函数返回整型字面量时，ArkTS-Dyn版本返回Promise\<number>，而ArkTS-Sta版本返回Promise\<int>，两者在ArkTS-Sta中不兼容。需要将async函数中返回整型字面量的情况修改为返回浮点型字面量。
   ```typescript
   // ArkTS-Dyn
   async function foo() {
     return 1; // 在ArkTS-Dyn中返回值类型是Promise<number>，在ArkTS-Sta中返回值类型是Promise<int>
   }

   async function foo1() : Promise<number>{
     return 1; // 在ArkTS-Dyn中返回值类型是Promise<number>，在ArkTS-Sta中返回值类型是Promise<int>
   }

   let func1 = async ()=> {return 1}; // 在ArkTS-Dyn中返回值类型是Promise<number>，在ArkTS-Sta中返回值类型是Promise<int>
   let func2 = async ():Promise<number> => {return 1}; // 在ArkTS-Dyn中返回值类型是Promise<number>，在ArkTS-Sta中返回值类型是Promise<int>

   class A {
     async method1() {
       return 1;
     }
     async method2():Promise<number> {
       return 1;
     }
   }

   // ArkTS-Sta
   async function foo() {
     return 1.0;
   }

   async function foo1() : Promise<number>{
     return 1.0;
   }

   let func1 = async ()=> {return 1.0};
   let func2 = async ():Promise<number> => {return 1.0};

   class A {
     async method1() {
       return 1.0;
     }
     async method2():Promise<number> {
       return 1.0;
     }
   }
   ```

- 场景11，在包含除法的复杂运算表达式中，表达式的结果应为number或double类型。
   ```typescript
   // ArkTS-Dyn
   let a = (1+1)/(2*3);

   // ArkTS-Sta
   let a:number = (1.0+1)/(2*3); // 表达式的第一个字面量如果为整型字面量，修改为浮点型字面量
   ```

- 场景12，lambda表达式的返回值场景，对于lambda表达式的返回值，在ArkTS-Sta中，整型字面量是int类型，int类型可赋值给number类型。lambda表达式返回int类型，与number类型协变，符合ArkTS-Sta语法规则。
   ```typescript
   // 公共代码
   let func1 = () => {return 1}; // 不告警
   let func2 = () => {return 2}; // 不告警
   // ArkTS-Dyn
   let r1 = func1()/func2(); // 在ArkTS-Sta中，参与了除法，结果为number/double，这里需要调用toDouble函数。
   // ArkTS-Sta
   let r1 = func1().toDouble()/func2();
   ```

- 场景13，enum的整型值参与除法操作。
   ```typescript
   // 公共代码
   enum X {
     A = 1,
     B = 2,
     C = -1
   }

   // ArkTS-Dyn
   let a = X.A/X.B;// ArkTS-Dyn结果为0.5，ArkTS-Sta结果为0
   // ArkTS-Sta
   let a = X.A.valueOf().toDouble() / X.B; // 先取到X.A的值，然后再转换为number/double
   ```

## 限制void类型的使用场景

**规则：** `arkts-limited-void-type`

**规则解释：**

在ArkTS-Dyn中，`void`类型可用于类型声明、类型断言、函数返回类型、泛型类型等场景。

在ArkTS-Sta中，`void`类型只能用作方法的返回类型和泛型类型，并且void类型函数的返回值不能作为值传递。

**变更原因：**

ArkTS-Sta对`void`类型的语义进行了收紧，限制其使用场景以增强类型安全性。

**适配建议：**

- 场景1，函数返回void类型无需修改；函数返回void联合类型需要改为undefined。
  ```typescript
  // ArkTS-Dyn
  function foo1(): void {};
  function foo2(): void | number {};
  // ArkTS-Sta
  function foo1(): void {};
  function foo2(): undefined | number { return undefined };
  ```
- 场景2，void类型变量和类型别名需要改为undefined。
  ```typescript
    // ArkTS-Dyn
  let s1: void;  // void类型变量
  let s2: void | number;   // void联合类型
  type t1 = void;  // void类型别名
    // ArkTS-Sta
  let s1 = undefined;
  let s2: undefined | number;
  type t1 = undefined;
  ```
- 场景3，void类型断言，需要改为undefined。
  ```typescript
  // ArkTS-Dyn
  let a: void | number = undefined;
  let x1 = a as void;
  let x2 = a as void | number;
  // ArkTS-Sta
  let a: undefined | number = undefined;
  let x1 = a as undefined; 
  let x2 = a as undefined | number;
  ```
- 场景4，void类型函数的返回值不能作为值传递。
  ```typescript
  // ArkTS-Dyn
  function foo():void{}
  function execute(v: void) {}
  // 在参数传递过程中执行foo方法
  execute(foo());   

  // ArkTS-Sta
  function foo():void{}
  function execute(v: () => void) {
    v();
  }
  // 改为在execute内部执行foo方法 
  execute(foo);    
  ```

## 不支持void操作符

**规则：** `arkts-no-void-operator`

**规则解释：**

ArkTS-Sta不支持void操作符获取undefined。

**变更原因：**
 
在ArkTS-Sta中，undefined是关键字，不能用作变量名称，因此无需使用void操作符获取undefined。

**适配建议：**

使用IIFE（立即执行函数表达式）来执行运算符的表达式，并返回undefined。

**示例：**

**ArkTS-Dyn**
```typescript
let s = void 'hello';
console.info(s);  // output: undefined

let a = 5;
let b = void (a + 1);

function logValue(value: string | undefined) {
  console.info(value);
}
logValue(void 'data');

let fn = () => void 0;
```

**ArkTS-Sta**
```typescript
(() => {
    'hello'
    return undefined;
})()

let a = 5;
let b = (() => {
    a + 1;
    return undefined;
})();  // 替换为 IIFE

let logValue = ((() => {
    'data';
    return undefined;
})());  // 替换为 IIFE

let fn = () => undefined;  // 直接返回 `undefined`
```

## 限定使用字面量类型

**规则：** `arkts-limited-literal-types`

**规则解释：**

ArkTS-Sta不支持数字字面量类型和布尔字面量类型。

**变更原因：**

ArkTS-Sta提供更细化的数值类型供开发者选择，关注数值范围而非特定数字值，同时简化代码，避免歧义，不引入复杂数值字面量类型语法。
 
**适配建议：**

请使用number和boolean类型替代字面量类型。

**示例：**

**ArkTS-Dyn**
```typescript
let n1: 1 = 1;
let n2: 0.1 = 0.1;
let f: true = true;

function getOne(): 1 {
  return 1;
}
function isAvailable(): true {
  return true;
}

function setFlag(flag: true) {
  console.info(flag.toString());
}
function setPrecision(precision: 0.1) {
  console.info(precision.toString());
}

interface Config {
  readonly enable: true;
  readonly threshold: 100;
}
```

**ArkTS-Sta**
```typescript
let n1: int = 1;
let n2: number = 0.1;
let f: boolean = true;

function getOne(): int {
  return 1;
}
function isAvailable(): boolean {
  return true;
}

function setFlag(flag: boolean) {
  console.info(flag);
}
function setPrecision(precision: number) {
  console.info(precision);
}

interface Config {
  readonly enable: boolean;
  readonly threshold: int;
}
```

## 不支持arguments对象

**规则：** `arkts-no-arguments-obj`

**规则解释：**

ArkTS-Sta不支持通过arguments对象获取参数。

**变更原因：**

ArkTS-Sta对函数调用进行严格参数检查，参数个数不符时编译报错，因此无需使用arguments机制。
 
**适配建议：**

请使用具体形参代替arguments对象获取参数。

**示例：**

**ArkTS-Dyn**
```typescript
function foo(u: string) {
  const args: object[] = Array.from(arguments);
  console.info(args[0].toString());
}

function bar(a: number, b?: number) {
  if (arguments.length === 1) {
    console.info("Only one argument passed");
  }
}

function sum() {
  let total = 0;
  const args: object[] = Array.from(arguments);
  for (let i = 0; i < args.length; i++) {
    total += Number(args[i]);
  }
  return total;
}

function test() {
  console.info(String(arguments.callee));
}
```

**ArkTS-Sta**
```typescript
function foo(u: string) {
  console.info(u);
}

function bar(a: number, b?: number) {
  if (b === undefined) {
    console.info("Only one argument passed");
  }
}

function sum(...args: number[]) {  
  // 使用 `...rest` 替代 `arguments`
  const res = args.reduce((acc: number, num: number) => acc + num);
  return res;
}

function test() {
  console.info(test);  // 直接使用函数名
}
```

## 数组索引必须是整型数据

**规则：** `arkts-array-index-expr-type`

**规则解释：**

数组索引必须为整数类型。当索引由其他模块或第三方库传递时，迁移工具可能无法解析其类型，导致数组索引处报错。请开发者确认变量类型是否为整数，并决定如何修改代码。

**变更原因：**

为了实现数组更快的访问，ArkTS-Sta支持数值类型的细化，并要求数组索引表达式必须是整数类型。
 
**适配建议：**

请将索引改为整数类型。

**示例：**

**ArkTS-Dyn**

```typescript
function foo(index: number) {
  let array = [1, 2, 3];
  let element = array[index];
}

function getIndex(): number {
  return Math.random() * 10; // 可能返回小数
}

let array = [1, 2, 3];
for (let i: number = 0; i < array.length; i++) {
  console.info(array[i].toString());
}
```

**ArkTS-Sta**

```typescript
function foo(index: int) {
  let array = [1, 2, 3];
  let element = array[index];
}

function getIndex(): int {
  return Math.floor(Math.random() * 10).toInt(); // 转换为 `int`
}

let array = [1, 2, 3];
for (let i: int = 0; i < array.length; i++) { // 改为 `int`
  console.info(array[i]);
}
```

## 不支持通过负数访问数组

**规则：** `arkts-array-index-negative`

**规则解释：**

ArkTS-Sta不支持使用负整数访问数组元素。当数组索引由其他模块或第三方库传递的变量决定时，这些变量的值需要在运行时确定。迁移工具无法判断索引值是否为负，因此会发出警报，请开发者确认索引值是否为负数，并进行相应修改。

**变更原因：**

在ArkTS-Dyn中，使用负数索引访问数组时，实际上是访问属性名为该负数的属性。如果数组不存在此属性，返回值为`undefined`。如果向负数索引写入值，实际上是为数组对象动态增加一个属性名为该负数的属性并赋值。ArkTS-Sta是静态类型语言，无法动态为数组对象增加属性，因此不支持使用负数索引访问数组元素。

**适配建议：**

请使用非负整数来访问数组元素。

**示例：**

**ArkTS-Dyn**

```typescript
let an_array = [1, 2, 3];
let element = an_array [-1];
console.info(getElement(an_array, -1).toString()); // 违反规则
for (let i: number = -1; i < an_array.length; i++) { // 违反规则
  console.info(an_array[i].toString());
}

function getElement(arr: number[], index: number) {
  return arr[index]; // 可能接收负数索引
}
```

**ArkTS-Sta**

```typescript
let an_array = [1, 2, 3];
let element = an_array [1];
console.info(getElement(an_array, 1)); // 传递非负索引
for (let i: int = 0; i < an_array.length; i++) { // 仅允许非负索引
  console.info(an_array[i]);
}

function getElement(arr: number[], index: int) {
  if (index < 0) throw new Error("Index must be a non-negative integer");
  return arr[index]; // 仅允许非负整数
}
```

## 增加数组越界运行时检查

**规则：** `arkts-runtime-array-check`

**规则解释：**

ArkTS-Sta会对数组索引的合法性进行运行时检查。请开发者自行确认索引的合法性，决定如何修改代码。

**变更原因：**

为了保证类型安全，ArkTS-Sta在校验索引的合法性后访问数组元素。
 
**适配建议：**

在访问数组前，必须对索引值进行校验。

**示例：**

**ArkTS-Dyn**

```typescript
let a: number[] = [];
a[100] = 5; // 可能越界
```

**ArkTS-Sta**

```typescript
let a: number[] = [];
if (100 < a.length) {
  a[100] = 5  // a[100]的值为5
}
```

## 元组和数组是两种不同类型

**规则：** `arkts-no-tuples-arrays`

**规则解释：**

ArkTS-Sta中数组和元组是不同的类型，元组不支持Array拥有的接口和属性。

**变更原因：**
 
ArkTS-Sta中数组和元组是不同的类型，运行时使用元组类型可以获得更好的性能。

**适配建议：**

不要使用数组类型标注元组，而应正确使用对象类型。

**示例：**

**ArkTS-Dyn**

```typescript
const tuple1: [number, number, boolean] = [1, 3.14, true];
const array: (number | boolean) [] = tuple1;

const tuple2: Array<number | boolean> = [1, 3.14, true]; // 违反规则

function getTuple(input: (number | boolean)[]): (number | boolean)[] { // 违反规则
  return input;
}

getTuple([1, 3.14, true]); // 传入元组

type Point = (number | boolean)[]; // 违反规则
const p: Point = [3, 5, true];

let a: [number, string] = [1, "a"];
console.info("length=" + a.length); // 可以通过.length获取元组长度
```

**ArkTS-Sta**

```typescript
const tuple1: [number, number, boolean] = [1, 3.14, true];
const array: [number, number, boolean] = tuple1;

const tuple2: [number, number, boolean] = [1, 3.14, true]; // 正确使用元组

function getTuple(input: [number, number, boolean]): [number, number, boolean] { // 正确使用元组
  return input;
}

getTuple([1, 3.14, true]);

type Point = [number, number, boolean]; // 使用元组
const p: Point = [3, 5, true];

let a: [number, string] = [1, "a"];
console.info("length=" + 2); // 元组不支持.length接口，元组长度固定，直接输入长度
```

## 函数类型转换及兼容原则

**规则：** `arkts-incompatible-function-types`

**规则解释：**

当函数类型返回void时，ArkTS-Dyn可返回任意类型，而ArkTS-Sta只能返回void类型。

**变更原因：**
 
对于函数类型转换，ArkTS-Dyn和ArkTS-Sta都遵循参数逆变和返回类型协变的规则。有关逆变和协变的详细解释，请参见[逆变和协变](#逆变和协变)。

而当函数类型返回void时，由于ArkTS-Dyn与ArkTS-Sta中void类型的变化，ArkTS-Sta仅支持返回void类型。详细情况请参考[void类型只能用在返回类型的场景](#void类型只能用在返回类型的场景)。

**适配建议：**

当函数类型返回void时，实现代码也要返回void。

**示例：**

**ArkTS-Dyn**

```typescript
type F = () => void;
// 可返回任意类型
let f: F = (): number => {
  return 0;
}
```

**ArkTS-Sta**

```typescript
type F = () => void;
// 改为相同的返回类型
let f1: F = (): void => {};
```

## 不支持指数操作符

**规则：** `arkts-no-exponent-op`

**规则解释：**

ArkTS-Sta不支持指数运算符（`**`和`**=`）。

**变更原因：**
 
ArkTS-Sta不支持指数运算符（`**`和`**=`），采用语言基础库。

**适配建议：**

使用Math库中的pow方法来代替指数运算符。

**示例：**

**ArkTS-Dyn**

```typescript
let x = 2 ** 5;

let y = 3;
y **= 4; // 违反规则

let result = (1 + 2) ** (3 * 2); // 违反规则

function power(base: number, exponent: number) {
  return base ** exponent; // 违反规则
}

let values = [1, 2, 3];
let squared = values.map(v => v ** 2); // 违反规则
```

**ArkTS-Sta**

```typescript
let x = Math.pow(2, 5);

let y: number = 3;
y = Math.pow(y, 4); // 直接使用 `Math.pow()`

let result = Math.pow(1 + 2, 3 * 2); // 直接使用 `Math.pow()`

function power(base: number, exponent: number) {
  return Math.pow(base, exponent); // 使用 `Math.pow()`
}

let values = [1, 2, 3];
let squared = values.map(v => Math.pow(v, 2)); // 使用 `Math.pow()`
```

## 不支持正则表达式字面量

**规则：** `arkts-no-regexp-literals`

**规则解释：**

ArkTS-Sta不支持正则表达式字面量。

**变更原因：**
 
ArkTS-Sta是静态类型语言，不支持正则表达式字面量，使用严格的类型来定义正则。

**适配建议：**

使用RegExp类代替正则表达式字面量。

**示例：**

**ArkTS-Dyn**

```typescript
let regex1: RegExp = /bc*d/;
let regex2 = /\d{2,4}-\w+/g; // 违反规则
function matchPattern(str: string) {
  return str.match(/hello\s+world/i); // 违反规则
}

let text = "Hello world!";
let result = text.replace(/world/, "ArkTS"); // 违反规则

let items = "apple,banana, cherry".split(/\s*,\s*/); // 违反规则
```

**ArkTS-Sta**

```typescript
let regex1: RegExp = new RegExp('bc*d');
let regex2 = new RegExp('\\d{2,4}-\\w+', 'g'); // 使用 `RegExp` 类
function matchPattern(str: string) {
  let regex = new RegExp('hello\\s+world', 'i'); // 使用 `RegExp`
  return str.match(regex);
}

let text = "Hello world!";
let regex3 = new RegExp('world'); // 使用 `RegExp` 类
let result = text.replace(regex3, "ArkTS");

let regex4 = new RegExp('\\s*,\\s*'); // 使用 `RegExp`
let items = "apple,banana, cherry".split(regex4);
```

## enum中当前语法不支持浮点数值

**规则：** `arkts-no-enum-mixed-types`

**规则解释：**

ArkTS-Sta中enum当前语法不支持浮点数值。

**变更原因：**
 
enum表示一组离散的数据，使用浮点数据不符合设计理念，可能造成精度损失。因此，ArkTS-Sta中enum的值必须为整型。

**适配建议：**

定义enum类型时，需显式声明number类型，以支持浮点数值。

**示例：**

**ArkTS-Dyn**

```typescript
enum Test {
  UP = 1.5,
  MIDDLE = 1,
  DOWN = 0.75
}
```

**ArkTS-Sta**

```typescript
enum Test: int {
  UP = 15,
  MIDDLE = 100,
  DOWN = 75
}
```

## 不支持为函数增加属性

**规则：** `arkts-no-func-props`

**规则解释：**

ArkTS-Sta不支持在函数上动态添加属性。

**变更原因：**
 
ArkTS-Sta是静态类型语言，不支持在函数，方法上动态增加属性。

**适配建议：**

使用类来封装函数和属性。

**示例：**

**ArkTS-Dyn**

```typescript
function foo(path: string): void {
  console.info(path);
}

foo.baz = 1;
console.info(foo.baz.toString());
```

**ArkTS-Sta**

```typescript
class T1 {
  static foo(path: string): void {
    console.info(path);
  }

  static bar: number = 1;
}

class T2 {
  static foo(path: string): void {
    console.info(path);
  }

  static baz: number = 2;
}

T2.foo("example");
console.info(T2.baz);
```

## 不支持TS装饰器

**规则：** `arkts-no-ts-decorators`

**规则解释：**

ArkTS-Sta不支持通过自定义装饰器动态改变类、方法、属性或函数参数。

**变更原因：**
 
由于自定义装饰器需要动态改变类、方法、属性，而ArkTS-Sta是静态类型语言，所以不支持自定义装饰器。

**适配建议：**

请参考以下示例修改代码。

**示例1：日志追踪装饰器**

**ArkTS-Dyn**

```typescript
// file1.ts
export function Log(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  descriptor.value = function (...args: any[]) {
    console.info(`[LOG] 方法 ${propertyKey} 被调用，参数: ${JSON.stringify(args)}`);
    const result = originalMethod.apply(this, args);
    console.info(`[LOG] 方法 ${propertyKey} 返回: ${result}`);
    return result;
  };
}

// index.ets
import { Log } from './file1';

@Entry
@Component
struct MyCounter {
  @State count: number = 0;

  @Log
  increment() {
    this.count++;
    return this.count;
  }

  build() {
    Button(`Count: ${this.count}`)
      .onClick(() => this.increment())
  }
}
```

**ArkTS-Sta**

```typescript
import { Component, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Component
struct Counter {
  @State count: number = 0;

  increment() {
    console.info(`[LOG] 方法 increment 被调用，参数: []`);
    this.count++;
    const result = this.count;
    console.info(`[LOG] 方法 increment 返回: ${result}`);
    return result;
  }

  build() {
    Button(`Count: ${this.count}`)
      .onClick((e:ClickEvent) => {this.increment()})
  }
}
```

**示例2：防抖装饰器**

**ArkTS-Dyn**

```typescript
// file1.ts
export function Debounce(delay: number = 300) {
  return function (target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    let timer: number = 0;
    const originalMethod = descriptor.value;
    descriptor.value = function (...args: any[]) {
      if (timer) {
        clearTimeout(timer);
      }
      timer = setTimeout(() => {
        originalMethod.apply(this, args);
        timer = 0;
      }, delay);
    };
  };
}

// index.ets
import { Debounce } from './file1';

@Entry
@Component
struct SearchBox {
  @State keyword: string = '';

  @Debounce(500)
  onSearchInput(keyword: string) {
    this.keyword = keyword;
    console.info(`搜索: ${keyword}`);
    // 调用搜索API...
  }

  build() {
    Row() {
      TextInput({ placeholder: '搜索...' })
        .onChange((value) => this.onSearchInput(value))
    }
  }
}
```

**ArkTS-Sta**

```typescript
import { Component, Button } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Component
struct SearchBox {
  @State keyword: string = '';
  private debounceTimer: Int = 0;

  onSearchInput(keyword: string) {
    if (this.debounceTimer) {
      clearTimeout(this.debounceTimer);
    }
    this.debounceTimer = setTimeout(() => {
      this.keyword = keyword;
      console.info(`搜索: ${keyword}`);
      // 调用搜索API...
    }, 500);
  }

  build() {
    // TextField({ placeholder: '搜索...' })
    //   .onChange((value) => {this.onSearchInput(value)})
  }
}
```

**示例3：权限校验装饰器**

**ArkTS-Dyn**

```typescript
// file1.ts
const checkUserPermission = (permission: string) => {
  return true; // 自定义权限检查函数
}

export function RequiresPermission(permission: string) {
  return function (target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;
    descriptor.value = function (...args: any[]) {
      if (checkUserPermission(permission)) {
        return originalMethod.apply(this, args);
      } else {
        console.error(`[权限不足] 需要 ${permission} 权限`);
        return null;
      }
    };
  };
}

// index.ets
import { RequiresPermission } from './file1';

@Entry
@Component
struct AdminPanel {
  @RequiresPermission('admin')
  deleteUser(userId: string) {
    // 删除用户逻辑...
  }

  build() {
    Button('删除用户')
      .onClick(() => this.deleteUser('123'))
  }
}
```

**ArkTS-Sta**

```typescript
import { Component, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Component
struct AdminPanel {
  deleteUser(userId: string) {
    if (!checkUserPermission('admin')) {  // 自定义权限检查函数
      console.error(`[权限不足] 需要 admin 权限`);
      return;
    }
    // 删除用户逻辑...
  }

  build() {
    Button('删除用户')
      .onClick((e:ClickEvent) => {this.deleteUser('123')})
  }
}
```

**示例4：性能监控装饰器**

**ArkTS-Dyn**

```typescript
// file1.ts
export function PerformanceMonitor(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  descriptor.value = function (...args: any[]) {
    const start = Date.now();
    const result = originalMethod.apply(this, args);
    const end = Date.now();
    console.info(`[性能] 方法 ${propertyKey} 执行耗时: ${end - start}ms`);
    return result;
  };
}

// index.ets
import { PerformanceMonitor } from './file1';

@Entry
@Component
struct DataLoader {
  @PerformanceMonitor
  loadLargeData() {
    // 模拟耗时操作
    let sum = 0;
    for (let i = 0; i < 1000000; i++) {
      sum += i;
    }
    return sum;
  }

  build() {
    Button('加载数据')
      .onClick(() => this.loadLargeData())
  }
}
```

**ArkTS-Sta**

```typescript
import { Component, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
@Component
struct DataLoader {
  loadLargeData() {
    const start = Date.now();
    // 模拟耗时操作
    let sum = 0;
    for (let i = 0; i < 1000000; i++) {
      sum += i;
    }
    const end = Date.now();
    console.info(`[性能] 方法 loadLargeData 执行耗时: ${end - start}ms`);
    return sum;
  }

  build() {
    Button('加载数据')
      .onClick((e:ClickEvent) => {this.loadLargeData()})
  }
}
```

**示例5：自动保存装饰器**

**ArkTS-Dyn**

```typescript
// file1.ts
export function AutoSave(key: string) {
  return function (target: any, propertyKey: string) {
    let value = target[propertyKey];

    const getter = () => value;
    const setter = (newVal: any) => {
      value = newVal;
      try {
        console.info(`[自动保存] 键: ${key}, 值: ${JSON.stringify(newVal)}`);
        // localStorage.setItem(key, JSON.stringify(newVal)); // 实际项目需使用存储API
      } catch (e) {
        console.error(`[自动保存失败] ${e}`);
      }
    };

    Object.defineProperty(target, propertyKey, {
      get: getter,
      set: setter,
      enumerable: true,
      configurable: true
    });
  };
}

// index.ets
import { AutoSave } from './file1';

@Entry
@Component
struct Settings {
  @AutoSave('user_settings')
  theme: string = 'light';

  build() {
    Row() {
      Button('切换主题')
        .onClick(() => this.theme = this.theme === 'light' ? 'dark' : 'light')
    }
  }
}
```

**ArkTS-Sta**

```typescript
import { Component, Button, ClickEvent,Row } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Component
struct Settings {
  @State theme: string = 'light';

  setTheme(newTheme: string) {
    this.theme = newTheme;
    try {
      console.info(`[自动保存] 键: user_settings, 值: ${JSON.stringify(newTheme)}`);
      localStorage.setItem('user_settings', JSON.stringify(newTheme));  // 实际项目需使用存储API
    } catch (e) {
      console.error(`[自动保存失败] ${e}`);
    }
  }

  build() {
    Row() {
      Button('切换主题')
        .onClick((e:ClickEvent) => {this.setTheme(this.theme === 'light' ? 'dark' : 'light')})
    }
  }
}
```

## 类实现接口时，不能用类方法替代对应interface属性

**规则：** `arkts-no-method-overriding-field`

**规则解释：**

在ArkTS-Sta中，类在实现接口时，lambda属性和方法不能混用。即不能用方法实现属性，也不能用属性实现方法。

**变更原因：**
 
在ArkTS-Dyn中，方法类型与函数属性类型兼容，类实现接口时可以混用。

在ArkTS-Sta中，属性和方法有本质区别，函数属性类型与方法类型不再兼容，因此不支持这种写法。

**适配建议：**

实现接口时，不要混用lambda属性和方法，确保实现与声明保持一致。

**示例：**

**ArkTS-Dyn**

```typescript
interface Person {
  cb1: () => void;
  cb2(): void;
}
class Student implements Person {
  cb1() { }          // 用方法实现lambda属性，ArkTS-Sta编译错误
  cb2:() => void = () => {}   // 用lambda属性实现方法，ArkTS-Sta编译错误
}
```

**ArkTS-Sta**

```typescript
interface Person {
  cb1: () => void;
  cb2();
}
class Student implements Person {
  cb1: () => void = () => { }  // 修改为lambda属性，与声明保持一致
  cb2() { }     // 修改为方法，与声明保持一致
}
```

## 限定switch语句中case语句类型

**规则：** `arkts-switch-expr`

**规则解释：**

ArkTS-Sta的switch表达式类型只能为number、string、enum。

**变更原因：**
 
提高代码可读性和执行性能。

**适配建议：**

使用number、string、enum作为switch表达式类型。

**示例：**

**ArkTS-Dyn**

```typescript
let isTrue: boolean = Boolean(1);
switch (isTrue) {
  case true:
    console.info('It\'s true');
    break;
  case false:
    console.info('It\'s false');
    break;
}

interface IObj {
  value: number
}

const obj: IObj = { value: 1 };
switch (obj) {
  case { value: 1 } as IObj:
    console.info('Matched');
    break;
}

const arr = [1, 2, 3];
switch (arr) {
  case [1, 2, 3]:
    console.info('Matched');
    break;
}
```

**ArkTS-Sta**

```typescript
const isTrue = 'true';
switch (isTrue) {
  case 'true':
    console.info('It\'s true');
    break;
  case 'false':
    console.info('It\'s false');
    break;
}

const objValue = 1; // 仅存储值
switch (objValue) {
  case 1:
    console.info('Matched');
    break;
}

const arrValue = '1,2,3'; // 变成字符串
switch (arrValue) {
  case '1,2,3':
    console.info('Matched');
    break;
}
```

## 不支持lazy关键字

**规则：** `arkts-no-lazy-import`

**规则解释：**

ArkTS-Sta不需要lazy关键字。

**变更原因：**
 
ArkTS-Sta默认支持懒加载，无需使用lazy关键字。

**适配建议：**

移除lazy关键字。

**示例：**

**ArkTS-Dyn**

```typescript
// file1.ets
let a='a';
let b='b';
let c='c';
export {a,b,c};

// file2.ets
import lazy { a } from './file1';
import lazy { b, c } from './file1'; // 违反规则
```

**ArkTS-Sta**

```typescript
// file1.ets
let a='a';
let b='b';
let c='c';
export {a,b,c};

// file2.ets
import { a } from './file1';
import { b, c } from './file1'; // 移除lazy
```

## 不支持动态import

**规则：** `arkts-no-dynamic-import`

**规则解释：**

在ArkTS-Sta中，不支持动态import。

**变更原因：**
 
ArkTS-Sta中模块加载默认支持懒加载，无需动态import。

**适配建议：**

将动态import改为静态import。

**示例：**

**ArkTS-Dyn**

```typescript
// file1.ets
export const a = 'file1';
// file2.ets
import('./file1').then((m) => { // 在ArkTS-Sta中动态import是不支持的
  console.info('success');
})
async () => {
  const module = await import('./file1'); // 在ArkTS-Sta中动态import是不支持的
}
```

**ArkTS-Sta**

```typescript
// file1.ets
export const a = 'file1';
// file2.ets
import {a} from './file1'  // 支持静态import
```

## 不支持副作用导入

**规则：** `arkts-no-side-effect-import`

**规则解释：**

ArkTS-Sta不支持副作用导入的功能。

**变更原因：**
 
ArkTS-Sta中模块加载支持懒加载，不支持副作用导入的功能。

**适配建议：**

将导入文件中的执行逻辑移到本文件中。

**示例：**

**ArkTS-Dyn**

```typescript
// logger.ets
console.info("Logger initialized!");

// main.ets
import "./logger";
console.info("Main program running...");
```

**ArkTS-Sta**

```typescript
// main.ets
console.info("Logger initialized!");
console.info("Main program running...");
```

## 不支持globalThis

**规则：** `arkts-no-globalthis`

**规则解释：**

ArkTS-Sta不支持globalThis。

**变更原因：**
 
ArkTS-Sta不支持动态更改对象布局，因此不支持全局作用域和globalThis。

**适配建议：**

按示例修改。

**示例：**

**ArkTS-Dyn**

```typescript
// globalThis里设置abc
globalThis.abc = 123;

// 从globalThis引用'abc'
const x: number = globalThis.abc;
```

**ArkTS-Sta**

```typescript
// file1
export let abc: number = 100;

// file2
import * as M from 'file1'

let x = M.abc;
```

## 不支持Function.bind方法

**规则：** `arkts-no-func-bind`

**规则解释：**

ArkTS-Sta不支持标准库函数Function.bind。

**变更原因：**
 
ArkTS-Sta中的方法会自动捕获上下文中的`this`，因此无需使用`Function.bind`显式绑定`this`。

**适配建议：**

使用“=”（等号）将函数赋值给变量。

**示例：**

**ArkTS-Dyn**

```typescript
class MyClass {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet() {
    console.info(`Hello, my name is ${this.name}`);
  }
}

const instance = new MyClass("Alice");
const boundGreet: Function = instance.greet.bind(instance);
boundGreet();
```

**ArkTS-Sta**

```typescript
class MyClass {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet() {
    console.info(`Hello, my name is ${this.name}`);
  }
}

const instance = new MyClass("Alice");
const boundGreet = () => instance.greet(); // 使用箭头函数
boundGreet(); // Hello, my name is Alice
```

## 不支持将类作为对象

**规则：** `arkts-no-classes-as-obj`

**规则解释：**

在ArkTS-Sta中，不支持将class用作对象。

**变更原因：**
 
在ArkTS-Sta中，class声明的是一个新的类型，而不是一个值。因此，不支持将class用作对象，例如赋值给变量。

**适配建议：**

通过反射来实现。

**示例：**

**ArkTS-Dyn**

```typescript
class MyClass {
  constructor() {
  }

  static test: string = "test";
}

let obj = MyClass; // obj是类型，并非对象

console.info(MyClass.test); // 输出：test
console.info((MyClass as object)['test']); // 输出：test
```

**ArkTS-Sta**

```typescript
class MyClass {
  constructor() {
  }

  static test: string = "test";
}

// 获取ClassType
let classType: ClassType | undefined = Type.from<MyClass>() as ClassType;

console.info(MyClass.test); // 输出：test
// console.info((MyClass as object)['test']) // 违反规则
```

## arkts-limited-stdlib

**规则：** `arkts-limited-stdlib`

**规则解释：**

ArkTS-Sta中禁止使用以下接口：

- 全局对象的属性和方法：`eval`

- Object： `__proto__`、`__defineGetter__`、`__defineSetter__`、`__lookupGetter__`、`__lookupSetter__`、`assign`、`create`、`defineProperties`、`defineProperty`、`freeze`、`fromEntries`、`getOwnPropertyDescriptor`、`getOwnPropertyDescriptors`、`getOwnPropertySymbols`、`getPrototypeOf`、`hasOwnProperty`、`is`、`isExtensible`、`isFrozen`、`isPrototypeOf`、`isSealed`、`preventExtensions`、`propertyIsEnumerable`、`seal`、`setPrototypeOf`

- Reflect：`apply`、`construct`、`defineProperty`、`deleteProperty`、`getOwnPropertyDescriptor`、`getPrototypeOf`、`isExtensible`、`preventExtensions`、`setPrototypeOf`

- Proxy：`handler.apply()`、`handler.construct()`、`handler.defineProperty()`、`handler.deleteProperty()`、`handler.get()`、`handler.getOwnPropertyDescriptor()`、`handler.getPrototypeOf()`、`handler.has()`、`handler.isExtensible()`、`handler.ownKeys()`、`handler.preventExtensions()`、`handler.set()`、`handler.setPrototypeOf()`

**变更原因：**
 
ArkTS-Sta不允许使用TypeScript或JavaScript标准库中的这些接口，这些接口大多与动态特性相关。

**适配建议：**

NA

## 不支持Structural Typing

**规则：** `arkts-no-structural-typing`

**规则解释：**
 
ArkTS-Sta不支持Structural Typing。

Structural Typing（结构化类型系统）是一种类型系统，其类型兼容性基于类型的实际结构而非声明名称。例如，两个类的属性和方法完全相同，即使名称不同，也被认为是同一个类型，可以互相赋值。

**变更原因：**
 
Structural Typing存在以下劣势，故ArkTS-Sta不支持。
- 意外匹配风险：结构相同但语义不同的类型可能被误用。
- 重构风险：修改结构可能影响远处代码。
- 可读性降低：类型关系不直观。

**适配建议：**

自行添加类型转换方法。

**示例：**

**ArkTS-Dyn**

```typescript
// 类型定义
class A {
  v: number = 0;
}

class B {
  v: number = 0;
}

class C<T> {
  u?: T
}

// 场景1，类型转换
let a = new B() as A;
// 场景2，泛型
let b: C<B> = new C<A>();
// 场景3，返回类型
let func = (): A => {
  return new B();
}
```

**ArkTS-Sta**
```typescript
class A {
  v: number = 0;
}

class B {
  v: number = 0;
}

class C<T> {
  u?: T
}

// 补充类型转换方法
function convertType(b: B): A {
  const a = new A();
  a.v = b.v;
  return a;
}

// 场景1，类型转换
let a = convertType(new B());

// 场景2，泛型
let b: C<B> = new C<B>();

// 场景3，返回类型
let func = (): A => {
  return convertType(new B());
}
```

## 禁止对表达式使用extends或implements

**规则：** `arkts-no-extends-expression`

**规则解释：**

ArkTS-Sta禁止对表达式使用extends或implements，如"extends a"，"extends getBase()"等。

**变更原因：**
 
ArkTS-Sta中规范了类的继承规则：类不能作为对象使用，且在继承时无法继承表达式。

**适配建议：**

改为extends/implements类或接口。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  v: number = 0;
}

let a = A;

class B extends a {
  u: number = 0;
}

function getBase() {
  class C {
    v: number = 0;
  }

  return C;
}

class D extends getBase() {
  u: number = 0;
}
```

**ArkTS-Sta**

```typescript
class A {
  v: number = 0;
}

class B extends A { // 直接继承类
}

class C {
  v: number = 0;
}

class D extends C { // 直接继承类
  u: number = 0;
}
```

## 不支持类TS重载

**规则：** `arkts-no-ts-overload`

**规则解释：**

ArkTS-Sta不支持TS-like的重载。

**变更原因：**
 
重载时使用不同的函数体可以提高执行效率。

**适配建议：**

重载时分别使用不同的函数体。

**示例：**

**ArkTS-Dyn**

```typescript
function foo(): void;

function foo(x: string): void;

function foo(x?: string): void {
  console.info(x);
}

function sum(x: number, y: number): number;

function sum(x: number, y: number, z: number): number;

function sum(x: number, y: number, z?: number): number {
  return z ? x + y + z : x + y;
}

function foo2(): string;

function foo2(x: number): number;

function foo2(x?: number): string | number {
  return x !== undefined ? x * 2 : "default";
}
```

**ArkTS-Sta**

```typescript
function foo(x?: string): void {
  /*body*/
}

function sumTwo(x: number, y: number): number {  // 独立实现
  return x + y;
}

function sumThree(x: number, y: number, z: number): number {  // 独立实现
  return x + y + z;
}

function fooString(): string {  // 独立实现
  return "default";
}

function fooNumber(x: number): number {  // 独立实现
  return x * 2;
}
```

## enum/class/interface的属性/方法名称须使用合法标识符

**规则：** `arkts-identifiers-as-prop-names`

**规则解释：**

ArkTS-Sta不支持将字符串作为class、interface、enum等属性或元素的名称，仅支持合法标识符作为属性。

**变更原因：**
 
在ArkTS-Sta中，为了增强对边界场景的约束，对象的属性名不能使用数字或字符串。

**适配建议：**

将属性名从字符串改为标识符。

**示例：**

**ArkTS-Dyn**

```typescript
enum A{
 'red' = '1'
}
```

**ArkTS-Sta**

```typescript
enum A{
  red = '1'
}
```

## 创建泛型实例需要类型实参

**规则：** `arkts-no-inferred-generic-params`

**规则解释：**

ArkTS-Sta中，创建泛型实例时需要指定类型实参。

**变更原因：**
 
ArkTS-Sta遵循空安全，未指定泛型类型实参时，创建实例时无法明确元素或属性类型。

**适配建议：**

创建泛型实例时指定类型实参。

**示例：**

```typescript
// 类型定义
class A<T> {
  constructor(value: T) {
  }
}
class B {
  static get<T>(value:T): string {
    return 'res';
  }
}
```

**ArkTS-Dyn**

```typescript
let a = new A(42); // 可省略泛型类型
let b = B.get('param');  // 可省略泛型类型
```

**ArkTS-Sta**

```typescript
let a = new A<number>(42); // 需要显式指定类型
let b = B.get<string>('param');  // 需要显式指定类型
```

## 不支持[]访问对象属性

**规则：** `arkts-no-props-by-index`

**规则解释：**

不能使用[]的方式动态访问object类型对象的属性。

**变更原因：**
 
在ArkTS-Sta中，对象结构在编译时已确定。为避免运行时错误并提升性能，不能使用[]方式动态访问object类型对象的属性。

**适配建议：**

使用点访问符代替[]。

**示例：**

**ArkTS-Dyn**

```typescript
interface Person {
  name: string;
  age: number;
}

function foo(u: object) {
  u['key'];
}

const person: Person = { name: "Alice", age: 30 };
console.info((person as object)['name']);

const data: object = JSON.parse('{ "name": "Alice" }');
console.info(data['name']);
```

**ArkTS-Sta**

```typescript
function foo(m: Map<string, Object>) {
    m.get('key'); // 使用 `Map`
}

interface Person {
    name: string;
    age: number;
}
const person: Person = {name: 'John',age: 30};
console.info(person.name); // 直接使用 `.` 访问

class UserData {
    name?: string;
}
const data =  JSON.parse<UserData>('{ "name": "Alice" }', Type.from<UserData>())!;
console.info(data.name); // 直接使用点访问符
```

## 对象字面量只包含属性不包含方法

**规则：** `arkts-obj-literal-props`

**规则解释：**

ArkTS-Sta中不支持在对象字面量中定义方法。

**变更原因：**
 
静态语言中，类的方法被所有实例共享，无法通过对象字面量重新定义。

**适配建议：**

使用属性赋值方式。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  foo: () => void = () => {
  };
}

let a: A = {
  foo() {
    console.info('hello');
  }
}

interface Person {
  sayHello: () => void;
}

let p: Person = {
  sayHello() {
    console.info('Hi');
  }
};
```

**ArkTS-Sta**

```typescript
class A {
  foo: () => void = () => {
  }
}

let a: A = {
  foo: () => {
    console.info('hello')
  }
}

interface Person {
  sayHello: () => void;
}

let p: Person = {
  sayHello: () => { // 使用属性赋值方式
    console.info('Hi');
  }
};
```

## 对象字面量生成类的实例

**规则：** `arkts-obj-literal-generate-class-instance`

**规则解释：**

ArkTS-Sta中，对象字面量会生成类的实例。

**变更原因：**
 
ArkTS-Sta是静态类型语言，所有的对象都要有对应的类型，因此对象字面量也要生成对应类的实例。

**适配建议：**

不涉及。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  v: number = 0
}

let a: A = { v: 123 }
console.info((a instanceof A).toString()); // 输出：false
```

**ArkTS-Sta**

```typescript
class A {
  v: number = 0
}

let a: A = { v: 123 }
console.info((a instanceof A).toString()); // 输出：true
```

## 增强对联合类型属性访问的编译时检查

**规则：** `arkts-common-union-member-access`

**规则解释：**

ArkTS-Sta在编译时会对联合类型的同名属性进行编译检查，要求同名属性具有相同的类型。

**变更原因：**

在ArkTS-Sta中，对象的结构在编译时确定。为了避免运行时错误，ArkTS-Sta在编译时会检查联合类型的同名属性，确保它们具有相同的类型。

**适配建议：**

避免使用联合类型。在使用联合类型时，可以通过as、重载等方式实现单一类型机制。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  v: number = 1;
}

class B {
  v: string = '';
}

function foo(a: A | B) {
  console.info(a.v.toString());
}
```

**ArkTS-Sta**

```typescript
class A {
  v: number = 1;
}

class B {
  u: string = '';
}

function foo(a: A) {
  console.info(a.v);
}

function foo(a: B) {
  console.info(a.u);
}
```

## 类的静态属性需要有初始值

**规则：** `arkts-class-static-initialization`

**规则解释：**

在ArkTS-Sta中，为了遵循null-safety（空安全），需要为属性赋上初始值。

**变更原因：**

ArkTS-Sta遵循null-safety（空安全），需要为类的静态属性赋初始值（具有默认值的类型除外）。

**适配建议：**

为静态属性赋初始值。

**示例：**

**ArkTS-Dyn**

```typescript
class O {
}

class A {
  static o: O
}

class B {
  static count: number;
}

interface IConfig {
  theme: string;
}

class C {
  static config: IConfig;
}

class D {
  static msg: string;

  constructor() {
    D.msg = "default";
  }
}
```

**ArkTS-Sta**

```typescript
class O {
}

class A {
  static o: O = new O(); // 提供初始值
}

class B {
  static count: number = 1; // 提供初始值
}

interface IConfig {
  theme: string;
}

class C {
  static config: IConfig = { theme: "light" }; // 提供初始值
}

class D {
  static name: string = "default"; // 在定义时初始化
}
```

## `Function`类型的调用方式与Typescript不同

**规则：** `arkts-no-ts-like-function-call`

**规则解释：**

ArkTS-Dyn中`Function`类型可以直接用括号调用。

ArkTS-Sta中`Function`类型的调用方式与Typescript不同，需要使用`unsafeCall`方法调用。

**变更原因：**

ArkTS-Sta对函数类型进行严格编译期检查，要求函数返回类型严格定义。`Function`对象必须通过`unsafeCall`调用后转换类型，以确保类型安全，替代ArkTS-Dyn中的括号调用。

**适配建议：**

使用`unsafeCall`方法代替括号调用`Function`类型。

**示例：**

**ArkTS-Dyn**

```typescript
let fn: Function = (): number => { return 11 };
let res: number = fn();
```

**ArkTS-Sta**

```typescript
let fn: Function = (): number => { return 11 };
let res: number = fn.unsafeCall() as number;
```

## 不支持可选方法

**规则：** `arkts-optional-methods`

**规则解释：**

ArkTS-Sta不支持类中的可选方法。

**变更原因：**

ArkTS-Sta中，类的方法由所有实例共享。增加可选方法支持会增加开发者判断空值的成本，影响性能。

**适配建议：**

用可选属性代替可选方法。

**示例：**

**ArkTS-Dyn**

```typescript
interface InterfaceA {
  aboutToDisappear?(): void
}
class ClassA {
  aboutToDisappear?(): void {}
}
```

**ArkTS-Sta**

```typescript
interface InterfaceA {
  aboutToDisappear?: () => void
}
class ClassA {
  aboutToDisappear?: () => void = () => {}
}
```

## 实例方法赋值给对象时会自动绑定this

**规则：** `arkts-instance-method-bind-this`

**规则解释：**

在ArkTS-Sta中，实例方法被赋值给对象时会自动绑定上下文中的`this`。

**变更原因：**

在ArkTS-Dyn中，实例方法的`this`指向取决于调用方式。当实例方法被赋值给对象时，`this`将不再指向实例，而是指向`undefined`。可以使用`bind`方法显式绑定，确保`this`正确指向实例。

在ArkTS-Sta中，实例方法直接赋值时会自动绑定`this`，确保方法调用时`this`始终指向原始实例，无需额外绑定。

**适配建议：**

开发者应移除不必要的bind绑定操作。

**示例：**

```typescript
// 类型定义
class A {
  n: string = 'a'
  foo() { console.info (this.n) }
}
```

**ArkTS-Dyn**

```typescript
let a = new A();
let foo = a.foo.bind(a) as Function;  // 显式绑定this
foo(); // 输出：'a'
```

**ArkTS-Sta**

```typescript
let a = new A();
const foo = a.foo;   // 直接赋值，自动绑定this
foo();   // 输出：'a'
```

## namespace内方法不能重名

**规则：** `arkts-no-duplicate-function-name`

**规则解释：**

在ArkTS-Sta中，相同namespace中的方法不能重名。

**变更原因：**

由于ArkTS-Sta中会将名称相同的namespace合并成一个namespace，同名方法会导致冲突。

**适配建议：**

相同namespace中的方法不能重名。

**示例：**

**ArkTS-Dyn**

```typescript
namespace A {
  function foo() {
    console.info('test1');
  }
}

namespace A {
  function foo() {
    console.info('test2');
  }
}
```

**ArkTS-Sta**

```typescript
namespace A {
  function foo1() {
    console.info('test1');
  }
}

namespace A {
  function foo2() {
    console.info('test2'); // 修改函数名称，避免命名冲突
  }
}
```

## 不支持在constructor中声明字段

**规则：** `arkts-no-ctor-prop-decls`

**规则解释：**

ArkTS-Sta不支持在constructor中声明类字段。

**变更原因：**

ArkTS-Sta在编译期确定类型布局，运行期不允许修改，以提高性能。

**适配建议：**

改为在class中声明字段。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  a: string

  constructor(a: string) {
    this.a = a;
  }
}

class Base {
  readonly b: string = "base";
}
```

**ArkTS-Sta**

```typescript
class A {
  readonly a: string

  constructor(a: string) {
    this.a = a
  }
}

class Base {
  readonly b: string = "base";
}
```

## 不支持tagged templates

**规则：** `arkts-no-tagged-templates`

**规则解释：**

ArkTS-Sta不支持Tagged templates（标签模板字符串）。

**变更原因：**

ArkTS-Sta规范函数调用方式，支持字符串相加，但不支持Tagged templates（标签模板字符串）。

**适配建议：**

改为函数调用和字符串加法。

**示例：**

**ArkTS-Dyn**

```typescript
function myTag(strings: TemplateStringsArray, value: string): string {
  return strings[0] + value.toUpperCase() + strings[1];
}

const name = 'john';
const result1 = myTag`Hello, ${name}!`;
console.info(result1);

function formatTag(strings: TemplateStringsArray, first: string, last: string): string {
  return `${strings[0]}${first.toUpperCase()} ${last.toUpperCase()}${strings[1]}`;
}

const firstName = 'john';
const lastName = 'doe';
const result2 = formatTag`Hello, ${firstName} ${lastName}!`;
console.info(result2);
```

**ArkTS-Sta**

```typescript
function myTagWithoutTemplate(strings: string, value: string): string {
  return strings + value.toUpperCase();
}

const name = 'john';

const part1 = 'Hello, ';
const part2 = '!';
const result1 = myTagWithoutTemplate(part1, name) + part2;
console.info(result1);

function formatWithoutTemplate(greeting: string, first: string, last: string, end: string): string {
  return greeting + first.toUpperCase() + ' ' + last.toUpperCase() + end;
}

const firstName = 'john';
const lastName = 'doe';
const result2 = formatWithoutTemplate('Hello, ', firstName, lastName, '!'); // 直接使用函数参数
console.info(result2);
```

## 不支持确定赋值断言

**规则：** `arkts-no-definite-assignment`

**规则解释：**

ArkTS-Sta不支持确定赋值断言，例如：let v!: T。

**变更原因：**

ArkTS-Sta语法层面不支持。

**适配建议：**

修改声明方式。

**示例：**

**ArkTS-Dyn**

```typescript
let x!: number // 提示：在使用前将x初始化

initialize();

function initialize() {
  x = 10;
}

console.info('x = ' + x);
```

**ArkTS-Sta**

```typescript
function initialize(): number {
  return 10;
}

let x: number = initialize();

console.info('x = ' + x);
```

## Record增加运行时类型

**规则：** `arkts-record-add-runtime-type`

**规则解释：**

在ArkTS-Dyn中，Record是一个编译时类型，而不是一个运行时构造函数或类。

在ArkTS-Sta中，Record对象具有运行时类型。

**变更原因：**

在ArkTS-Sta中，对象字面量会生成类的实例。

**适配建议：**

开发者需要将点访问符改为[]访问符。

**示例：**

**ArkTS-Dyn**

```typescript
  let a: Record<string, number> = { 'v': 123 };
  console.info(String(a instanceof Record)) // error
  console.info(a['v'] + '') // 输出：123
  console.info(a.v + '') // 输出：123
```

**ArkTS-Sta**

```typescript
let a: Record<string, number> = { 'v': 123 };
console.info(String(a instanceof Record)) // 输出：true
console.info(a['v'] + '') // 输出：123
console.info(a.v + '') // error
```

## as具有运行时语义

**规则：** `arkts-no-ts-like-as`

**规则解释：**

ArkTS-Sta中`as`具有运行时语义。

**变更原因：**

ArkTS-Dyn中的`as`只在编译时提供类型信息，如果类型断言失败，报错时机取决于后续的代码操作。

ArkTS-Sta中的`as`会在运行时进行类型检查和可能的类型转换，如果类型断言失败，会立即抛出错误。

**适配建议：**

修改异常处理逻辑。

**示例：**

**ArkTS-Dyn**

```typescript
interface I {}
class A implements I {
  m: number = 0;
}

class B implements I {
  n: string = 'a';
}

let a: A = new A();
let i: I = a;
let t: B = i as B; // 正常编译运行
t.n.toString();    // 编译正常，运行时报错
```

**ArkTS-Sta**

```typescript
interface I {}
class A implements I {
    m: number = 0;
}

class B implements I {
    n: string = 'a';
}

let a: A = new A();
let i: I = a;
let t: B = i as B; // 编译正常，运行时报错
t.n.toString();
```

## catch语句中是error类型

**规则：** `arkts-no-ts-like-catch-type`

**规则解释：**

在ArkTS-Sta的静态模式中，类型必须明确，同时需考虑与ArkTS-Dyn的兼容性。对于catch(e)的语法，默认e为Error类型。

**变更原因：**

在ArkTS-Dyn上catch语句中的e是any类型。编译器不会对catch语句中的异常进行编译时类型检查。当ArkTS-Dyn上限制throw时，只能抛出Error类型。

在ArkTS-Sta中，类型必须明确。对于catch(e)的语法，默认e为Error类型，以保持与ArkTS-Dyn的兼容性。

**适配建议：**

开发者需要将catch(e)转换成需要处理的异常类型，例如：`(e as SomeError).prop`。

**示例：**

**ArkTS-Dyn**

```typescript
try {
  throw new Error();
} catch(e) {  // e是any类型
  e.message; // ArkTS-Dyn编译通过，运行正常
  e.prop;     // ArkTS-Dyn编译通过，输出undefined
}
```

**ArkTS-Sta**

```typescript
try {
  throw new Error();
} catch(e:Error) {  // e是Error类型
  e.message;   // ArkTS-Sta编译通过，运行正常
  e.prop;      // ArkTS-Sta编译错误，需要将e转换成需要处理的异常类型，例如：(e as SomeError).prop
}
```

## 不支持逻辑赋值运算

**规则：** `arkts-unsupport-operator`

**规则解释：**

ArkTS-Sta暂不支持`&&=`、`||=`、`??=`这三种逻辑赋值运算符。

**变更原因：**

语言层面暂不支持`&&=`、`||=`、`??=`，但是支持`&=`、`|=`、`?=`这类逻辑赋值运算符。

**适配建议：**
 
开发者自行替换为运算后赋值的写法，如：`x &&= y`替换为`x = x && y`。

**示例：**

**ArkTS-Dyn**

```typescript
let a = 1;
a &&= 2;    // 结果: 2，ArkTS-Sta暂不支持
a ||= 3;   // 结果: 2，ArkTS-Sta暂不支持
a ??= 4;  // 结果: 2，ArkTS-Sta暂不支持
```

**ArkTS-Sta**

```typescript
let a = 1;
a = a && 2;   // 结果: 2
a = a || 3;   // 结果: 2
a = a ?? 4;   // 结果: 2
```

## 非十进制bigint字面量

**规则：** `arkts-only-support-decimal-bigint-literal`

**规则解释：**

ArkTS-Sta暂不支持非十进制bigint字面量。

**变更原因：**

语言层面暂不支持。

**适配建议：**

开发者自行替换为BigInt()函数。

**示例：**

**ArkTS-Dyn**

```typescript
let a1: bigint = 0xBAD3n;  // 十六进制字面量，ArkTS-Sta暂不支持
let a2: bigint = 0o777n;   // 八进制字面量，ArkTS-Sta暂不支持
let a3: bigint = 0b101n;  // 二进制字面量，ArkTS-Sta暂不支持
```

**ArkTS-Sta**

```typescript
let a1: bigint = BigInt(0xBAD3);
let a2: bigint = BigInt(0o777);
let a3: bigint = BigInt(0b101);
```

## 数值类型和bigint类型的比较

**规则：** `arkts-numeric-bigint-compare`

**规则解释：**

ArkTS-Sta暂不支持数值类型和bigint类型的比较。

**变更原因：**

语言层面暂不支持。

**适配建议：**

开发者需将值转换为BigInt类型再进行比较。

**示例：**

**ArkTS-Dyn**

```typescript
let n1: number = 123;
let n2: bigint = 456n;

n1 <= n2;   // 编译通过
n1 == n2;   // 编译失败
n1 >= n2;   // 编译通过
```

**ArkTS-Sta**

```typescript
let n1: number = 123;
let n2: bigint = 456n;

BigInt(n1) <= n2;
BigInt(n1) == n2;
BigInt(n1) >= n2;
```

## 通过new创建的Number/Boolean/String对象不再是object类型

**规则：** `arkts-primitive-type-normalization`

**规则解释：**

在ArkTS-Sta中，用new创建的Number、Boolean和String对象不再是object类型，进行判断、比较等操作时，与ArkTS-Dyn的表现不同。

请开发者自行决定是否需要修改代码。

**变更原因：**

在ArkTS-Sta中，基本类型和其对应的包装类型在语言层面是相同的类型，这提高了语言的一致性和性能。

**适配建议：**

避免使用new创建的Number、Boolean和String对象进行比较和判断操作，建议使用基础类型。

**示例：**

**包装类型**

```typescript
// ArkTS-Dyn结果："object"
// ArkTS-Sta结果："number"
typeof new Number(1);

// ArkTS-Dyn结果：false
// ArkTS-Sta结果：true
new Number(1) == new Number(1); 

// ArkTS-Dyn结果：true（这里if语句判断的是Boolean对象是否为空，而不是拆箱后的结果，所以结果为true）
// ArkTS-Sta结果：false
if (new Boolean(false)) {}
```

**基础类型**

```typescript
// ArkTS-Dyn&ArkTS-Sta结果均为："number"
typeof 1;

// ArkTS-Dyn&ArkTS-Sta结果均为：true
1 == 1;

// ArkTS-Dyn&ArkTS-Sta结果均为：false
if (false) {}
```

## enum的元素不能作为类型

**规则：** `arkts-no-enum-prop-as-type`

**规则解释：**

ArkTS-Sta中enum（枚举）的元素不能作为类型使用。

**变更原因：**

ArkTS-Dyn中的枚举是编译时概念，在运行时仍是普通对象。

ArkTS-Sta中枚举的每个元素是枚举类的实例，无法作为类型使用。

**适配建议：**

使用枚举类型/字符串字面量类型。

**示例：**

**ArkTS-Dyn**

```typescript
enum A { E = 'A' }
function foo(a: A.E) {}
```

**ArkTS-Sta**

```typescript
enum A { E = 'A' }
function foo1(a: 'A') { }
function foo2(a: A) { }
```

## 不支持debugger 

**规则：** `arkts-no-debugger`

**规则解释：**

不支持debugger语句。

**变更原因：**

1. 静态类型语言具备编译时检查和强类型约束，DevEco Studio已具备完善的调试机制。

2. 使用debugger会侵入式地修改源码。

3. debugger语句会被优化，可能导致行为不一致。

**适配建议：**

使用DevEco Studio断点调试代替debugger语句。

**示例：**

**ArkTS-Dyn**

```typescript
// ArkTS-Dyn 
// ...
debugger;
// ...
```

**ArkTS-Sta**

```typescript
// ArkTS-Sta   移除debugger语句
// ...
```

## 不支持空数组/稀疏数组 

**规则：** `arkts-no-sparse-array`

**规则解释：**

ArkTS-Sta要求数组元素类型明确（显式声明类型或可通过上下文推导类型），禁止稀疏存储（避免内存浪费），且不允许undefined空位（确保空值安全）。

**变更原因：**

1. ArkTS-Sta遵循静态类型。如果空数组无法根据上下文推导出元素类型，会导致编译错误。

2. ArkTS-Sta的数组是连续存储的。使用空位（如 [1, , , 2]）会浪费内存。

3. ArkTS-Sta遵循空值安全，无法使用默认undefined表示空缺。

**适配建议：**

为数组标注合适的类型，不使用具有空洞的数组。

**示例：**

**ArkTS-Dyn**

```typescript
let a = []; // ArkTS-Sta，编译错误，需要从上下文中推导数组类型
let b = [1, , , 2]; // 不支持数组中的空位
b[1];  // undefined 
```

**ArkTS-Sta**

```typescript
let a: number[] = [];  // 支持，ArkTS-Sta上可以从上下文推导出类型
let b = [1, undefined, undefined, 2];
```

## 智能类型差异

**规则：** `arkts-no-ts-like-smart-type`

**规则解释：**

在ArkTS-Sta中，线程共享对象在做[智能转换](#智能转换)时会表现的与ArkTS-Dyn不一致。

**变更原因：**

在ArkTS-Sta中，由于线程共享对象在多线程中使用，编译器在做类型推导和分析时需要考虑并发场景下变量类型/值的变化。

**适配建议：**

线程共享对象要通过局部变量进行[智能转换](#智能转换)。

**示例：**

**ArkTS-Dyn**

```typescript
class AA {
  public static instance?: number;
  getInstance(): number {
    if (!AA.instance) {
      return 0;
    }
    return AA.instance;
  }
}
```

**ArkTS-Sta**

```typescript
class AA {
  public static instance?: number;
  getInstance(): number {
    let a = AA.instance     // 需通过局部变量进行类型转换。
    if (!a) {
      return 0;
    }
    return a;
  }
}
```

## 数组/元组类型在继承关系中遵循不变性原则

**规则：** `arkts-array-type-immutable`

**规则解释：**

在ArkTS-Sta中，数组在继承关系中遵循不变性原则，会通过编译时检查保证类型安全。

**变更原因：**

在ArkTS-Sta中，数组在继承关系中遵循不变性原则，编译时检查确保类型安全，将潜在的运行时错误提前到编译期，避免运行时失败，提高执行性能。

**适配建议：**

避免将不同类型的数组互相赋值。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  a: number = 0;
}

class B {
  b: number = 0;
}

// ArkTS-Dyn 
let arr1: A[] = [new A()];
let arr2: (A | B)[] = arr1;   // ArkTS-Sta编译错误
```

**ArkTS-Sta**

```typescript
class A {
  a: number = 0;
}

class B {
  b: number = 0;
}

// ArkTS-Sta 
let arr1: [ A | B ] = [new A()];
let arr2: [ A | B ] = arr1;  // 需要相同类型的元组
```

## 默认参数必须放在必选参数之后

**规则：** `arkts-default-args-behind-required-args`

**规则解释：**

在ArkTS-Sta中，函数、方法及lambda表达式的默认参数必须放在必选参数之后。

**变更原因：**

将默认参数置于必选参数前没有实际意义，开发者仍需为每个默认参数提供值。

**适配建议：**

默认参数放在必选参数之后。

**示例：**

**ArkTS-Dyn**

```typescript
function add(left: number = 0, right: number) { 
  return left + right;
}
```

**ArkTS-Sta**

```typescript
function add(left: number, right: number = 0) {
  return left + right;
}
```

## class的懒加载

**规则：** `arkts-class-lazy-import`

**规则解释：**

ArkTS-Sta的类默认是懒加载的。

**变更原因：**

ArkTS-Sta的类默认是懒加载的，这可以提升启动性能并减少内存占用。

**适配建议：**

将类中未执行的初始化逻辑移到外部。

**示例：**

**ArkTS-Dyn**

```typescript
class C {
  static {
    console.info('init');  // ArkTS-Sta上不会立即执行
  }
}
```

**ArkTS-Sta**

```typescript
// ArkTS-Sta  如果依赖没有被使用的class执行逻辑，那么将该段逻辑移出class
class C {
  static {}
}
console.info('init');
```

## 继承/实现方法时参数遵循逆变原则，返回类型遵循协变原则

**规则：** `arkts-method-inherit-rule`

**规则解释：**

ArkTS-Dyn与ArkTS-Sta在继承/实现方法时遵循以下规则。有关逆变和协变的详细解释，请参见[逆变和协变](#逆变和协变)。
|  类型位置 &nbsp;&nbsp;  |  ArkTS-Dyn规则   | ArkTS-Sta规则  | 
|  ----  |  ----  | ----  |
| 参数类型 | 逆变&协变  | 逆变 |
| 返回类型 | 协变  | 协变 |

**变更原因：**

参数类型逆变，可以通过编译时检查保证类型安全，提前发现潜在错误，避免运行时失败，提升执行性能。

返回类型协变，可以确保调用方按父类声明操作返回值时，所有父类声明的属性和方法必然存在。这样可以避免运行时出现属性或方法缺失的情况。

**适配建议：**

根据规则修改参数类型协变的代码。

**示例：**

**ArkTS-Dyn**

```typescript
class A { u = 0 }
class B { v = 0 }
class Father {
  fun1(a: A | B) { }
  fun2(a: A) { }
  fun3(): A | B { return new A() }
  fun4(x: A) { }
}
class Son extends Father {
  // 方法参数类型：协变
  override fun1(a: A) { }
  // 方法参数类型：逆变
  override fun2(a: A | B) { }
  // 方法返回类型：协变
  override fun3(): A { return new A() }
  // 父类是普通函数，子类是异步函数
  override async fun4(x: A | B) {
    await new Promise<void>(() => {});
  }
}
```

**ArkTS-Sta**

```typescript
class A { u = 0 }
class B { v = 0 }
class Father {
  fun1(a: A) { }
  fun2(): A | B { return new A() }
  fun3(x: A) { }
}
class Son extends Father {
  // 方法参数类型：逆变
  override fun1(a: A | B) { }
  // 方法返回类型：协变
  override fun2(): A { return new A() }
  // 父类是普通函数，子类是异步函数，需要改为普通函数，将异步的部分抽取出来
  override fun3(x: A | B) {
    this.asyncFunc();
  }
  async asyncFunc() {
    await new Promise<void>(() => {});
  }
}
```

## Enum不可以通过索引访问成员

**规则：** `arkts-enum-no-props-by-index`

**规则解释：**

ArkTS-Sta强化枚举静态类型约束（运行时保留类型信息），禁止通过索引访问以替代ArkTS-Dyn的动态对象行为。

**变更原因：**

1. ArkTS-Dyn已对索引访问元素的语法做了限制，ArkTS-Sta进一步增强了对枚举场景的约束。具体内容请参考[不支持通过索引访问字段](typescript-to-arkts-migration-guide.md#不支持通过索引访问字段)。

2. 在ArkTS-Dyn上，枚举是动态对象；而在ArkTS-Sta上，枚举是静态类型，并具有运行时类型，因此对索引访问做了限制以提高性能。

**适配建议：**

通过枚举的API来实现对应功能。

**示例：**

**ArkTS-Dyn**

```typescript
enum TEST {
  A,
  B,
  C
}

TEST['A'];       // ArkTS-Sta上不支持这种语法
TEST[0];    // ArkTS-Sta上不支持这种语法
```

**ArkTS-Sta**

```typescript
enum TEST {
  A,
  B,
  C
}

TEST.A;          // 使用点操作符或者enum的值
TEST.A.getName();  // 使用enum对应的方法获取enum的key
```

## 对象没有constructor

**规则：** `arkts-obj-no-constructor`

**规则解释：**

ArkTS-Sta不支持通过constructor获取类型信息。

**变更原因：**

ArkTS-Sta支持天然共享的能力，运行时需要确定类型信息，实现上不再是基于原型的语言，而是基于class的语言。

**适配建议：**

使用反射接口获取类型。

**示例：**

**ArkTS-Dyn**

```typescript
class A {}
let a = new A().constructor;   // ArkTS-Sta上编译错误
```

**ArkTS-Sta**

```typescript
class A {}
let a = new A();
let cls = Type.of(a); 
```

## 子类有参构造函数需要显式定义，且必须调用父类的构造函数

**规则：** `arkts-subclass-must-call-super-constructor-with-args`

**规则解释：**

ArkTS-Sta禁止隐式传递参数，子类有参构造函数需要显式定义，且必须调用父类的构造函数。

**变更原因：**

ArkTS-Dyn在运行时不对函数调用进行检查，并使用arguments机制获取所有参数并传入父类构造函数。

ArkTS-Sta不支持arguments机制，在编译时会对函数参数的个数和类型进行检查，以确保程序的安全性和正确性。子类显式定义有参构造函数，显式调用父类构造函数，可以避免继承二义性问题。

**适配建议：**

按规则声明对应的有参构造函数。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  constructor(a: number) {}
}
class B extends A {}       // ArkTS-Sta上编译报错
let b = new B(123);
```

**ArkTS-Sta**

```typescript
class A {
  constructor(a: number) {}
}
class B extends A {
  constructor(a: number) {
    super(a)
  }
}
let b = new B(123);
```

## 不支持可选元组类型

**规则：** `arkts-no-optional-tuple`

**规则解释：**

ArkTS-Sta不支持可选元组类型。

**变更原因：**

ArkTS-Sta不支持带有可选元素的元组类型。编译时检查确保类型安全，提前发现潜在的运行时错误，从而提高执行性能。

**适配建议：**

使用确定的元组类型或者使用联合类型。

**示例：**

**ArkTS-Dyn**

```typescript
let t: [number] = [1];
let t1: [number, boolean?] = t;   // ArkTS-Sta编译错误
```

**ArkTS-Sta**

```typescript
let t: [number] = [1];
let t1: [number, boolean] | [number] = t;
```

## 不支持超大数字字面量

**规则：** `arkts-no-big-numeric-literal`

**规则解释：**

ArkTS-Sta禁止超出int/long/double范围的数字字面量（编译报错），以避免隐式转换的性能损耗和浮点精度损失风险。

**变更原因：**

1. ArkTS-Sta支持更多数值类型细化，提高性能。超出int/long/double范围的数字字面量会导致编译错误。

2. 支持隐式转换会造成额外的性能损耗。

3. 浮点数据的隐式转换可能带来精度损失，违反开发者预期。清晰的数值边界可以提升代码的准确性和可读性。

**适配建议：**

数字字面量和具体的数值类型相匹配。

**示例：**

**ArkTS-Dyn**

```typescript
let s = 1000000000000000000000000000000000000; // 在ArkTS-Dyn中，该值会被转换为浮点形式数据，而ArkTS-Sta中则会导致编译错误。
let t = 1E+309;                               // 在ArkTS-Dyn中，该值会被转换为Infinity，而在ArkTS-Sta中则会导致编译错误。
```

**ArkTS-Sta**

```typescript
let s = 1000000000000000000000000000000000000.0; // ok，浮点形式数据
let t = Infinity;                                // ok，值为Infinity
```

## 对象的属性名必须是合法的标识符

**规则：** `arkts-identifier-as-prop-names`

**规则解释：**

ArkTS-Sta对象的属性名必须是合法标识符，不能为数字或字符串。

**变更原因：**

1. ArkTS-Dyn已进行约束，ArkTS-Sta增强了边界场景的约束。详情请参考[对象的属性名必须是合法的标识符](typescript-to-arkts-migration-guide.md#对象的属性名必须是合法的标识符)。

2. 静态类型中对属性的访问可提高执行性能。

3. 使用字符串作为属性名称可能引起二义性。

**适配建议：**

使用合法标识符作为对象的属性名。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  's' = 1;
}
```

**ArkTS-Sta**

```typescript
class A {
  s = 1;
}
```

## 子类不可以声明和父类的方法同名的lambda属性

**规则：** `arkts-no-subclass-lamada-prop-name-same-as-superclass-method`

**规则解释：**

ArkTS-Sta中子类不可以声明和父类的方法同名的lambda属性。

**变更原因：**

在ArkTS-Dyn中，方法类型与函数属性类型是兼容的，因此子类可以用兼容类型的函数属性来覆盖父类方法。

在ArkTS-Sta中，属性和方法有本质区别，函数属性类型不再与方法类型兼容，因此不支持这种写法。

**适配建议：**

请将子类中的lambda属性改为方法。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  foo() {
    console.info('A');
  }
}

class B extends A {
  foo: () => void = () => {
    console.info('B');
  }
}
```

**ArkTS-Sta**

```typescript
class A {
  foo() {
    console.info('A');
  }
}

class B extends A {
  foo() {
    console.info('B');
  }
}
```

## 子类不能在static context中调用super

**规则：** `arkts-no-super-call-in-static-context`

**规则解释：**

ArkTS-Sta子类不能在静态上下文中使用super访问父类。

**变更原因：**

1. ArkTS-Sta不再基于原型实现继承，没有原型或构造函数的概念，无需通过super访问父类。

2. super定义在子类的静态上下文中，容易混淆指向，与实例方法中指向父类实例的super相冲突，造成开发者混用。使用类名访问静态成员更清晰、可维护，易于理解。

**适配建议：**

使用父类名称访问父类的静态成员。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  static foo() {
    return 123;
  }
}

class B extends A {
  static foo() {
    return super.foo() + 456;
  }
}
```

**ArkTS-Sta**

```typescript
class A {
  static foo() {
    return 123;
  }
}

class B extends A {
  static foo() {
    return A.foo() + 456;
  }
}
```

## 实现接口时，对于接口中的属性需要实现get/set方法

**规则：** `arkts-class-implement-interface-prop-getter-setter`

**规则解释：**

ArkTS-Sta中实现接口时，对于接口中的属性需要实现get/set方法。

**变更原因：**

ArkTS-Sta遵循严格的类型检查，通过编译时检查保证类型安全，提前发现潜在错误，提高执行性能。

**适配建议：**

实现接口时，对于接口中的属性需要实现get/set方法（只读属性可以只实现get）。

**示例：**

**ArkTS-Dyn**

```typescript
interface I {
  v: number
}

class A implements I {
  get v(): number {
    return 1;
  }
}
```

**ArkTS-Sta**

```typescript
interface I {
  readonly v: number
}

class A implements I {
  get v(): number {
    return 1;
  }
}
```

## 不能将超出枚举范围的值赋值给枚举类型的变量

**规则：** `arkts-out-of-enum-index`

**规则解释：**

ArkTS-Sta中不能将超出枚举范围的值赋值给枚举类型的变量。

**变更原因：**

ArkTS-Sta采用类型安全的枚举设计，编译器执行严格的编译期值域检查，杜绝非法枚举赋值。枚举值为编译期常量，任何运行时越界赋值将触发类型错误，保障代码健壮性。

**适配建议：**

没有直接的替代写法，建议使用类或容器等结构实现。

**示例：**

**ArkTS-Dyn**

```typescript
enum T {
  A = 0,
  B = 1,
  C = 2
}

let num: number = 123;

let t1: T = 0;
let t2: T = -1;
let t3: T = num;
```

**ArkTS-Sta**

NA

## 不支持不定长的元组类型

**规则：** `arkts-no-unfixed-len-tuple`

**规则解释：**

ArkTS-Sta上不支持可变元组。

**变更原因：**

ArkTS-Sta不支持可变元组，以保证类型安全和提高执行性能。

**适配建议：**

使用数组代替可变元组。

**示例：**

**ArkTS-Dyn**

```typescript
const s: [string, ...boolean[]]=['', true];
```

**ArkTS-Sta**

```typescript
const s: (string | boolean)[] =['', true];
```

## 类实例不支持关系表达式

**规则：** `arkts-no-class-instance-relational-expression`

**规则解释：**

ArkTS-Sta限制关系表达式仅适用于基本类型（数值、字符串、布尔、枚举），不支持对象比较。

**变更原因：**

1. 在ArkTS-Sta中，为确保类型安全，关系表达式操作符仅限于数值、字符串、布尔和枚举类型，以避免隐式转换导致的非预期异常。

2. 对象的比较缺乏默认语义，会破坏语言的一致性。

**适配建议：**

通过方法或属性来比较对象。

**示例：**

**ArkTS-Dyn**

```typescript
class A {
  valueOf () {
    return 3;
  }
}

class B {
  valueOf () {
    return 4;
  }
}

let a = new A();
let b = new B();
console.info('a<b:', a < b);
```

**ArkTS-Sta**

```typescript
class A {
  valueOf () {
    return 3;
  }
}

class B {
  valueOf () {
    return 4;
  }
}

let a = new A();
let b = new B();
console.info(a.valueOf() < b.valueOf());
```

## instanceof的目标类型不能是函数

**规则：** `arkts-no-instanceof-func`

**规则解释：**

ArkTS-Sta中instanceof的目标类型不能是函数。

**变更原因：**

ArkTS-Sta不再基于原型实现继承，没有原型或构造函数的概念，不能通过任意函数创建对象。

**适配建议：**

请将instanceof的目标修改为类型。

**示例：**

**ArkTS-Dyn**

```typescript
function foo() {}
function bar(obj: Object) {
  console.info('obj instanceof foo :' ,obj instanceof foo);
}
```

**ArkTS-Sta**
```typescript
function bar(obj: Object) {
console.info('obj instanceof foo :', obj instanceof string);
}
```

## 静态加载包内模块某一文件时ohmurl路径变更

**规则：** `arkts-ohmurl-path-change`

**规则解释：**

在ArkTS-Sta中，静态加载包内模块的某个文件时，ohmurl路径必须完整，不可省略路径中的"src/main"。

**变更原因：**

有助于开发者更准确地定位模块文件位置。

**适配建议：**

补充路径中省略的"src/main"。

**示例：**

**ArkTS-Dyn**

```typescript
// library/ets/components/Index.ets
import { MainPage } from 'library/ets/components/MainPage'
```

**ArkTS-Sta**

```typescript
// library/ets/components/Index.ets
import { MainPage } from 'library/src/main/ets/components/MainPage'
```

## Number类型逻辑运算符结果类型变更

**场景描述：**

当两个number类型数值采用`||`、`&&`运算符时，在两个版本中结果存在差异。

在ArkTS-Dyn中，运算结果类型是number。

在ArkTS-Sta中，运算结果类型是boolean。

**示例：**

```typescript
let array = [1, 2];

array[1 && 1];
array[1 || 1];
```

## 抽象方法禁止重名

**场景描述：**

在ArkTS-Dyn中，支持抽象方法重名。

在ArkTS-Sta中，抽象方法重名会编译报错。

**示例：**

```typescript
abstract class Base6 {
  abstract foo1();

  abstract foo1();

  abstract foo1(): boolean;

  abstract foo1(): number;
}
```

## 仅有set访问器时属性读取限制

**场景描述：**

当类中只存在set访问器时，ArkTS-Dyn可以读取，ArkTS-Sta会编译报错。

**示例：**

```typescript
class Person {
  private _age: number = 0;

  // get age(): number {
  //   return this._age;
  // }

  set age(value: number) {
    this._age = value > 0 ? value : 0;
  }
}

let a: Person = new Person();

let b = a.age;
```

## 元组类型声明文件生成兼容性问题

**场景描述：**

在ArkTS-Sta中，当引用ArkTS-Dyn包含可选元素的元组类型或者包含rest展开的元组类型时，生成的声明文件会编译报错。

**示例：**

**ArkTS-Dyn**

```typescript
export type OptionalTuples = [number, boolean, string?];

export type VariableTuples = [string, ...string[]];
```

## 函数不定参数类型转换异常

**场景描述：**

在ArkTS-Dyn中，当引用ArkTS-Sta的函数不定参数，且参数为int类型（映射在ArkTS-Dyn中为number类型），调用时会引起运行时包类型转换异常。

**示例：**

```typescript
export function arg_rest_int_function(...args: int[]): int {
  return args[0];
}

arg_rest_int_function(1, 2, 3) === 1;
arg_rest_int_function(0) === 0;
```

## `return this`使用限制

**场景描述：**

在ArkTS-Dyn中，在类的`constructor`里可以使用`return this`，而在ArkTS-Sta中这种写法会报错。

**示例：**

```typescript
class Base {
  constructor() {
    return this;
  }
}
```

## this关键字作用域限制

**场景描述：**

在ArkTS-Dyn中，可以在`class`之外使用`this`，ArkTS-Sta只能在`class`内部使用。

**示例：**

```typescript
let that = this;
```

## 默认导出访问方式变更

**场景描述：**

在ArkTS-Dyn中，通过`import * as A`引入`A`之后可以用`A.default`访问到`A`里的`default`，但在ArkTS-Sta中这种写法会报错。

**示例：**

```typescript
// tt.ets
'use static'

export let num = 111;

export { num as default };
```

```typescript
// index.ets
import * as AAA from "./tt";

this.stateVar += AAA.default; // 在ArkTS-Sta中报错
```

## ArkTS-Sta多个剩余参数不能同时传入一个函数

**场景描述：**

在ArkTS-Sta中，多个剩余参数不能同时传入一个函数。

**适配建议：**

把多个元组参数合并后再传入。

**示例：**

**ArkTS-Dyn**

```typescript
const arr1: number[] = [1, 2, 3];
const arr2: number[] = [4, 5, 6];
const arr3: number[] = [7, 8, 9];

let testRestParameter = (...args: number[]) => {
  return args.toString();
}

testRestParameter(...arr1, ...arr2, ...arr3); 
```

**ArkTS-Sta**

```typescript
const arr1: number[] = [1, 2, 3];
const arr2: number[] = [4, 5, 6];
const arr3: number[] = [7, 8, 9];

function testRestParameter(...args: number[]) {
  return args.toString();
};

testRestParameter(...arr1.concat(arr2, arr3)); // 将多个参数合并再传入
```

## ArkTS-Sta在数字相乘超过int时会溢出

**场景描述：**

在ArkTS-Sta中，当int数值相乘结果太大，超出int最大值（-2147483648, 2147483647）时会溢出。

**适配建议：**

将int类型改为long类型。

**示例：**

**ArkTS-Dyn**

```typescript
let a = (24 * 60 * 60 * 1000) * (52 * 365 + 9 * 30 + 23);
console.info(a.toString()); // dynamic ： 1665187200000   static  ：-1260110848
```

**ArkTS-Sta**

```typescript
let tempa: long = 1000;
let a = (24 * 60 * 60 * tempa) * (52 * 365 + 9 * 30 + 23);
console.info(a.toString());
```

## 泛型上不存在.toString方法

**场景描述：**

在ArkTS-Sta中，如果泛型没有约束，会在编译时当成Any类型处理，Any类型不存在`.toString()`方法。

**适配建议：**

泛型加上`extends object`，继承object就有`.toString()`方法。

**示例：**

**ArkTS-Dyn**

```typescript
class Tp<T> {
  t: T;

  constructor(t: T) {
    this.t = t;
  }

  toString(): string {
    return "Tp: " + this.t?.toString();
  }
}
```

**ArkTS-Sta**

```typescript
class Tp<T extends object> {
  t: T;

  constructor(t: T) {
    this.t = t;
  }

  toString(): string {
    return "Tp: " + this.t?.toString();
  }
}
```

## 不支持Record中使用enum作为key

**场景描述：**

在ArkTS-Sta中：

1.不允许将字符串隐式转换成enum的值。

2.不支持计算属性的方式定义对象字面量。

**适配建议：**

在Record类型中，使用string作为key。

**示例：**

**ArkTS-Dyn**

```typescript
enum E {
  A = 'a',
  B = 'b'
}

let s1: Record<E, number> = {
  'a': 0,
  'b': 1
}
```

**ArkTS-Sta**

```typescript
enum E {
  A = 'a',
  B = 'b'
}

let s1: Record<string, number> = {
  'a': 0,
  'b': 1
}
```
