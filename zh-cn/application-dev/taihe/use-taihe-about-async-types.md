# 使用Taihe进行底层异步相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

Taihe提供了两种异步编程模型：

1. **`@async`/`@promise`注解（高层异步）**：将同步函数在ETS侧通过`launch`能力自动包装为异步版本。C++侧的实现仍然是同步的——即C++函数只需完成计算并返回结果，无需关心异步任务的创建、调度和完成等细节，异步行为完全由自动生成的ETS代码负责。适用于C++侧逻辑本身是同步，但因为涉及耗时操作，为了避免阻塞主线程而希望在ETS侧以异步方式调用的场景。详见[使用Taihe进行高层异步相关开发](use-taihe-about-async.md)。
2. **`Future<T>`/`Completer<T>`类型（底层异步）**：可在C++和ETS之间直接传递异步结果的底层机制。与高层异步不同，底层异步机制允许在C++侧**真正地控制异步操作的执行**（如线程创建、任务调度等），并通过`taihe::completer`手动控制异步结果的发送时机；同时也支持反向场景，即C++侧调用ETS侧实现的异步接口，并通过`taihe::future`注册回调处理结果。适用于需要在C++侧实现真正的异步逻辑（如跨线程、异步I/O、进程间通信）或需要双向异步交互的场景。详见下文。

本文介绍第二种模型在ANI场景下的使用方法。

## 基本概念

### 类型映射

| Taihe类型 | C++侧类型 | 对应的ETS侧类型 |
| --- | --- | --- |
| `Completer<T>` | `taihe::completer<taihe::expected<T, taihe::error>>` | `(error: BusinessError\|null, data: T\|undefined) => void` |
| `Future<T>` | `taihe::future<taihe::expected<T, taihe::error>>` | `Promise<T>` |

`Completer<T>`和`Future<T>`在概念上通常是成对出现的，它们可以被看作一条异步管道的两端，其中`Completer<T>`是发送端，`Future<T>`是接收端。

- **`Completer<T>`**：一个一次性使用的对象，由异步结果的生产者持有，用于在异步操作完成时发送结果。
- **`Future<T>`**：一个表示异步操作结果的对象，由异步结果的消费者持有，可以注册回调，当另一端操作完成并发送结果，回调会被触发。

> `Completer<T>`和`Future<T>`在C++侧的类型映射中使用了`taihe::expected<T, taihe::error>`，该类型表示异步任务的结果既有可能是一个成功的值（`T`），也有可能是一个错误（`taihe::error`），`taihe::expected`类型的具体用法可参考[使用Taihe进行异常相关开发](use-taihe-about-exception.md)。

### 核心C++ API

通过`taihe::make_async_pair<T>()`创建一对关联的`taihe::completer<T>`和`taihe::future<T>`：

```cpp
// 创建一对关联的completer和future
auto [completer, future] = taihe::make_async_pair<taihe::expected<taihe::string, taihe::error>>();
```

在`taihe::completer<T>`上调用`complete`方法设置结果：

```cpp
// 在completer上设置成功结果
completer.complete("result_value");

// 在completer上设置错误结果
completer.complete(taihe::unexpected<taihe::error>(some_error));
```

在`taihe::future<T>`上可以注册完成回调：

```cpp
// 在future上注册完成回调
future.on_complete([](taihe::expected<taihe::string, taihe::error>&& result) {
    if (result) {
        // 处理成功结果
        std::cout << "Got result: " << result.value() << std::endl;
    } else {
        // 处理错误结果
        std::cerr << "Got error: " << result.error().message() << std::endl;
    }
});
```

> 注意：在**正向异步**（C++侧执行异步操作，并在任务完成时将结果推送给ETS侧）的场景下，通常不需要在C++侧注册回调，而是直接将`Future`返回给ETS侧，由Taihe生成的绑定代码将其自动转换为`Promise`，并由上层调用者注册回调。但在**反向异步**（ETS侧实现异步接口，C++侧调用并处理结果）的场景下，C++侧作为消费者，则需要在`Future`上注册回调来处理ETS侧生产者发送的结果。

## 使用示例

### 示例一：正向异步——回调模式（Completer）

C++侧执行异步任务，并在任务完成时通过`Completer`将结果发送到ETS侧。

这种场景下不需要在C++侧手动调用`make_async_pair`来创建`Completer`和`Future`，而是由Taihe生成的绑定代码将ETS侧的`AsyncCallback`自动绑定到C++侧的`taihe::completer`，C++侧直接调用其`complete`方法发送结果即可，调用时会自动触发该`AsyncCallback`回调。

**Taihe声明**

```rust
function futureResultWithCallback(ms: i64, val: String, completer: Completer<String>);
```

**C++实现**

```cpp
#include "hello.impl.hpp"
#include <chrono>
#include <iostream>
#include <thread>

namespace {
void futureResultWithCallback(
    int64_t ms, ::taihe::string_view val,
    ::taihe::completer<::taihe::expected<::taihe::string, ::taihe::error>> completer)
{
    // 模拟创建一个下层异步任务
    std::thread([ms, val = taihe::string(val), completer = std::move(completer)]() mutable {
        std::cout << "[Future Result] Waiting for " << ms << " milliseconds..." << std::endl;
        std::this_thread::sleep_for(std::chrono::milliseconds(ms));
        std::cout << "[Future Result] Task completed." << std::endl;
        // 生产者：任务完成时通过completer发送异步结果回ETS侧
        completer.complete("C++AsyncProcessed-" + val);
    }).detach();
    return;
}
}  // namespace

TH_EXPORT_CPP_API_futureResultWithCallback(futureResultWithCallback);
```

需要注意，`taihe::completer`上的`complete`方法是一次性的，调用一次后该`completer`就被视为已完成状态，重复调用会触发断言失败。此外，即使将一个`completer`对象拷贝成多个实例，这些实例也共享同一个完成状态，因此只能在其中一个实例上调用`complete`。

除了`complete`方法外，`taihe::completer`还提供了`try_complete`方法用于**竞争式完成**，该方法允许多个持有者重复调用，这种情况下，只有第一个调用`try_complete`成功的持有者会将结果发送出去并得到返回值`true`，而后续再调用`try_complete`的持有者会发送失败并得到返回值`false`，这种机制适用于多个线程竞争完成同一个异步操作的场景。

**生成ETS接口**

`Completer<String>`在ETS侧投影为`AsyncCallback<string>`类型的回调函数。

```typescript
export function futureResultWithCallback(ms: long, val: string, completer: AsyncCallback<string>): void;
```

**ETS使用**

```typescript
import {BusinessError} from "@ohos.base";
import * as hello from "hello";

console.log("Calling futureResultWithCallback...");
hello.futureResultWithCallback(
    1000, "InitialValue",
    // 消费者：该回调函数将接收到C++侧生产者通过completer发送的异步结果
    (err: BusinessError|null, res: String|undefined) => {
        console.log("Callback Result: " + res);
    });
console.log("Waiting for callback...");
```

输出结果：
```sh
Calling futureResultWithCallback...
Waiting for callback...
[Future Result] Waiting for 1000 milliseconds...
[Future Result] Task completed.
Callback Result: C++AsyncProcessed-InitialValue
```

### 示例二：正向异步——Promise模式（Future）

C++侧返回一个`Future`，ETS侧自动获得一个`Promise`。

**Taihe声明**

```rust
function futureResultReturnsPromise(ms: i64, val: String): Future<String>;
```

**C++实现**

使用`taihe::make_async_pair`创建一对关联的`completer`和`future`。将`completer`传给异步任务，`future`返回给调用方。

```cpp
namespace {
using expected_string = ::taihe::expected<::taihe::string, ::taihe::error>;

taihe::future<expected_string> futureResultReturnsPromise(int64_t ms, ::taihe::string_view val)
{
    // 创建一对关联的completer和future：completer由生产者持有，future由消费者持有
    auto [completer, future] = taihe::make_async_pair<expected_string>();

    // 这段逻辑和示例一中的异步任务逻辑相同，只不过completer是我们通过make_async_pair创建的，而不是由Taihe生成的绑定代码传入的
    std::thread([ms, val = taihe::string(val), completer = std::move(completer)]() mutable {
        std::cout << "[Future Result] Waiting for " << ms << " milliseconds..." << std::endl;
        std::this_thread::sleep_for(std::chrono::milliseconds(ms));
        std::cout << "[Future Result] Task completed." << std::endl;
        // 生产者：任务完成时通过completer发送异步结果
        completer.complete("C++AsyncProcessed-" + val);
    }).detach();

    // 将future返回给消费者侧，Taihe生成的绑定代码会自动将其转换为ETS侧的Promise
    return std::move(future);
}
}  // namespace

TH_EXPORT_CPP_API_futureResultReturnsPromise(futureResultReturnsPromise);
```

**生成ETS代码**

`Future<String>`在ETS侧直接映射为`Promise<string>`。

```typescript
export function futureResultReturnsPromise(ms: long, val: string): Promise<string>;
```

**ETS使用**

```typescript
import * as hello from "hello";

console.log("Calling futureResultReturnsPromise...");
let x = hello.futureResultReturnsPromise(1000, "InitialValue");
console.log("Waiting for result...");
// 消费者：在Promise上注册回调，当C++侧的future完成时会自动触发这个回调
x.then((s: String) => {
    console.log("Promise Result: " + s);
});
```

输出结果：
```sh
Calling futureResultReturnsPromise...
Waiting for result...
[Future Result] Waiting for 1000 milliseconds...
[Future Result] Task completed.
Promise Result: C++AsyncProcessed-InitialValue
```

### 示例三：反向异步——回调模式（Completer）

在ETS侧实现接受`AsyncCallback`作为参数的异步方法。C++侧创建`completer`/`future`对，将`completer`传入该ETS侧方法（由Taihe生成的绑定代码自动将其转换为`AsyncCallback`），并在`future`上注册回调，当ETS侧调用该`AsyncCallback`时，C++侧`future`上注册的回调会被触发，接收到ETS侧发送的结果。

**Taihe声明**

```rust
interface UserTypeWithCallback {
    makeFutureStringWithCallback(callback: Completer<String>);
}

function processFutureString1(user: UserTypeWithCallback): Future<String>;
```

`UserTypeWithCallback`接口由ETS用户自行实现，在C++侧的`processFutureString1`函数中调用该接口方法并处理异步结果。

**C++实现**

```cpp
namespace {
using expected_string = ::taihe::expected<::taihe::string, ::taihe::error>;

taihe::future<expected_string> processUserTypeWithCallback(
    ::hello::weak::UserTypeWithCallback user)
{
    // 创建第一个completer/future对，用于接收ETS侧通过回调传回的结果
    auto [com1, fut1] = taihe::make_async_pair<expected_string>();

    // 将第一个completer传给ETS侧异步方法，该completer会在ETS侧被绑定到一个AsyncCallback，调用该AsyncCallback就相当于调用com1.complete()，进而触发fut1上注册的回调
    user->makeFutureStringWithCallback(std::move(com1));

    // 创建第二个completer/future对，用于将最终结果返回给上层调用方
    auto [com2, fut2] = taihe::make_async_pair<expected_string>();

    // 消费者：在fut1上注册回调，当ETS侧的AsyncCallback被调用时会自动触发这个回调
    fut1.on_complete([com2 = std::move(com2)](expected_string&& res) mutable {
        if (res) {
            // 在第一个异步结果的基础上进行一些C++侧的处理，然后通过第二个completer将最终结果发送回ETS侧
            com2.complete("C++AsyncProcessed-" + res.value());
        } else {
            com2.complete(taihe::unexpected<taihe::error>(res.error()));
        }
    });

    // 返回第二个future给调用方
    return std::move(fut2);
}
}  // namespace

TH_EXPORT_CPP_API_processFutureString1(processUserTypeWithCallback);
```

关键流程说明：
1. C++调用ETS侧的异步方法（`user->makeFutureStringWithCallback`），该调用的**同步部分**立即返回。
2. 使用`make_async_pair`创建两对`completer`/`future`：第一对用于接收ETS侧的回调结果，第二对用于将最终结果返回给调用方。
3. 通过`fut1.on_complete(...)`注册回调（消费者），在ETS侧生产者完成后执行C++侧的后续处理。
4. 在回调中处理结果后，通过`com2.complete(...)`将最终结果发送回ETS侧。

**生成ETS代码**

```typescript
export interface UserTypeWithCallback {
    makeFutureStringWithCallback(callback: AsyncCallback<string>): void;
}
export function processFutureString1(user: UserTypeWithCallback): Promise<string>;
```

`Completer<String>`映射为`AsyncCallback<string>`类型的回调函数。

**ETS使用**

```typescript
import {BusinessError} from "@ohos.base";
import * as hello from "hello";

class UserTypeWithCallbackImpl implements hello.UserTypeWithCallback {
    makeFutureStringWithCallback(callback: AsyncCallback<string>): void {
        setTimeout(() => {
            // 生产者：ETS侧在异步操作完成时通过callback（即C++侧传入的completer）发送结果回C++侧
            callback(null, "ValueFromCallback");
        }, 1000);
    }
}

let x = hello.processFutureString1(new UserTypeWithCallbackImpl());
x.then((s: String) => {
    console.log("Reverse Callback Result: " + s);
});
```

输出结果：
```sh
Reverse Callback Result: C++AsyncProcessed-ValueFromCallback
```

### 示例四：反向异步——Promise模式（Future）

ETS侧实现返回`Future`的接口方法，C++侧调用该方法并直接获得对应的`future`对象，然后在C++侧的`future`上注册回调，以处理ETS侧生产者发送的结果。

**Taihe声明**

```rust
interface UserTypeReturnsPromise {
    makeFutureStringReturnsPromise(): Future<String>;
}

function processFutureString2(user: UserTypeReturnsPromise): Future<String>;
```

`UserTypeReturnsPromise`接口由ETS用户自行实现，在C++侧的`processFutureString2`函数中调用该接口方法并处理异步结果。

**C++实现**

与示例三的回调模式相比，Promise模式无需手动创建第一个`completer`再传入ETS侧，而是直接从ETS侧方法返回值获得`future`对象，其余处理逻辑相同。

```cpp
namespace {
using expected_string = ::taihe::expected<::taihe::string, ::taihe::error>;

taihe::future<expected_string> processUserTypeReturnsPromise(
    ::hello::weak::UserTypeReturnsPromise user)
{
    // 调用ETS侧的异步方法，直接获得一个对应于ETS侧Promise的future对象
    auto fut1 = user->makeFutureStringReturnsPromise();

    // 创建另一个completer/future对，用于将最终结果返回给调用方
    auto [com2, fut2] = taihe::make_async_pair<expected_string>();

    // 消费者：在fut1上注册回调，当ETS侧的Promise完成时会自动触发这个回调
    fut1.on_complete([com2 = std::move(com2)](expected_string&& res) mutable {
        if (res) {
            // 在异步结果的基础上进行一些C++侧的处理后，通过completer将最终结果发送回ETS侧
            com2.complete("C++AsyncProcessed-" + res.value());
        } else {
            com2.complete(taihe::unexpected<taihe::error>(res.error()));
        }
    });

    // 返回第二个future给调用方
    return std::move(fut2);
}
}  // namespace

TH_EXPORT_CPP_API_processFutureString2(processUserTypeReturnsPromise);
```

**生成ETS代码**

```typescript
export interface UserTypeReturnsPromise {
    makeFutureStringReturnsPromise(): Promise<string>;
}
export function processFutureString2(user: UserTypeReturnsPromise): Promise<string>;
```

`Future<String>`映射为`Promise<string>`。

**ETS使用**

```typescript
import * as hello from "hello";

class UserTypeReturnsPromiseImpl implements hello.UserTypeReturnsPromise {
    makeFutureStringReturnsPromise(): Promise<string> {
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                // 生产者：ETS侧在异步操作完成时通过resolve发送结果回C++侧，C++侧的future会收到这个结果并触发相应的回调
                resolve("ValueFromPromise");
            }, 1000);
        });
    }
}

let y = hello.processFutureString2(new UserTypeReturnsPromiseImpl());
y.then((s: String) => {
    console.log("Reverse Promise Result: " + s);
});
```

输出结果：
```sh
Reverse Promise Result: C++AsyncProcessed-ValueFromPromise
```

## 与`@async` / `@promise`的对比

| 特性 | `@async` / `@promise` | `Future<T>` / `Completer<T>` |
| --- | --- | --- |
| C++侧实现 | 同步（异步由ETS侧`launch`完成） | 真正异步（C++侧控制完成时机） |
| 适用场景 | 简单的计算密集型任务 | 跨线程、异步I/O、双向异步交互 |
| 反向异步 | 不支持 | 支持（ETS实现接口） |
| 异步链式调用 | 不适用 | 支持（`on_complete`回调链） |
| 线程安全 | 由`launch`保证 | 开发者负责 |

## 注意事项

1. `future.on_complete()`是一次性的，即使将一个`future`拷贝成多个实例，也只能在其中一个实例上至多调用一次`on_complete`注册回调。多次调用会触发断言失败。
2. `completer.complete()`同样只能调用一次，调用多次会触发断言失败。如果需要竞争式地完成一个`completer`，可以调用`completer.try_complete()`，如果已经有其他线程完成了该`completer`，`try_complete()`会返回`false`，否则返回`true`。
3. **闭包捕获生命周期**：`on_complete`的回调可能在任意线程上执行，确保闭包中捕获的对象在回调执行时仍然有效。
4. **错误传播**：使用`taihe::unexpected<taihe::error>(err)`构造错误结果传递给`completer.complete()`，ETS侧收到的`Promise`会被reject或`AsyncCallback`的error参数非空。
