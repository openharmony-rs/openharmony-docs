# 使用 Taihe 进行 struct extend 相关开发

## 简介

Taihe支持struct继承struct，@class struct继承struct。本文着重介绍struct的@extend注解的用法，需要用户对[struct](./use-taihe-about-struct.md)和[class](./use-taihe-about-class.md)有基础的了解。

## 基本概念

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
```

以下是对应的 ets 代码

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

function process_g(a: G): G;
function process_h(a: H): H;
```

### C++ 实现

```cpp
G process_g(G const& a) {
  return {{a.f.f + 1}, a.g + 2};
}

H process_h(H const& a) {
  return {{{a.g.f.f + 1}, a.g.g + 2}, a.h +3};
}
```

### ets 侧使用

```typescript
let g: G = { f: 0, g: 0 };
let new_g = process_g(g);
let h = new H(0, 0, 0);
let new_h = process_h(h);
console.log("process g:", new_g.f, new_g.g);
console.log("process h:", new_h.f, new_h.g, new_h.h);
```

Output：

```sh
process g: 1 2
process h: 1 2 3
```
