# 使用Taihe进行overload相关开发

## 简介

在 Taihe 中，使用`@rename`注解来实现函数重载的功能。

## 基本概念

重载指的是在同一个作用域中定义多个同名函数，但参数列表不同。编译器会根据传入的参数自动选择合适的函数。

Taihe使用`@rename`来实现ArkTS的重载。该注解可以作用于**全局函数**和对象的**成员方法**。

**Taihe 声明代码**
```rust
@rename("add")
function sum_two(a: i32, b: i32): i32;
@rename("add")
function sum_arr(a: Array<i32>): i32;
```

重载的注解如上述样例所示，使用`@rename("{sts_name}")` 。

使用该注解后，实现侧的函数名仍为Taihe IDL文件声明的函数名。

**生成ets代码**
```typescript
export function add(a: int, b: int): int {
    return _taihe_sum_two_native(a, b);
}
export function add(a: Array<int>): int {
    return _taihe_sum_arr_native(a);
}
```

## 使用示例

### Taihe 声明

```rust
@rename("add")
function sum_two(a: i32, b: i32): i32;
@rename("add")
function sum_arr(a: Array<i32>): i32;
```

### C++ 实现

```cpp
int32_t sum_two(int32_t a, int32_t b) {
    return a + b;
}
int32_t sum_arr(array_view<int32_t> a) {
    if (a.size() == 0) return 0;
    int32_t result = 0;
    for (int i = 0; i < a.size(); ++i) {
        result += a[i];
    }
    return result;
}
```

### ets 使用

```typescript
let a: int = 1
let b: int = 2
let numbers: int[] = [1, 2, 3, 4, 5];
console.log("add_two: " + overload.add(a, b))
console.log("add_arr: " + overload.add(numbers))
```

输出结果如下：

```sh
add_two: 3
add_arr: 15
```
