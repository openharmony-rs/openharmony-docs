# 使用 Taihe 进行 struct extend 相关开发

## 简介

Taihe支持struct继承struct，@class struct继承struct，@class struct继承@class struct。struct使用@extend注解实现继承，本文着重介绍该注解的用法，需要用户对[struct](./use-taihe-about-struct.md)和[class](./use-taihe-about-class.md)有基础的了解。

## 基本概念

以下述代码为例，其中包含：
- struct继承struct，：G继承F；
- @class struct继承struct：H继承G；
- @class struct继承@class struct：I继承H。

Taihe 相关代码示例

```rust
struct F {
    f: i32;
}

struct G {
    @extends f: F;
    g: i32;
}

@class
struct H {
    @extends g: G;
    h: i32;
}

@class
struct I {
    @extends h: H;
    i: i32;
}
```

以下是Taihe生成的ets代码。

由于存在多级继承，且Taihe struct对应纯数据类，因此每个类会包含自身、基类、间接基类的成员变量。

```typescript
export interface F {
  f: int;
}

// struct 继承 struct 表现为 extends
export interface G extends F {
  g: int;
}

// @class struct 继承 struct 表现为 implements
export class H implements G {
  f: int;
  g: int;
  h: int;
  constructor(f: int, g: int, h: int) {
    this.f = f;
    this.g = g;
    this.h = h;
  }
}

// @class struct 继承 @class struct 表现为 extends
export class I extends H {
  i: int;
  constructor(f: int, g: int, h: int, i: int) {
    super(f, g, h);
    this.i = i;
  }
}
```

## 使用示例

### Taihe 声明

```rust
struct F {
    f: i32;
}

struct G {
    @extends f: F;
    g: i32;
}

@class
struct H {
    @extends g: G;
    h: i32;
}

@class
struct I {
    @extends h: H;
    i: i32;
}

// 自定义的工具函数
function process_g(a: G): G;
function process_h(a: H): H;
function process_i(a: I): I;
```

### C++ 实现

用户的native实现：

```cpp
G process_g(G const& a) {
  return {{a.f.f + 1}, a.g + 2};
}

H process_h(H const& a) {
  return {{{a.g.f.f + 1}, a.g.g + 2}, a.h +3};
}

I process_i(I const& a) {
  return {{{{a.h.g.f.f + 1}, a.h.g.g + 2}, a.h.h +3}, a.i + 4};
}
```

### ets 侧使用

```typescript
let g: G = { f: 0, g: 0 };
let new_g = process_g(g);
let h = new H(0, 0, 0);
let new_h = process_h(h);
let i = new I(0, 0, 0, 0);
let new_i = process_i(i);
console.log("process g:", new_g.f, new_g.g);
console.log("process h:", new_h.f, new_h.g, new_h.h);
console.log("process i:", new_i.f, new_i.g, new_i.h, new_i.i);
```

Output：

```sh
process g: 1 2
process h: 1 2 3
process i: 1 2 3 4
```
