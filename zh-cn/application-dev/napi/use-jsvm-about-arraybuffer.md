---
kits: ["ArkTS / 方舟编程语言"]
description: "介绍如何使用JSVM-API创建ArrayBuffer二进制缓冲区，获取底层数据指针与长度，执行Detach分离操作并判断分离状态；并介绍如何使用SharedArrayBuffer与JSVM_BackingStore句柄实现跨线程、跨虚拟机共享二进制数据。"
keywords: [OH_JSVM_CreateArraybuffer, OH_JSVM_GetArraybufferInfo, OH_JSVM_DetachArraybuffer, OH_JSVM_IsArraybuffer, OH_JSVM_IsDetachedArraybuffer, OH_JSVM_CreateSharedArrayBuffer, OH_JSVM_IsSharedArrayBuffer, JSVM_BackingStore, ArrayBuffer, SharedArrayBuffer, 二进制数据缓冲区, TypedArray, DataView]
doctype: guide
status: active
---

# 使用JSVM-API接口进行ArrayBuffer相关开发
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->

## 简介

ArrayBuffer 是 JavaScript 中的一种数据类型，用于表示通用的、固定长度的原始二进制数据缓冲区。它提供了一种在 JavaScript 中有效地表示和操作原始二进制数据的方式。SharedArrayBuffer是特殊的ArrayBuffer，主要用于表示可共享的、固定长度的原始二进制数据缓冲区。与ArrayBuffer不同，SharedArrayBuffer的底层内存可以被多个线程、甚至同一进程内的多个JSVM虚拟机实例同时引用，适用于Worker线程间共享数据、native与JS层共享一块热数据等场景。

## 基本概念

- **ArrayBuffer**：ArrayBuffer 对象用来表示一个通用的、固定长度的原始二进制数据缓冲区。不能直接操作 ArrayBuffer 的内容，而是需要通过包装成 TypedArray 对象或 DataView 对象来读写。ArrayBuffer 常用于处理固定长度的原始二进制数据，如文件、网络数据包等。
- **生命周期和内存管理**：在使用 JSVM 处理 ArrayBuffer 时，需要特别注意对象的生命周期管理，确保及时释放内存。
- **SharedArrayBuffer与ArrayBuffer的区别**：两者都是二进制缓冲区，但SharedArrayBuffer的底层内存是共享的，**不支持Detach操作**（调用[OH_JSVM_DetachArraybuffer](../reference/common/capi-jsvm-h.md#oh_jsvm_detacharraybuffer)会返回JSVM_ARRAYBUFFER_EXPECTED）。同一块共享内存可以被多个JSVM实例以各自的SharedArrayBuffer对象形式引用。
- **JSVM_BackingStore句柄**：一个**与虚拟机无关**的native句柄，代表对共享内存的一个独立引用。每个通过JSVM-API获取或复制的句柄都必须调用`OH_JSVM_ReleaseBackingStore`释放一次。句柄在其源SharedArrayBuffer对象甚至源虚拟机销毁后依然有效，可以在另一个虚拟机中重建SharedArrayBuffer。
- **视图对象**：与ArrayBuffer一样，SharedArrayBuffer在JS侧不能直接按索引读写，需要通过TypedArray或DataView视图访问；[OH_JSVM_CreateTypedarray](../reference/common/capi-jsvm-h.md#oh_jsvm_createtypedarray)与[OH_JSVM_CreateDataview](../reference/common/capi-jsvm-h.md#oh_jsvm_createdataview)均可接受SharedArrayBuffer作为底层缓冲区。native侧则可直接通过数据指针读写。
- **并发同步**：多个线程并发读写同一块共享内存时，必须由开发者保证同步（如JS侧使用Atomics、native侧使用锁），否则会产生数据竞争。

## 接口说明

| 接口                         | 功能说明                                   |
| ---------------------------- | ------------------------------------------ |
| OH_JSVM_GetArraybufferInfo    | 检索 ArrayBuffer 的底层数据缓冲区及其长度。 |
| OH_JSVM_IsArraybuffer        | 判断一个 JavaScript 对象是否为 ArrayBuffer 类型对象。        |
| OH_JSVM_DetachArraybuffer    | 调用 ArrayBuffer 对象的 Detach 操作。            |
| OH_JSVM_IsDetachedArraybuffer | 检查给定的 ArrayBuffer 是否已被分离(Detached)。        |
| OH_JSVM_CreateArraybuffer      | 创建一个指定大小的 ArrayBuffer 对象。   |
| OH_JSVM_CreateSharedArrayBuffer | 创建一个指定大小的SharedArrayBuffer对象。 |
| OH_JSVM_IsSharedArrayBuffer | 判断一个对象是否为SharedArrayBuffer类型对象。 |
| OH_JSVM_GetSharedArrayBufferInfo | 检索SharedArrayBuffer的底层数据缓冲区、字节长度与最大字节长度。 |
| OH_JSVM_GetSharedArrayBufferBackingStore | 获取SharedArrayBuffer底层内存的JSVM_BackingStore句柄。 |
| OH_JSVM_RetainBackingStore | 复制一个JSVM_BackingStore句柄，新句柄独立持有引用。 |
| OH_JSVM_ReleaseBackingStore | 释放一个JSVM_BackingStore句柄持有的引用。 |
| OH_JSVM_GetBackingStoreInfo | 检索JSVM_BackingStore句柄的数据指针、长度及共享/可增长属性。 |
| OH_JSVM_CreateSharedArrayBufferFromBackingStore | 基于已有的JSVM_BackingStore句柄，在当前环境创建一个新的SharedArrayBuffer对象。 |

### 注意事项

1. **需开启实验性宏**：在`#include "ark_runtime/jsvm.h"`和`#include "ark_runtime/jsvm_types.h"`前必须`#define JSVM_EXPERIMENTAL`，否则接口不可见。
2. **句柄必须释放**：`OH_JSVM_GetSharedArrayBufferBackingStore`和`OH_JSVM_RetainBackingStore`每返回一个句柄，就对应一次`OH_JSVM_ReleaseBackingStore`调用，否则会造成内存泄漏。释放句柄不影响仍然存活的SharedArrayBuffer对象（它们持有自己的引用）。
3. **跨虚拟机传递**：JSVM_BackingStore句柄可以跨线程、跨JSVM实例传递，但其本身不是线程安全的，并发访问需要外部同步。
4. **不可分离**：SharedArrayBuffer不支持Detach，对SharedArrayBuffer调用`OH_JSVM_DetachArraybuffer`返回JSVM_ARRAYBUFFER_EXPECTED。
5. **视图越界**：在SharedArrayBuffer上创建TypedArray/DataView时，越界或未按元素大小对齐同样抛出RangeError。

## 使用示例

JSVM-API 接口开发流程参考[使用JSVM-API实现JS与C/C++语言交互开发流程](use-jsvm-process.md)，本文仅对接口对应 C++ 相关代码进行展示。

### OH_JSVM_GetArraybufferInfo

检索 ArrayBuffer 的底层数据缓冲区及其长度。

cpp部分代码：

<!-- @[oh_jsvm_get_arraybuffer_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/JsvmAboutArraybuffer/getarraybufferinfo/src/main/cpp/hello.cpp) -->

``` C++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// OH_JSVM_GetArraybufferInfo的样例方法
static JSVM_Value GetArraybufferInfo(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    // 解析传递的参数
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // 检查参数是否为ArrayBuffer
    bool isArrayBuffer = false;
    OH_JSVM_IsArraybuffer(env, args[0], &isArrayBuffer);
    if (!isArrayBuffer) {
        OH_LOG_ERROR(LOG_APP, "JSVM GetArraybufferInfo isArrayBuffer:false");
    }
    void *data;
    size_t byteLength = 0;
    // 获取ArrayBuffer的底层数据缓冲区和长度
    JSVM_Status status = OH_JSVM_GetArraybufferInfo(env, args[0], &data, &byteLength);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM GetArraybufferInfo: failed");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM GetArraybufferInfo: success");
    }
    return args[0];
}
// GetArraybufferInfo注册回调
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = GetArraybufferInfo},
};
static JSVM_CallbackStruct *method = param;
// GetArraybufferInfo方法别名，供JS调用
static JSVM_PropertyDescriptor descriptor[] = {
    {"getArraybufferInfo", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// 样例测试js
const char *SRC_CALL_NATIVE = R"JS(
getArraybufferInfo(new ArrayBuffer(10));
)JS";
```

预期结果：
```txt
JSVM GetArraybufferInfo: success
```

### OH_JSVM_IsArraybuffer

判断一个 JavaScript 对象是否为 ArrayBuffer 类型对象。

cpp部分代码：

<!-- @[oh_jsvm_is_arraybuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/JsvmAboutArraybuffer/isarraybuffer/src/main/cpp/hello.cpp) -->

``` C++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// OH_JSVM_IsArraybuffer的样例方法
static JSVM_Value IsArrayBuffer(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // 调用OH_JSVM_IsArraybuffer接口判断给定入参是否为ArrayBuffer数据
    bool isArrayBuffer = false;
    JSVM_Status status = OH_JSVM_IsArraybuffer(env, args[0], &isArrayBuffer);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM IsArrayBuffer: failed");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM IsArrayBuffer: success");
        OH_LOG_INFO(LOG_APP, "JSVM IsArrayBuffer: %{public}d", isArrayBuffer);
    }
    JSVM_Value boolean = nullptr;
    OH_JSVM_GetBoolean(env, isArrayBuffer, &boolean);
    return boolean;
}
// IsArrayBuffer注册回调
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = IsArrayBuffer},
};
static JSVM_CallbackStruct *method = param;
// IsArrayBuffer方法别名，供JS调用
static JSVM_PropertyDescriptor descriptor[] = {
    {"isArrayBuffer", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// 样例测试js
const char *SRC_CALL_NATIVE = R"JS(
isArrayBuffer(new ArrayBuffer(8));
)JS";
```

预期结果：
```txt
JSVM IsArrayBuffer: success
JSVM IsArrayBuffer: 1
```

### OH_JSVM_DetachArraybuffer

调用 ArrayBuffer 对象的 Detach 操作。

示例代码与OH_JSVM_IsDetachedArraybuffer合并展示，请参考下文[OH_JSVM_IsDetachedArraybuffer](#oh_jsvm_isdetachedarraybuffer)中的`DetachArraybuffer`方法。

### OH_JSVM_IsDetachedArraybuffer

检查给定的 ArrayBuffer 是否已被分离。

cpp部分代码：

<!-- @[oh_jsvm_is_detached_arraybuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/JsvmAboutArraybuffer/isdetachedarraybuffer/src/main/cpp/hello.cpp) -->

``` C++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// OH_JSVM_DetachArraybuffer、OH_JSVM_IsDetachedArraybuffer的样例方法
static JSVM_Value DetachArraybuffer(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    JSVM_Value arraybuffer = args[0];
    JSVM_Status status = OH_JSVM_DetachArraybuffer(env, arraybuffer);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM DetachArraybuffer: failed");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM DetachArraybuffer: success");
    }
    return arraybuffer;
}
static JSVM_Value IsDetachedArraybuffer(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    JSVM_Value arraybuffer = args[0];
    OH_JSVM_DetachArraybuffer(env, arraybuffer);
    bool result = false;
    JSVM_Status status = OH_JSVM_IsDetachedArraybuffer(env, arraybuffer, &result);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM IsDetachedArraybuffer: failed");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM IsDetachedArraybuffer: success");
        OH_LOG_INFO(LOG_APP, "JSVM IsDetachedArraybuffer: %{public}d", result);
    }
    JSVM_Value isDetached = nullptr;
    OH_JSVM_GetBoolean(env, result, &isDetached);
    return isDetached;
}
// DetachArraybuffer、IsDetachedArraybuffer注册回调
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = DetachArraybuffer},
    {.data = nullptr, .callback = IsDetachedArraybuffer},
};
static JSVM_CallbackStruct *method = param;
// DetachArraybuffer、IsDetachedArraybuffer方法别名，TS侧调用
static JSVM_PropertyDescriptor descriptor[] = {
    {"detachArraybuffer", nullptr, method, nullptr, nullptr, nullptr, JSVM_DEFAULT},
    {"isDetachedArraybuffer", nullptr, method+1, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// 样例测试js
const char *SRC_CALL_NATIVE = R"JS(
let arrayBuffer = new ArrayBuffer(10);
detachArraybuffer(arrayBuffer);
isDetachedArraybuffer(arrayBuffer);
)JS";
```

预期结果：
```txt
JSVM DetachArraybuffer: success
JSVM IsDetachedArraybuffer: success
JSVM IsDetachedArraybuffer: 1
```

### OH_JSVM_CreateArraybuffer

创建一个指定大小的 ArrayBuffer 对象。

cpp部分代码：

<!-- @[oh_jsvm_create_arraybuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/JsvmAboutArraybuffer/createarraybuffer/src/main/cpp/hello.cpp) -->

``` C++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// OH_JSVM_CreateArraybuffer的样例方法
static JSVM_Value CreateArraybuffer(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value argv[1] = {nullptr};
    JSVM_Value result = nullptr;
    // 解析传递的参数
    OH_JSVM_GetCbInfo(env, info, &argc, argv, nullptr, nullptr);
    int32_t value = 0;
    size_t length = 0;
    JSVM_CALL(OH_JSVM_GetValueInt32(env, argv[0], &value));
    length = size_t(value);
    void *data;
    // 创建一个新的ArrayBuffer
    JSVM_Status status = OH_JSVM_CreateArraybuffer(env, length, &data, &result);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateArraybuffer: failed");
        return nullptr;
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM CreateArraybuffer: success");
        OH_LOG_INFO(LOG_APP, "JSVM ArrayBuffer length: %{public}d", length);
    }
    // 返回创建好的ArrayBuffer
    return result;
}
// CreateArraybuffer注册回调
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = CreateArraybuffer},
};
static JSVM_CallbackStruct *method = param;
// CreateArraybuffer方法别名，供TS侧调用
static JSVM_PropertyDescriptor descriptor[] = {
    {"createArraybuffer", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// 样例测试js
const char *SRC_CALL_NATIVE = R"JS(
createArraybuffer(8);
)JS";
```

预期结果：
```txt
JSVM CreateArraybuffer: success
JSVM ArrayBuffer length: 8
```

### SharedArrayBuffer
SharedArrayBuffer多个接口联合使用体现共享能力。

``` C++
#define JSVM_EXPERIMENTAL  // 必须在include jsvm.h之前定义，否则无法调用实验接口
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// OH_JSVM_CreateSharedArrayBuffer等接口的样例方法
static JSVM_Value CreateSharedArrayBuffer(JSVM_Env env, JSVM_CallbackInfo info)
{
    constexpr size_t bufferSize = 16;
    void *data = nullptr;
    JSVM_Value sharedArrayBuffer = nullptr;
    // 1. 创建SharedArrayBuffer，并取得底层数据指针
    JSVM_Status status = OH_JSVM_CreateSharedArrayBuffer(env, bufferSize, &data, &sharedArrayBuffer);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateSharedArrayBuffer: failed");
        return nullptr;
    }
    // 2. native侧直接写入数据
    uint8_t *bytes = static_cast<uint8_t *>(data);
    for (size_t i = 0; i < bufferSize; i++) {
        bytes[i] = static_cast<uint8_t>(i);
    }
    // 3. 在SharedArrayBuffer上创建Uint8Array视图，供JS侧读写
    JSVM_Value typedArray = nullptr;
    status = OH_JSVM_CreateTypedarray(env, JSVM_UINT8_ARRAY, bufferSize, sharedArrayBuffer, 0, &typedArray);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateTypedarray over SharedArrayBuffer: failed");
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "JSVM CreateSharedArrayBuffer: success, byteLength=%{public}zu", bufferSize);
    return typedArray;
}

// 演示JSVM_BackingStore句柄跨虚拟机存活的样例方法
static JSVM_Value BackingStoreAcrossVM(JSVM_Env env, JSVM_CallbackInfo info)
{
    constexpr size_t bufferSize = 8;
    constexpr uint8_t marker = 0x5A;
    JSVM_BackingStore backingStore = nullptr;
    void *sourceData = nullptr;

    // 1. 创建源虚拟机并在其中创建SharedArrayBuffer
    JSVM_VM sourceVm = nullptr;
    JSVM_VMScope vmScope = nullptr;
    JSVM_Env sourceEnv = nullptr;
    JSVM_EnvScope envScope = nullptr;
    JSVM_HandleScope handleScope = nullptr;
    OH_JSVM_CreateVM(nullptr, &sourceVm);
    OH_JSVM_OpenVMScope(sourceVm, &vmScope);
    OH_JSVM_CreateEnv(sourceVm, 0, nullptr, &sourceEnv);
    OH_JSVM_OpenEnvScope(sourceEnv, &envScope);
    OH_JSVM_OpenHandleScope(sourceEnv, &handleScope);

    JSVM_Value sourceSab = nullptr;
    if (OH_JSVM_CreateSharedArrayBuffer(sourceEnv, bufferSize, &sourceData, &sourceSab) != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateSharedArrayBuffer in source VM: failed");
        return nullptr;
    }
    static_cast<uint8_t *>(sourceData)[0] = marker;
    // 2. 获取BackingStore句柄
    OH_JSVM_GetSharedArrayBufferBackingStore(sourceEnv, sourceSab, &backingStore);

    // 3. 销毁源虚拟机，句柄仍然有效
    OH_JSVM_CloseHandleScope(sourceEnv, handleScope);
    OH_JSVM_CloseEnvScope(sourceEnv, envScope);
    OH_JSVM_DestroyEnv(sourceEnv);
    OH_JSVM_CloseVMScope(sourceVm, vmScope);
    OH_JSVM_DestroyVM(sourceVm);

    // 4. 通过句柄查询共享内存：数据未随源虚拟机销毁而丢失
    void *survivingData = nullptr;
    size_t survivingLength = 0;
    bool isShared = false;
    OH_JSVM_GetBackingStoreInfo(backingStore, &survivingData, &survivingLength, nullptr, &isShared, nullptr);
    OH_LOG_INFO(LOG_APP, "JSVM BackingStore survives source VM: length=%{public}zu, isShared=%{public}d, "
                "marker=%{public}d", survivingLength, isShared,
                survivingData != nullptr ? static_cast<uint8_t *>(survivingData)[0] : -1);

    // 5. 在当前虚拟机中基于句柄重建SharedArrayBuffer，与源共享同一块内存
    JSVM_Value targetSab = nullptr;
    if (OH_JSVM_CreateSharedArrayBufferFromBackingStore(env, backingStore, &targetSab) != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateSharedArrayBufferFromBackingStore: failed");
        OH_JSVM_ReleaseBackingStore(backingStore);
        return nullptr;
    }
    // 6. 释放句柄。targetSab持有自己的引用，不受影响
    OH_JSVM_ReleaseBackingStore(backingStore);

    void *targetData = nullptr;
    OH_JSVM_GetSharedArrayBufferInfo(env, targetSab, &targetData, nullptr, nullptr);
    bool isSab = false;
    OH_JSVM_IsSharedArrayBuffer(env, targetSab, &isSab);
    OH_LOG_INFO(LOG_APP, "JSVM rebuild SharedArrayBuffer in another VM: isSharedArrayBuffer=%{public}d, "
                "marker=%{public}d", isSab,
                targetData != nullptr ? static_cast<uint8_t *>(targetData)[0] : -1);
    return targetSab;
}

// CreateSharedArrayBuffer注册回调
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = CreateSharedArrayBuffer},
    {.data = nullptr, .callback = BackingStoreAcrossVM},
};
static JSVM_CallbackStruct *method = param;
// 方法别名，供JS调用
static JSVM_PropertyDescriptor descriptor[] = {
    {"createSharedArrayBuffer", nullptr, method, nullptr, nullptr, nullptr, JSVM_DEFAULT},
    {"backingStoreAcrossVM", nullptr, method + 1, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// 样例测试js
const char *SRC_CALL_NATIVE = R"JS(
let view = createSharedArrayBuffer();
if (view[0] !== 0 || view[15] !== 15) {
    throw new Error('bad Uint8Array over SharedArrayBuffer');
}
view[0] = 100;
backingStoreAcrossVM();
)JS";
```

预期结果：
```txt
JSVM CreateSharedArrayBuffer: success, byteLength=16
JSVM BackingStore survives source VM: length=8, isShared=1, marker=90
JSVM rebuild SharedArrayBuffer in another VM: isSharedArrayBuffer=1, marker=90
```
