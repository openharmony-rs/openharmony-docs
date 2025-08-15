# Taihe IDL 语言规范

本文档旨在描述 Taihe IDL 的语法和语义规范。

## 包

### 定义包

- **源文件与包的一一对应**
   - 一个源文件只能描述一个包。
   - 一个包不能分布在多个源文件中。

- **包名中的每一部分必须是合法的标识符**
   - 包名由多个部分组成，每个部分用点号（`.`）分隔。
   - 每个部分必须是[合法的标识符](#合法的标识符)。

- **包名由源文件名唯一确定**
   - 示例：在 `ohos.hardware.sensors.ohidl` 文件中，描述了 `ohos.hardware.sensors` 包中的各个成员。

- **包的成员名称不得与包名相同**
   - 示例：如果 `ohos.hardware.sensors` 包下定义了 `enum SensorManager`，则不允许同时存在包 `ohos.hardware.sensors.SensorManager`。
   - 原因：动态语言（如 JS、Python）通常不支持在同一作用域内存在同名成员。

### 使用包管理命名空间

- **默认可直接引用当前包下的名称**
   ```rust
   // example.types.ohidl
   struct Foo { a: i32; }
   struct Bar { b: String; }

   function func1(foo: Foo): void;          // OK
   function func2(bar: Bar): void;          // OK
   ```

- **导入其他包并生成别名**
   使用 `use ... as` 或 `from ... use` 为其他包的名称生成别名。
   ```rust
   // example.test1.ohidl
   use example.types as myfoo;
   function func3(foo: myfoo.Foo): void;    // OK

   // example.test2.ohidl
   from example.types use Bar, Foo as Foobar;
   function func4(foo: Foobar): void;       // OK
   function func5(foo: Bar): void;          // OK
   ```

- **包间互相隔离，无从属关系**
   ```rust
   // example.ohidl
   from types use Foo;            // Error: package `types` does not exist
   use types as mytypes;          // Error: package `types` does not exist
   from example.types use Foo;    // OK
   use example.types;             // OK
   function func6(foo: Foo): void;           // OK
   function func7(foo: example.types.Foo): void; // OK
   ```

## 内置类型

提供以下基础类型：

- **整型**
  - 无符号：`u8`, `u16`, `u32`, `u64`（注：ArkTS 1.2 中不支持直接使用无符号类型作为函数参数、返回值或数据结构成员等）
  - 有符号：`i8`, `i16`, `i32`, `i64`
- **浮点型**
  - `f32`, `f64`
- **布尔型**
  - `bool`
- **字符串类型**
  - `String`
- **容器类型**
  - `Optional<T>`：可选类型，表示值可能存在或不存在，支持任意类型 `T`。
  - `Array<T>`：长度在创建后即不可变数组类型，支持任意成员类型 `T`。
  - `Map<K, V>`：映射类型，支持键值对，其中键类型为 `K`，值类型为 `V`。
  - `Set<T>`：集合类型，支持任意成员类型 `T`。
  - `Vector<T>`：可动态变长的数组类型，支持任意成员类型 `T`。
- **函数闭包类型**
  - `(arg1: Type1, arg2: Type2, ...) => ReturnType`：表示函数类型，支持任意数量的参数和一个返回值。


## 合法的标识符

标识符用于命名包、类型、函数、成员、属性等。合法的标识符必须满足以下规则：

- 只能包含英文大小写字母、数字和下划线，且不能以数字开头。
- 不能使用保留字，如 `if`, `else`, `function`, `enum`, `struct`, `union`, `interface` 等，详见[附录：Taihe 关键字全集](#附录taihe-关键字全集)。
- 区分大小写，如 `Foo` 和 `foo` 是不同的标识符。

## 函数

Taihe 支持定义函数作为包的顶层成员。它们是 API 作者对外提供的 API 的入口。

- **函数参数**

  函数可拥有任意数量的参数，每个参数由参数名和参数类型组成。

- **返回值**

  函数可以有一个返回值。若需返回多个值，建议使用结构体。省略返回值时，返回值类型为 `void`。

合法与非法声明示例：
```rust
function func1(foo: i32): void;                    // OK
function func2(foo: String);                       // OK
function func3(m: i32, n: i32): (String, String);  // Error: cannot have multiple return values
struct StringPair {
  a: String;
  b: String;
}
function func4(m: i32, n: i32): StringPair;        // OK
```

## 枚举类型

枚举类型用于定义一组命名的常量，且在定义时必须指定一个特定的类型作为其成员的类型，支持整数、浮点数、布尔值和字符串类型。枚举类型的成员被称为枚举项，每个枚举项可以有一个指定的字面值，该值需要与枚举类型一致。
```rust
enum Foo: i32 {
  A = 0,
  B = 1,
  C = 2,
}

enum Bar: String {
  X = "x",
  Y = "y",
  Z = "z",
}
```

### 省略枚举值

枚举项可以省略值，若未指定值，则会根据枚举类型的规则自动分配默认值。

- 对于整数类型的枚举，若未指定值，则从上一个元素的值递增，第一个元素默认为 0。
  ```rust
  enum Foo: i32 {
    A,          // 0
    B,          // 1
    C = -10,
    D,          // -9
  }
  ```

- 对于字符串类型的枚举，若未指定值，默认使用枚举项的名称作为值。
  ```rust
  enum Bar: String {
    X,          // "X"
    Y,          // "Y"
    Z = "z_value",
  }
  ```

- 对于布尔类型和浮点类型的枚举，默认值分别为 `false` 或 `0.0`。

### 枚举值重复

同一个枚举类型中，可以有多个不同的枚举项具有相同的值。
```rust
enum Foo: i32 {
  A = 0,
  B = 1,
  C = 1,  // 重复值，合法
}
```

在上面的例子中，虽然 `B` 和 `C` 的值相同，但它们会被认为是不同的枚举项，且对应不同的 ABI，因此在运行时是可区分的。

## 结构体

结构体是数据成员的组合，其成员可以是任意 Taihe 支持的数据类型。如[内置类型](#内置类型)、[枚举类型](#枚举)、[接口类型](#接口)、[标签联合](#标签联合)和其他[结构体类型](#结构体)等：
```rust
interface Base {}
struct Foo {
  a: i32;
  s: String;
  i: Base;
  x: Array<i32>;
}
```

空的结构体是禁止的，至少需要一个成员：
```rust
struct Empty {};  // Error: empty struct is not allowed
struct NonEmpty { a: i32; };  // OK
```

## 标签联合

标签联合用于表示多种可能的数据类型，每个标签对应一种数据类型。多个标签可以对应同一个数据类型。标签联合的定义方式如下：
```rust
struct Bar {
  x: i32;
  y: String;
}

union Foo {
  A: i32;
  B: String;
  C: bool;
  D: Bar;
  E: Bar;
}
```

和结构体一样，标签联合也禁止为空，至少需要一种数据成员：
```rust
union Empty {};  // Error: empty union is not allowed
union NonEmpty { a: i32; };  // OK
```

## 接口

接口用于定义一组方法的集合，接口中只能声明方法，不能包含数据成员。语法如下：
```rust
interface Base {
  getId(): u64;
  setId(id: u64): void;
}
```

接口可以继承其他接口，表示实现该接口的类型需要实现所有继承的接口中的方法。
```rust
interface Derived: Base {
  getName(): String;
  setName(name: String): void;
}
```

接口可以同时继承多个其他接口：
```rust
interface BaseA {
  baseAFunc(): i32;
}

interface BaseB {
  baseBFunc(): String;
}

interface Derived: BaseA, BaseB {
  derivedFunc(): bool;
}
```

## 注解

注解用于为代码中的语法元素添加附加属性，从而使得可以在 Taihe 基本语法的基础上针对特定语言后端添加扩展能力支持，本章节主要介绍 Taihe 的注解语法，具体注解由特定语言后端提供。

注解的基本语法如下：
```rust
// 前缀注解（@name）
@attribute_name(value1, value2, ..., key1 = value1, key2 = value2, ...)
function myFunc(color: RGB): void;

// 内联注解（@!name）
interface MyInterface {
  @!attribute_name(value1, value2, ..., key1 = value1, key2 = value2, ...)
  myMethod(param: Type): ReturnType;
}
```

### 前缀注解

语法为 `@name`，用于指定给其后面紧跟的语法元素添加属性。
```rust
@class // 用于修饰 interface MyInterface
interface MyInterface {
  @get("name") // 用于修饰方法 getName
  getName(): String;
  @set("name") // 用于修饰方法 setName
  setName(name: String): void;
}

@class // 用于修饰结构体 A
struct A {
  param: i32;
}

@promise // 用于修饰函数 fetchData
function fetchData(url: String): Response;

@async // 用于修饰函数 processData
function processData(data: String): void;

function test(@optional param: Optional<String>); // 注解 @optional 用于修饰参数 param

union MyUnion {
  stringValue: @arraybuffer Array<i8>; // 注解 @arraybuffer 用于修饰类型 Array<i8>
}
```

### 内联注解

语法为 `@!name`，写在某个域内部（如接口、结构体等或包的顶层），用于为其所在的域对应的语法元素添加属性。
```rust
@!namespace("example", namespace = "a.b") // 用于修饰所在的整个包

interface MyInterface {
  @!class  // 用于修饰 interface MyInterface，等价于在 interface 前添加 @class
}
```

### 简写规则

无参数注解的括号可以被省略，例如，以下两种写法是等价的：
```rust
@attribute_name()
function myFunc(): void; // OK

@attribute_name
function myFunc(): void; // OK, same as above
```

## 其他规则

### 递归包含与继承

- 函数和类型的声明无先后顺序。
  ```rust
  struct Foo {
    bar: Bar;
  }
  struct Bar {
    val: i32;
  }
  // OK
  ```

- 禁止结构体与结构体、联合体与联合体、结构体与联合体之间的递归包含：
  ```rust
  struct RecursiveStruct {
    e: RecursiveUnion;
  }
  union RecursiveUnion {
    s: RecursiveStruct;
  }
  // Error: recursive inclusion
  //        RecursiveStruct -> RecursiveUnion -> RecursiveStruct
  ```

  但是使用容器类型则允许递归：
  ```rust
  struct Foo {
    bar: Array<Foo>;
  }
  // OK

  union Bar {
    val: Optional<Bar>;
  }
  // OK
  ```

- 接口间不能递归扩展：
  ```rust
  interface RecursiveIfaceA: RecursiveIfaceB {}
  interface RecursiveIfaceB: RecursiveIfaceA {}
  // Error: recursive inheritance
  //        RecursiveIfaceA -> RecursiveIfaceB -> RecursiveIfaceA
  ```

## 附录：Taihe 关键字全集

以下列出了 Taihe IDL 中所有的关键字（保留字），它们在语法中具有特定含义，不允许作为普通标识符（如变量名、函数名、类型名等）使用。

### 模块与导入关键字

| 关键字 | 含义                   |
|--------|------------------------|
| `use`  | 引入包或符号           |
| `from` | 指定从某个包中引入符号 |
| `as`   | 指定导入时的别名       |

### 顶层声明类型关键字

| 关键字     | 含义           |
|------------|----------------|
| `enum`     | 定义枚举类型   |
| `struct`   | 定义结构体类型 |
| `union`    | 定义联合体类型 |
| `interface`| 定义接口类型   |
| `function` | 定义全局函数   |

### 类型与值相关关键字

| 关键字 | 含义         |
|--------|--------------|
| `true` | 布尔值：真   |
| `false`| 布尔值：假   |

### 条件表达式关键字

| 关键字 | 含义                     |
|--------|--------------------------|
| `if`   | 条件判断起始             |
| `then` | 条件成立时的执行分支     |
| `else` | 条件不成立时的执行分支   |

### 运算符符号（Token 保留字）

以下符号在 Taihe 语言中通过词法规则定义为**保留符号**，具有特定语义，不可作为普通标识符使用：

**算术与比较运算符**

| 符号 | 含义             |
|------|------------------|
| `+`  | 加法             |
| `-`  | 减法 / 负号      |
| `*`  | 乘法             |
| `/`  | 除法             |
| `%`  | 取余             |
| `==` | 等于比较         |
| `!=` | 不等比较         |
| `<`  | 小于             |
| `<=` | 小于等于         |
| `>`  | 大于             |
| `>=` | 大于等于         |

**位运算与逻辑运算符**

| 符号   | 含义           |
|--------|----------------|
| `&`    | 按位与         |
| `\|`   | 按位或         |
| `^`    | 按位异或       |
| `~`    | 按位取反       |
| `!`    | 逻辑非         |
| `&&`   | 逻辑与         |
| `\|\|` | 逻辑或         |
| `<<`   | 左移           |
| `>>`   | 右移           |

**其他符号**

| 符号 | 含义                 |
|------|----------------------|
| `=`  | 属性参数绑定         |
| `=>` | 回调类型返回值标识符 |
| `@`  | 前缀注解语法标识     |
| `@!` | 内联注解语法标识     |
