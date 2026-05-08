# 在Taihe中使用关键字避让
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

使用`@rename`注解来实现修改生成的ets代码中的函数、方法、属性、类型等的投影名称的功能。

另外，可以在IDL中的标识符前使用`#`符号来实现Taihe关键字避让。

## 背景

在使用Taihe时，默认情况下，目标语言（如C++/ArkTS）中生成的函数、类型等标识符会与Taihe IDL文件中声明的名称保持一致。然而，在某些情况下，可能会遇到命名冲突的问题，例如：

-**目标语言内建宏/关键字冲突（使用`@rename`）**：比如`NULL`是C/C++常用的宏。若直接在Taihe内声明`NULL`这个名称，可能会导致生成的C++代码编译出错。此时可以使用一个安全的内部名（如`fieldNULL`），并使用`@rename("NULL")`表示在映射到ArkTS时改回`NULL`从而规避C++关键字的语法冲突。

-**Taihe关键字冲突（使用`#`转义）**：如果需要在接口里使用Taihe语言关键字作为参数或方法名（如`use`,`from`），可以通过在标识符前加上`#`（如`#use`）来转义。Taihe内部仅视其为普通的标识符，且不会在生成代码里引入`#`字符。

## 基本概念

`@rename`注解可以用于**全局函数**、**成员方法**、**结构体成员**、**枚举成员**以及**类型名**等的声明上。

**Taihe声明代码**
```rust
@class
@rename("AniRenamed")
interface AniOrigin {
    @rename("barRenamed")
    bar(): void;
}

// @ctor/@static中需使用重命名后的类名
@ctor("AniRenamed")
function createAniRenamed(): AniOrigin;

@static("AniRenamed")
function staticAni(): void;
```

用户对类使用了`@rename`注解，会使得生成的ets代码中类名为`AniRenamed`，而非IDL中声明的`AniOrigin`。同样地，用户对成员方法使用了`@rename`注解后，生成的ets代码中方法名为`barRenamed`，而非IDL中声明的`bar`。

**生成ets代码**
```typescript
export interface AniRenamed {
    barRenamed(): void;

    constructor();
    static staticAni(): void;
}
```

## 使用示例

### Taihe声明

**File: `idl/rename_example.taihe`**

**函数重命名**

```rust
@rename("newFoo")
function oldFoo(a: i32, b: i32): i32;
```

ArkTS侧将生成`newFoo`，C++侧仍使用`oldFoo`。

**Enum重命名（类型和成员）**

```rust
@rename("Color")
enum OldColor: i32 {
    @rename("red") RED = 0,
    @rename("green") GREEN = 1,
    @rename("blue") BLUE = 2,
}
```

ArkTS侧类型名为`Color`，成员名为`red`、`green`、`blue`。

**Struct重命名（类型和字段）**

```rust
@rename("Point")
struct OldPoint {
    @rename("xPos") x: i32;
    @rename("yPos") y: i32;
}

function createPoint(x: i32, y: i32): OldPoint;  // 在IDL中仍使用OldPoint
```

ArkTS侧类型名为`Point`，字段名为`xPos`、`yPos`。

**Interface重命名（类型和方法）**

```rust
@rename("Greeter")
interface OldGreeter {
    @rename("greetRenamed") greet(): String;
}

function createGreeter(name: String): OldGreeter; // 在IDL中仍使用OldGreeter
```

ArkTS侧类型名为`Greeter`，方法名为`greetRenamed`。

### C++实现

`@rename`注解只影响生成的ArkTS代码，在C++实现侧仍使用Taihe IDL文件中声明的函数、类型等名称。

```cpp
int32_t oldFoo(int32_t a, int32_t b) {
    return a + b;
}

OldPoint createPoint(int32_t x, int32_t y) {
    return OldPoint{x, y};
}
struct MyGreeter {
    std::string name_;

    MyGreeter(std::string name) : name_(std::move(name)) {}

    taihe::string greet() override {
        return "Hello from " + name_;
    }
};

OldGreeter createGreeter(std::string name) {
    return taihe::make_holder<MyGreeter, OldGreeter>(std::move(name));
}
```

### ets使用

```typescript
import * as rename_example from "rename_example";

loadLibrary("rename_example");

function main() {
    // 函数：ArkTS侧使用新名称
    let res = rename_example.newFoo(1, 2);
    console.info("newFoo(1, 2) = " + res);  // 3

    // Enum：类型和成员均使用新名称
    let c: rename_example.Color = rename_example.Color.red;

    // Struct：类型和字段使用新名称
    let p = rename_example.createPoint(10, 20);
    console.info("Point.xPos = " + p.xPos);  // 10

    // Interface：类型使用新名称
    let g: rename_example.Greeter = rename_example.createGreeter("Taihe");
    console.info(g.greetRenamed());  // Hello from Taihe
}
```

输出结果如下：

```sh
newFoo(1, 2) = 3
Point.xPos = 10
Hello from Taihe
```
