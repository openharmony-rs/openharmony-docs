# Taihe IDL语言规范

本文档旨在描述Taihe IDL的语法规范和语义规则。

## 词法结构

### 注释

- 单行注释以`//`开头，直到行尾结束。
- 多行注释以`/*`开头，以`*/`结尾。

### 关键字

见[附录：Taihe关键字全集](#附录taihe关键字全集)。

### 标识符

标识符用于命名包、类型、函数、成员、属性等。合法的标识符必须满足以下规则：

- 只能包含英文大小写字母、数字和下划线。
- 首个字符不能是数字。
- 不能使用关键字。
- 区分大小写，如`Foo`和`foo`是不同的标识符。

### 字面值

- **整数**：支持十进制、十六进制（以`0x`开头）、八进制（以`0o`开头）和二进制（以`0b`开头）表示法。
- **浮点数**：带有小数点，或使用科学计数法（如`1.23e-4`, `1e10`）表示的数字。
- **布尔值**：`true`和`false`。
- **字符串**：使用双引号（`"`）括起来的字符序列，支持常见的转义字符（如`\n`, `\t`, `\\`, `\"`）。另外，使用三重双引号（`"""`）括起来的字符串可以跨多行，并且不需要转义内部的双引号。

## 源文件与包

### 定义包

- **包的命名规则**
  - 包名由多个部分组成，每个部分用点号（`.`）分隔。
  - 每个部分必须是合法的标识符。

- **包名的确定**
  - 源文件名（不含路径和扩展名）即为包名。例如，`idl/ohos.hardware.sensors.ohidl`文件定义的包名为`ohos.hardware.sensors`。

- **源文件与包的一一对应**
  - 一个源文件只能描述一个包。
  - 一个包不能分散到多个源文件中。

- **包内成员不可与其他成员或包冲突**
  - 同一包内所有顶层成员（包括全局函数和用户自定义类型等）的名称必须唯一，不可重复。
  - 包内顶层成员的全名不可与其他包名冲突。例如，若已经存在包`ohos.hardware.sensors.example`，则不允许在`ohos.hardware.sensors`包中定义名为`example`的成员。这是为了避免在投影到如Python等动态语言中时产生命名冲突，在这些语言中，包（模块）和其内部定义的成员共享同一命名空间。

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

  使用`use ...;`语法导入其他包。导入后需要使用完整包名来引用导入包中的成员。

  ```rust
  // example.test1.ohidl
  use example.types;
  function func3(foo: example.types.Foo): void; // OK，需要使用完整包名
  ```

  可以使用`use ... as ...;`语法为导入的包生成别名。

  ```rust
  // example.test2.ohidl
  use example.types as mytypes;
  function func4(foo: mytypes.Foo): void;       // OK
  function func5(foo: mytypes.Bar): void;       // OK
  ```

- **导入其他包中的单个顶层成员**

  使用`from ... use ...;`语法从其他包中导入单个顶层成员，可以同时导入多个成员，并且可以通过`as`关键字为导入的成员生成别名。

  ```rust
  // example.test3.ohidl
  from example.types use Foo, Bar as Foobar;
  function func6(foo: Foo): void;           // OK
  function func7(foo: Foobar): void;        // OK
  ```

- **包间互相隔离，无从属关系，所有导入必须使用完整包名**

  ```rust
  // example.ohidl
  use types;                     // Error: package `types` does not exist
  from types use Foo;            // Error: package `types` does not exist
  use example.types;             // OK
  from example.types use Foo;    // OK
  function func6(foo: Foo): void;           // OK
  function func7(foo: example.types.Foo): void; // OK
  ```

## 数据类型

Taihe提供了以下内置数据类型：

- **Void类型**
  - `void`：表示空类型，通常只能用作函数的返回值类型，表示函数没有返回值。
- **单位类型**
  - `unit`：表示无值的类型。
- **整型**
  - 无符号：`u8`, `u16`, `u32`, `u64`
  - 有符号：`i8`, `i16`, `i32`, `i64`
- **浮点型**
  - `f32`, `f64`
- **布尔型**
  - `bool`
- **字符串类型**
  - `String`
- **容器类型**
  - `Optional<T>`：可选类型，表示值可能存在或不存在，支持任意非空类型`T`。
  - `Array<T>`：长度在创建后即不可变数组类型，支持任意非空成员类型`T`。
  - `Map<K, V>`：映射类型，支持键值对，其中键类型为任意非空类型`K`，值类型为任意非空的`V`。
  - `Set<T>`：集合类型，支持任意非空成员类型`T`。
  - `Vector<T>`：可动态变长的数组类型，支持任意非空成员类型`T`。
- **函数闭包类型**
  - `(arg1: Type1, arg2: Type2, ...) => ReturnType`：表示函数类型，支持任意数量的参数和一个返回值，参数类型非空且参数名不可省略。

除了上述内置类型外，用户通过`enum`、`struct`、`union`和`interface`定义的类型也属于Taihe支持的数据类型。

## 函数

Taihe支持定义函数作为包的顶层成员。它们是API作者对外提供的API的入口。

- **函数参数**

  函数可拥有任意数量的参数，每个参数由参数名和非空的参数类型组成。

- **返回值**

  函数最多只能有一个返回值。可以是任意的类型。当省略返回值时，返回值类型默认为`void`。

以下是一些合法的函数声明：

```rust
function func1(foo: i32): void;              // OK
function func2(foo: String);                 // OK，省略返回值时返回值类型默认为void

struct StringPair {
  a: String;
  b: String;
}
function func3(m: i32, n: i32): StringPair;  // OK，如果要返回多个值，可以使用结构体封装
```

## 枚举类型

枚举类型用于定义一组命名的常量。

在定义枚举类型时，必须指定一个特定的基础类型（包括整型、浮点型、布尔型和字符串类型）作为其所有成员的类型。枚举类型的成员被称为枚举项，每个枚举项对应一个枚举值，枚举值可以是一个字面值或常量表达式，并且其类型需要与前面选定的基础类型匹配。

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

枚举项的值可以省略，若未指定值，则会根据枚举类型的规则自动分配默认值。

- 对于整数类型的枚举，若未指定值，则从上一个元素的值递增，第一个元素默认为0。

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

- 对于布尔类型和浮点类型的枚举，默认值分别为`false`或`0.0`。

### 枚举值重复

虽然在同一个枚举类型中枚举项本身不可以重复，但是可以有多个不同的枚举项对应相同的值。

```rust
enum Foo: i32 {
  A = 0,
  B = 1,
  C = 1,  // 重复值，合法
}
```

在上面的例子中，虽然`B`和`C`的值相同，但它们会被认为是不同的枚举项，且对应不同的ABI，因此在运行时是可区分的。

## 结构体

结构体是数据成员的组合，每个成员有唯一的名称，并可以是任意非空类型。结构体的定义方式如下：

```rust
interface Base {}
struct Foo {
  a: i32;
  s: String;
  i: Base;
  x: Array<i32>;
}
```

空结构体是禁止的，至少需要一个成员：

```rust
struct Empty {};  // Error: empty struct is not allowed
struct NonEmpty { a: i32; };  // OK
```

## 标签联合

标签联合用于表示多种可能的数据类型，每个标签对应一种非空数据类型。多个标签可以对应同一种数据类型，但标签名必须唯一。标签联合的定义方式如下：

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

### 省略类型

标签联合的成员可以省略类型，默认使用`unit`类型。

```rust
union MyUnion {
  A: String;
  B;  // 默认类型为unit
}
```

## 接口

接口用于定义一组方法的集合，接口中只能声明方法，不能包含数据成员。语法如下：

```rust
interface Base {
  getId(): u64;
  setId(id: u64): void;
}
```

### 继承

接口可以继承其他接口，表示实现该接口的类型需要同时实现所有继承的接口中的方法。

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

### 禁止方法重载

同一接口中的方法名不能重复，即使它们有不同的参数列表，这是为了避免在动态语言中调用时出现二义性：

```rust
interface MyInterface {
  func(): void;
  func(param: i32): void;  // Error: duplicate method name 'func'
}
```

### 禁止方法覆盖，但允许有继承关系的接口间定义同名方法

子接口中可以定义与父接口同名的方法，但需要注意的是，这种情况下，子接口中重新定义的方法并不是对父接口方法的重写，而是一个全新的方法，这主要是为了版本兼容性考虑（假如父接口在后续版本中新增了方法，且与子接口中已有的方法同名，则不会引起冲突）。

```rust
interface Base {
  func(): void;
}

interface Derived: Base {
  func(): i32;  // OK, new method, not override
}

interface MoreDerived: Derived {
  func(): i32;  // OK, still not override
}
```

类似地，也允许子接口继承多个父接口，而这些父接口中可能存在同名方法：

```rust
interface BaseA {
  func(): void;
}

interface BaseB {
  func(): i32;
}

interface Derived: BaseA, BaseB {
  // OK, inherits both func() from BaseA and func() from BaseB
}
```

## 注解

注解用于为代码中的语法元素添加附加属性，从而使得可以在Taihe基本语法的基础上针对特定语言后端添加扩展能力支持，本章节主要介绍Taihe的注解语法。

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

### 参数

注解可以带有位置参数和命名参数：

- **位置参数**：按顺序传递给注解，类型可以是任意常量表达式，包括整数、浮点数、布尔值、字符串。
- **命名参数**：以`key = value`形式传递，`key`必须是合法的标识符，`value`可以是任意常量表达式。

### 前缀注解

语法为`@name(...)`，用于指定给其后面紧跟的语法元素添加属性。

```rust
@class // 用于修饰interface MyInterface
interface MyInterface {
  @get("name") // 用于修饰方法getName
  getName(): String;
  @set("name") // 用于修饰方法setName
  setName(name: String): void;
}

@class // 用于修饰结构体A
struct A {
  param: i32;
}

@promise // 用于修饰函数fetchData
function fetchData(url: String): Response;

@async // 用于修饰函数processData
function processData(data: String): void;

function test(@optional param: Optional<String>); // 注解@optional用于修饰参数param

union MyUnion {
  stringValue: @arraybuffer Array<i8>; // 注解@arraybuffer用于修饰类型Array<i8>
}
```

### 内联注解

语法为`@!name(...)`，写在某个域内部（如接口、结构体等或包的顶层），用于为其所在的域对应的语法元素添加属性。

```rust
@!namespace("example", namespace = "a.b") // 用于修饰所在的整个包

interface MyInterface {
  @!class  // 用于修饰interface MyInterface，等价于在interface前添加@class
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

## 语义约束

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

  但是，使用容器类型（`Optional`、`Array`、`Map`、`Set`、`Vector`）等可以实现间接递归包含：

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

- 接口间禁止递归继承：

  ```rust
  interface RecursiveIfaceA: RecursiveIfaceB {}
  interface RecursiveIfaceB: RecursiveIfaceA {}
  // Error: recursive inheritance
  //        RecursiveIfaceA -> RecursiveIfaceB -> RecursiveIfaceA
  ```

## 附录：Taihe关键字全集

以下列出了Taihe IDL中所有的关键字（保留字），它们在语法中具有特定含义，不允许作为普通标识符（如变量名、函数名、类型名等）使用。

### 包导入

|关键字|含义|
|--------|------------------------|
| `use`  |引入包或符号|
| `from` |指定从某个包中引入符号|
| `as`   |指定导入时的别名|

### 顶层声明

|关键字|含义|
|-------------|----------------|
| `enum`      |定义枚举类型|
| `struct`    |定义结构体类型|
| `union`     |定义联合体类型|
| `interface` |定义接口类型|
| `function`  |定义全局函数|

### 值

|关键字|含义|
|---------|------------|
| `true`  |布尔值：真|
| `false` |布尔值：假|

### 条件表达式

|关键字|含义|
|--------|------------------------|
| `if`   |条件判断起始|
| `then` |条件成立时的执行分支|
| `else` |条件不成立时的执行分支|
