# 使用 Taihe 进行 rename 相关开发

## 简介

在 Taihe 中，使用 `@rename` 注解来实现生成的 ets 代码中的函数重命名功能。

## 基本概念

`@rename` 注解可以用于**全局函数**和**成员方法**。

**Taihe 声明代码**
```rust
@rename("newFoo")
function oldFoo(a: i32, b: i32): i32;
```

用户对函数使用了 `@rename` 注解，会使得生成的 ets 代码的 export 函数名重命名为新名字。

**生成ets代码**
```typescript
native function _taihe_oldFoo_native(a: int, b: int): int;
// 此处函数名为 @rename 注解的参数值
export function newFoo(a: int, b: int): int {
    return _taihe_oldFoo_native(a, b);
}
function _taihe_oldFoo_reverse(a: int, b: int): int {
    return newFoo(a, b);
}
```

## 使用示例

### Taihe 声明

```rust
@rename("newFoo")
function oldFoo(a: i32, b: i32): i32;
```

### C++ 实现

```cpp
int32_t oldFoo(int32_t a, int32_t b) {
  return a + b;
}
```

### ets 使用

```typescript
let res = rename_example.newFoo(1, 2);
console.log("res = " + res);
```

输出结果如下：
```sh
res = 3
```
