# ArkTS-Sta与ArkTS-Dyn互操作迁移规则

## ArkTS-Dyn中使用ArkTS-Sta

### ArkTS-Sta导出ArkTS-Dyn实体

**规则：** `arkts-interop-d2s-export-entity`

**规则解释：**

ArkTS-Sta中不允许将导入ArkTS-Dyn模块中的实体重新导出。

**变更原因：**

确保模块之间的静态与动态边界清晰，防止动态模块中的不确定行为影响静态模块的类型安全和编译优化。

**适配建议：**

避免将导入ArkTS-Dyn模块中的实体重新导出。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export function foo() {}
export class X {}
export interface Y {}

// file2.ets
import { foo } from './file1';
export { foo };

export { X, Y } from './file1';
```

**ArkTS-Sta**
```typescript
// file1.ets ArkTS-Dyn
export function foo() {}
export class X {}
export interface Y {}

// file2.ets ArkTS-Sta
'use static'
import { foo } from './file1';
export { foo }; // 编译报错

export { X, Y } from './file2'; // 编译报错
```

### ArkTS-Sta判断ArkTS-Dyn装箱类型

**规则：** `arkts-interop-d2s-boxed-type`

**规则解释：**

ArkTS-Sta判断ArkTS-Dyn的装箱类型时会转换为对应的基本类型并使用。

**变更原因：**

在ArkTS-Sta中，语言层面不再区分基本类型和装箱类型。因此，当与JS或ArkTS-Dyn进行互操作时，ArkTS-Sta会自动拆箱，转换为对应的基本类型并使用。

**适配建议：**

避免使用装箱类型或对装箱类型进行typeof操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export let a = new Number(123);
export let b = new Boolean(true);
export let c = new String('hello');
typeof a; // 'object'
typeof b; // 'object'
typeof c; // 'object'

//file2.ets
import { a, b, c } from './file1';
typeof a; // 'object'
typeof b; // 'object'
typeof c; // 'object'
```

**ArkTS-Sta**
```typescript
// file1.ets ArkTS-Sta
'use static'
export let a = new Number(123);
export let b = new Boolean(true);
export let c = new String('hello');
typeof a; // 'number'
typeof b; // 'boolean'
typeof c; // 'string'

//file2.ets  ArkTS-Dyn
import { a, b, c } from './file1';
typeof a; // 'number'
typeof b; // 'boolean'
typeof c; // 'string'
```

### ArkTS-Sta使用ArkTS-Dyn的@Sendable和@Concurrent

**规则：** `arkts-interop-d2s-no-concurrent-decorators`

**规则解释：**

ArkTS-Sta不支持@Sendable和@Concurrent注解。

**变更原因：**

ArkTS-Sta的对象天然支持并发共享，不需要加@Sendable和@Concurrent注解。

**适配建议：**

使用ArkTS-Sta的并发特性时不需要添加@Sendable和@Concurrent注解。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
@Sendable
class X {}

@Concurrent
function foo() {}
```

**ArkTS-Sta**
```typescript
// file1.ets
'use static'
class X {}

function foo() {}
```

### ArkTS-Dyn的Object内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-d2s-dynamic-object-on-static-instance`

**规则解释：**

ArkTS-Dyn的Object内置方法作用在ArkTS-Sta对象需要重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export function foo(prx: Object) {
  Object.getOwnPropertyNames(prx); // ["a"]
  Object.hasOwn(prx, 'a'); // true
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}

// file2.ets
import { foo } from './file1';
class X {
  a = 1;
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// Object.keys的解决方案，与Object.values的情况类似
// file0.ets  ArkTS-Sta
'use static'
export function getKeys(prx: Object | ESValue): string[] | undefined {
  if (prx instanceof Object) {
    return Object.keys(prx);
  }
  return undefined;
}

// file1.ets ArkTS-Dyn
import { getKeys } from './file0';
function myGetKeys(prx: Object) {
  let ret = getKeys(prx);
  if (ret == undefined) {
    // prx is dynamic
    return Object.keys(prx);
  }
  return ret;
}
export function foo(prx: Object) {
  Object.getOwnPropertyNames(prx); // []
  Object.hasOwn(prx, 'a'); // false
  Object.keys(prx); // []
  myGetKeys(prx); // ['a']
  Object.values(prx); // []
}

// file2.ets  ArkTS-Sta
'use static'
import { foo } from './file1';
class X {
  a = 1;
}
foo(new X());
```

### ArkTS-Dyn的Reflect内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-d2s-dynamic-reflect-on-static-instance`

**规则解释：**

ArkTS-Dyn的Reflect内置方法作用在ArkTS-Sta对象需要重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
import { foo } from './file1';
export class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}

// file2.ets
import { X } from './file1';
function foo(prx: Object) {
  Reflect.ownKeys(prx); // ['a']
  Reflect.set(prx, 'newField', 7); // true
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// static ownKeys的解决方案
// file0.ets ArkTS-Sta
'use static'
export getOwnKeys(prx: Object | ESValue): string[] | undefined {
    if (prx instanceof Object) { return Reflect.ownKeys(prx) }
    return undefined
}

// file1.ets ArkTS-Dyn
import { getOwnKeys } from './file0'
export function myOwnKeys(prx: Object) {
    let ret = getOwnKeys(prx)
    if (ret == undefined) {  // prx是动态对象
        return Reflect.ownKeys(prx)
    }
    return ret
}

export function foo(prx: Object) {
    Reflect.ownKeys(prx)  // []
    myOwnKeys(prx)  // ['a']
    Reflect.set(prx, 'newField', 7)  // false
}

// file2.ets  ArkTS-Sta
'use static'
import { foo } from './file1'
export class X {
    a: string = 'hello'
    getName() { return this.a }
}
foo(new X())
```

### ArkTS-Sta的Object内置方法作用在ArkTS-Dyn对象

**规则：** `arkts-interop-d2s-static-object-on-dynamic-instance`

**规则解释：**

ArkTS-Sta的Object内置方法作用在ArkTS-Dyn对象时参数类型不匹配。

**变更原因：**

Object的接口参数类型为静态Object。ArkTS-Dyn对象在ArkTS-Sta中不是静态Object实例，因此参数类型不匹配。

**适配建议：**

使用动态Object的接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export class X {
  a = 1;
}

// file2.ets
import { X } from 'file1';
export function foo(prx: Object) {
  Object.entries(prx); // [a, 1]
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.ets  ArkTS-Dyn
export class X {
  a = 1;
}

// file2.ets  ArkTS-Sta
'use static'
import { X } from 'file1';
export function foo(prx: Object) {
  Object.entries(prx); // [a, 1]
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}
foo(new X()); // 编译报错
```

### ArkTS-Sta的Reflect内置方法作用在ArkTS-Dyn对象

**规则：** `arkts-interop-d2s-static-reflect-on-dynamic-instance`

**规则解释：**

ArkTS-Sta的Reflect内置方法作用在ArkTS-Dyn对象时参数类型不匹配。

**变更原因：**

Reflect接口参数类型为静态Object。ArkTS-Dyn对象在ArkTS-Sta中不是静态Object实例，因此参数类型不匹配。

**适配建议：**

使用动态Reflect接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets 
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}

// file2.ets 
import { X } from './file1';
export function foo(prx: Object) {
  Reflect.get(prx, 'a'); // 'hello'
  Reflect.set(prx, 'a', 'world'); // true
  Reflect.ownKeys(prx); // ['a']
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.ets  ArkTS-Dyn
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}

// file2.ets  ArkTS-Sta
'use static'
import { X } from './file1';
export function foo(prx: Object) {
  Reflect.get(prx, 'a'); // 编译报错
  Reflect.set(prx, 'a', 'world'); // 编译报错
  Reflect.ownKeys(prx); // 编译报错
}
foo(new X()); 
```

### ArkTS-Sta动态导入ArkTS-Dyn

**规则：** `arkts-interop-d2s-dynamic-import`

**规则解释：**

ArkTS-Sta不支持直接动态导入ArkTS-Dyn模块和调用接口。

**变更原因：**

ArkTS-Sta没有动态import语法，使用ESValue接口动态导入动态模块。

**适配建议：**

使用ESValue接口动态导入模块和调用接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export class A {}

// file2.ets
let mod = await import('./file1');
let A: ESValue = mod.A;
let a = new A() as A;

// 动态导入class、function、enum变量
```

**ArkTS-Sta**
```typescript
// file1.ets  ArkTS-Dyn
export class A {}

// file2.ets   ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let A: ESValue = mod.getProperty('A');
let a = A.instantiate() as A;
```

### ArkTS-Sta创建ArkTS-Dyn的没有无参构造函数的类的对象字面量

**规则：** `arkts-interop-d2s-object-literal-no-args-constructor`

**规则解释：**

ArkTS-Sta不支持创建ArkTS-Dyn中没有无参构造函数的类的对象字面量。

**变更原因：**

由于ArkTS-Sta的语法限制，当ArkTS-Sta创建ArkTS-Dyn的没有无参构造函数的类的对象字面量时，需要使用new关键字和构造函数。

**适配建议：**

使用new关键字进行创建。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export class X {
  name: string;
  constructor(arg: string) {
    this.name = arg;
  }
}
// file2.ets
import { X } from './file1';
let x = new X('hello');
```

**ArkTS-Sta**
```typescript
// file1.ets  ArkTS-Dyn
export class X {
  name: string;
  constructor(arg: string) {
    this.name = arg;
  }
}
// file2.ets  ArkTS-Sta
'use static'
import { X } from './file1';
let x1: X = {name: 'hello'}   //编译报错
let x2: X = new X('hello')    // OK
```

### ArkTS-Sta创建ArkTS-Dyn具有二义性的对象字面量

**规则：** `arkts-interop-d2s-object-literal-no-ambiguity`

**规则解释：**

ArkTS-Sta不支持创建ArkTS-Dyn具有二义性的对象字面量。

**变更原因：**

由于ArkTS-Sta的语法限制，当一个对象的类型被声明为联合类型，而右侧实际赋值的是一个类的实例时，会引发类型系统的二义性（对象可以是联合类型的任一类型，但实际运行时明确是一个类的实例，这种差异会导致类型检查或运行时的不确定性）。

**适配建议：**

使用as确定类型。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export class X {
  name: string = '';
}
export interface Y {
  name: string;
  age?: number;
}

// file2.ets
import { X, Y } from './file1';
let x: X | Y = { name: 'hello' };
```

**ArkTS-Sta**
```typescript
// file1.ets  ArkTS-Dyn
export class X {
  name: string = '';
}
export interface Y {
  name: string;
  age?: number;
}

// file2.ets  ArkTS-Sta
'use static'
import { X, Y } from './file1';
let x: X | Y = { name: 'hello' }; //编译报错
let x: X | Y = new X('hello'); // OK
```

### ArkTS-Sta创建ArkTS-Dyn的类的对象字面量

**规则：** `arkts-interop-d2s-object-literal`

**规则解释：**

ArkTS-Sta创建ArkTS-Dyn的类的对象字面量时，不支持使用instanceof判断字面量类型。

**变更原因：**

由于ArkTS-Sta的语义变更，在创建ArkTS-Dyn的类的对象字面量时，不支持使用instanceof判断字面量类型。

**适配建议：**

ArkTS-Sta创建ArkTS-Dyn的类的对象字面量时，不要使用instanceof判断字面量类型。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export class A {
  name: string = '';
}

// file2.ets
import { A } from './file1';
let a: A = { name: 'hello' }; // a是创建的对象自变量

a instanceof A; // false
```

**ArkTS-Sta**
```typescript
// file1.ets ArkTS-Dyn
export class A {
  name: string = '';
}

// file2.ets ArkTS-Sta
'use static'
import { A } from './file1';
let a: A = { name: 'hello' }; // a是创建的对象

a instanceof A; // true
```

## ArkTS-Sta中使用ArkTS-Dyn

### ArkTS-Dyn判断ArkTS-Sta装箱类型

**规则：** `arkts-interop-s2d-boxed-type`

**规则解释：**

ArkTS-Dyn判断ArkTS-Sta的装箱类型时，会根据ArkTS-Sta自动拆箱的结果进行处理。

**变更原因：**

在ArkTS-Sta中，语言层面不再区分基本类型和装箱类型。因此，当与JS或ArkTS-Dyn进行互操作时，ArkTS-Sta会自动拆箱，转换为对应的基本类型并使用。

**适配建议：**

避免使用装箱类型或对装箱类型进行typeof操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export let a = new Number(123);
export let b = new Boolean(true);
export let c = new String('hello');
typeof a; // 'object'
typeof b; // 'object'
typeof c; // 'object'

//file2.ets
import { a, b, c } from './file1';
typeof a; // 'object'
typeof b; // 'object'
typeof c; // 'object'
```

**ArkTS-Sta**
```typescript
// file1.ets ArkTS-Sta
'use static'
export let a = new Number(123);
export let b = new Boolean(true);
export let c = new String('hello');
typeof a; // 'number'
typeof b; // 'boolean'
typeof c; // 'string'

//file2.ets  ArkTS-Dyn
import { a, b, c } from './file1';
typeof a; // 'number'
typeof b; // 'boolean'
typeof c; // 'string'
```

### ArkTS-Dyn创建ArkTS-Sta对象字面量

**规则：** `arkts-interop-s2d-object-literal`

**规则解释：**

ArkTS-Dyn中使用构造函数创建ArkTS-Sta对象字面量。

**变更原因：**

ArkTS-Dyn的对象字面量是动态对象，不是真正的标注类型，所以ArkTS-Dyn中使用构造函数创建ArkTS-Sta对象字面量。

**适配建议：**

使用构造函数创建对象字面量。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export class X {
  name: string = '';
  constructor(arg: string) {
    this.name = arg;
  }
}
export interface Y {
  data: number;
}
export type MyRecord = Record<string, number>;
export function foo(arg: X) {}
export function bar(arg: Y) {}

// file2.ets
import { X, Y } from './file1';
let x = { name: 'hello' };
let y: Y = { data: 123 };
foo({ name: 'world' });
bar({ data: 456 });
// 返回值 zoo(): X { return {..}}
// 嵌套场景
interface Z {
  x: X;
}
let z: Z = {x: { name: 'hello' }};
```

**ArkTS-Sta**
```typescript
// file1.ets ArkTS-Sta
'use static'
export class X { name: string = '' }
export interface Y { data: number }
export function foo(arg: X) { }
export function bar(arg: Y) { }
export function createY(d: number): Y {
  let y: Y = { data: d }
  return y
}

// file2.ets ArkTS-Dyn
import { X, Y, createY } from "./file1"
let x: X = new X("hello")
let y: Y = createY(123)
foo(new X("world"))
bar(createY(456))
```

### ArkTS-Dyn传参或赋值给ArkTS-Sta

**规则：** `arkts-interop-s2d-dynamic-args-to-static`

**规则解释：**

ArkTS-Dyn对象无法直接传参或赋值给ArkTS-Sta。

**变更原因：**

ArkTS-Dyn对象是动态的，无法传参或赋值给ArkTS-Sta静态类型。

**适配建议：**

将ArkTS-Sta接收的动态对象参数或字段的类型声明为ESObject。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export function foo(obj: Object) {}
export class A {
  data: Object = 0;
}

// file2.ets
import { foo, A } from './file1';

class X {}
foo(new X());
interface Y {
  s: string;
}
let y: Y = { s: 'Hi' };
let a = new A();
a.data = y;
// 动态对象的来源：class/interface/对象字面量
```

**ArkTS-Sta**
```typescript
// file1.ets ArkTS-Sta
'use static'
export function foo(obj: Object) {}
// solution: export function foo(obj: ESValue | Object) {}
export class A {
  data: Object = 0;
}
// solution: export class A { data: ESValue = ESValue.wrap(0) }

// file2.ets ArkTS-Dyn
import { foo, A } from './file1';

class X {}
foo(new X()); // 运行时报错
interface Y {
  s: string;
}
let y: Y = { s: 'Hi' };
let a = new A();
a.data = y; // 运行时报错
```

### ArkTS-Dyn的Object内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-s2d-dynamic-object-on-static-instance`

**规则解释：**

ArkTS-Dyn的Object内置方法作用在ArkTS-Sta对象需要重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file2.ets
export class X {
  a = 1;
}

// file1.ets
import { X } from './file2';
function foo(prx: Object) {
  Object.getOwnPropertyNames(prx); // ["a"]
  Object.hasOwn(prx, 'a'); // true
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}

foo(new X());
```

**ArkTS-Sta**
```typescript
// file2.ets ArkTS-Sta
'use static'
export class X {
  a = 1;
}
// Object.keys的解决方案，与Object.values的情况类似
export function getKeys(prx: Object | ESValue): string[] | undefined {
  if (prx instanceof Object) {
    return Object.keys(prx);
  }
  return undefined;
}
// file1.ets ArkTS-Dyn
import { X, getKeys } from './file2';
function myGetKeys(prx: Object) {
  let ret = getKeys(prx);
  if (ret == undefined) {
    // prx is dynamic
    return Object.keys(prx);
  }
  return ret;
}
export function foo(prx: Object) {
  Object.getOwnPropertyNames(prx); // []
  Object.hasOwn(prx, 'a'); // false
  Object.keys(prx); // []
  myGetKeys(prx); // ['a']
  Object.values(prx); // []
}

foo(new X());
```

### ArkTS-Dyn的Reflect内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-s2d-dynamic-reflect-on-static-instance`

**规则解释：**

ArkTS-Dyn的Reflect内置方法作用在ArkTS-Sta对象需要重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file2.ets
export class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}

// file1.ets
import { X } from './file2';
function foo(prx: Object) {
  Reflect.ownKeys(prx); // ['a']
  Reflect.set(prx, 'newField', 7); // true
}

foo(new X());
```

**ArkTS-Sta**
```typescript
// file2.ets  ArkTS-Sta
'use static'
export class X {
  a: string = 'hello'
  getName() { return this.a }
}

// static ownKeys的解决方案
export getOwnKeys(prx: Object | ESValue): string[] | undefined {
  if (prx instanceof Object) { return Reflect.ownKeys(prx) }
  return undefined
}

// file1.ets ArkTS-Dyn
import { X, getOwnKeys } from "./file2"
function myOwnKeys(prx: Object) {
  let ret = getOwnKeys(prx)
  if (ret == undefined) {  // prx is dynamic
      return Reflect.ownKeys(prx)
  }
  return ret
}

function foo(prx: Object) {
  Reflect.ownKeys(prx)  // []
  myOwnKeys(prx)  // ['a']
  Reflect.set(prx, 'newField', 7)  // false
}

foo(new X())
```

### ArkTS-Sta的Object内置方法作用在ArkTS-Dyn对象

**规则：** `arkts-interop-s2d-static-object-on-dynamic-instance`

**规则解释：**

ArkTS-Sta的Object内置方法作用在ArkTS-Dyn对象需要重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

使用动态Object的接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export function foo(prx: Object) {
  Object.entries(prx); // [a, 1]
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}

// file2.ets
import { foo } from './file1';
class X {
  a = 1;
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.ets  ArkTS-Sta
'use static'
export function foo(prx: Object) {
  Object.entries(prx); // [a, 1]
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}

// file2.ets  ArkTS-Dyn
import { foo } from './file1';
class X {
  a = 1;
}
foo(new X()); // 运行时报错
```

### ArkTS-Sta的Reflect内置方法作用在ArkTS-Dyn对象

**规则：** `arkts-interop-s2d-static-reflect-on-dynamic-instance`

**规则解释：**

ArkTS-Sta的Reflect内置方法不应作用在ArkTS-Dyn对象。

**变更原因：**

ArkTS-Dyn对象在ArkTS-Sta中表现为ESObject实例，不是Object实例，因此参数类型不匹配。

**适配建议：**

使用动态Reflect接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export function foo(prx: Object) {
  Reflect.get(prx, 'a'); // 'hello'
  Reflect.set(prx, 'a', 'world'); // true
  Reflect.ownKeys(prx); // ['a']
}

// file2.ets
import { foo } from './file1';
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.ets  ArkTS-Sta
'use static'
export function foo(prx: Object) {
  Reflect.get(prx, 'a'); // 'hello'
  Reflect.set(prx, 'a', 'world'); // true
  Reflect.ownKeys(prx); // ['a']
}

// file2.ets  ArkTS-Dyn
import { foo } from './file1';
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}
foo(new X()); // 运行时报错
```

### ArkTS-Dyn代码调用ArkTS-Sta中废弃的方法

**规则：** `arkts-interop-s2d-dynamic-call-builtin-api-not-in-static`

**规则解释：**

不支持在ArkTS-Dyn代码中导入并调用ArkTS-Sta中已被移除的方法。

**变更原因：**

在ArkTS-Dyn代码中导入ArkTS-Sta的Builtin类型对象，并调用一个在ArkTS-Sta版本中已被移除（但在ArkTS-Dyn中仍存在）的方法，导致潜在的兼容性问题出现。

**适配建议：**

避免在ArkTS-Dyn代码中调用ArkTS-Sta中废弃的方法。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ets
export let arr: Array<number> = new Array<number>(1, 2, 3);

// file2.ets
import {arr} from "./file1"

class C {
  base: number;
  constructor(base:number) {
  this.base = base;
}
compare(value: number, index: number, arr: Array<number>) {
  return value >= this.base
}
}
let a = new C(2);
let b = new C(3);
arr.find(a.compare, a) // Result: 2
arr.find(a.compare, b) // Result: 3
```

**ArkTS-Sta**
```typescript
// file1.ets ArkTS-Sta
'use static'
export let arr: Array<number> = new Array<number>(1, 2, 3);

// file2.ets ArkTS-Dyn
import {arr} from "./file1"

class C {
  base: number;
  constructor(base:number) {
  this.base = base;
}
compare(value: number, index: number, arr: Array<number>) {
  return value >= this.base
}
}
let a = new C(2);
let b = new C(3);
arr.find(a.compare, a) // 运行时报错
arr.find(a.compare, b) // 运行时报错
```

## ArkTS-Sta中使用TS

### ArkTS-Sta使用TS装饰器

**规则：** `arkts-interop-ts2s-no-ts-decorator`

**规则解释：**

ArkTS-Sta不支持TS装饰器。

**变更原因：**

装饰器会动态修改类或对象的布局，ArkTS-Sta中不支持通过自定义装饰器对类、方法、属性和函数参数进行动态改变。

**适配建议：**

利用注解和反射重构。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export function MyClassDecorator(klass: Object) {}

// file2.ets
import { MyClassDecorator } from './file1';
@MyClassDecorator
class K {}
```

**ArkTS-Sta**
```typescript
NA;
```

### ArkTS-Sta访问TS独有类型的实体

**规则：** `arkts-interop-ts2s-static-access-ts-type`

**规则解释：**

ArkTS-Sta中不支持TS中独有的类型。

**变更原因：**

TS独有类型包括如下类型：
- any
- unknown
- symbol
- Function
- object literal （例如 {x: number, y: string}）
- mixing enum （例如 enum X {a = 0, b = '1'}）
- call signature （例如 {(arg: number): string}）
- constructor signature （例如 {new(): Object}）
- index signature （例如 {[index: number]: string}）
- intersection （例如 TypeA & TypeB）
- keyof （例如 interface X<T> { props: keyof T}）
- typeof（例如 let p = {x: 1, y: ''}, let q: typeof p）
- indexed access type（例如 MyArray = [{ name: "Alice", age: 15 }] type Person = typeof MyArray[number]）
- conditional types （例如 type Swap<T extends A | B> = T extends A ? B : A）
- mapped types （例如 type A<T> = {[K in keyof T]: T[K]}）
- template literal types （例如 type AB = "A" | "B", type AllLocaleIDs = `${AB}_id`）
- Pick<Type, Keys>
- Omit<Type, Keys>
- Exclude<UnionType, ExcludedMembers>
- Extract<Type, Union>
- NonNullable<Type>
- Parameters<Type>
- ConstructorParameters<Type>
- ReturnType<Type>
- InstanceType<Type>
- NoInfer<Type>
- ThisParameterType<Type>
- OmitThisParameter<Type>
- ThisType<Type>
- Uppercase<StringType>
- Lowercase<StringType>
- Capitalize<StringType>
- Uncapitalize<StringType>

ArkTS-Sta中不支持这些类型。

**适配建议：**

使用ESValue接口进行交互。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export let obj: Symbol;

// file2.ets
import { obj } from './file1';
let val = obj.prop;
obj.prop = 1;
obj.foo();
let item = obj[0];
```

**ArkTS-Sta**
```typescript
// file1.ts
export let obj: Symbol;
// 从ArkTS-Sta看来，这个声明为
// export let obj: ESValue

// file2.ets ArkTS-Sta
'use static'
import { obj } from './file1';
obj.setProperty('prop', ESValue.wrap(1));
```

### ArkTS-Dyn的Object内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-ts2s-ts-object-on-static-instance`

**规则解释：**

ArkTS-Dyn的Object内置方法作用在ArkTS-Sta对象需要重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export function foo(prx: any) {
  Object.getOwnPropertyNames(prx); // ["a"]
  Object.hasOwn(prx, 'a'); // true
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}

// file2.ets
import { foo } from './file1';
class X {
  a = 1;
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.ts
export function foo(prx: any) {
  Object.getOwnPropertyNames(prx) // []
  Object.hasOwn(prx, "a")  // false
  Object.keys(prx)  // []
  Object.values(prx)  // []
}

// file2.ets
'use static'
import {foo} from "./file1"
class X { a = 1 }
foo(ESValue.wrap(new X()))
```

### ArkTS-Dyn的Reflect内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-ts2s-ts-reflect-on-static-instance`

**规则解释：**

ArkTS-Dyn的Reflect内置方法作用在ArkTS-Sta对象需要重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export function foo(prx: any) {
  Reflect.ownKeys(prx); // ['a']
  Reflect.set(prx, 'newField', 7); // true
}

// file2.ets
import { foo } from './file1';
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.ts
export function foo(prx: any) {
  Reflect.ownKeys(prx); // []
  Reflect.set(prx, 'newField', 7); // false
}

// file2.ets
'use static'
import { foo } from './file1';
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}
foo(ESValue.wrap(new X()));
```

### ArkTS-Sta处理TS非常规异常

**规则：** `arkts-interop-ts2s-ts-exception`

**规则解释：**

ArkTS-Sta不支持直接处理TS的非常规异常。

**变更原因：**

ArkTS-Sta中throw和catch的对象只能是Error的实例，针对非常规的TS异常对象，交互时会被包装到ESError中。

**适配建议：**

通过getValue()方法获取包装了原始异常对象的ESValue实例后再进行处理。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export function foo() {
  throw 123;
}

// file2.ets
import { foo } from './file1';

try {
  foo();
} catch (e) {
  console.log("result is " + (e as number)); // 123
}
```

**ArkTS-Sta**
```typescript
// file1.ts
export function foo() {
  throw 123;
}

// file2.ets  // ArkTS-Sta
'use static'
import { foo } from './file1';

try {
  foo();
} catch (e) {
  let err: ESValue = (e as ESError).getValue();
  err.toNumber(); // 123
}
```

### ArkTS-Sta判断TS装箱类型

**规则：** `arkts-interop-ts2s-boxed-type`

**规则解释：**

ArkTS-Sta判断TS的装箱类型时会转换为对应的基本类型并使用。

**变更原因：**

在ArkTS-Sta中，语言层面不再区分基本类型和装箱类型。因此，当与JS或ArkTS-Dyn进行互操作时，ArkTS-Sta会自动拆箱，转换为对应的基本类型并使用。

**适配建议：**

避免使用装箱类型或对装箱类型进行typeof操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export let a = new Number(123);
export let b = new Boolean(true);
export let c = new String('hello');
typeof a; // 'object'
typeof b; // 'object'
typeof c; // 'object'

//file2.ets
import { a, b, c } from './file1';
typeof a; // 'object'
typeof b; // 'object'
typeof c; // 'object'
```

**ArkTS-Sta**
```typescript
// file1.ts
export let a = new Number(123);
export let b = new Boolean(true);
export let c = new String('hello');
typeof a; // 'object'
typeof b; // 'object'
typeof c; // 'object'

//file2.ets  ArkTS-Sta
'use static'
import { a, b, c } from './file1';
typeof a; // 'number'
typeof b; // 'boolean'
typeof c; // 'string'
```
### ArkTS-Sta动态导入TS

**规则：** `arkts-interop-ts2s-dynamic-import-ts`

**规则解释：**

ArkTS-Sta不支持直接动态导入TS模块和调用接口。

**变更原因：**

ArkTS-Sta没有动态import语法，使用ESValue接口动态导入动态模块。

**适配建议：**

使用ESValue接口动态导入模块和调用接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export class A {}

// file2.ets
let mod = await import('./file1');
let A: ESValue = mod.A;
let a = new A() as A;
```

**ArkTS-Sta**
```typescript
// file1.ets ts
export class A {}

// file2.ets   ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let A: ESValue = mod.getProperty('A');
let a = A.instantiate() as A;
```

### ArkTS-Sta创建TS的类的对象字面量

**规则：** `arkts-interop-ts2s-object-literal`

**规则解释：**

ArkTS-Sta创建TS的类的对象字面量时，不支持使用instanceof判断字面量类型。

**变更原因：**

由于ArkTS-Sta的语义变更，在创建TS的类的对象字面量时，不支持使用instanceof判断字面量类型。

**适配建议：**

不要使用instanceof判断字面量类型。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.ts
export class A {
  name: string = '';
}

// file2.ets
import { A } from './file1';
let a: A = { name: 'hello' };

a instanceof A; // false
```

**ArkTS-Sta**
```typescript
// file1.ts
export class A {
  name: string = '';
}

// file2.ets ArkTS-Sta
'use static'
import { A } from './file1';
let a: A = { name: 'hello' };

a instanceof A; // true
```

## ArkTS-Sta中使用JS

### ArkTS-Sta导入JS文件

**规则：** `arkts-interop-js2s-import-js`

**规则解释：**

ArkTS-Sta不支持直接导入JS文件。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口导入JS模块和调用接口。


**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo() {}

// file2.ets
import { foo } from './file1';
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo() {}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
```

### ArkTS-Sta导出JS实体

**规则：** `arkts-interop-js2s-export-js`

**规则解释：**

ArkTS-Sta不能以`export {A} from "./file1"`的形式直接在ets文件中导出JS对象。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口导入JS模块和调用接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo() {}
export class A {}

// file2.ets
import { foo } from './file1';
export { foo };

export { A } from './file1';

// 函数、类、变量、枚举
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo() {}
export class A {}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let A = mod.getProperty('A');

export { foo, A };
```

### ArkTS-Sta调用JS函数和传参

**规则：** `arkts-interop-js2s-call-js-func`

**规则解释：**

ArkTS-Sta中不能直接调用JS函数和传参。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口调用，接口接收参数为ESValue类型，传参时需要用wrap接口构造ESValue实例再传参。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo() {}
export function bar(a) {}

// file2.ets
import { foo, bar } from './file1';
foo();
bar(123);
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo() {}
export function bar(a) {}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let bar = mod.getProperty('bar');
foo.invoke();
bar.invoke(ESValue.wrap(123));
```

### ArkTS-Sta实例化JS对象

**规则：** `arkts-interop-js2s-create-js-instance`

**规则解释：**

ArkTS-Sta不能直接实例化JS对象。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口实例化，接口接收参数为ESValue类型，传参时需要用wrap接口构造ESValue实例再传参。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
class foo {
  constructor(a) {}
}
// file2.ets
import { foo } from './file1';
new foo(123);
```

**ArkTS-Sta**
```typescript
// file1.js
class foo {
  constructor(a) {}
}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
foo.instantiate(ESValue.wrap(123));
```

### ArkTS-Sta访问JS属性

**规则：** `arkts-interop-js2s-access-js-prop`

**规则解释：**

ArkTS-Sta不能直接访问JS属性。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口访问属性，接口接收参数为ESValue类型，传参时需要用wrap接口构造ESValue实例再传参。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { name: '123' };
// file2.ets
import { foo } from './file1';
foo.name;
foo.name = '456';
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = {name: "123"}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1')
let foo = mod.getProperty('foo')
foo.getProperty('name')
foo.setProperty('name', ESValue.wrap("456")）
```

### ArkTS-Sta调用js方法和传参

**规则：** `arkts-interop-js2s-call-js-method`

**规则解释：**

ArkTS-Sta不能直接调用JS方法和传参。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口调用方法，接口接收参数为ESValue类型，传参时需要用wrap接口构造ESValue实例再传参。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
class Foo {
  bar(a) {}
}
export let foo = new Foo();
// file2.ets
import { foo } from './file1';
foo.bar(123);
```

**ArkTS-Sta**
```typescript
// file1.js
class Foo {
  bar(a) {}
}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
foo.invokeMethod('bar', ESValue.wrap(123));
```

### ArkTS-Sta访问JS索引

**规则：** `arkts-interop-js2s-access-js-index`

**规则解释：**

ArkTS-Sta不支持直接访问JS索引。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue接口访问索引，接口接收参数为ESValue类型，传参时需要用wrap接口构造ESValue实例再传参。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { arr: [1, 2, 3] };
// file2.ets
import { foo } from './file1';
let arr = foo.arr;
arr[1];
arr[3] = 4;
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = [1, 2, 3];

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let arr = foo.getProperty('arr');
arr.getProperty(1);
arr.setProperty(3, ESValue.wrap(4));
```

### ArkTS-Sta转换JS对象类型

**规则：** `arkts-interop-js2s-convert-js-type`

**规则解释：**

ArkTS-Sta不支持直接转换JS对象类型。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口转换类型。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo1 = { num: 123 };
export let foo2 = { bool: true };
export let foo3 = { str: '123' };
export let foo4 = { big: 123n };

// file2.ets
import { foo } from './file1';
let a: number = foo1.num as number;
let b: boolean = foo2.bool as boolean;
let c: string = foo3.str as string;
let d: bigint = foo4.big as bigint;
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo1 = { num: 123 };
export let foo2 = { bool: true };
export let foo3 = { str: '123' };
export let foo4 = { big: 123n };

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo1 = mod.getProperty('foo1');
let num = foo1.getProperty('num');
let a1: number = num.toNumber();

let foo2 = mod.getProperty('foo2');
let bool = foo2.getProperty('bool');
let a2: boolean = bool.toBoolean();

let foo3 = mod.getProperty('foo3');
let str = foo3.getProperty('str');
let a3: string = str.toString();

let foo4 = mod.getProperty('foo4');
let big = foo4.getProperty('big');
let a4: bigint = big.toBigInt();
```

### ArkTS-Sta获取JS对象类型

**规则：** `arkts-interop-js2s-typeof-js-type`

**规则解释：**

ArkTS-Sta不支持直接获取JS对象类型。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口获取类型。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { num: 123 };

// file2.ets
import { foo } from './file1';
typeof foo.num; // 'number'
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = 123;

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let num = foo.getProperty('num');

num.typeOf(); // 'number'
```

### ArkTS-Sta判断JS对象类型

**规则：** `arkts-interop-js2s-instanceof-js-type`

**规则解释：**

ArkTS-Sta不能直接判断JS对象类型。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口判断类型。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export class Foo {}
export let foo = new Foo();

// file2.ets
import { Foo, foo } from './file1';
foo instanceof Foo;
```

**ArkTS-Sta**
```typescript
// file1.js
export class Foo {}
export let foo = new Foo();

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let Foo = mod.getProperty('Foo');
let foo = mod.getProperty('foo');

foo.isInstanceOf(Foo);
```

### ArkTS-Sta对JS对象自增自减

**规则：** `arkts-interop-js2s-self-addtion-reduction`

**规则解释：**

ArkTS-Sta不支持直接对JS对象自增自减。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口转换为数字后再操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { num: 0 };

// file2.ets
import { foo } from './file1';
let a: number = 0;
a = foo.num++;
a = ++foo.num;
a = foo.num--;
a = --foo.num;
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = { num: 0 };

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let a: number = 0;

// a = foo.num++
let num = foo.getProperty('num');
let tmp: number = num.toNumber();
a = tmp;
foo.setProperty('num', ESValue(tmp + 1));

// a = ++foo.num

num = foo.getProperty('num');
tmp = num.toNumber() + 1;
foo.setProperty('num', ESValue(tmp));
a = tmp;

// the cases "foo.num--" and "--foo.num" are similar
```

### ArkTS-Sta对JS对象进行一元运算

**规则：** `arkts-interop-js2s-unary-op`

**规则解释：**

ArkTS-Sta不支持直接对JS对象进行一元运算。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口转换为数字后再操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { num: 0 };
// file2.ets
import { foo } from './file1';
+foo.num;
-foo.num;
!foo.num;
~foo.num;
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = { num: 0 };

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let num = foo.getProperty('num');
// +foo.num
+num.toNumber();
// -foo.num
-num.toNumber();
// !foo.num
!num.toNumber();
// ~foo.num
~num.toNumber();
```

### ArkTS-Sta对JS对象进行二元运算

**规则：** `arkts-interop-js2s-binary-op`

**规则解释：**

ArkTS-Sta不支持直接对JS对象进行二元运算。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口转换为数字后再操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { a: 1, b: 2 };

// file2.ets
import { foo } from './file1';
let a = foo.a;
let b = foo.b;
a + b;
a - b;
a * b;
a / b;
a % b;
a ** b;
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = { a: 1, b: 2 };

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let a = foo.getProperty('a').toNumber();
let b = foo.getProperty('b').toNumber();
a + b;
a - b;
a * b;
a / b;
a % b;
a ** b;
```

### ArkTS-Sta await JS Promise对象

**规则：** `arkts-interop-js2s-await-js-promise`

**规则解释：**

ArkTS-Sta 不支持直接await JS中的Promise对象。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue接口转换为Promise对象后再await。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
async function foo(){}
export let p = foo()

// file2.ets
import {p} from "./file1"
async function bar() {
  await p.toPromise();
}
```

**ArkTS-Sta**
```typescript
// file1.js
async function foo(){}
export let p = foo()

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1')
let p = mod.getProperty('p')

async function bar() {
  await p.toPromise();
}
```

### ArkTS-Sta对JS数据进行比较

**规则：** `arkts-interop-js2s-compare-js-data`

**规则解释：**

ArkTS-Sta不能直接对JS数据进行比较。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue接口转换为数字再操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { a: 1, b: 2 };

// file2.ets
import { foo } from './file1';
let a = foo.a;
let b = foo.b;
a > b;
a < b;
a >= b;
a <= b;
```

**ArkTS-Sta**
```typescript
// file1.js
export let a = 1;
export let b = 2;

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let a = foo.getProperty('a').toNumber();
let b = foo.getProperty('b').toNumber();

a > b;
a < b;
a >= b;
a <= b;
```

### ArkTS-Sta对JS数据进行相等判断

**规则：** `arkts-interop-js2s-equality-judgment`

**规则解释：**

ArkTS-Sta不支持直接对JS数据进行相等判断。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口进行判断。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
class A {}
export let a = new A();
export let b = new A();

// file2.ets
import { a, b } from './file1';
a == b;
a != b;
a === b;
a !== b;
```

**ArkTS-Sta**
```typescript
// file1.js
class A {}
export let a = new A();
export let b = new A();

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let a = mod.getProperty('a');
let b = mod.getProperty('b');

a.isEqualTo(b);
!a.isEqualTo(b);
a.isStrictlyEqualTo(b);
!a.isStrictlyEqualTo(b);
```

### ArkTS-Sta对JS对象进行条件判断

**规则：** `arkts-interop-js2s-condition-judgment`

**规则解释：**

ArkTS-Sta不支持直接对JS对象进行条件判断。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口转换为boolean类型后再判断。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { isGood: true };

// file2.ets
import { foo } from './file1';

if (foo.isGood) {}
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = { isGood: true };

// file2.ets
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');

let isGood = foo.getProperty('isGood').toBoolean();
if (isGood) {}
```

### ArkTS-Sta继承JS的类

**规则：** `arkts-interop-js2s-inherit-js-class`

**规则解释：**

ArkTS-Sta不能直接继承JS的类。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue的接口构造JS类并传递JS父类。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export class A {}

// file2.ets
import { A } from './file1';
class B extends A {}
let b = new B();
```

**ArkTS-Sta**
```typescript
// file1.js
export class A {}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let A = mod.getProperty('A');
let fixArr: FixedArray<ESValue> = [];
let esvalueCB = (argThis: ESValue, argNewTgt: ESValue, args: FixedArray<ESValue>, data?: ESValueCallbackData) => {
  return ESValue.Undefined;
};
let B: ESValue = ESValue.defineClass('B', esvalueCB, undefined, undefined, A);
let b = B.instantiate();
```

### ArkTS-Sta处理JS非常规异常

**规则：** `arkts-interop-js2s-js-exception`

**规则解释：**

ArkTS-Sta不支持直接处理JS的非常规异常。

**变更原因：**

ArkTS-Sta中throw和catch的对象只能是Error的实例，针对非常规的JS异常对象，交互时会被包装到ESError中。

**适配建议：**

通过getValue()方法获取包装了原始异常对象的ESValue实例后再进行处理。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo() {
  throw 123;
}

// file2.ets
import { foo } from './file1';

try {
  foo();
} catch (e) {
  console.log("result is " + (e as number)); //123
}
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo() {
  throw 123;
}

// file2.ets
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');

try {
  foo.invoke();
} catch (e) {
  let err: ESValue = (e as ESError).getValue();
  err.toNumber(); // 123
}
```

### ArkTS-Sta访问JS的装箱类型

**规则：** `arkts-interop-js2s-boxed-type`

**规则解释：**

ArkTS-Sta访问JS的装箱类型时会转换为对应的基本类型并使用。

**变更原因：**

在ArkTS-Sta中，语言层面不再区分基本类型和装箱类型。因此，当与JS或ArkTS-Dyn进行互操作时，ArkTS-Sta会自动拆箱，转换为对应的基本类型并使用。

**适配建议：**

避免使用装箱类型或对装箱类型进行typeof操作。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = {
  num: new Number(123),
  bool: new Boolean(true),
  str: new String('hello'),
};

// file2.ets
import { foo } from './file1';
typeof foo.num; // 'object'
typeof foo.bool; // 'object'
typeof foo.str; // 'object'
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = {
  num: new Number(123),
  bool: new Boolean(true),
  str: new String('hello'),
};

// file2.ets
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');

foo.getProperty('num').typeOf(); // 'number'
foo.getProperty('bool').typeOf(); // 'boolean'
foo.getProperty('str').typeOf(); // 'string'
```

### ArkTS-Sta遍历JS对象

**规则：** `arkts-interop-js2s-traverse-js-instance`

**规则解释：**

ArkTS-Sta遍历JS对象时，不能直接访问索引和属性。

**变更原因：**

ArkTS-Sta中只能和有类型声明的文件进行交互。
ArkTS-Sta中限制ESValue的动态行为，形成动静态更清晰的界限，减少开发者滥用ESValue导致性能劣化的场景。

**适配建议：**

使用ESValue接口访问索引和属性。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export let foo = { arr: [1, 2, 3] };
// file2.ets
import { foo } from './file1';
let arr = foo.arr;
let len = arr.length as number;
for (let i = 0; i < len; ++i) {
  arr[i] as number;
  arr[i] = 0;
}
```

**ArkTS-Sta**
```typescript
// file1.js
export let foo = { arr: [1, 2, 3] };

// file2.ets  ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
let arr = foo.getProerpty('arr');
let len = arr.getProerpty('length').toNumber();
for (let i = 0; i < len; ++i) {
  arr.getProperty(i).toNumber();
  arr.setProperty(i, ESValue.wrap(0));
}
```

### JS调用ArkTS-Sta函数和传参

**规则：** `arkts-interop-js2s-js-call-static-func`

**规则解释：**

JS不能直接调用ArkTS-Sta函数和传参。

**变更原因：**

ArkTS-Sta的函数运行时会检查参数类型，需要确保参数类型匹配。

**适配建议：**

传参时确保匹配参数生命的类型。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function handle(cb) {
  let p = { name: 'hello' };
  cb(p);
}

// file2.ets
import { handle } from './file1';
interface Person {
  name: string;
}

function foo(p: Person) {}
let lambda = (p: Person) => {};

handle(foo);
handle(lambda);
```

**ArkTS-Sta**
```typescript
// file1.js
export function handle(cb) {
  let p = { name: 'hello' };
  cb(p);
}

// file2.ets
'use static'
let mod = ESValue.load('./file1');
let handle = mod.getProperty('handle');
interface Person {
  name: string;
}
function foo(p: Person) {}
// solution: function foo(p: ESValue) {}
let lambda = (p: Person) => {};
// solution: let lambda = (p: ESValue) => {}

handle.invoke(ESValue.wrap(foo));
handle.invoke(ESValue.wrap(lambda));
```

### JS增删改ArkTS-Sta对象属性

**规则：** `arkts-interop-js2s-js-add-delete-static-prop`

**规则解释：**

JS增删改ArkTS-Sta对象属性时避免动态修改对象布局。

**变更原因：**

ArkTS-Sta的对象布局在编译时就已经确定，不能动态修改。

**适配建议：**

避免动态修改对象布局，需要新增的属性提前在类型中声明，需要删除的属性使用undefined置空。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo(obj) {
  obj.newField = 1; // 增加属性
  delete obj.data; // 删除属性
  obj.name = '123'; // 修改属性值（同类型）
  obj.name = { firstName: '456' }; // 修改属性值（不同类型）
}

// file2.ets
import { foo } from './file1';
class X {
  name: string = '';
  data: number = 0;
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo(obj) {
  obj.newField = 1; // 增加属性   运行时报错
  delete obj.data; // 删除属性   运行时报错
  obj.name = '123'; // 修改属性值（同类型）OK
  obj.name = { firstName: '456' }; // 修改属性值（不同类型）运行时报错
}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
class X {
  name: string = '';
  data: number = 0;
}
foo.invoke(ESValue.wrap(new X()));
```

### JS的Object内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-js2s-js-object-on-static-instance`

**规则解释：**

JS的Object内置方法作用在ArkTS-Sta对象时，需重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo(prx) {
  Object.getOwnPropertyNames(prx); // ["a"]
  Object.hasOwn(prx, 'a'); // true
  Object.keys(prx); // ["a"]
  Object.values(prx); // [1]
}

// file2.ets
import { foo } from './file1';
class X {
  a = 1;
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo(prx) {
  Object.getOwnPropertyNames(prx) // []
  Object.hasOwn(prx, "a")  // false
  Object.keys(prx)  // []
  Object.values(prx)  // []
}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1')
let foo = mod.getProperty('foo')
class X { a = 1 }
foo.invoke(ESValue.wrap(new X()))
```

### JS的Reflect内置方法作用在ArkTS-Sta对象

**规则：** `arkts-interop-js2s-js-reflect-on-static-instance`

**规则解释：**

JS的Reflect内置方法作用在ArkTS-Sta对象时，需重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，表现为密封状态（sealed），不能修改对象布局。

**适配建议：**

根据变化重新适配代码，或者避免使用这些内置底层接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo(prx) {
  Reflect.ownKeys(prx); // ['a']
  Reflect.set(prx, 'newField', 7); // true
}

// file2.ets
import { foo } from './file1';
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}
foo(new X());
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo(prx) {
  Reflect.ownKeys(prx); // []
  Reflect.set(prx, 'newField', 7); // false
}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1');
let foo = mod.getProperty('foo');
class X {
  a: string = 'hello';
  getName() {
    return this.a;
  }
}
foo.invoke(ESValue.wrap(new X()));
```

### JS对ArkTS-Sta对象进行展开语法

**规则：** `arkts-interop-js2s-js-expand-static-instance`

**规则解释：**

JS对ArkTS-Sta对象进行展开语法时，需重新适配代码。

**变更原因：**

ArkTS-Sta对象在动态上下文中没有自有属性，相关解构操作会失效。

**适配建议：**

根据变化重新适配代码，或者避免使用解构语法。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export function foo(obj) {
let x = {...obj} // x会是{ a = 1; b = 2; c = 3 }
let {a, b, ...rest} = obj  // a会是1, b会是2, rest会是{c: 3}

// file2.ets
import {foo} from "./file1"
class X { a = 1; b = 2; c = 3 }
foo(new X())

// class interface Record
```

**ArkTS-Sta**
```typescript
// file1.js
export function foo(obj) {
let x = {...obj} // x会是空对象{}，因为静态对象没有自有属性
// 解决方案：let x = {a: obj.a, b: obj.b, c: obj.c}
// 或者使用keys + Reflect.get
let {a, b, ...rest} = obj  // a会是1，b会是2，rest会是空对象{}，因为静态对象没有自有属性
// 解决方案: let rest = {c: obj.c}

// file2.ets  // ArkTS-Sta
'use static'
let mod = ESValue.load('./file1')
let foo = mod.getProperty('foo')
class X { a = 1; b = 2; c = 3 }
foo.invoke(ESValue.wrap(new X()))
```

### ArkTS-Sta动态导入JS

**规则：** `arkts-interop-js2s-dynamic-import-js`

**规则解释：**

ArkTS-Sta不支持直接动态导入JS模块和调用接口。

**变更原因：**

ArkTS-Sta没有动态import语法，使用ESValue接口动态导入动态模块。

**适配建议：**

使用ESValue接口动态导入模块和调用接口。

**示例：**

**ArkTS-Dyn**
```typescript
// file1.js
export class A {}

// file2.ets ArkTS-Dyn
let mod: ESObject = await import('./file1')
let A: ESObject = mod.A
new A()
```

**ArkTS-Sta**
```typescript
// file1.js
export class A {}

// file2.ets ArkTS-Sta
'use static'
let mod: ESValue = ESValue.load('./file1')
let A: ESValue = mod.getProperty('A')
A.instantiate()
```

