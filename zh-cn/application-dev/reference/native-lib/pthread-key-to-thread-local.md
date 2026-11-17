# pthread key 迁移到 C++ thread_local 指南

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## 迁移目的与适用范围

本文面向 OpenHarmony 原生 C++ 模块开发者，介绍如何将使用 `pthread_key_t` 保存的、用途固定的线程私有数据迁移到 C++11 `thread_local` 变量，减少业务重复创建 key 的情况，并说明迁移中的生命周期管理和资源清理要求。

TSD（Thread-Specific Data，线程私有数据）是通过 `pthread_key_create()` 创建 key，并通过 `pthread_setspecific()` 和 `pthread_getspecific()` 设置、读取各线程关联值的机制。TLS（Thread-Local Storage，线程局部存储）用于保存每个线程独立的数据，C++ `thread_local` 是声明此类变量的语言机制。

以当前 [OpenHarmony musl](https://gitcode.com/openharmony/third_party_musl/blob/master/include/limits.h) 实现为例，`PTHREAD_KEYS_MAX` 的值为 128，即进程可同时分配的 key 数量上限。应用、运行时和三方库共享这份额度。具体上限以目标产品所用的源码版本和构建配置为准。同一个 key 供所有线程共用，每个线程存取各自的值。因此同一用途只需创建一次，不必按线程或按请求重复创建。

> **注意：**
>
> POSIX 要求实现至少支持 128 个 key（[`_POSIX_THREAD_KEYS_MAX`](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/limits.h.html)），这不是所有平台统一的上限。不同平台的实际限额可能不同，移植代码时不能沿用其他平台的容量假设，迁移前应检查业务及其依赖库的 key 使用量，避免 `pthread_key_create()` 因额度不足返回 `EAGAIN`。

如果每个线程需要保存的状态在编写代码时就能确定（例如一个固定的计数器或上下文对象），可以直接用 `thread_local` 变量代替 pthread key。每个线程会自动获得该变量的一份独立副本，业务无需再调用 `pthread_key_create()`、`pthread_getspecific()` 和 `pthread_setspecific()`。

| 业务场景 | 迁移建议 |
| --- | --- |
| C++ 模块固定的每个线程计数、缓存或上下文 | 可以评估迁移，通过统一访问函数取得当前线程实例 |
| 对象拥有内存、文件或其他资源 | 使用有明确析构逻辑的类型或智能指针，不能只替换为裸指针变量 |
| 需要在运行时按需创建数量不固定的 key，或由外部调用者传入 key | 保留原接口或重新设计上下文管理，无法直接替换为固定变量 |
| 纯 C 模块 | C++ `thread_local` 不能直接写入 C 源文件；可评估 `_Thread_local` 或 C++ 封装，但清理规则需要单独设计 |
| 线程池任务、协程或可能跨线程调度的任务上下文 | 先确认真正需要的是线程状态还是任务状态；`thread_local` 绑定执行线程，不会自动随任务迁移 |

## 前后对照示例

下面的上下文只保存一个计数，不拥有额外资源。示例适用于 C++11 及以上。

### 迁移前（通过 pthread key 访问）

```cpp
#include <cerrno>
#include <new>
#include <pthread.h>

struct ThreadContext {
    unsigned int requestCount;
};

static pthread_once_t g_once = PTHREAD_ONCE_INIT;
static pthread_key_t g_contextKey;
static int g_keyError;

static void DestroyContext(void *value)
{
    delete static_cast<ThreadContext *>(value);
}

static void CreateContextKey()
{
    g_keyError = pthread_key_create(&g_contextKey, DestroyContext);
}

int GetThreadContext(ThreadContext **out)
{
    if (out == nullptr) {
        return EINVAL;
    }
    *out = nullptr;
    int ret = pthread_once(&g_once, CreateContextKey);
    if (ret != 0 || g_keyError != 0) {
        return ret != 0 ? ret : g_keyError;
    }
    auto *context = static_cast<ThreadContext *>(pthread_getspecific(g_contextKey));
    if (context == nullptr) {
        context = new (std::nothrow) ThreadContext{};
        if (context == nullptr) {
            return ENOMEM;
        }
        ret = pthread_setspecific(g_contextKey, context);
        if (ret != 0) {
            delete context;
            return ret;
        }
    }
    *out = context;
    return 0;
}
```

此处整个模块只申请一个 key，并非每个线程申请一个。示例用 `new/delete` 管理对象，原有业务也应保持分配与释放方式匹配。

### 迁移后（通过 thread_local 访问）

```cpp
#include <cerrno>
#include <iostream>
#include <thread>

struct ThreadContext {
    unsigned int requestCount = 0;
};

int GetThreadContext(ThreadContext **out)
{
    if (out == nullptr) {
        return EINVAL;
    }
    static thread_local ThreadContext context{};
    *out = &context;
    return 0;
}

int main()
{
    auto worker = [](const char *name) {
        ThreadContext *ctx = nullptr;
        GetThreadContext(&ctx);
        ctx->requestCount++;
        GetThreadContext(&ctx);
        ctx->requestCount++;
        std::cout << name << ": count=" << ctx->requestCount << std::endl;
    };

    std::thread t1(worker, "thread-1");
    std::thread t2(worker, "thread-2");
    worker("main");
    t1.join();
    t2.join();
    return 0;
}
```

调用方仍通过 `GetThreadContext()` 取得上下文。同一线程多次调用得到同一实例，不同线程得到各自的实例。这里不再需要业务的 key、`pthread_once_t` 初始化控制对象及相应回调；业务原有的 key 耗尽和堆分配失败路径也随实现改变，不能把此例的行为推广到有复杂构造函数的类型。

这个函数应在一个 `.cpp` 文件中提供唯一实现。不建议把带 `static` 内部链接的访问函数复制到多个源文件或公共头文件中，否则可能为同一业务产生多份独立状态。跨动态库调用也应统一入口，不能仅凭相同变量名认为所有模块共享同一份 TLS 定义。

## 资源所有权与主动清理

`thread_local ThreadContext *context` 只让指针本身按线程保存，不会在线程退出时自动 `delete` 它指向的对象。若原 key 的析构函数会释放对象，迁移后必须保持原有资源所有权关系，并实现等价的资源清理逻辑。

可以直接保存拥有资源的对象，让其析构函数完成清理；若需要按需创建和提前释放，可使用智能指针。例如：

```cpp
#include <memory>
#include <new>

struct ThreadContext {
    unsigned int requestCount = 0;
};

static std::unique_ptr<ThreadContext>& CurrentContext()
{
    static thread_local std::unique_ptr<ThreadContext> context;
    return context;
}

ThreadContext *GetOrCreateContext()
{
    auto& context = CurrentContext();
    if (!context) {
        context.reset(new (std::nothrow) ThreadContext);
    }
    return context.get();
}

void ResetCurrentContext()
{
    CurrentContext().reset();
}
```

调用方应检查 `GetOrCreateContext()` 是否返回空指针。`new (std::nothrow)` 在对象存储分配失败时返回空指针；若构造函数可能抛出异常，还需遵循项目的异常处理策略。调用方获取的指针在 `ResetCurrentContext()` 后立即失效，不应跨重置操作持有。

`ResetCurrentContext()` 只清理调用线程的对象。线程池中，线程可能长期不退出，因此请求结束或租户切换时需要主动重置状态，不能等待线程退出后才清理敏感信息或资源。旧的 `pthread_setspecific(key, nullptr)` 只是清空关联值，不自动释放旧对象；智能指针的 `reset()` 会释放，迁移前应核对旧代码的清理责任，避免重复释放。

若原 key 保存的是外部拥有的“当前上下文”指针，应保留借用关系、设置和清空接口，以及嵌套调用时旧指针的保存与恢复；不能直接改成拥有资源所有权的封装。不同业务实例原先各自创建 key 时，也不能用一个 TLS 变量将它们的状态合并。

## 生命周期与兼容性风险

`thread_local` 变量的析构由运行时自动管理。其实现仍可能依赖 pthread key：例如 [`cxa_thread_atexit_impl.c`](https://gitcode.com/openharmony/third_party_musl/blob/master/src/exit/cxa_thread_atexit_impl.c) 保留了 `CXA_THREAD_USE_TSD` 和 `CXA_THREAD_USE_TLS` 两条实现路径，具体使用哪条路径取决于构建配置。TSD 路径使用一个内部 key 管理 C++ TLS 析构，并非每个 `thread_local` 对象各创建一个 key。因此，迁移到 `thread_local` 并不意味着整个进程不再使用 pthread key，或完全没有运行时开销。这里减少的是业务显式申请的 key，而非运行时内部的 key。

- **析构语义需要重新核对。** 线程退出时，pthread key 会对已设置的非空值调用 `pthread_key_create()` 登记的析构函数；`pthread_key_delete()` 只是注销 key 本身，不调用值的析构。C++ `thread_local` 对象在线程退出时按构造的逆序自动析构。迁移时需要逐项核对原有的清理逻辑是否被等价覆盖。
- **迁移不提供进程级撤销操作。** `pthread_key_delete()` 撤销的是进程共享的 key，不会析构关联对象；`thread_local` 不提供统一撤销所有线程实例的接口，重置操作也只作用于调用线程。需要提前回收对象时，应由各线程协作，或调整模块生命周期。
- **动态库卸载要验证。** 在 `dlopen/dlclose`、TLS 析构回调和工作线程同时存在时，必须确认目标运行时的卸载策略和模块生命周期。
- **内存和失败路径会变化。** 如果 `thread_local` 变量本身占用的存储空间较大（例如大数组或含较多成员的结构体），它会直接占用每个线程的 TLS 块空间，按线程数倍增内存占用；动态初始化和析构登记也可能分配内存。复杂构造和析构不应放入信号处理、分配器重入等敏感路径。按实际线程数评估开销。
- **C 和 C++ TLS 清理规则不同。** C11 `_Thread_local` 或编译器 `__thread` 不提供 C++ 对象的 RAII 析构，不能据此直接替代有清理回调的 key。编译器、目标架构及运行时支持也需要确认。
- **异常退出不保证清理。** 崩溃、强制结束及 `_exit()` 等路径不能依赖常规线程析构释放业务资源。迁移也不改变多线程进程 `fork()` 后、`exec` 前的异步信号安全限制。

## 迁移步骤与验证建议

1. 盘点同一 key 的 `pthread_key_create()`、`pthread_getspecific()`、`pthread_setspecific()`、`pthread_key_delete()` 和析构回调，确认它表示固定的每个线程状态，梳理所有权及主动清理时机。
2. 将访问集中到一个模块入口，再引入 `thread_local`；固定小状态可直接保存对象，需要按需分配或重置的状态可用拥有所有权的封装。
3. 将原 `pthread_setspecific()`、替换及清空操作转换为对象赋值、重置或专用接口，逐项核对旧值释放、错误返回与调用方预期。
4. 完成所有调用点迁移后，移除不再使用的业务 key 初始化、once、析构回调和 `delete` 路径。运行中的旧对象不能只靠 `pthread_key_delete()` 回收，应安排停用和清理。
5. 在目标产品构建中验证：同线程状态保持、不同线程隔离；线程退出时资源只清理一次；线程池任务切换后的重置；初始化失败；涉及模块的加载和卸载。

迁移收益应按模块显式创建的 key 数量评估。一个由所有线程共用的业务 key，迁移后只减少一个显式申请的 key，减少数量不会随线程数增加。如果只是重复创建同类 key，也可以先修正为创建一次并复用，再决定是否迁移到 `thread_local`。

## 实现参考

以下链接指向 OpenHarmony musl 仓的 master 分支，用于说明当前实现。key 上限、TLS 析构实现及运行时行为应以目标产品所用的源码版本和构建配置为准。

- [key 创建、删除与 TSD 析构](https://gitcode.com/openharmony/third_party_musl/blob/master/src/thread/pthread_key_create.c)
- [C++ TLS 析构登记](https://gitcode.com/openharmony/third_party_musl/blob/master/src/exit/cxa_thread_atexit_impl.c)
- [OpenHarmony Linux 线程退出](https://gitcode.com/openharmony/third_party_musl/blob/master/src/thread/linux/pthread_create.c)
- [当前 key 上限定义](https://gitcode.com/openharmony/third_party_musl/blob/master/include/limits.h)
