# 使用Taihe进行ets协同开发

## 简介

Taihe提供注解`@!sts_inject`，可以将代码注入到生成的ets文件中。

## 基本概念

`@!sts_inject("""...""")`：Taihe IDL文件顶层注解。可以将一段ets代码注入到当前Taihe文件对应的ets namespace中。

`@!sts_inject_into_module("""...""")`：Taihe IDL文件顶层注解。可以将一段ets代码注入到当前Taihe文件所对应的ets namespace所在的module头部。

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

`@!sts_inject_into_interface("""...""")`：可加在Taihe IDL中声明的struct/interface上。用于将一段ets代码注入到对应生成的ets interface中。

`@!sts_inject_into_class("""...""")`：可加在Taihe IDL中声明的struct/interface上。用于将一段ets代码注入到对应生成的ets class中。

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

### Taihe声明

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

### C++实现

此处代码示例无需实现具体代码，因此无需提供C++实现。

### ets使用

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
