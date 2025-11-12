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

#### 基本类型

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

#### 函数

| **类别**               | **ArkTS-Sta type (T)**                               | **ArkTS-Dyn type (f(T))**                                            |
| ---------------------- | ---------------------------------------------- | -------------------------------------------------------------  |
| 普通函数               | `function foo(arg1: K1, arg2: K2): R`          | `function foo(arg1: f(K1), arg2: f(K2)): f(R)`                 |

#### 类

TODO: 美化表格

| **类别**                                 | **ArkTS-Sta type (T)**                                                                                          | **ArkTS-Dyn type (f(T))**                                                                                                                                       |
| ---------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 普通类                                   | class A { field: F1; m(arg: U1): M1; static sf: F2; static sm(arg: U2): M2; get a(): V; set a(v: V): void; } | class A { get field(): f(F1); set field(arg: f(F1)): void; m(arg: f(U1)): f(M1); static sf: f(F2); static sm(arg: f(U2)): f(M2); get a(): f(V); set a(v: f(V)): void; } |
| public/private | class A { public field: F1; private m(arg: U1): M1; } | class A { public field: f(F1); private m(arg: f(U1)): f(M1); } |                                                                                      |
| 继承类和override                         | class C extends A { override foo(arg: U1): M1; };                                                           | class C extends A { override foo(arg: f(U1)): f(M1); };                                                                                                       |
| 实现类                                   | class A implements Inface { ... };                                                                         | class A implements Inface { ... };                                                                                                                         |

#### 接口

TODO: 美化表格

| **类别** | **ArkTS-Sta type (T)**                                                | **ArkTS-Dyn type (f(T))**                                                         |
| -------- | --------------------------------------------------------------- | --------------------------------------------------------------------------- |
| 普通接口 | inteface A {field: F1m(arg: U1): M1get a(): Vset a(v: V): void} | class A {field: f(F1)m(arg: f(U1)): f(M1)get a(): f(V)set a(v: f(V)): void} |
| 继承接口 | interface A extends B { ... }                                   | interface A extends B { ... }                                               |

### ArkTS-Dyn类型映射到ArkTS-Sta类型

#### 基本类型

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

#### 函数

| **类别**   | **ArkTS-Dyn type (T)**                               | **ArkTS-Sta type (f(T))**                                     |
| ---------- | ---------------------------------------------- | ------------------------------------------------------- |
| 普通函数   | `function foo(arg1: K1, arg2: K2): R`          | `function foo(arg1: f(K1), arg2: f(K2)): f(R)`          |

#### 类

TODO: 美化表格

| **类别**                          | **ArkTS-Dyn type (T)**                                                                                | **ArkTS-Sta type (f(T))**                                                                                                     |
| --------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 普通类                            | class A {field: F1m(arg: U1): M1static sf: F2static sm(arg: U2): M2get a(): Vset a(v: V): void} | class A {field: f(F1)m(arg: f(U1)): f(M1)static sf: f(F2)static sm(arg: f(U2)): f(M2)get a(): f(V)set a(v: f(V)): void} |
| public/private | class A {public field: F1;private m(arg: U1): M1}            | class A {public field: f(F1);private m(arg: f(U1)): f(M1)}                     |                                                  |
| 继承类和override                  | class C extends A {override foo(arg: U1): M1}                                                   | class C extends A {override foo(arg: f(U1)): f(M1)}                                                                     |
| 实现类                            | class A implements Inface { ... }                                                               | class A implements Inface { ... }                                                                                       |

#### 接口

TODO: 美化表格

| **类别** | **ArkTS-Dyn type (T)**                                                 | **ArkTS-Sta type (f(T))**                                                             |
| -------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| 普通接口 | interface A {field: F1m(arg: U1): M1get a(): Vset a(v: V): void} | interface A {field: f(F1)m(arg: f(U1)): f(M1)get a(): f(V)set a(v: f(V)): void} |

### TS类型映射到ArkTS-Sta类型

#### 基本类型

| **TS type (T)**       | **ArkTS-Sta type (f(T))**   |
| --------------------- | --------------------- |
| `number/Number`       | `number`              |
| `string/String`       | `string`              |
| `boolean/Boolean`     | `boolean`             |
| `bigint/BigInt`       | `bigint`              |
| `null`                | `null`                |
| `undefined`           | `undefined`           |
| `void`                | `void`                |

#### 函数

| **类别**   | **TS type (T)**                                | **ArkTS-Sta type (f(T))**                                     |
| ---------- | ---------------------------------------------- | ------------------------------------------------------- |
| 普通函数   | `function foo(arg1: K1, arg2: K2): R`          | `function foo(arg1: f(K1), arg2: f(K2)): f(R)`          |

#### 类

TODO: 美化表格

| **类别**                          | **TS type (T)**                                                                                 | **ArkTS-Sta type (f(T))**                                                                                                     |
| --------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 普通类                            | class A {field: F1m(arg: U1): M1static sf: F2static sm(arg: U2): M2get a(): Vset a(v: V): void} | class A {field: f(F1)m(arg: f(U1)): f(M1)static sf: f(F2)static sm(arg: f(U2)): f(M2)get a(): f(V)set a(v: f(V)): void} |
| public/private | class A {public field: F1;private m(arg: U1): M1}            | class A {public field: f(F1);private m(arg: f(U1)): f(M1)}                     |
| 继承类和override                  | class C extends A {override foo(arg: U1): M1}                                                   | class C extends A {override foo(arg: f(U1)): f(M1)}                                                                     |
| 实现类                            | class A implements Inface { ... }                                                               | class A implements Inface { ... }                                                                                       |

#### 接口

TODO: 美化表格

| **类别** | **TS type (T)**                                                  | **ArkTS-Sta type (f(T))**                                                             |
| -------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| 普通接口 | interface A {field: F1m(arg: U1): M1get a(): Vset a(v: V): void} | interface A {field: f(F1)m(arg: f(U1)): f(M1)get a(): f(V)set a(v: f(V)): void} |
| 继承接口 | interface A extends B { ... }                                    | interface A extends B { ... }                                                   |
