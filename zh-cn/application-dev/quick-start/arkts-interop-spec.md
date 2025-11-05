# ArkTS-Sta互操作特性规范

## ArkTS-Sta互操作场景

### ArkTS-Dyn中使用ArkTS-Sta

#### 文件导入

在ArkTS-Sta中使用`import`函数导入ArkTS-Dyn的文件相关的内容，包含函数，类，对象等。

```typescript
// file1.ets ArkTS-Sta
'use static'
export function func(){}
export class A{}
export const a: A = new A();

// file2.ets ArkTS-Dyn
import { func, A, a} from './file1'
```

#### 类实例化

在ArkTS-Dyn中可以使用从ArkTS-Sta中导入的类，用new来创建该类的实例。

```typescript
// file1.ets ArkTS-Sta
'use static'
export class A {}
export class B extends A {}
interface interA {}
export class C implements interA {}

// file2.ets ArkTS-Dyn
import { A, B, C } from "file1";
let a = new A();
let b = new B();
let c = new C();
```

#### 属性读写

在ArkTS-Dyn中可以读写ArkTS-Sta中导入的对象的属性。

```typescript
// file1.ets ArkTS-Sta
'use static'
export class Person {
  name: string = "unknown"
}

// file2.ets ArkTS-Dyn
import { Person } from "file1";
let a = new Person();
let b = a.name; // "unknown"
a.name = "John";
```

#### 函数调用

在ArkTS-Dyn中可以直接调用ArkTS-Sta中导入的函数。

```typescript
// file1.ets ArkTS-Sta
'use static'
export function foo1() {}
export function foo2(a: number, b: number): number {
  return a + b;
}

// file2.ets ArkTS-Dyn
import { foo1, foo2 } from "file1";
foo1();
foo2(1.5, 2.5);
```

#### 对象方法调用

在ArkTS-Sta中可以直接访问ArkTS-Dyn导入对象的方法。

```typescript
// file1.ets ArkTS-Sta
'use static'
export class A {
  log() {
    console.log("123")
  }
}
class B {
  foo() : void {}
}
export class C extends B {
  override foo() : void { console.log('D.foo') }
}

// file2.ets ArkTS-Dyn
import { A, C } from 'file1'
let a = new A()
a.log()
let c = new C()
c.foo()  // Output: D.foo
```

#### 参数传递

在ArkTS-Dyn中可以将ArkTS-Dyn的参数传至导入的函数，从而回传至ArkTS-Sta。

```typescript
// file1.ets ArkTS-Sta
'use static'
export function foo(a: string) {
  console.log(a);
}
export class C {
  static foo(a: string) {
    console.log(a);
  }
  bar(a: string) {
    console.log(a);
  }
}
export interface Iface {
  foo(a: string): void;
}

// file2.ets ArkTS-Dyn
import { foo, C, Iface } from "file1";

foo("Hi"); // Output: Hi
C.foo("Hi"); // Output: Hi
new C().bar("Hi"); // Output: Hi

function baz(i: Iface) {
  i.foo("Hi"); // OK
}
```

### ArkTS-Sta中使用TS

#### 文件导入

在ArkTS-Sta中使用`import`函数导入ArkTS-Dyn的文件相关的内容，包含函数，类，对象等。

```typescript
// file1.ts
export function func(){}
export class A{}
export const a: A = new A();

// file2.ets ArkTS-Sta
'use static'
import { func, A, a} from './file1'
```

#### 类实例化

在ArkTS-Dyn中可以使用从ArkTS-Sta中导入的类，用new来创建该类的实例。可以访问实例的方法和属性。也可以使用ArkTS-Dyn的类扩展ArkTS-Sta的类后创建实例对象。

```typescript
// file1.ts
export class A {}
export class B extends A {}
interface interA {}
export class C implements interA {}

// file2.ets ArkTS-Sta
'use static'
import { A, B, C } from "file1";
let a = new A();
let b = new B();
let c = new C();
```

#### 属性读写

在ArkTS-Sta中可以读写从TS中导入对象。

```typescript
// file1.ts
export class Person {
  name: string = "unknown"
}

// file2.ets ArkTS-Sta
'use static'
import { Person } from "file1";
let a = new Person();
let b = a.name; // "unknown"
a.name = "John";
```

#### 函数调用

在ArkTS-Sta中可以调用从TS中导入函数。

```typescript
// file1.ts
export function foo1() {}
export function foo2(a: number, b: number): number {
  return a + b;
}

// file2.ets ArkTS-Sta
'use static'
import { foo1, foo2 } from "file1";
foo1();
foo2(1.5, 2.5);
```

#### 对象方法调用

在ArkTS-Sta中可以调用从TS中导入的对象，并调用该对象的方法。

```typescript
// file1.ts
export class A {
  log() {
    console.log("123")
  }
}
class B {
  foo() : void {}
}
export class C extends B {
  override foo() : void { console.log('D.foo') }
}

// file2.ets ArkTS-Sta
'use static'
import { A, C } from 'file1'
let a = new A()
a.log()
let c = new C()
c.foo()  // Output: D.foo
```

#### 参数传递

在ArkTS-Sta中可以调用从TS中导入的函数，并将参数传递至TS。

```typescript
// file1.ts
export function foo(a: string) {
  console.log(a);
}
export class C {
  static foo(a: string) {
    console.log(a);
  }
  bar(a: string) {
    console.log(a);
  }
}
export interface Iface {
  foo(a: string): void;
}

// file2.ets ArkTS-Sta
'use static'
import { foo, C, Iface } from "file1";

foo("Hi"); // Output: Hi
C.foo("Hi"); // Output: Hi
new C().bar("Hi"); // Output: Hi

function baz(i: Iface) {
  i.foo("Hi"); // OK
}
```

### ArkTS-Sta中使用JS

#### 文件导入

```typescript
// file1.js
export function func(){}
export class A{}
export const a: A = new A();

// file2.ets ArkTS-Sta
'use static'
let mod: ESValue = ESValue.load('./file1')
let func: ESValue = mod.getProperty('func')
let A: ESValue = mod.getProperty('A')
let a: ESValue = mod.getProperty('a')
```

#### 类实例化

可以在ArkTS-Sta中创建新的JS类，通过ESValue创建JS类的实例。

```typescript
// file1.js
export class A {}

// file2.ets ArkTS-Sta
'use static'
let mod: ESValue = ESValue.load("./file1");
let A: ESValue = module.getProperty("A");
let a: ESValue = A.instantiate();  // 创建A的实例，这个实例被包装在a中
```

#### 属性读写

在ArkTS-Sta中可以访问JS类实例的字段和方法。

```typescript
// file1.js
export class A {
  name = "unknown"
}

// file2.ets ArkTS-Sta
'use static'
let module = ESValue.load('./file1')
let A = module.getProperty('A');
let a = A.instantiate()
b.getProperty('name').toString()  // "unknown"
a.setProperty('name', ESValue.wrap('John'))
b.getProperty('name').toString()  // "John"
```

#### 函数调用

在ArkTS-Sta中可以通过ESValue来调用JS的函数。

```typescript
// file1.js
export function foo() {
    return 100
}

// file2.ets ArkTS-Sta
'use static'
let foo: ESValue = ESValue.load("./file1").getProperty("foo");
let res: ESValue = foo.invoke();
let resNum: string = res.toNumber();  // 100
```

#### 对象方法调用

在ArkTS-Sta中可以通过ESValue来调用JS的对象的方法。

```typescript
//file1.js
export class A {
  sayHi(msg: string) {
    console.log(msg)
    return msg
  }
  static getInstance() {
    return new A()
  }
}

//file2.ets  ArkTS-Sta
'use static'
let A = ESValue.load('./file1').getProperty('A')
let a: ESValue = A.invokeMethod('getInstance')  // 调用静态方法
let msg: ESValue = a.invokeMethod('sayHi', ESValue.wrap('hello'))  // 调用实例方法, 打印hello
msg.toString()  // 'hello'
```

#### 参数传递

在ArkTS-Sta中可以通过ESValue来调用JS的函数将参数传递至JS。

```typescript
// file1.js
export function foo(msg, count) {
  for (let i = 0; i < count; ++i) {
    console.log(msg)
  }
}

// file2.ets ArkTS-Sta
'use static'
let foo = ESValue.load("./file1").getProperty("foo");
foo.invoke(ESValue.wrap("hello"), ESValue.wrap(3));  // 打印3次hello
```
