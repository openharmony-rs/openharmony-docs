# ArkTS-Sta互操作场景

## ArkTS-Sta中使用ArkTS-Dyn或TS

### 文件导入

在ArkTS-Sta中使用`import`函数导入ArkTS-Dyn模块的对象。

```typescript
// file1.ets ArkTS-Dyn
export function foo() {}
export class A {
  field: number = 0;
  test() {}
}
```

```typescript
// file2.ets ArkTS-Sta
'use static'
import { foo, A } from "./file1";
```

### 类实例化

在ArkTS-Sta中使用从ArkTS-Dyn中导入的类，并用new来创建该类的实例。

```typescript
// file1.ets ArkTS-Dyn
export class A {
  id: number = 0;
  constructor(arg: number) {
    this.id = arg;
  }
}
export class B extends A {
  name: string = "";
  constructor(arg0: number, arg1: string) {
    super(arg0);
    this.name = arg1;
  }
}
export interface Inface {
  x: number;
  y: number;
  normSquare(): number;
}
export class C implements Inface {
  x: number = 0;
  y: number = 0;
  normSquare(): number {
    return this.x * this.x + this.y * this.y;
  }
}
```

```typescript
// file2.ets ArkTS-Sta
'use static'
import { A, B, C } from "./file1";
let a = new A(123);
let b = new B(456, "Bob");
let c = new C();
```

### 属性读写

在ArkTS-Sta中读写ArkTS-Dyn对象的属性。

```typescript
// file1.ets ArkTS-Dyn
export class Person {
  public id: number = 0;
  private name_: string = "";
  constructor(name: string) {
    this.name_ = name;
  }
  get name(): string {
    return this.name_;
  }
  set name(name: string) {
    this.name_ = name;
  }
}
```

```typescript
// file2.ets ArkTS-Sta
'use static'
import { Person } from "./file1";
let p = new Person("John");
console.log(p.name); // Output: John
p.name = "Alice";
console.log(p.name); // Output: Alice
p.id = 123456;
console.log(p.id); // Output: 123456
```

### 函数调用

在ArkTS-Sta中直接调用从ArkTS-Dyn导入的函数。

```typescript
// file1.ets ArkTS-Dyn
export function myAdd(a: number, b: number): number {
  let ret = a + b;
  console.log("result is " + ret);
  return ret;
}
```

```typescript
// file2.ets ArkTS-Sta
'use static'
import { myAdd } from "file1";
myAdd(3, 4); // Output: 7
```

### 对象方法调用

在ArkTS-Sta中直接调用ArkTS-Dyn导入对象的方法。

```typescript
// file1.ets ArkTS-Dyn
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
```

```typescript
// file2.ets ArkTS-Sta
'use static'
import { A, C, itA, arr } from "file1";
let a = new A();
a.log();
let c = new C();
c.foo(); // Output: D.foo
```

### 参数传递

可以将ArkTS-Sta的对象直接作为参数传入到`import`来的ArkTS-Dyn函数。

```typescript
// file1.ets ArkTS-Dyn
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
