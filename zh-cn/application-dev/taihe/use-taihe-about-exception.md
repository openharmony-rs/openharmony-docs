# 使用Taihe进行异常相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

在Taihe中，为处理跨语言过程中的错误传递，提供了一套异常处理方式。所有函数、方法和回调的返回值都是`::taihe::expected`类型，包含成功值或错误信息。

## 基本概念

### ::taihe::expected

`::taihe::expected<T, ::taihe::error>`是一个类型安全的错误处理容器，用于表示可能成功或失败的操作结果。

- **成功状态**：包含一个类型为`T`的值
- **失败状态**：包含一个类型为`::taihe::error`的错误

**Taihe声明代码**

```rust
function sayHello(a: i32): i32;
```

**生成的C++代码**

```cpp
taihe::expected<int32_t, taihe::error> sayHello(int32_t a);
```

### ::taihe::error

`::taihe::error`是Taihe中表示错误的类型，包含以下属性：

- **message**：错误消息（string），描述错误详情
- **code**：错误码（int32_t），默认为0

**C++代码示例**

```cpp
// 创建错误对象
taihe::error err("error message");                    // code默认为0
taihe::error err_with_code("error message", 5);      // code为5

// 访问错误属性
string msg = err.message();                           // 获取错误消息
int32_t code = err.code();                            // 获取错误码
```

### @noexcept注解

对于确定不会抛出异常的函数，可以使用`@noexcept`注解标记。这将启用生成代码优化，消除错误处理开销。

**Taihe声明代码**

```rust
@noexcept function sayHello(a: i32): i32;
```

**生成的C++代码**

```cpp
int32_t sayHello(int32_t a);
```

## 使用示例

### Taihe声明

```rust
function sayHello_ii(a: i32): i32;
interface Foo{
    bar(): void;
    @noexcept bar_ss(a: String): String;
}
function createFoo(): Foo;
function callcb(f: () => void): void;
@noexcept function concat(a: String, b: String): String;
function test_cb_v(f: @noexcept () => void): void;
```

### C++实现

```cpp
class FooImpl {
public:
    // 实现普通的接口方法
    ::taihe::expected<void, taihe::error> bar()
    {
        return ::taihe::expected<void, ::taihe::error>(::taihe::unexpect, "A Error in bar", 12);
    }

    // 实现noexpect的接口方法
    ::taihe::string bar_ss(::taihe::string a)
    {
        return a + "_cpp";
    }
};

// 实现普通的全局函数
::taihe::expected<int32_t, taihe::error> sayHello_ii(int32_t a)
{
    if (a >= 10) {
        return ::taihe::unexpected<::taihe::error>(::taihe::error("Index out of range", 10));
    }
    return a;
}

::taihe::expected<::hello::Foo, ::taihe::error> createFoo()
{
    return taihe::make_holder<FooImpl, ::hello::Foo>();
}

::taihe::expected<void, ::taihe::error> callcb(::taihe::callback_view<::taihe::expected<void, ::taihe::error>()> f)
{
    // 调用普通的回调
    ::taihe::expected<void, ::taihe::error> res = f();
    if (!res.has_value()) {
        std::cout << "catch error in cpp callcb: " << res.error().message() << ", code: " << res.error().code(0)
                  << std::endl;
    }
    return res;
}

::taihe::expected<void, ::taihe::error> test_cb_v(::taihe::callback_view<void()> f)
{
    std::cout << "CPP impl test_cb_v " << std::endl;
    // 调用noexcept的回调
    f();
    return {};
}

// 实现noexcept的全局函数
taihe::string ohos_concat_str(taihe::string_view a, taihe::string_view b)
{
    return a + b;
}
```

### ets的使用

```typescript

// 普通全局函数
let error_code: number = 0;
let errorMsg: string = "";
try {
    hello.sayHello_ii(10);
} catch (error) {
    errorMsg = error.toString();
    error = error as BusinessError
    error_code = error.code
    console.info("error code: ", error_code, "error message: ", errorMsg);
}

// noexcept全局函数
let res: string = "";
try {
    res = hello.concat("a", "b");
    console.info("result: ", res);
} catch (error) {
    console.info("Error in testConcat")
}

let x = hello.createFoo();

// 普通接口方法
let error_code: number = 0;
let errorMsg: string = "";
try {
    x.bar();
} catch (error) {
    errorMsg = error.toString();
    error = error as BusinessError
    error_code = error.code
    console.info("error code: ", error_code, "error message: ", errorMsg);
}

// noexcept接口方法
let result: string = "";
try {
    result = x.bar_ss("call_foo_bar_string");
    console.info("result: ", result);
} catch (error) {
    console.info("Error in testFooBarWithString")
}

// 普通回调
let error_code: number = 0;
let errorMsg: string = "";
try {
    hello.callcb(() => {
        console.info("Callback called");
        throw new BusinessError(1001, new Error("Callback error"));
    });
} catch (error) {
    errorMsg = error.toString();
    error = error as BusinessError
    error_code = error.code
    console.info("error code: ", error_code, "error message: ", errorMsg);
}

// noexcept回调
try {
    hello.test_cb_v(() => {
        console.info("test_cb_v in ets");
    });
} catch (error) {
    console.info("Error in testCallbackVoid")
}
```

输出结果如下：

```sh
error code:  10 error message:  Error: Index out of range
result:  ab
error code:  12 error message:  Error: A Error in bar
result:  call_foo_bar_string_cpp
Callback called
catch error in cpp callcb: Callback error, code: 1001
error code:  1001 error message:  Error: Callback error
CPP impl test_cb_v 
test_cb_v in ets
```
