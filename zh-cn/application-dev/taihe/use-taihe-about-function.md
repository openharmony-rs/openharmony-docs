# 使用 Taihe 进行 function 相关开发

## 简介

使用 Taihe 进行函数相关开发时，编写 Taihe IDL 文件描述函数声明，就可以使得 ets 侧调用到 C++ 侧的实现。

注意，在使用 Taihe 生成 ANI 桥接代码时，会在 ets 侧自动将所有函数的首字母转换为小写，如有需要保持函数首字母大写，可以使用 `-Csts:keep-name` 参数。

## 基本概念

Taihe 相关代码示例

```rust
function add(a: i32, b: i32): i32;
```

以下是对应的 ets 代码

```typescript
// native 函数对应 ANI register 的实现函数，函数名经过 name mangling 避免重名
native function _taihe_add_native(a: int, b: int): int;

// export 函数提供给 ets 侧使用，其内部调用了 native 函数
export function add(a: int, b: int): int {
    return _taihe_add_native(a, b);
}
```

每个函数都会在 ets 侧生成 native function 和 export function 两个函数。

## 使用示例

### Taihe 声明

```rust
function add(a: i32, b: i32): i32;
```

### C++ 实现

```cpp
int32_t add(int32_t a, int32_t b) {
  return a + b;
}

// 导出函数的具体实现
TH_EXPORT_CPP_API_add(add);
```

### ets 侧使用

```typescript
let a = add(1, 2);
console.log("test add:", a);
```

Output：

```sh
test add: 3
```

## 函数调用链

以示例函数为例，当 ets 侧调用函数 add 时，它会经历如下步骤：

1. 进入自动生成的 `.ets` 文件中的 `add` 函数实现。

   **.ets**

   ```typescript
   export function add(a: int, b: int): int {
     return _taihe_add_native(a, b);
   }
   ```

2. 该 `add` 函数中会进一步调用进同一文件中的 `_taihe_add_native` 函数，该函数与生成代码中的 `.ani.cpp` 文件中的 `local::add` 函数相绑定。

   **.ets**

   ```typescript
   native function _taihe_add_native(a: int, b: int): int;
   ```

3. `local::add` 函数会先解析参数，将 ets 对象转换为 Taihe 对象，然后调用 C++ 实现函数，再将返回值由 Taihe 对象转换为 ets 对象。

   **.ani.cpp**

   ```cpp
   namespace local {
   static ani_int add([[maybe_unused]] ani_env *env, ani_int ani_arg_a, ani_int ani_arg_b) {
       // 参数类型转换
       int32_t cpp_arg_a = static_cast<int32_t>(ani_arg_a);
       int32_t cpp_arg_b = static_cast<int32_t>(ani_arg_b);

       // 调用 C++ 实现
       int32_t cpp_result = ::package_name::add(cpp_arg_a, cpp_arg_b);

       // 判断函数是否顺利执行
       if (::taihe::has_error()) { return ani_int{}; }

       // 返回值解析
       ani_int ani_result = static_cast<ani_int>(cpp_result);

       // 向上层返回函数调用结果
       return ani_result;
   }
   }
   ```

4. 接下来，`local::add` 函数会调用 `package_name::add` 函数，这个函数的调用会被自动转发到 C++ 实现文件中，通过 TH_EXPORT_CPP_API_add 这个宏所导出的具体实现。

   **.impl.cpp**

   ```cpp
   // C++ 实现
   int32_t add(int32_t a, int32_t b) {
     return a + b;
   }
   TH_EXPORT_CPP_API_add(add);
   ```

5. `package_name::add` 函数执行完毕后，将返回第 3 步所示的函数，如果函数实现过程中发生错误，直接返回空对象给 ets 侧函数；如果函数函数顺利实现完毕，将获取到的返回值转换为 ets 类型，返回给 ets 侧函数。
