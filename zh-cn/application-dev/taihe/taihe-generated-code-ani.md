# 深入解析Taihe生成的代码（ANI桥接层）

本文档旨在介绍Taihe ANI后端生成的代码和函数调用链，帮助用户理解如何在自己的代码中使用并调试这些自动生成的接口。

## ⚠️ 特别注意 ⚠️

***自动生成的ets文件中，所有以`_taihe_`为前缀的函数和变量，均为Taihe的内部接口，我们不会保证这些接口的稳定性，因此，请不要在用户代码或注入代码中直接调用这些接口！！！***

## 生成代码的目录结构解析

以下面的Taihe IDL文件为例，来说明生成代码的目录结构和文件内容。
```rust
// File: example/idl/my.package.ohidl
struct Data {
    a: i32;
    b: String;
}
union Result {
    ok: i32;
    err: String;
}
interface IFoo {
    init(): void;
}
interface IBar: IFoo {
    process(data: Data): Result;
}
function processWithBar(bar: IBar, data: Data): Result;
```

生成的代码目录结构如下：
```
test/xxx/generated/
├── include
│   ├── my.package.*.abi.{0,1,2}.h
│   ├── my.package.abi.h
│   ├── my.package.*.proj.{0,1,2}.hpp
│   ├── my.package.proj.hpp
│   ├── my.package.impl.hpp
│   ├── my.package.user.hpp
│   ├── my.package.*.ani.{0,1}.hpp
│   └── my.package.ani.hpp
├── src
│   ├── my.package.abi.c
│   └── my.package.ani.cpp
├── my.package.ets
└── temp
    ├── ani_constructor.cpp
    ├── my.package.*.template.cpp
    ├── my.package.*.template.hpp
    └── my.package.impl.cpp
```

其中，`*.abi.h`, `*.proj.hpp`, `*.user.hpp`, `*.impl.hpp`的说明可参考[Taihe ABI层及C++层生成代码解析](./taihe-generated-code-cpp.md)。

ANI生成的相关文件说明如下：
- `include/my.package.*.ani.{0,1}.hpp`：包含了所有`my.package.ohidl`中定义的结构体、枚举、接口等数据类型在C++和ANI间相互转换的函数。`*.ani.0.hpp`包含转换函数的前向声明，`*.ani.1.hpp`包含这些函数的具体实现。
- `include/my.package.ani.hpp`：包含了`my::package::ANI_Register`函数的声明，该函数用于将`my.package.ohidl`中定义的所有函数注册到ANI虚拟机中。
- `src/my.package.ani.cpp`：包含了所有`my.package.ohidl`中定义的函数的native侧桥接代码，以及`my::package::ANI_Register`函数的实现。
- `my.package.ets`：包含了所有`my.package.ohidl`中定义的数据类型和函数的ArkTS侧桥接代码。
- `temp/ani_constructor.cpp`：`ANI_Constructor`函数的实现模板代码，其中调用了`ANI_Register`函数，将所有函数的native侧实现注册到ANI虚拟机中。
- `temp/my.package.*.template.{cpp,hpp}`：`interface`类型的实现模板代码。

## 基本函数的正向调用链

假设我们有一个Taihe IDL文件`my.package.ohidl`，其中定义了两个简单的结构体`MyParam`和`MyResult`，以及一个函数`process`：
```rust
struct MyParam {
    a: i32;
    b: i32;
}

struct MyResult {
    sum: i32;
}

function process(param: MyParam): MyResult;
```

当在上层代码`user/main.ets`中调用该`process`函数时，它会经历如下步骤：

1. `process`函数内部会自动调用同一文件中的`_taihe_process_native`函数，该函数是一个native函数，它与`generated/src`目录下的`my.package.ani.cpp`文件中的`local::process`函数相绑定。

    **generated/my.package.ets**
    ```typescript
    // 这是暴露给ArkTS用户的顶层函数。
    export function process(param: _taihe_my_package.MyParam): _taihe_my_package.MyResult {
        // 内部调用一个native函数，将请求转发到C++ Native层。
        return _taihe_process_native(param);
    }

    // 声明一个native函数，其实现由C++提供。
    // 这个函数是ArkTS和C++之间的直接桥梁。
    native function _taihe_process_native(param: _taihe_my_package.MyParam): _taihe_my_package.MyResult;
    ```

2. `local::process`函数会先处理参数，将`MyParam`在上层对应的JS对象（在ANI中的类型为ani_object）转换为taihe自动生成的`my::package::MyParam`结构体对象，这一转换的具体逻辑通常会实现在`generated/include/my.package.MyParam.ani.1.hpp`文件中，对应的转换函数为`taihe::from_ani<my::package::MyParam>`。

    **generated/src/my.package.ani.cpp**
    ```cpp
    namespace local {
    // 这是C++层的桥接函数，与ArkTS中的`_taihe_process_native`绑定。
    static ani_object process([[maybe_unused]] ani_env *env, ani_object ani_arg_param) {
        // 1. 将从ArkTS传入的ani_object参数转换为C++层的my::package::MyParam结构体。
        ::my::package::MyParam cpp_arg_param = ::taihe::from_ani<::my::package::MyParam>(env, ani_arg_param); // here
        // 2. 调用真正的C++业务逻辑实现。
        ::my::package::MyResult cpp_result = ::my::package::process(cpp_arg_param);
        // 检查在业务逻辑调用中是否发生了错误。
        if (::taihe::has_error()) { return ani_object{}; }
        // 3. 将C++业务逻辑返回的MyResult结构体转换为ArkTS可以理解的ani_object。
        ani_object ani_result = ::taihe::into_ani<::my::package::MyResult>(env, cpp_result);
        // 4. 将转换后的ani_object返回给ArkTS层。
        return ani_result;
    }
    }
    ```

    **generated/include/my.package.MyParam.ani.1.hpp**
    ```cpp
    // from_ani_t的特化版本，定义了如何将ani_object转换为C++的MyParam结构体。
    inline ::my::package::MyParam taihe::from_ani_t<::my::package::MyParam>::operator()(ani_env* env, ani_object ani_obj) const {
        // 从ArkTS对象中获取名为'a'的属性值。
        ani_int ani_field_a;
        env->Object_CallMethod_Int(ani_obj, TH_ANI_FIND_CLASS_METHOD(env, "my.package.MyParam", "<get>a", nullptr), reinterpret_cast<ani_int*>(&ani_field_a));
        int32_t cpp_field_a = (int32_t)ani_field_a;
        // 从ArkTS对象中获取名为'b'的属性值。
        ani_int ani_field_b;
        env->Object_CallMethod_Int(ani_obj, TH_ANI_FIND_CLASS_METHOD(env, "my.package.MyParam", "<get>b", nullptr), reinterpret_cast<ani_int*>(&ani_field_b));
        int32_t cpp_field_b = (int32_t)ani_field_b;
        // 使用获取到的字段值构造并返回C++结构体对象。
        return ::my::package::MyParam{std::move(cpp_field_a), std::move(cpp_field_b)};
    }
    ```

3. 接下来，`local::process`函数会调用`my::package::process`函数，该调用会自动转发到接口作者在C++实现文件中通过`TH_EXPORT_CPP_API_process`宏导出的具体实现。

    **generated/src/my.package.ani.cpp**
    ```cpp
    namespace local {
    static ani_object process([[maybe_unused]] ani_env *env, ani_object ani_arg_param) {
        ::my::package::MyParam cpp_arg_param = ::taihe::from_ani<::my::package::MyParam>(env, ani_arg_param);
        // 调用由TH_EXPORT_CPP_API_process宏导出的、用户自己编写的C++业务逻辑函数。
        ::my::package::MyResult cpp_result = ::my::package::process(cpp_arg_param); // here
        if (::taihe::has_error()) { return ani_object{}; }
        ani_object ani_result = ::taihe::into_ani<::my::package::MyResult>(env, cpp_result);
        return ani_result;
    }
    }
    ```

4. `my::package::process`函数执行完毕后，拿到`MyResult`结构体对象，并将其转换为ani_object对象，与第3步类似，该转换的具体逻辑会实现在`generated/include/my.package.MyResult.ani.1.hpp`文件中的`taihe::into_ani<my::package::MyResult>`函数里。

    **generated/src/my.package.ani.cpp**
    ```cpp
    static ani_object process([[maybe_unused]] ani_env *env, ani_object ani_arg_param) {
        ::my::package::MyParam cpp_arg_param = ::taihe::from_ani<::my::package::MyParam>(env, ani_arg_param);
        ::my::package::MyResult cpp_result = ::my::package::process(cpp_arg_param);
        if (::taihe::has_error()) { return ani_object{}; }
        // 将C++的返回结果cpp_result转换为ArkTS的ani_object。
        ani_object ani_result = ::taihe::into_ani<::my::package::MyResult>(env, cpp_result); // here
        return ani_result;
    }
    ```

    **generated/include/my.package.MyResult.ani.1.hpp**
    ```cpp
    // into_ani_t的特化版本，定义了如何将C++的MyResult结构体转换为ani_object。
    inline ani_object taihe::into_ani_t<::my::package::MyResult>::operator()(ani_env* env, ::my::package::MyResult cpp_obj) const {
        // 从C++结构体中获取字段值。
        ani_int ani_field_sum = (int32_t)cpp_obj.sum;
        ani_object ani_obj;
        // 在ArkTS虚拟机中创建一个新的`_taihe_MyResult_inner`对象，
        // 并将C++结构体的字段值作为构造函数参数传入。
        env->Object_New(TH_ANI_FIND_CLASS(env, "my.package._taihe_MyResult_inner"), TH_ANI_FIND_CLASS_METHOD(env, "my.package._taihe_MyResult_inner", "<ctor>", nullptr), &ani_obj, ani_field_sum);
        return ani_obj;
    }
    ```

5. 最后`local::process`函数的返回值会被传递回上层的`_taihe_process_native`函数，进而返回到`process`函数，最终返回到用户代码中。

## 反向调用链

反向调用指的是从C++ Native代码回调到上层的JS代码。例如：
```rust
interface MyCallback {
    onResult(result: MyParam): MyResult;
}

function processWithCallback(myCallback: MyCallback): void;
```

在这种情况下，回调的过程如下：
1. 首先，当`myCallback`对象从上层传入时，它会从JS对象被封装成一个Taihe代理对象。你可以在`generated/include/my.package.MyCallback.ani.1.hpp`文件中的函数`taihe::from_ani<test::MyCallback>`里找到对应的封装/转换逻辑（如果是`() => void`这样的匿名函数，则应在`generated/src/my.package.ani.cpp`文件中找到对应的转换逻辑）。这一封装过程会将Taihe代理对象上的`onResult`方法与ets代码中`interface MyCallback`内由Taihe自动生成的`_taihe_onResult_revert`方法相绑定。

    **generated/src/my.package.MyCallback.ani.1.hpp**
    ```cpp
    // from_ani_t的特化版本，定义了如何将一个ArkTS回调对象（ani_object）转换为C++可调用的接口代理对象。
    inline ::my::package::MyCallback taihe::from_ani_t<::my::package::MyCallback>::operator()(ani_env* env, ani_object ani_obj) const {
        // 定义一个代理实现结构体，它将实现MyCallback C++接口。
        struct cpp_impl_t : ::taihe::dref_guard {
            cpp_impl_t(ani_env* env, ani_ref val) : ::taihe::dref_guard(env, val) {}
            // 这是C++ Native代码实际调用的方法。
            ::my::package::MyResult onResult(::my::package::MyParam const& cpp_arg_result) {
                ::taihe::env_guard guard;
                ani_env *env = guard.get_env();
                // 1. 将C++传入的参数转换为ArkTS的ani_object。
                ani_object ani_arg_result = ::taihe::into_ani<::my::package::MyParam>(env, cpp_arg_result);
                ani_object ani_result;
                // 2. 通过ANI调用ArkTS对象上的`_taihe_onResult_revert`方法，实现反向调用。
                env->Object_CallMethod_Ref(static_cast<ani_object>(this->ref), TH_ANI_FIND_CLASS_METHOD(env, "my.package.MyCallback", "_taihe_onResult_revert", nullptr), reinterpret_cast<ani_ref*>(&ani_result), ani_arg_result);
                // 3. 将ArkTS回调返回的结果（ani_object）转换回C++类型。
                ::my::package::MyResult cpp_result = ::taihe::from_ani<::my::package::MyResult>(env, ani_result);
                // 4. 将C++结果返回给Native层的调用者。
                return cpp_result;
            }
            uintptr_t getGlobalReference() const {
                return reinterpret_cast<uintptr_t>(this->ref);
            }
        };
        // 创建并返回一个持有代理实现的C++接口对象。
        return ::taihe::make_holder<cpp_impl_t, ::my::package::MyCallback, ::taihe::platform::ani::AniObject>(env, ani_obj);
    }
    ```

2. 当`myCallback->onResult`被调用时，会进入代理对象的`onResult`方法，该方法中会先将回调所需的参数`MyParam`结构体对象转换为ani_object对象，这一转换过程和正向调用链中的第5步类似。

    **generated/src/my.package.MyCallback.ani.1.hpp**
    ```cpp
    inline ::my::package::MyCallback taihe::from_ani_t<::my::package::MyCallback>::operator()(ani_env* env, ani_object ani_obj) const {
        struct cpp_impl_t : ::taihe::dref_guard {
            cpp_impl_t(ani_env* env, ani_ref val) : ::taihe::dref_guard(env, val) {}
            ::my::package::MyResult onResult(::my::package::MyParam const& cpp_arg_result) {
                ::taihe::env_guard guard;
                ani_env *env = guard.get_env();
                // 在反向调用前，将C++参数cpp_arg_result转换为ArkTS对象ani_arg_result。
                ani_object ani_arg_result = ::taihe::into_ani<::my::package::MyParam>(env, cpp_arg_result); // here
                ani_object ani_result;
                env->Object_CallMethod_Ref(static_cast<ani_object>(this->ref), TH_ANI_FIND_CLASS_METHOD(env, "my.package.MyCallback", "_taihe_onResult_revert", nullptr), reinterpret_cast<ani_ref*>(&ani_result), ani_arg_result);
                ::my::package::MyResult cpp_result = ::taihe::from_ani<::my::package::MyResult>(env, ani_result);
                return cpp_result;
            }
            uintptr_t getGlobalReference() const {
                return reinterpret_cast<uintptr_t>(this->ref);
            }
        };
        return ::taihe::make_holder<cpp_impl_t, ::my::package::MyCallback, ::taihe::platform::ani::AniObject>(env, ani_obj);
    }
    ```

    **generated/include/my.package.MyParam.ani.1.hpp**
    ```cpp
    // into_ani_t的特化版本，定义了如何将C++的MyParam结构体转换为ani_object。
    inline ani_object taihe::into_ani_t<::my::package::MyParam>::operator()(ani_env* env, ::my::package::MyParam cpp_obj) const {
        ani_int ani_field_a = (int32_t)cpp_obj.a;
        ani_int ani_field_b = (int32_t)cpp_obj.b;
        ani_object ani_obj;
        // 在ArkTS虚拟机中创建一个新的`_taihe_MyParam_inner`对象，并传入字段值。
        env->Object_New(TH_ANI_FIND_CLASS(env, "my.package._taihe_MyParam_inner"), TH_ANI_FIND_CLASS_METHOD(env, "my.package._taihe_MyParam_inner", "<ctor>", nullptr), &ani_obj, ani_field_a, ani_field_b);
        return ani_obj;
    }
    ```

3. 接下来，代理对象上的`onResult`方法会通过ANI的FunctionCall调用进上层的`_taihe_onResult_revert`方法。

    **generated/src/my.package.MyCallback.ani.1.hpp**
    ```cpp
    inline ::my::package::MyCallback taihe::from_ani_t<::my::package::MyCallback>::operator()(ani_env* env, ani_object ani_obj) const {
        struct cpp_impl_t : ::taihe::dref_guard {
            cpp_impl_t(ani_env* env, ani_ref val) : ::taihe::dref_guard(env, val) {}
            ::my::package::MyResult onResult(::my::package::MyParam const& cpp_arg_result) {
                ::taihe::env_guard guard;
                ani_env *env = guard.get_env();
                ani_object ani_arg_result = ::taihe::into_ani<::my::package::MyParam>(env, cpp_arg_result);
                ani_object ani_result;
                // 通过ANI调用，执行ArkTS对象上的`_taihe_onResult_revert`方法。
                env->Object_CallMethod_Ref(static_cast<ani_object>(this->ref), TH_ANI_FIND_CLASS_METHOD(env, "my.package.MyCallback", "_taihe_onResult_revert", nullptr), reinterpret_cast<ani_ref*>(&ani_result), ani_arg_result); // here
                ::my::package::MyResult cpp_result = ::taihe::from_ani<::my::package::MyResult>(env, ani_result);
                return cpp_result;
            }
            uintptr_t getGlobalReference() const {
                return reinterpret_cast<uintptr_t>(this->ref);
            }
        };
        return ::taihe::make_holder<cpp_impl_t, ::my::package::MyCallback, ::taihe::platform::ani::AniObject>(env, ani_obj);
    }
    ```

4. `_taihe_onResult_revert`方法会进一步调用上层JS对象上的`onResult`方法，执行完毕后拿到返回值（如果有），然后回到下层。

    **generated/my.package.ets**
    ```typescript
    // 这是用户需要实现的ArkTS接口。
    export interface MyCallback {
        // 用户需要实现这个方法来处理回调。
        onResult(result: _taihe_my_package.MyParam): _taihe_my_package.MyResult;

        // 这是Taihe自动生成的内部反向调用入口。
        // C++代理对象会调用这个方法。
        _taihe_onResult_revert(result: _taihe_my_package.MyParam): _taihe_my_package.MyResult {
            // 该方法内部会调用用户实现的onResult方法。
            return this.onResult(result);
        }
    }
    ```

5. 在Taihe代理对象的`onResult`方法中再将返回值从ani_object转换为对应的C++对象（同正向调用链第3步），并返回到`myCallback->onResult`的调用处。

    **generated/src/my.package.MyCallback.ani.1.hpp**
    ```cpp
    inline ::my::package::MyCallback taihe::from_ani_t<::my::package::MyCallback>::operator()(ani_env* env, ani_object ani_obj) const {
        struct cpp_impl_t : ::taihe::dref_guard {
            cpp_impl_t(ani_env* env, ani_ref val) : ::taihe::dref_guard(env, val) {}
            ::my::package::MyResult onResult(::my::package::MyParam const& cpp_arg_result) {
                ::taihe::env_guard guard;
                ani_env *env = guard.get_env();
                ani_object ani_arg_result = ::taihe::into_ani<::my::package::MyParam>(env, cpp_arg_result);
                ani_object ani_result;
                env->Object_CallMethod_Ref(static_cast<ani_object>(this->ref), TH_ANI_FIND_CLASS_METHOD(env, "my.package.MyCallback", "_taihe_onResult_revert", nullptr), reinterpret_cast<ani_ref*>(&ani_result), ani_arg_result);
                // 将从ArkTS返回的ani_result对象转换回C++的MyResult类型。
                ::my::package::MyResult cpp_result = ::taihe::from_ani<::my::package::MyResult>(env, ani_result); // here
                return cpp_result;
            }
            uintptr_t getGlobalReference() const {
                return reinterpret_cast<uintptr_t>(this->ref);
            }
        };
        return ::taihe::make_holder<cpp_impl_t, ::my::package::MyCallback, ::taihe::platform::ani::AniObject>(env, ani_obj);
    }
    ```

    **generated/include/my.package.MyResult.ani.1.hpp**
    ```cpp
    // from_ani_t的特化版本，定义了如何将ani_object转换为C++的MyResult结构体。
    inline ::my::package::MyResult taihe::from_ani_t<::my::package::MyResult>::operator()(ani_env* env, ani_object ani_obj) const {
        // 从ArkTS对象中获取名为'sum'的属性值。
        ani_int ani_field_sum;
        env->Object_CallMethod_Int(ani_obj, TH_ANI_FIND_CLASS_METHOD(env, "my.package.MyResult", "<get>sum", nullptr), reinterpret_cast<ani_int*>(&ani_field_sum));
        int32_t cpp_field_sum = (int32_t)ani_field_sum;
        // 使用获取到的字段值构造并返回C++结构体对象。
        return ::my::package::MyResult{std::move(cpp_field_sum)};
    }
    ```
