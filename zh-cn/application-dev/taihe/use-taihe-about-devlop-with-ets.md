# 使用 Taihe 进行 ets 协同开发

## 简介

Taihe 提供注解 `@!sts_inject`，可以将代码注入到生成的 ets 文件中。

## 基本概念

`@!sts_inject("""...""")`：Taihe IDL 文件顶层注解。可以将一段 ets 代码注入到当前 Taihe 文件对应的 ets namespace 中。

`@!sts_inject_into_module("""...""")`：Taihe IDL 文件顶层注解。可以将一段 ets 代码注入到当前 Taihe 文件所对应的 ets namespace 所在的 module 头部。

**moduleA.foo.ohidl**
```rust
@!namespace("moduleA", "foo")

@!sts_inject("""export function foo(a: int): int { return a; }""")
@!sts_inject_into_module("""export function toplevelFunc(a: string): string { return a; }""")
```

**生成的moduleA.ets**
```typescript
export function toplevelFunc(a: string): string { return a; } // injected
export namespace foo {
    export function foo(a: int): int { return a; } // injected
}
```

`@!sts_inject_into_interface("""...""")`：可加在 Taihe IDL 中声明的 struct/interface 上。用于将一段 ets 代码注入到对应生成的 ets interface 中。

`@!sts_inject_into_class("""...""")`：可加在 Taihe IDL 中声明的 struct/interface 上。用于将一段 ets 代码注入到对应生成的 ets class 中。

**taihe声明**
```rust
struct RGB {
    @!sts_inject_into_interface("""color: string;""")
    @!sts_inject_into_class("""color: string = "red";""")

    r: i32;
    g: i32;
    b: i32;
}
```

**生成的ets代码**
```typescript
export interface RGB {
    color: string; // injected

    r: int;
    g: int;
    b: int;
}
class _taihe_RGB_inner implements RGB {
    color: string = "red"; // injected

    r: int;
    g: int;
    b: int;
    constructor(
        r: int,
        g: int,
        b: int,
    )
    {
        this.r = r;
        this.g = g;
        this.b = b;
    }
}
```

## 使用示例

### Taihe 声明

**moduleA.foo.ohidl**
```rust
@!sts_inject("""export function foo(a: int): int { return a; }""")
@!sts_inject_into_module("""export function toplevelFunc(a: string): string { return a; }""")
@!namespace("moduleA", "foo")
struct RGB {
    @!sts_inject_into_interface("""color: string;""")
    @!sts_inject_into_class("""color: string = "red";""")

    r: i32;
    g: i32;
    b: i32;
}
```

### C++ 实现

此处代码示例无需实现具体代码，因此无需提供 C++ 实现。

### ets 使用

```typescript
let res1: string = moduleA.toplevelFunc("hello");
console.log("toplevelFunc: " + res1);
let res2: int = moduleA.foo.foo(100);
console.log("foo.foo: " + res2);
let structObj: moduleA.RGB = {
    color: "red",
    r: 255,
    g: 0,
    b: 0,
};
console.log(structObj.color + " " + structObj.r);
```

输出结果如下：
```sh
toplevelFunc: hello
foo.foo: 100
red 255
```
