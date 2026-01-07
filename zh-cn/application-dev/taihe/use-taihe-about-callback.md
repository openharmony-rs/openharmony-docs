# 使用Taihe进行Callback相关开发

## 简介

`Callback`（回调）可以理解为把一个函数作为参数传给另一个函数，在特定的事件发生时再调用它，在 Taihe 中使用 `({param_type}) => {return_type}` 来描述作为参数的函数。

## 基本概念

| Taihe描述                         | C++ 侧类型                    | C++ 侧类型（作为参数时）           |
| --------------------------------- | ----------------------------- | ---------------------------------- |
| `({param_type}) => {return_type}` | `taihe::callback<R(Args...)>` | `taihe::callback_view<R(Args...)>` |

`Callback` 对应 Taihe C++ 实现侧的 `taihe::callback<R(Args...)>`，Taihe 支持 `Callback` 对象的比较。

`callback` 在 Taihe C++ 实现侧有 view 类型（视图类型）和非 view 类型（持有者类型），其中，view 类型的语义是不拥有所有权，只是对现有类型的引用，而非 view 类型则是拥有当前类型的所有权。

建议**只有**在**必须获取所有权**的情况下使用 `taihe::callback<R(Args...)>`，其他情况使用``taihe::callback_view<R(Args...)>``。

## 使用示例

接下来介绍使用 Taihe 进行 `Callback` 开发的流程

以下示例介绍五种情况：无参数无返回值、有参数无返回值、有参数有返回值、以 struct 作为参数和返回值、`Callback` 对象比较。

### 在 Taihe 文件中声明

```rust
// 无参数无返回值
function cbVoidVoid(f: () => void): void;
// 有参数无返回值
function cbIVoid(f: (a: i32) => void): void;
// 有参数有返回值
function cbStrStr(f: (a: String) => String): String;

struct Person {
  name: String;
  age: i32;
}
// 以 struct 作为参数和返回值
function cbStruct(f: (data: Person) => Person): void;

// Callback 对象比较
function cbCompare(cb1: () => String, cb2: () => String): bool;
```

### C++ 侧 实现声明的接口

```cpp
// 无参数无返回值
void cbVoidVoid(taihe::callback_view<void()> f) {
    f();
}
// 有参数无返回值
void cbIVoid(taihe::callback_view<void(int32_t)> f) {
    f(1);
}
// 有参数有返回值
string cbStrStr(taihe::callback_view<string(string_view)> f) {
    taihe::string out = f("hello");
    return "hello";
}
// 以 struct 作为参数和返回值
void cbStruct(taihe::callback_view<::callback::Person(::callback::Person const&)> f) {
    ::callback::Person result = f(::callback::Person{"Tom", 18});
    std::cout<< result.name << " " << result.age << std::endl;
    return;
}
// Callback 对象比较
bool cbCompare(taihe::callback_view<string()> cb1, taihe::callback_view<string()> cb2) {
    return cb1 == cb2 ? true : false;
}
```

### 生成 `callback.ets`

```typescript
native function _taihe_cbVoidVoid_native(f: (() => void)): void;
native function _taihe_cbIVoid_native(f: ((a: int) => void)): void;
native function _taihe_cbStrStr_native(f: ((a: string) => string)): string;
native function _taihe_cbStruct_native(f: ((data: _taihe_callback.Person) => _taihe_callback.Person)): void;
native function _taihe_cbCompare_native(cb1: (() => string), cb2: (() => string)): boolean;
export function cbVoidVoid(f: (() => void)): void {
    return _taihe_cbVoidVoid_native(f);
}
export function cbIVoid(f: ((a: int) => void)): void {
    return _taihe_cbIVoid_native(f);
}
export function cbStrStr(f: ((a: string) => string)): string {
    return _taihe_cbStrStr_native(f);
}
export function cbStruct(f: ((data: _taihe_callback.Person) => _taihe_callback.Person)): void {
    return _taihe_cbStruct_native(f);
}
export function cbCompare(cb1: (() => string), cb2: (() => string)): boolean {
    return _taihe_cbCompare_native(cb1, cb2);
}
export interface Person {
    name: string;
    age: int;
}
class _taihe_Person_inner implements Person {
    name: string;
    age: int;
    constructor(
        name: string,
        age: int,
    )
    {
        this.name = name;
        this.age = age;
    }
}
function _taihe_cbVoidVoid_reverse(f: (() => void)): void {
    return cbVoidVoid(f);
}
function _taihe_cbIVoid_reverse(f: ((a: int) => void)): void {
    return cbIVoid(f);
}
function _taihe_cbStrStr_reverse(f: ((a: string) => string)): string {
    return cbStrStr(f);
}
function _taihe_cbStruct_reverse(f: ((data: _taihe_callback.Person) => _taihe_callback.Person)): void {
    return cbStruct(f);
}
function _taihe_cbCompare_reverse(cb1: (() => string), cb2: (() => string)): boolean {
    return cbCompare(cb1, cb2);
}
```

### ets 侧使用

```typescript
// 无参数无返回值
callback_lib.cbVoidVoid(() => {
    console.log("void input void output callback!");
});
// 输出：
// void input void output callback!
```

```typescript
// 有参数无返回值
callback_lib.cbIVoid((a: int) => {
    console.log("int input void output callback! input is: ", a);
});
// 输出：
// int input void output callback! input is:  1
```

```typescript
// 有参数有返回值
let result = callback_lib.cbStrStr((a: string) => {
    console.log("param a is: ", a);
    return "my return value";
});
console.log("global function output: ", result);
// 输出：
// param a is:  hello
// global function output:  hello
```

```typescript
// 以 struct 作为参数和返回值
callback_lib.cbStruct((a: callback_lib.Person) => {
    let person: callback_lib.Person = {name: a.name + " Swift", age: a.age + 18 }; 
    return person;
});
// 输出：
// Tom Swift 36
```

```typescript
// Callback 对象比较
// 定义两个 callback
let callback_1 = () => {
    console.log("Callback 1 executed");
    return "Callback 1 result";
};
let callback_2 = () => {
    console.log("Callback 2 executed");
    return "Callback 2 result";
};
// 使用函数进行比较
console.log("same callback: " + callback_lib.cbCompare(callback_1, callback_1))
console.log("different callback: " + callback_lib.cbCompare(callback_1, callback_2))
// 输出
// same callback: true
// different callback: false
```

## C++ 侧 taihe::callback<R(Args...)> 介绍

### 1. 创建回调

使用 `taihe::make_holder` 创建一个持有回调的对象。以下示例展示了创建一个处理字符串输入并返回结果的回调：
```cpp
#include <taihe/callback.hpp>

struct MyProcessor {
    taihe::string prefix;

    MyProcessor(taihe::string_view p) : prefix(p) {}
    
    taihe::string operator()(taihe::string_view input) {
        return prefix + ": " + input;
    }
};

taihe::callback<taihe::string(taihe::string_view)> callback = \
    taihe::make_holder<
        MyProcessor,
        taihe::callback<taihe::string(taihe::string_view)>
    >("Result");
```

> **💡 注意：**
>
> `taihe::callback` 的参数和返回值类型都必须是 Taihe 支持的 C++ 投影类型，例如参数类型可以是 `taihe::string_view`、`taihe::vector_view<T>`、`int32_t` 等，返回值类型可以是 `taihe::string`、`float` 等等，但不能是其他 C++ 的原生类型（如 `std::string`、`std::vector`）。这是因为 Taihe 的回调中需要储存 ABI 稳定的函数指针，而 C++ 的原生类型作为函数参数或返回值时，调用约定（Calling convention）不能被保证，因此无法在不同编译器或不同版本的编译器之间保持 ABI 兼容。

### 2. 调用回调

回调可以像普通函数一样调用，可使用 `operator()` 或直接调用：
```cpp
// 直接调用
taihe::string result = callback("Hello");
```

### 3. 进阶：函数闭包和接口的关系

Taihe 函数闭包和接口的底层结构几乎相同，它们的 ABI 结构都是一个数据指针加一个虚函数指针/虚表指针。函数闭包可以视为一种特殊的接口类型，具备大多数接口的特性，例如，你可以将一个 C++ 类同时实现为接口和函数闭包：
```cpp
class CallableImpl {
public:
    // 实现函数调用运算符
    taihe::string operator()(taihe::string_view input);

    // 实现接口方法
    taihe::string getId() const;
    double calculateArea() const;

    // 其他方法
    void myOtherMethod();
};

auto callableImpl =
    taihe::make_holder<
        CallableImpl,
        taihe::callback<taihe::string(taihe::string_view)>,
        taihe::weak::IShape
    >("CallableImpl");

callableImpl->getId();  // 调用接口方法
callableImpl->calculateArea();  // 调用接口方法

callableImpl->myOtherMethod();  // 调用其他方法，这也是合法的，因为 callableImpl 的实际类型为
                            // taihe::impl_holder<
                            //     CallableImpl,
                            //     taihe::callback<taihe::string(taihe::string_view)>,
                            //     taihe::weak::IShape
                            // >

callableImpl("Hello");  // 当作函数闭包调用，taihe::impl_holder 重载了 operator() 方法

taihe::callback<taihe::string(taihe::string_view)> cb = callableImpl;  // 转换为函数闭包
taihe::weak::IShape shape = callableImpl;  // 转换为接口
```

并且你可以尝试将函数闭包动态转换为接口：
```cpp
auto cb_as_shape = taihe::weak::IShape(cb);  // 尝试将函数闭包转换为接口
assert(not cb_as_shape.is_error());
```

但是，函数闭包类型不具备 IID（Interface Identifier，接口标识符），因此不能从其他接口转换为函数闭包
```cpp
auto shape_as_cb = taihe::callback_view<taihe::string(taihe::string_view)>(cb_as_shape);  // 错误：无法从接口转换为函数闭包
```
