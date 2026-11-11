---
kits: ["NDK / Native Development Kit"]
description: "介绍使用Node-API扩展接口限制微任务的执行，控制微任务队列的执行时机，使微任务在原生逻辑完成后统一执行。"
keywords: [Node-API, 微任务, napi_open_microtask_scope, napi_close_microtask_scope, Promise回调, 微任务作用域]
doctype: guide
status: active
---

# 使用扩展的Node-API接口限制微任务的执行

<!--Kit: NDK-->
<!--Subsystem: arkcompiler-->
<!--Owner: @shilei123; @liudachuan3-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

Node-API扩展接口`napi_open_microtask_scope`用于打开微任务作用域，`napi_close_microtask_scope`用于关闭微任务作用域。

>**注意：**
>
> 微任务作用域打开期间，微任务不会被执行，待作用域关闭时同步执行。同一运行时中只能打开一个微任务作用域，不支持嵌套打开；微任务作用域为运行时级，同一运行时中创建的多个上下文环境共享该作用域。长时间保持微任务作用域打开会限制Promise回调等微任务驱动的逻辑，建议在原生逻辑完成后及时关闭。

## 场景介绍

在原生与ArkTS交互过程中，`napi_call_function`、`napi_new_instance`、`napi_resolve_deferred`、`napi_reject_deferred`四个Node-API接口执行完成后会自动清空微任务队列，Promise的回调可能在原生逻辑执行中途被调用。当原生侧需要在一次调用链中多次进入ArkTS，并希望期间产生的微任务在所有原生逻辑完成后统一执行时，可以通过`napi_open_microtask_scope`打开微任务作用域进行控制。

## 微任务作用域的打开与关闭

| 接口 | 描述 | 起始支持版本 |
| -------- | -------- | -------- |
| napi_open_microtask_scope | 打开微任务作用域，限制微任务的执行。 | 26.1.0 |
| napi_close_microtask_scope | 关闭微任务作用域，并同步执行作用域打开期间累积的微任务。 | 26.1.0 |

>**注意：**
>
>1. 微任务作用域不支持嵌套打开。在已打开微任务作用域的情况下再次调用`napi_open_microtask_scope`，接口返回napi_invalid_arg。
>
>2. 在未打开微任务作用域的情况下调用`napi_close_microtask_scope`（包括对同一作用域重复关闭），接口返回napi_invalid_arg。
>
>3. 微任务只被限制，不会丢失：作用域打开期间累积的微任务，会在`napi_close_microtask_scope`关闭作用域时同步执行完毕。
>
>4. 若调用`napi_open_microtask_scope`前或调用过程中存在未捕获的ArkTS异常，接口返回napi_pending_exception，此时不会打开微任务作用域，出参scope不会被赋值。可通过`napi_get_and_clear_last_exception`处理异常后重新调用该接口。
>
>5. 若调用`napi_close_microtask_scope`前或调用过程中存在未捕获的ArkTS异常，接口返回napi_pending_exception，此时微任务作用域已完成关闭，异常仍保留在环境中，可通过`napi_get_and_clear_last_exception`处理异常。尚未执行的累积微任务不会丢失，将保留在微任务队列中，待异常处理完成后，在后续微任务队列清空时执行。

## 示例代码

- cpp部分代码

  <!-- @[napi_open_microtask_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/cpp/napi_init.cpp) -->

  ```c++
  // napi_open_microtask_scope & napi_close_microtask_scope
  // 使用C++的RAII机制管理微任务作用域，避免遗漏关闭
  // 仅用作示例，也可以通过其他方式进行封装，或直接使用原始接口
  class MyMicrotaskScope {
      napi_env env_{};
      napi_microtask_scope scope_{};

  public:
      explicit MyMicrotaskScope(napi_env env) : env_(env)
      {
          if (napi_open_microtask_scope(env_, &scope_) != napi_ok) {
              // 失败时，进行一些必要的错误处理，此处省略。
              // 常见失败原因：
              // 1. env不是有效的Node-API执行上下文（如：env参数为nullptr）。
              // 2. 已存在打开的微任务作用域，微任务作用域不支持嵌套打开。
          }
      }

      // 查询微任务作用域是否成功打开
      bool IsValid() const { return scope_ != nullptr; }

      ~MyMicrotaskScope()
      {
          Close();
      }

      inline void Close()
      {
          if (scope_ == nullptr) {
              return;
          }
          // 关闭微任务作用域，并统一执行作用域打开期间累积的微任务
          if (napi_close_microtask_scope(env_, scope_) != napi_ok) {
              // 失败时，进行一些必要的错误处理，此处省略。
              // 常见失败原因：
              // 1. 没有处于打开状态的微任务作用域（如：重复关闭）。
              // 2. env不是有效的Node-API执行上下文（如：空指针）。
              // 3. scope不是有效的微任务作用域句柄（如：空指针）。
              // 4. 调用该接口前或调用过程中出现未捕获的ArkTS异常（此时作用域已完成关闭，异常仍保留在环境中，可按需处理）。
          }
          scope_ = nullptr;
      }
  };

  // Promise的then回调，执行时通过data指针置位调用方传入的标记
  static napi_value OnFulfilled(napi_env env, napi_callback_info info)
  {
      // 取出创建回调时传入的data指针（指向调用方的bool标记）
      void* data = nullptr;
      napi_get_cb_info(env, info, nullptr, nullptr, nullptr, &data);
      if (data != nullptr) {
          *static_cast<bool*>(data) = true;
      }
      return nullptr;
  }

  // returnCode位含义：bit0=1 作用域打开期间then回调未执行（被限制执行）
  //                   bit1=1 作用域关闭后then回调已执行
  static constexpr int32_t BIT_REACTION_NOT_CALLED_IN_SCOPE = 1 << 0;
  static constexpr int32_t BIT_REACTION_CALLED_AFTER_CLOSE = 1 << 1;

  static napi_value DeferredMicrotask(napi_env env, napi_callback_info info)
  {
      int32_t returnCode = 0;
      // then回调是否已执行的标记，经napi_create_function的data参数传给回调，避免使用全局状态
      bool reactionCalled = false;

      // 创建Promise并注册then回调
      napi_deferred deferred = nullptr;
      napi_value promise = nullptr;
      napi_create_promise(env, &deferred, &promise);

      napi_value callback = nullptr;
      napi_create_function(env, "onFulfilled", NAPI_AUTO_LENGTH, OnFulfilled, &reactionCalled, &callback);
      napi_value key = nullptr;
      napi_value thenFunction = nullptr;
      napi_create_string_utf8(env, "then", NAPI_AUTO_LENGTH, &key);
      napi_get_property(env, promise, key, &thenFunction);

      {
          // 打开微任务作用域，期间触发的微任务被限制执行
          MyMicrotaskScope scope(env);
          // 打开失败（如嵌套打开）时，微任务作用域未生效，示例语义不成立，直接返回错误
          if (!scope.IsValid()) {
              napi_throw_error(env, nullptr, "napi_open_microtask_scope failed");
              return nullptr;
          }

          napi_value callResult = nullptr;
          napi_call_function(env, promise, thenFunction, 1, &callback, &callResult);
          napi_value resolution = nullptr;
          napi_create_int32(env, 1, &resolution);
          napi_resolve_deferred(env, deferred, resolution);

          // 微任务作用域打开期间，then回调不会随接口返回被立即执行
          if (!reactionCalled) {
              returnCode |= BIT_REACTION_NOT_CALLED_IN_SCOPE;
          }
          OH_LOG_INFO(LOG_APP, "in microtask scope: reactionCalled = %{public}d, returnCode = %{public}d",
              reactionCalled, returnCode);

          // 关闭微任务作用域，累积的微任务统一执行
          scope.Close();
      }

      // 作用域关闭后，then回调已被执行
      if (reactionCalled) {
          returnCode |= BIT_REACTION_CALLED_AFTER_CLOSE;
      }
      OH_LOG_INFO(LOG_APP, "after scope closed: reactionCalled = %{public}d, returnCode = %{public}d",
          reactionCalled, returnCode);

      // 预期返回3（二进制0b11）：bit0与bit1同时置位，证明then回调在作用域打开期间被限制、关闭后统一执行
      napi_value returnResult = nullptr;
      napi_create_int32(env, returnCode, &returnResult);
      return returnResult;
  }
  ```

- 模块注册

  本示例的模块注册方式如下（仅注册本示例使用的`deferredMicrotask`接口，完整示例可参见[NodeAPIPromise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/cpp/napi_init.cpp)）：

  ```c++
  // napi_init.cpp
  EXTERN_C_START
  static napi_value Init(napi_env env, napi_value exports)
  {
      napi_property_descriptor desc[] = {
          {"deferredMicrotask", nullptr, DeferredMicrotask, nullptr, nullptr, nullptr, napi_default, nullptr}};
      napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
      return exports;
  }
  EXTERN_C_END

  static napi_module demoModule = {
      .nm_version = 1,
      .nm_flags = 0,
      .nm_filename = nullptr,
      .nm_register_func = Init,
      .nm_modname = "entry",
      .nm_priv = ((void *)0),
      .reserved = {0},
  };

  extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
  {
      napi_module_register(&demoModule);
  }
  ```

- 编译配置

  以上cpp代码中使用了OH_LOG_INFO打印日志，需在CMakeLists.txt文件中添加以下配置信息（并添加头文件：#include "hilog/log.h"）：

  ```text
  // CMakeLists.txt
  add_definitions( "-DLOG_DOMAIN=0xd0d0" )
  add_definitions( "-DLOG_TAG=\"testTag\"" )
  target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
  ```

- 接口声明

  <!-- @[napi_open_microtask_scope_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/cpp/types/libentry/Index.d.ts) -->

  ```ts
  export const deferredMicrotask: () => number; // napi_open_microtask_scope & napi_close_microtask_scope
  ```

- ArkTS侧示例代码

  ArkTS侧示例代码所需的模块导入如下：

  ```ts
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import testNapi from 'libentry.so';
  ```

  <!-- @[ark_napi_open_microtask_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/ets/pages/Index.ets) -->

  ```ts
  // napi_open_microtask_scope & napi_close_microtask_scope
  // 返回值位含义：bit0=1 作用域打开期间then回调未执行，bit1=1 作用域关闭后then回调已执行
  let value = testNapi.deferredMicrotask(); // 预期结果: 3（二进制0b11）
  hilog.info(0x0000, 'Node-API', 'deferredMicrotask %{public}s', value.toString());
  // ...
  ```

`deferredMicrotask`的返回值可用于验证微任务作用域的效果：

- 不使用微任务作用域：`napi_resolve_deferred`执行后，then回调会立即执行，`deferredMicrotask`的返回值为2。
- 使用微任务作用域：then回调被限制执行，待作用域关闭时同步执行，`deferredMicrotask`的返回值为3（二进制0b11）。其中，bit0=1表示作用域打开期间then回调未执行，bit1=1表示作用域关闭后then回调已执行。

上述两处OH_LOG_INFO日志可用于对比验证：第一条日志在微任务作用域打开期间输出，第二条日志在微任务作用域关闭后输出。预期输出如下：

| 场景 | 第一条日志 | 第二条日志 |
| -------- | -------- | -------- |
| 使用微任务作用域 | reactionCalled = 0，returnCode = 1 | reactionCalled = 1，returnCode = 3 |
| 不使用微任务作用域（去掉MyMicrotaskScope） | reactionCalled = 1，returnCode = 0 | reactionCalled = 1，returnCode = 2 |
