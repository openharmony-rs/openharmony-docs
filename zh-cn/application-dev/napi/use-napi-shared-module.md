---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍使用Node-API的napi_shared_module_register接口注册Sendable共享模块，实现多Worker/TaskPool共享同一导出根对象，native init只执行一次。"
keywords: [Node-API, Sendable, 共享模块, napi_shared_module_register, 多Worker, TaskPool, 导出根, Sendable对象, 跨线程共享]
doctype: guide
status: active
---

# 使用Node-API实现多Worker/TaskPool共享NAPI模块
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @shilei123; @liudachuan3-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## 场景介绍

在多Worker或TaskPool场景下，每个工作线程可能需要使用同一个Node-API原生模块（如日志、网络、数据库等）。默认情况下，每个Worker的虚拟机（VM）会独立加载并初始化该模块，导致：

- native init回调被重复执行多次，造成资源浪费和初始化耗时增加。
- 每个Worker获得各自独立的导出对象，无法跨Worker共享对象身份和原生状态。

通过`napi_shared_module_register`注册Sendable共享模块后：

- native init回调在进程内**只执行一次**，返回完整Sendable导出根对象。
- 不同Worker VM获得**同一个**导出根对象，减少内存占用。

**适用场景：**

- 多个Worker需要共享同一个原生状态（如全局计数器、连接池）。
- 需要跨Worker验证对象身份一致性（`napi_strict_equals`为`true`）。
- 希望减少重复初始化的开销。

## 约束限制

- **起始版本：** 26.1.0
- **导出根必须为Sendable对象：** init回调必须通过`napi_create_sendable_object_with_properties`创建并返回Sendable对象，返回普通`Object`、`Function`、`undefined`或`nullptr`会导致模块初始化失败。
- **exports参数不可用：** init回调的第二个参数（`exports`）在共享模块中为`undefined`，不可像普通模块那样在其上挂载属性。
- **初始化失败不可恢复：** init回调失败后，该模块在进程内永久标记为失败状态，后续所有线程的import均返回`undefined`，不会重试。
- **线程安全要求：** 模块的native回调（init及导出方法）必须线程安全，因为它们可能在不同Worker线程上被并发调用。

## 术语与能力选型

### 术语

| 术语 | 说明 |
|:-----|:-----|
| 共享模块 | 通过`napi_shared_module_register`注册的Node-API模块，区别于HAR/HSP共享包（后者是ArkTS源码/字节码共享，不涉及native init）。 |
| 导出根对象 | init回调返回的Sendable对象，作为所有Worker共享的导出根，其上的属性和方法对所有线程可见。 |
| init回调 | `napi_module`的`nm_register_func`字段，在模块首次被import时执行一次。 |

### 能力选型对比

| 特性 | `napi_module_register` | `napi_shared_module_register` |
|:-----|:-----|:-----|
| init执行次数 | 每个VM各执行一次 | 进程内只执行一次 |
| 导出对象 | 每个VM独立创建 | 所有VM共享同一个Sendable对象 |
| 导出对象类型 | 普通`Object` | Sendable Object |
| 跨VM对象身份 | 不同 | 相同 |
| 导出对象创建方式 | 通过入参exports挂载属性 | 自行创建Sendable对象并返回 |
| 适用场景 | 不需要跨线程共享状态的模块 | 需要跨Worker共享原生状态或对象身份 |

## 开发准备

### 接口声明

```ts
// index.d.ts
export const getInitCount: () => number;
```

### 编译配置

```cmake
# the minimum version of CMake.
cmake_minimum_required(VERSION 3.5.0)
project(shared_module_demo)

set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

if(DEFINED PACKAGE_FIND_FILE)
    include(${PACKAGE_FIND_FILE})
endif()

include_directories(${NATIVERENDER_ROOT_PATH}
                    ${NATIVERENDER_ROOT_PATH}/include)

add_definitions("-DLOG_DOMAIN=0x0000")
add_definitions("-DLOG_TAG=\"testTag\"")

add_library(entry SHARED napi_init.cpp)
target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
```

在`build-profile.json5`中确保`nativeLibPath`配置正确，使`libentry.so`能被ArkTS侧`import`识别。

## 开发步骤

### 注册共享模块

使用`napi_shared_module_register`替代`napi_module_register`注册模块，接口签名为：

```cpp
void napi_shared_module_register(napi_module* mod);
```

| 参数 | 说明 |
|:-----|:-----|
| mod | 指向`napi_module`结构体的指针，描述模块信息。 |

与`napi_module_register`的核心差异：模块的`nm_register_func`回调将在首次被任一线程（主线程或Worker）import时执行一次，返回的Sendable导出根对象将被缓存并共享给所有Worker。

```cpp
// napi_init.cpp
#include "napi/native_api.h"
#include "hilog/log.h"
#include <atomic>

// 记录 init 回调被执行的次数
static std::atomic<int> g_initCount{0};

static napi_value GetInitCount(napi_env env, napi_callback_info info)
{
    napi_value result = nullptr;
    napi_create_int32(env, g_initCount.load(), &result);
    return result;
}

// init 回调：必须返回一个 Sendable 对象作为导出根
static napi_value Init(napi_env env, napi_value /* unused */)
{
    g_initCount.fetch_add(1);
    OH_LOG_INFO(LOG_APP, "shared module init, count: %{public}d", g_initCount.load());
    napi_property_descriptor desc[] = {
        {"getInitCount", nullptr, GetInitCount, nullptr, nullptr, nullptr, napi_default, nullptr},
    };
    napi_value exports = nullptr;
    napi_status status = napi_create_sendable_object_with_properties(
        env, sizeof(desc) / sizeof(desc[0]), desc, &exports);
    if (status != napi_ok) {
        return nullptr;
    }
    return exports;
}

// 使用 napi_shared_module_register 替代 napi_module_register
static napi_module module = {
    .nm_version = 1,
    .nm_flags = 0,
    .nm_filename = __FILE__,
    .nm_register_func = Init,
    .nm_modname = "entry",
    .nm_priv = nullptr,
    .reserved = {0},
};

extern "C" __attribute__((constructor)) void RegisterModule()
{
    napi_shared_module_register(&module);
}
```

### 设计导出根

init回调必须通过`napi_create_sendable_object_with_properties`创建Sendable对象并返回。回调的第二个参数（`exports`）为`undefined`，不能像普通模块那样在其上挂载属性。

```cpp
// 正确：返回 Sendable 对象
static napi_value Init(napi_env env, napi_value /* unused */)
{
    napi_property_descriptor desc[] = {
        {"foo", nullptr, Foo, nullptr, nullptr, nullptr, napi_default, nullptr},
    };
    napi_value exports = nullptr;
    napi_status status = napi_create_sendable_object_with_properties(
        env, sizeof(desc) / sizeof(desc[0]), desc, &exports);
    if (status != napi_ok) {
        return nullptr;
    }
    return exports;
}
```

```cpp
// 错误：返回普通 Object
static napi_value InitBad(napi_env env, napi_value /* unused */)
{
    napi_value obj = nullptr;
    napi_create_object(env, &obj);  // 普通 Object，非 Sendable
    return obj;  // 初始化失败
}
```

### ArkTS侧使用

主线程首次import触发init，Worker中再次import同一模块时init不会重复执行，获得同一个导出根对象。TaskPool中使用`@Concurrent`装饰的函数import同一模块时，同样共享同一个导出根对象。

```ts
// 主线程 Index.ets
import { taskpool, MessageEvents, worker } from '@kit.ArkTS';
import testNapi from 'libentry.so';

// 主线程首次 import 触发 init，initCount 为 1
console.info(`Main getInitCount: ${testNapi.getInitCount()}`); // Main getInitCount: 1

// 创建 Worker，Worker 中再次 import 同一模块
const w = new worker.ThreadWorker('entry/ets/workers/Worker.ets');

w.onmessage = (e: MessageEvents): void => { console.info('Received worker message: ' + e.data); };
w.postMessage("work");

// 通过 TaskPool 执行 @Concurrent 函数，同样共享同一个导出根对象
@Concurrent
function getSharedInitCount(): number {
    return testNapi.getInitCount();
}

taskpool.execute(getSharedInitCount).then((val: Object) => {
    console.info('TaskPool getInitCount: ' + val); // TaskPool getInitCount: 1
});
```

```ts
// Worker.ets
import testNapi from 'libentry.so';
import { MessageEvents, worker } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    // 共享模块 init 只执行一次，Worker 看到的 initCount 仍为 1
    // 若使用普通模块（napi_module_register），此处会返回 2
    const count = testNapi.getInitCount();
    try {
        workerPort.postMessage(count.toString());
    } catch (error) {
        console.error(`Worker postMessage failed. Code: ${error.code}, message: ${error.message}`);
    }
};
```

## 线程安全与生命周期

- **线程安全：** 导出根上的方法可能在不同Worker线程上并发调用，native代码中访问共享状态时必须使用锁或原子变量保护。禁止缓存`napi_env`或`napi_value`跨线程使用，每个回调应使用运行时传入的`env`。
- **生命周期：** 导出根对象在进程内一直存活，Worker退出/重建不影响其有效性。Worker退出时无需手动释放导出根，运行时自动管理`SendableGlobal`的生命周期。
- **初始化失败：** init回调失败后模块永久标记为失败，可通过hilog日志（搜索"shared module init failed"）定位失败原因。

常见错误：

| 现象 | 原因 | 修复 |
|:-----|:-----|:-----|
| Worker中import返回`undefined` | init回调返回了非Sendable对象 | 确保回调返回`napi_create_sendable_object_with_properties`创建的对象。 |
| init回调执行多次 | 使用了`napi_module_register`而非`napi_shared_module_register` | 改用`napi_shared_module_register`。 |
| 跨线程调用方法崩溃 | 缓存了`napi_env`跨线程使用 | 每个回调使用传入的`env`，不缓存。 |

## 调测验证

通过`getInitCount`验证init只执行一次：主线程import后initCount为1，Worker import后initCount仍为1。若使用普通模块（`napi_module_register`），Worker import后initCount会变为2。

| 验证项 | 共享模块预期 | 普通模块预期 |
|:-----|:-----|:-----|
| 主线程initCount | 1 | 1 |
| Worker initCount | 1 | 2 |
| TaskPool initCount | 1 | 2 |
| 跨Worker对象身份 | 相同 | 不同 |

## 安全、性能与兼容性

- **安全：** 共享模块的导出根对所有Worker可见，不应在导出对象上暴露敏感数据（如密钥、隐私信息）。native回调中应对外部输入进行校验。
- **性能：** 共享模块减少重复init开销和内存占用，适合初始化耗时较长或内存占用较大的模块。对于轻量模块，收益可能不明显。
- **兼容性：** 共享模块与普通模块可在同一进程内共存。已有模块从`napi_module_register`迁移到`napi_shared_module_register`时，需确保init回调改为返回Sendable对象。API版本低于26.1.0的设备不支持此接口。

## 相关文档

- [Native与Sendable ArkTS对象绑定](use-sendable-napi.md)
- [使用Node-API接口创建对ArkTS对象的Sendable强引用](use-napi-about-sendable-reference.md)
- [Sendable](../arkts-utils/arkts-sendable.md)
- [TaskPool与Worker对比](../arkts-utils/taskpool-vs-worker.md)
