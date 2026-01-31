# ArkTS-Sta互操作类型映射规则

## 编译类型检查原则

- 编译类型检查将会根据源码文件的种类来进行：
  - ArkTS-Sta的文件按照ArkTS-Sta的类型检查规则
  - ArkTS-Dyn的文件按照ArkTS-Dyn的类型检查规则
  - 针对源码中的交互部分，编译器会使用特定的类型映射规则将交互部分的类型映射到所在文件的类型后，再进行编译检查。

## 类型映射基本原则

- 基本类型映射为基本类型（比如`number <-> number`）。
- 组合类型映射为组合类型（比如`class <-> class`）。

## 类型映射详细规则

ArkTS-Sta采用递归的方式定义类型映射，例如以下的类型映射。

| **T**           | **f(T)**              |
| --------------- | --------------------- |
| `number/Number` | `number`              |
| `function func(arg: A): R` | `function func(arg: f(A)): f(R)` |

这表示：
1. 第一行表示`Number`和`number`都被映射到`number`。
2. 第二行中，函数类型 `function func(arg: A): R` 会被映射为其参数类型为 `f(A)`、返回值类型为 `f(R)` 的函数类型，即 `function func(arg: f(A)): f(R)`；例如 `function func(arg: number): Number` 会被映射为 `function func(arg: f(number)): f(Number)`，即 `function func(arg: number): number`。

### ArkTS-Sta类型映射到ArkTS-Dyn类型

**基本类型**

| **ArkTS-Sta type (T)**      | **ArkTS-Dyn type (f(T))**   |
| --------------------- | --------------------- |
| `number/Number`       | `number`              |
| `double/Double`       | `number`              |
| `string/String`       | `string`              |
| `boolean/Boolean`     | `boolean`             |
| `bigint/BigInt`       | `bigint`              |
| `null`                | `null`                |
| `undefined`           | `undefined`           |
| `void`                | `void`                |
| `Any`                 | `ESObject`            |

**函数**

| **类别**               | **ArkTS-Sta type (T)**                               | **ArkTS-Dyn type (f(T))**                                            |
| ---------------------- | ---------------------------------------------- | -------------------------------------------------------------  |
| 普通函数               | `function foo(arg1: K1, arg2: K2): R`          | `function foo(arg1: f(K1), arg2: f(K2)): f(R)`                 |

**类**

| **类别** | **ArkTS-Sta type (T)** | **ArkTS-Dyn type (f(T))** |
| :--- | :--- | :--- |
| 普通类 | `class A {`<br>&nbsp;&nbsp;`field: F1;`<br>&nbsp;&nbsp;`m(arg: U1): M1;`<br>&nbsp;&nbsp;`static sf: F2;`<br>&nbsp;&nbsp;`static sm(arg: U2): M2;`<br>&nbsp;&nbsp;`get a(): V;`<br>&nbsp;&nbsp;`set a(v: V): void;`<br>`}` | `class A {`<br>&nbsp;&nbsp;`get field(): f(F1);`<br>&nbsp;&nbsp;`set field(arg: f(F1)): void;`<br>&nbsp;&nbsp;`m(arg: f(U1)): f(M1);`<br>&nbsp;&nbsp;`static sf: f(F2);`<br>&nbsp;&nbsp;`static sm(arg: f(U2)): f(M2);`<br>&nbsp;&nbsp;`get a(): f(V);`<br>&nbsp;&nbsp;`set a(v: f(V)): void;`<br>`}` |
| public/private | `class A {`<br>&nbsp;&nbsp;`public field: F1;`<br>&nbsp;&nbsp;`private m(arg: U1): M1;`<br>`}` | `class A {`<br>&nbsp;&nbsp;`public field: f(F1);`<br>&nbsp;&nbsp;`private m(arg: f(U1)): f(M1);`<br>`}` |
| 继承类和override | `class C extends A {`<br>&nbsp;&nbsp;`override foo(arg: U1): M1;`<br>`}` | `class C extends A {`<br>&nbsp;&nbsp;`override foo(arg: f(U1)): f(M1);`<br>`}` |
| 实现类 | `class A implements Inface {`<br>&nbsp;&nbsp;`// ...`<br>`}` | `class A implements Inface {`<br>&nbsp;&nbsp;`// ...`<br>`}` |
**接口**

| **类别** | **ArkTS-Sta type (T)** | **ArkTS-Dyn type (f(T))** |
|----------|------------------------|----------------------------|
| 普通接口 | `interface A {`<br>&nbsp;&nbsp;`field: F1`<br>&nbsp;&nbsp;`m(arg: U1): M1`<br>&nbsp;&nbsp;`get a(): V`<br>&nbsp;&nbsp;`set a(v: V): void`<br>`}` | `class A {`<br>&nbsp;&nbsp;`field: f(F1)`<br>&nbsp;&nbsp;`m(arg: f(U1)): f(M1)`<br>&nbsp;&nbsp;`get a(): f(V)`<br>&nbsp;&nbsp;`set a(v: f(V)): void`<br>`}` |
| 继承接口 | `interface A extends B {`<br>&nbsp;&nbsp;`// ...`<br>`}` | `interface A extends B {`<br>&nbsp;&nbsp;`// ...`<br>`}` |


### ArkTS-Dyn类型映射到ArkTS-Sta类型

**基本类型**

| **ArkTS-Dyn type (T)**      | **ArkTS-Sta type (f(T))**   |
| --------------------- | --------------------- |
| `number/Number`       | `number`              |
| `string/String`       | `string`              |
| `boolean/Boolean`     | `boolean`             |
| `bigint/BigInt`       | `bigint`              |
| `null`                | `null`                |
| `undefined`           | `undefined`           |
| `void`                | `void`                |
| `ESObject`            | `Any`                 |

**函数**

| **类别**   | **ArkTS-Dyn type (T)**                               | **ArkTS-Sta type (f(T))**                                     |
| ---------- | ---------------------------------------------- | ------------------------------------------------------- |
| 普通函数   | `function foo(arg1: K1, arg2: K2): R`          | `function foo(arg1: f(K1), arg2: f(K2)): f(R)`          |

**类**

| **类别** | **ArkTS-Dyn type (T)** | **ArkTS-Sta type (f(T))** |
| :--- | :--- | :--- |
| 普通类 | `class A {`<br>&nbsp;&nbsp;`field: F1`<br>&nbsp;&nbsp;`m(arg: U1): M1`<br>&nbsp;&nbsp;`static sf: F2`<br>&nbsp;&nbsp;`static sm(arg: U2): M2`<br>&nbsp;&nbsp;`get a(): V`<br>&nbsp;&nbsp;`set a(v: V): void`<br>`}` | `class A {`<br>&nbsp;&nbsp;`field: f(F1)`<br>&nbsp;&nbsp;`m(arg: f(U1)): f(M1)`<br>&nbsp;&nbsp;`static sf: f(F2)`<br>&nbsp;&nbsp;`static sm(arg: f(U2)): f(M2)`<br>&nbsp;&nbsp;`get a(): f(V)`<br>&nbsp;&nbsp;`set a(v: f(V)): void`<br>`}` |
| public/private | `class A {`<br>&nbsp;&nbsp;`public field: F1;`<br>&nbsp;&nbsp;`private m(arg: U1): M1`<br>`}` | `class A {`<br>&nbsp;&nbsp;`public field: f(F1);`<br>&nbsp;&nbsp;`private m(arg: f(U1)): f(M1)`<br>`}` |
| 继承类和override | `class C extends A {`<br>&nbsp;&nbsp;`override foo(arg: U1): M1`<br>`}` | `class C extends A {`<br>&nbsp;&nbsp;`override foo(arg: f(U1)): f(M1)`<br>`}` |
| 实现类 | `class A implements Inface {`<br>&nbsp;&nbsp;`// ...`<br>`}` | `class A implements Inface {`<br>&nbsp;&nbsp;`// ...`<br>`}` |

**接口**

| **类别** | **ArkTS-Dyn type (T)** | **ArkTS-Sta type (f(T))** |
|----------|------------------------|----------------------------|
| 普通接口 | `interface A {`<br>&nbsp;&nbsp;`field: F1`<br>&nbsp;&nbsp;`m(arg: U1): M1`<br>&nbsp;&nbsp;`get a(): V`<br>&nbsp;&nbsp;`set a(v: V): void`<br>`}` | `interface A {`<br>&nbsp;&nbsp;`field: f(F1)`<br>&nbsp;&nbsp;`m(arg: f(U1)): f(M1)`<br>&nbsp;&nbsp;`get a(): f(V)`<br>&nbsp;&nbsp;`set a(v: f(V)): void`<br>`}` |


### TS类型映射到ArkTS-Sta类型

**基本类型**

| **TS type (T)**       | **ArkTS-Sta type (f(T))**   |
| --------------------- | --------------------- |
| `number/Number`       | `number`              |
| `string/String`       | `string`              |
| `boolean/Boolean`     | `boolean`             |
| `bigint/BigInt`       | `bigint`              |
| `null`                | `null`                |
| `undefined`           | `undefined`           |
| `void`                | `void`                |

**函数**

| **类别**   | **TS type (T)**                                | **ArkTS-Sta type (f(T))**                                     |
| ---------- | ---------------------------------------------- | ------------------------------------------------------- |
| 普通函数   | `function foo(arg1: K1, arg2: K2): R`          | `function foo(arg1: f(K1), arg2: f(K2)): f(R)`          |

**类**

| **类别** | **TS type (T)** | **ArkTS-Sta type (f(T))** |
|----------|-----------------|----------------------------|
| 普通类 | `class A {`<br>&nbsp;&nbsp;`field: F1`<br>&nbsp;&nbsp;`m(arg: U1): M1`<br>&nbsp;&nbsp;`static sf: F2`<br>&nbsp;&nbsp;`static sm(arg: U2): M2`<br>&nbsp;&nbsp;`get a(): V`<br>&nbsp;&nbsp;`set a(v: V): void`<br>`}` | `class A {`<br>&nbsp;&nbsp;`field: f(F1)`<br>&nbsp;&nbsp;`m(arg: f(U1)): f(M1)`<br>&nbsp;&nbsp;`static sf: f(F2)`<br>&nbsp;&nbsp;`static sm(arg: f(U2)): f(M2)`<br>&nbsp;&nbsp;`get a(): f(V)`<br>&nbsp;&nbsp;`set a(v: f(V)): void`<br>`}` |
| public/private | `class A {`<br>&nbsp;&nbsp;`public field: F1;`<br>&nbsp;&nbsp;`private m(arg: U1): M1`<br>`}` | `class A {`<br>&nbsp;&nbsp;`public field: f(F1);`<br>&nbsp;&nbsp;`private m(arg: f(U1)): f(M1)`<br>`}` |
| 继承类和 override | `class C extends A {`<br>&nbsp;&nbsp;`override foo(arg: U1): M1`<br>`}` | `class C extends A {`<br>&nbsp;&nbsp;`override foo(arg: f(U1)): f(M1)`<br>`}` |
| 实现类 | `class A implements Inface {`<br>&nbsp;&nbsp;`// ...`<br>`}` | `class A implements Inface {`<br>&nbsp;&nbsp;`// ...`<br>`}` |


**接口**

| **类别** | **TS type (T)** | **ArkTS-Sta type (f(T))** |
|----------|-----------------|----------------------------|
| 普通接口 | `interface A {`<br>&nbsp;&nbsp;`field: F1`<br>&nbsp;&nbsp;`m(arg: U1): M1`<br>&nbsp;&nbsp;`get a(): V`<br>&nbsp;&nbsp;`set a(v: V): void`<br>`}` | `interface A {`<br>&nbsp;&nbsp;`field: f(F1)`<br>&nbsp;&nbsp;`m(arg: f(U1)): f(M1)`<br>&nbsp;&nbsp;`get a(): f(V)`<br>&nbsp;&nbsp;`set a(v: f(V)): void`<br>`}` |
| 继承接口 | `interface A extends B {`<br>&nbsp;&nbsp;`// ...`<br>`}` | `interface A extends B {`<br>&nbsp;&nbsp;`// ...`<br>`}` |

