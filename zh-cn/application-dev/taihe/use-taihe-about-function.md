# 使用Taihe进行function相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

使用Taihe进行函数相关开发时，编写Taihe IDL文件描述函数声明，就可以使得ets侧调用到C++侧的实现。

注意，在使用Taihe生成ANI桥接代码时，会在ets侧自动将所有函数的首字母转换为小写，如有需要保持函数首字母大写，可以使用`-Csts:keep-name`参数。

## 基本概念

Taihe相关代码示例

```rust
function add(a: i32, b: i32): i32;
```

以下是对应的ets代码

```typescript
// native函数对应ANI register的实现函数，函数名经过name mangling避免重名
native function _taihe_add_native(a: int, b: int): int;

// export函数提供给ets侧使用，其内部调用了native函数
export function add(a: int, b: int): int {
    return _taihe_add_native(a, b);
}
```

每个函数都会在ets侧生成native function和export function两个函数。

## 使用示例

### Taihe声明

```rust
function add(a: i32, b: i32): i32;
```

### C++实现

```cpp
int32_t add(int32_t a, int32_t b) {
  return a + b;
}

// 导出函数的具体实现
TH_EXPORT_CPP_API_add(add);
```

### ets侧使用

```typescript
let a = add(1, 2);
console.info("test add:", a);
```

Output：

```sh
test add: 3
```

## 函数调用链

以示例函数为例，当ets侧调用函数add时，它会经历如下步骤：

1. 进入自动生成的`.ets`文件中的`add`函数实现。

   **.ets**

   ```typescript
   export function add(a: int, b: int): int {
     return _taihe_add_native(a, b);
   }
   ```

2. 该`add`函数中会进一步调用进同一文件中的`_taihe_add_native`函数，该函数与生成代码中的`.ani.cpp`文件中的`local::add`函数相绑定。

   **.ets**

   ```typescript
   native function _taihe_add_native(a: int, b: int): int;
   ```

3. `local::add`函数会先解析参数，将ets对象转换为Taihe对象，然后调用C++实现函数，再将返回值由Taihe对象转换为ets对象。

   **.ani.cpp**

   ```cpp
   namespace local {
   static ani_int add([[maybe_unused]] ani_env *env, ani_int ani_arg_a, ani_int ani_arg_b) {
       // 参数类型转换
       int32_t cpp_arg_a = static_cast<int32_t>(ani_arg_a);
       int32_t cpp_arg_b = static_cast<int32_t>(ani_arg_b);

       // 调用C++实现
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

4. 接下来，`local::add`函数会调用`package_name::add`函数，这个函数的调用会被自动转发到C++实现文件中，通过TH_EXPORT_CPP_API_add这个宏所导出的具体实现。

   **.impl.cpp**

   ```cpp
   // C++实现
   int32_t add(int32_t a, int32_t b) {
     return a + b;
   }
   TH_EXPORT_CPP_API_add(add);
   ```

5. `package_name::add`函数执行完毕后，将返回第3步所示的函数，如果函数实现过程中发生错误，直接返回空对象给ets侧函数；如果函数函数顺利实现完毕，将获取到的返回值转换为ets类型，返回给ets侧函数。
