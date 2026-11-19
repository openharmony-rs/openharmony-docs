# 使用Taihe进行异常相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @k1ngqaquuu-->

## 简介

在Taihe中，为处理跨语言过程中的错误传递，提供了一套异常处理方式。除非使用[`@noexcept`注解](#noexcept注解)，否则所有函数、方法和回调的返回值都是`taihe::expected`类型，包含成功值或错误信息。

## 基本概念

### `taihe::error`

`taihe::error`是Taihe C++投影中用于表示错误的基本类型，其包含以下属性：

- **`message`**：错误消息（`string`），描述错误详情
- **`code`**：错误码（`int32_t`），默认为0

**C++中的使用方式**

```cpp
// 创建错误对象
taihe::error err("error message");                    // code默认为0
taihe::error err_with_code("error message", 5);       // code为5

// 访问错误属性
taihe::string msg = err.message();                    // 获取错误消息
int32_t code = err.code();                            // 获取错误码
```

### `taihe::expected`

`taihe::expected<T, taihe::error>`是Taihe C++投影中用于表示一个可能成功也可能失败的操作结果的类型。

- **成功状态**：包含一个类型为`T`的值
- **失败状态**：包含一个类型为`taihe::error`的错误

**C++中的使用方式**

```cpp
taihe::expected<taihe::string, taihe::error> toString(int32_t a) {
    if (a < 0) {
        // 通过taihe::unexpected(error)返回错误
        return taihe::unexpected(taihe::error("Negative value is not allowed", 1));
    }
    // 直接返回成功结果
    return taihe::to_string(a);
}

taihe::expected<void, taihe::error> mayFail(bool fail) {
    if (fail) {
        return taihe::unexpected(taihe::error("Operation failed", 100));
    }
    // 对于taihe::expected<void, taihe::error>类型，需使用{}表示成功返回的空值
    return {};
}

// 调用返回taihe::expected的函数并处理结果
taihe::expected<taihe::string, taihe::error> result = toString(5);
if (!result.has_value()) {  // 通过has_value()检查是否有错误
    // 发生错误时，可通过error()获取错误
    taihe::error err = std::move(result.error());
} else {
    // 调用成功时，可通过解引用获取成功结果
    taihe::string value = std::move(*result);
    // 也可以使用value()获取成功结果，下面这行与上面的解引用写法是等价的
    // taihe::string value = std::move(result.value());
}
```

当函数或方法未使用`@noexcept`注解，且`taihec`命令未开启`-C noexcept-all`选项时，在Taihe IDL中声明的函数、方法或回调，则C++侧的返回值将默认使用这种类型：

**Taihe声明代码**

```rust
function toString(a: i32): String;
```

**对应的C++声明**

```cpp
taihe::expected<taihe::string, taihe::error> toString(int32_t a);
```

此外，`taihe::expected`也用于表示异步操作完成后的结果，见[使用Taihe进行底层异步相关开发](use-taihe-about-async-types.md)

### `@noexcept`注解

对于确定不会抛出异常的函数或方法，可以使用`@noexcept`注解标记。这会告诉编译器该函数不会抛出异常，因此在生成的C++代码中不会使用`taihe::expected`来包装返回值，而是直接返回原始类型的值。

此外，如果在`taihec`命令中开启了`-C noexcept-all`选项，则所有函数、方法和回调都会被视为`@noexcept`，从而在C++侧的返回值中不使用`taihe::expected`。

**Taihe声明代码**

```rust
@noexcept function toStringNoexcept(a: i32): String;
```

**生成的C++代码**

```cpp
taihe::string toStringNoexcept(int32_t a);
```

## 使用示例

### Taihe声明

```rust
// 普通函数和noexcept函数的声明示例
function toString(a: i32): String;
@noexcept function toStringNoexcept(a: i32): String;

// 普通接口方法和noexcept接口方法的声明示例
interface Foo{
    getValue(a: i32): i32;
    @noexcept getValueWithDefault(a: i32, d: i32): i32;
}
function createFoo(initializeValues: Array<i32>): Foo;

// 普通回调和noexcept回调的声明示例
function invokeCallback(f: () => void): void;
function invokeNoexceptCallback(f: @noexcept () => void): void;
```

### C++实现

```cpp
// 实现普通的全局函数
taihe::expected<taihe::string, taihe::error> toString(int32_t a)
{
    if (a < 0) {
        // 发生错误的情况
        return taihe::unexpected(taihe::error("Negative value is not allowed", 1));
    }
    // 正常返回结果
    return taihe::to_string(a);
}

// 实现noexcept的全局函数
taihe::string toStringNoexcept(int32_t a)
{
    return taihe::to_string(a);
}

class FooImpl {
    taihe::array<int32_t> values_;

public:
    FooImpl(taihe::array_view<int32_t> values) : values_(values) {}

    // 实现普通的接口方法
    taihe::expected<int32_t, taihe::error> getValue(int32_t a)
    {
        if (a < 0 || a >= values_.size()) {
            // 发生错误的情况
            return taihe::unexpected(taihe::error("Index out of range", 2));
        }
        // 正常返回结果
        return values_[a];
    }

    // 实现noexcept的接口方法
    int32_t getValueWithDefault(int32_t a, int32_t d)
    {
        if (a < 0 || a >= values_.size()) {
            return d;
        }
        return values_[a];
    }
};

taihe::expected<::hello::Foo, taihe::error> createFoo(taihe::array_view<int32_t> initializeValues)
{
    return taihe::make_holder<FooImpl, ::hello::Foo>(initializeValues);
}

taihe::expected<void, taihe::error> invokeCallback(taihe::callback_view<taihe::expected<void, taihe::error>()> f)
{
    // 调用未标记为noexcept的回调时，必须检查返回的错误结果
    taihe::expected<void, taihe::error> res = f();
    if (!res.has_value()) {  // 通过has_value()检查是否有错误
        std::cerr << "Caught error in C++"
                  << ", message: "
                  << res.error().message()
                  << ", code: "
                  << res.error().code()
                  << ", forwarding to the ETS caller..."
                  << std::endl;
        return taihe::unexpected(std::move(res.error()));  // 将错误结果继续返回给上层调用者
    }
    return {};
}

taihe::expected<void, taihe::error> invokeNoexceptCallback(taihe::callback_view<void()> f)
{
    // 调用标记为noexcept的回调时，不需要检查返回的错误结果
    f();
    return {};
}
```

### ets的使用

```typescript
// 普通全局函数
try {
    let res = hello.toString(-5);
    console.info("result:", res);
} catch (error) {
    let businessError = error as BusinessError;
    console.info("Caught error in ETS, code:", businessError.code, "message:", businessError.message);
}

// noexcept全局函数
let resNoexcept = hello.toStringNoexcept(-5);
console.info("result:", resNoexcept);


let x = hello.createFoo([1, 2, 3]);

// 普通接口方法
try {
    let result = x.getValue(10);
    console.info("result:", result);
} catch (error) {
    let businessError = error as BusinessError;
    console.info("Caught error in ETS, code:", businessError.code, "message:", businessError.message);
}

// noexcept接口方法
let resultNoexcept = x.getValueWithDefault(10, 42);
console.info("result:", resultNoexcept);


// 普通回调
try {
    hello.invokeCallback(() => {
        console.info("Callback is invoked");
        // 在普通回调中可以抛出异常
        throw new BusinessError(1001, new Error("Callback error"));
    });
} catch (error) {
    let businessError = error as BusinessError;
    console.info("Caught error in ETS, code:", businessError.code, "message:", businessError.message);
}

// noexcept回调
hello.invokeNoexceptCallback(() => {
    console.info("Noexcept callback is invoked");
    // 在noexcept回调中不允许抛出异常
    // 例如下面这行代码在运行时会直接导致程序终止，而不会在C++层被捕获
    // throw new BusinessError(1002, new Error("Noexcept callback error"));
});
```

输出结果如下：

```text
Caught error in ETS, code: 1, message: Negative value is not allowed
result: -5

Caught error in ETS, code: 2, message: Index out of range
result: 42

Callback is invoked
Caught error in C++, message: Callback error, code: 1001, forwarding to the ETS caller...
Caught error in ETS, code: 1001, message: Callback error
Noexcept callback is invoked
```
