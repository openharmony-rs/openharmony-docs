# ArkTS-Sta互操作概述

## 背景

ArkTS-Sta在ArkTS-Dyn版本的基础上增强了类型安全和并发能力，带来了基于静态类型系统的编译器和运行时实现。为了让开发者能够达到更好的并发性能等目的，可选择ArkTS-Sta作为开发语言，或将存量应用逐步改造为ArkTS-Sta版本。在此场景下，为了让开发者能够复用已有的生态资产，以及让存量应用的开发者可以便捷地逐步迁移到ArkTS-Sta，我们需要提供ArkTS-Sta和ArkTS-Dyn以及TS/JS代码的交互能力。

## 可交互方向

- ArkTS-Sta可以导入ArkTS-Dyn, TS, JS。
- ArkTS-Dyn可以导入ArkTS-Sta。
- TS/JS不可以导入ArkTS-Sta/ArkTS-Dyn。

## ArkTS-Sta 静态语义原则

- ArkTS-Sta的对象的布局不能被修改，动态修改对象布局（包括新增或删除对象属性，以及修改对象属性的类型）将会出现编译时报错或者运行时报错。
- ArkTS-Sta的函数参数需要匹配声明的类型，否则会出现编译报错或运行时报错。
- ArkTS-Sta代码中的类型转换如果不能在运行时以合理的方式进行，将会出现编译报错或运行时报错。

## ArkTS-Sta类型系统

- ArkTS-Sta的顶层类型有：`undefined`，`null`和`Any`。
  - `Any`有子类`Object`，`Object`有子类`ESValue`。ArkTS-Sta中的自定义类，标准库(`Array/Map/Set`等)等类型都是`Object`的子类型。

### ESValue

- `ESValue`是`Object`的子类。
- `ESValue`可用于封装来自于JS的对象。
- `ESValue`提供了多种方法来对应对象的常见操作。比如：加载 JS 模块、实例化`new obj(x)`、函数调用`obj(x)`、属性访问`obj.prop`、方法调用`obj.foo(x)`、索引访问`obj[idx]`等。
- ArkTS-Sta的`ESValue`作为普通的类型，并无额外限制和额外特权。比如：ArkTS-Sta中`ESValue`可以用于类型标注和泛型，但针对`ESValue`类型对象的操作也只能通过调用它的方法来进行。

```txt
AnyObject
    |
Object
    |
ESValue  -|- (static) load(path: string): ESValue                            // 模块加载
          |- wrap(arg: Any)                                                  // 将对象包装成ESValue实例
          |- getProperty(key: string | number): ESValue                      // 读属性
          |- setProperty(key: string | number, newVal: ESValue): void        // 写属性
          |- instantiate(...args: ESValue[]): ESValue                        // 实例化
          |- invoke(...args: ESValue[]): ESValue                             // 函数调用
          |- invokeMethod(methodName: string, ...args: ESValue[]): ESValue   // 方法调用
          |- toString(): string                                              // 将包装的对象转换为string
          |- toNumber(): number                                              // 将包装的对象转换为number
          |- ...
```

（TODO：加链接）`ESValue`接口说明文档。

## 交互基本原则

- ArkTS-Sta特有的语言特性不能用于和ArkTS-Dyn交互（比如：重载、注解、final、尾随闭包、function with receiver）。
- ArkTS-Dyn特有的语言特性不能用于和ArkTS-Sta交互（比如：@Sendable/@Concurrenct）。
- TS特有的语言特性不能用于和ArkTS-Sta交互（比如：decorator、call-signature）。
- ArkTS-Sta的对象属性在动态上下文使用时有如下特点：
  - 没有自身属性（own property）。
  - 对象和对象的属性都是密封的（sealed）。
- ArkTS-Sta和JS的交互，需要开发者显式调用API来进行交互。
- 使用规格之外的交互特性，可能导致未定义的行为，并且后续演进的兼容性无法保证。
> **说明：**
>
> ArkTS-Sta的对象在动态上下文中没有自身属性，导致在动态上下文中使用JSON.stringify获取ArkTS-Sta对象的json字符串时，不能得到预期的结果。
> 本规格仅支持ArkTS-Sta与ArkTS-Dyn、ArkTS-Sta与TS之间的交互，如果希望ArkTS-Sta与JS的直接或间接的易用性交互，开发者需要为JS提供声明文件。

```javascript
// file1.js
export class A {
  constructor() {
    console.log("new A");
  }
  msg = "hello";
  data = [1, 2, 3];
  say(arg) {
    console.log(this.msg + arg);
  }
}
export function foo(arg) {
  return arg;
}
```

```typescript
// file2.ets ArkTS-Sta
'use static'
// 加载模块
let module: ESValue = ESValue.load('./file1')
let foo: ESValue = module.getProperty('foo')
let A: ESValue = module.getProperty('A')
// 实例化
let aa: ESValue = A.instantiate()
// 调用函数
let a: ESValue = foo.invoke(aa)
// 读属性
let msg: ESValue = a.getProperty('msg')
let msgStr: string = msg.toString()  // 'hello'
let data: ESValue = a.getProperty('data')
// 写属性
let newMsgValue: ESValue = ESValue.wrap('world')  // 将对象包装成ESValue实例
a.setProperty('msg', newMsgValue)
// 调用方法
a.invokeMethod('say', ESValue.wrap(' cup'))  // 打印'world cup'
// 读索引元素
let element0 = data.getProperty(0)
element0.toNumber()  // 1
// 写索引元素
data.setProperty(2, ESValue.wrap(4))
```

- ArkTS-Sta和ArkTS-Dyn/TS的交互，不需要开发者显式调用API来进行交互。

```typescript
// file1.ts
export class A {
  constructor() {
    console.log("new A");
  }
  msg: string = "hello";
  say(arg: string): void {
    console.log(this.msg + arg);
  }
}
export function foo(arg: A): A {
  return arg;
}
```

```typescript
// file2.ets ArkTS-Sta
'use static'
// 加载模块
import { A, foo } from "./file1";
// 实例化
let aa: A = new A();
// 调用函数
let a: A = foo(aa);
// 读属性
let msg: string = a.msg; // 'hello'
// 写属性
a.msg = "world";
// 调用方法
a.say(" cup"); // 打印'world cup'
```

### 函数
支持交互的函数需要满足下面所有条件：
- 支持交互的函数包括function、方法和getter/setter，不包括lambda。
- 函数的入参和返回值类型必须是[类型映射](arkts-interop-type-mapping.md)章节中支持的类型。
- 函数的入参需要是非默认参数，非可选参数，以及非剩余参数。
- 函数必须是非泛型函数，非异步函数。
- 函数必须是非重载的。
- 整个函数没有装饰器或注解。
> **说明：**
>
> 函数会被映射为函数，不满足条件的函数可以封装成满足条件的函数再进行交互。

### 接口
支持交互的接口需要满足下面所有条件：
- 接口方法须满足[函数](#函数)章节的限制。
- 接口需要是非泛型的。
- 接口只能单继承。
- 字段是必选字段。
- 方法没有默认实现。
- 方法是必选方法。
- 相对于父接口，字段和方法不支持重写。
- 接口中字段类型必须是[类型映射](arkts-interop-type-mapping.md)章节中支持的类型。
- 接口只能继承自定义的接口（即，非语言内置的接口），父接口也必须满足上述要求。
- 整个接口没有装饰器或注解。
> **说明：**
>
> 接口会被映射成接口，接口的属性会被映射成属性，接口的方法会被映射成方法。

### 类
支持交互的类需要满足下面所有条件：
- 构造函数/实例方法/静态方法须满足[函数](#函数)章节的限制。
- 类需要是非泛型的。
- 字段和父类的字段名字不同（字段不支持重写）。
- 类不能被final或abstract修饰。
- 类只能单实现。
- 类实现的接口只能是自定义的接口(即，非语言内置的接口)，并且需要满足接口交互的要求。
- 字段类型必须是[类型映射](arkts-interop-type-mapping.md)章节中支持的类型。
- 类继承的父类只能是Object或其它自定义类(即，非语言内置的类)，父类也必须满足上述要求。
- 整个类没有装饰器或注解。
> **说明：**
>
> 类会被映射成类，类的方法会被映射为方法。ArkTS-Sta中类的属性会被映射为ArkTS-Dyn的getter/setter方法，ArkTS-Dyn中类的属性会被映射为ArkTS-Sta属性。

## 交互规格
交互规格基于上面支持的类型。
- import  
支持import const变量，函数，类，接口，其中const变量的类型必须是[类型映射](arkts-interop-type-mapping.md)章节中支持的类型，函数，类，接口必须分别满足[类型映射](arkts-interop-type-mapping.md)章节中的要求。仅支持 import { xxx1,xxx2 } from yyy 和 import xxx1, xx2 from yyy的语法。(不支持 import * as 等其它import语法)。
- 调用函数
- 调用方法
- 访问属性
- new类实例
- 运算  
**算术运算**  
操作数类型需要为number。  
加减乘除模: +, -, *, /, %。  
以及它们和赋值组合的运算: +=, -=, *=, /=, %=。  
以及自增自减: ++, --。  
**位运算**  
操作数类型需要为number。  
与或非异或: &, |, ~, ^。  
以及它们和赋值组合的运算: &=, |=, ^= 。  
算术左移，算术右移，无符号右移: <<, >>, >>>。  
以及它们和赋值组合的运算: <<=, >>=, >>>=。  
**逻辑运算**  
操作数类型需要为布尔。  
与或非: &&, ||, !。  
以及与和或和赋值运算组合: &&=, ||=。  
**比较运算**  
`<`, `>`, `<=`, `>=` 操作数类型需要为number。  
`==`, `===`, `!=`, `!==` 操作数类型无限制。  


注意：以上没有明确说明要支持的场景都不支持，比如：
- 不支持跨ArkTS-Dyn和ArkTS-Sta的继承和实现。
- 不支持创建对象字面量。
- 不支持访问数组及其子类的下标。
- 不支持for-of遍历可迭代对象的元素。
- 不支持await Promise对象。
- 不支持catch异常。
- 不支持类型标注。
- 不支持typeof运算。
- 不支持instanceof运算。
- 不支持ArkTS-Dyn的类继承ArkTS-Sta的类。
- 不支持ArkTS-Dyn的类实现ArkTS-Sta的类。
- 不支持ArkTS-Dyn的接口继承ArkTS-Sta的接口。
- 不支持异步/并发/多线程上下文中交互。