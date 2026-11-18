---
kits: ["NDK"]
description: "Describes how to use Node-API extensions to defer microtask execution and control when the microtask queue is drained so that microtasks execute together after native logic completes."
keywords: [Node-API, microtasks, napi_open_microtask_scope, napi_close_microtask_scope, Promise callbacks, microtask scope]
doctype: guide
status: active
---

# Deferring Microtask Execution Using Node-API Extensions

<!--Kit: NDK-->
<!--Subsystem: arkcompiler-->
<!--Owner: @shilei123; @liudachuan3-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e1179fcf9f901221cede77c428024df1bad69e0a translatedAt=2026-11-09T08:52:17.377Z nl=1 -->

The Node-API extension `napi_open_microtask_scope` opens a microtask scope, and `napi_close_microtask_scope` closes it.

>**CAUTION**
>
> Microtasks do not execute while a microtask scope is open. They execute synchronously when the scope is closed. Only one microtask scope can be open in a runtime at a time; nesting is not supported. A microtask scope is runtime-wide and shared by all contexts created in the same runtime. Keeping the scope open for a long time defers microtask-driven logic such as Promise callbacks. Close it promptly after the native logic completes.

## When to Use

During interaction between native code and ArkTS, `napi_call_function`, `napi_new_instance`, `napi_resolve_deferred`, and `napi_reject_deferred` automatically drain the microtask queue after execution. As a result, Promise callbacks may run before the native logic completes. If native code needs to enter ArkTS multiple times in a single call chain and the resulting microtasks should execute together after all native logic completes, call `napi_open_microtask_scope` to open a microtask scope.

## Opening and Closing a Microtask Scope

| API | Description | Supported Since |
| -------- | -------- | -------- |
| napi_open_microtask_scope | Opens a microtask scope to defer microtask execution. | 26.1.0 |
| napi_close_microtask_scope | Closes a microtask scope and synchronously executes the microtasks accumulated while it was open. | 26.1.0 |

>**CAUTION**
>
>1. Microtask scopes cannot be nested. Calling `napi_open_microtask_scope` when a microtask scope is already open returns `napi_invalid_arg`.
>
>2. Calling `napi_close_microtask_scope` when no microtask scope is open (including closing the same scope more than once) returns `napi_invalid_arg`.
>
>3. Microtasks are deferred, not lost. Microtasks accumulated while the scope is open execute synchronously to completion when `napi_close_microtask_scope` closes it.
>
>4. If an uncaught ArkTS exception exists before or occurs during a call to `napi_open_microtask_scope`, the API returns `napi_pending_exception`. The microtask scope is not opened, and the output parameter `scope` is not assigned a value. Handle the exception with `napi_get_and_clear_last_exception` and call the API again.
>
>5. If an uncaught ArkTS exception exists before or occurs during a call to `napi_close_microtask_scope`, the API returns `napi_pending_exception`. The microtask scope has already been closed, but the exception remains in the environment. Handle it with `napi_get_and_clear_last_exception`. Accumulated microtasks that have not yet executed are not lost: they remain in the microtask queue and execute when the queue is subsequently drained after the exception is handled.

## Sample Code

- C++ code

  <!-- @[napi_open_microtask_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/cpp/napi_init.cpp) -->

  ```c++
  // napi_open_microtask_scope & napi_close_microtask_scope
  // Use C++ RAII to manage the microtask scope so that it is always closed.
  // This is only an example. You can use another wrapper or call the underlying APIs directly.
  class MyMicrotaskScope {
      napi_env env_{};
      napi_microtask_scope scope_{};

  public:
      explicit MyMicrotaskScope(napi_env env) : env_(env)
      {
          if (napi_open_microtask_scope(env_, &scope_) != napi_ok) {
              // Perform the necessary error handling on failure (omitted here).
              // Common causes of failure:
              // 1. env is not a valid Node-API execution context (for example, env is nullptr).
              // 2. A microtask scope is already open. Nested microtask scopes are not supported.
          }
      }

      // Check whether the microtask scope was opened successfully.
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
          // Close the microtask scope and execute all microtasks accumulated while it was open.
          if (napi_close_microtask_scope(env_, scope_) != napi_ok) {
              // Perform the necessary error handling on failure (omitted here).
              // Common causes of failure:
              // 1. No microtask scope is open (for example, the scope is closed again).
              // 2. env is not a valid Node-API execution context (for example, it is a null pointer).
              // 3. scope is not a valid microtask scope handle (for example, it is a null pointer).
              // 4. An uncaught ArkTS exception exists before or occurs during this call. The scope is already closed, but the exception remains in the environment and can be handled as needed.
          }
          scope_ = nullptr;
      }
  };

  // Promise then callback: set the flag supplied by the caller through the data pointer.
  static napi_value OnFulfilled(napi_env env, napi_callback_info info)
  {
      // Obtain the data pointer passed when the callback was created (it points to the caller's bool flag).
      void* data = nullptr;
      napi_get_cb_info(env, info, nullptr, nullptr, nullptr, &data);
      if (data != nullptr) {
          *static_cast<bool*>(data) = true;
      }
      return nullptr;
  }

  // returnCode bits: bit0=1 means the then callback did not execute while the scope was open (execution was deferred).
  //                  bit1=1 means the then callback executed after the scope was closed.
  static constexpr int32_t BIT_REACTION_NOT_CALLED_IN_SCOPE = 1 << 0;
  static constexpr int32_t BIT_REACTION_CALLED_AFTER_CLOSE = 1 << 1;

  static napi_value DeferredMicrotask(napi_env env, napi_callback_info info)
  {
      int32_t returnCode = 0;
      // Pass the then callback execution flag through the data parameter of napi_create_function to avoid global state.
      bool reactionCalled = false;

      // Create a Promise and register its then callback.
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
          // Open a microtask scope to defer microtasks triggered while it is open.
          MyMicrotaskScope scope(env);
          // If opening fails (for example, due to nesting), the scope is inactive and the example cannot work as intended. Return an error.
          if (!scope.IsValid()) {
              napi_throw_error(env, nullptr, "napi_open_microtask_scope failed");
              return nullptr;
          }

          napi_value callResult = nullptr;
          napi_call_function(env, promise, thenFunction, 1, &callback, &callResult);
          napi_value resolution = nullptr;
          napi_create_int32(env, 1, &resolution);
          napi_resolve_deferred(env, deferred, resolution);

          // While the microtask scope is open, the then callback does not execute immediately when the API returns.
          if (!reactionCalled) {
              returnCode |= BIT_REACTION_NOT_CALLED_IN_SCOPE;
          }
          OH_LOG_INFO(LOG_APP, "in microtask scope: reactionCalled = %{public}d, returnCode = %{public}d",
              reactionCalled, returnCode);

          // Close the microtask scope and execute the accumulated microtasks together.
          scope.Close();
      }

      // The then callback has executed after the scope is closed.
      if (reactionCalled) {
          returnCode |= BIT_REACTION_CALLED_AFTER_CLOSE;
      }
      OH_LOG_INFO(LOG_APP, "after scope closed: reactionCalled = %{public}d, returnCode = %{public}d",
          reactionCalled, returnCode);

      // Expect 3 (binary 0b11): both bit0 and bit1 are set, showing that the then callback was deferred while the scope was open and executed on closing.
      napi_value returnResult = nullptr;
      napi_create_int32(env, returnCode, &returnResult);
      return returnResult;
  }
  ```

- Module registration

  Register the module as follows (only the `deferredMicrotask` API used in this example is registered; for the complete example, see [NodeAPIPromise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/cpp/napi_init.cpp)):

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

- Build configuration

  The preceding C++ code uses OH_LOG_INFO to print logs. Add the following configuration to CMakeLists.txt and include the header file #include "hilog/log.h":

  ```text
  // CMakeLists.txt
  add_definitions( "-DLOG_DOMAIN=0xd0d0" )
  add_definitions( "-DLOG_TAG=\"testTag\"" )
  target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
  ```

- API declaration

  <!-- @[napi_open_microtask_scope_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/cpp/types/libentry/Index.d.ts) -->

  ```ts
  export const deferredMicrotask: () => number; // napi_open_microtask_scope & napi_close_microtask_scope
  ```

- ArkTS sample code

  Import the following modules for the ArkTS sample code:

  ```ts
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import testNapi from 'libentry.so';
  ```

  <!-- @[ark_napi_open_microtask_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIPromise/entry/src/main/ets/pages/Index.ets) -->

  ```ts
  // napi_open_microtask_scope & napi_close_microtask_scope
  // Return value bits: bit0=1 means the then callback did not execute while the scope was open; bit1=1 means it executed after the scope was closed.
  let value = testNapi.deferredMicrotask(); // Expected result: 3 (binary 0b11).
  hilog.info(0x0000, 'Node-API', 'deferredMicrotask %{public}s', value.toString());
  // ...
  ```

The return value of `deferredMicrotask` can be used to verify the effect of the microtask scope:

- Without a microtask scope: The then callback executes immediately after `napi_resolve_deferred` executes, and `deferredMicrotask` returns 2.
- With a microtask scope: The then callback is deferred and executes synchronously when the scope is closed. `deferredMicrotask` returns 3 (binary 0b11), where bit0=1 indicates that the then callback did not execute while the scope was open, and bit1=1 indicates that it executed after the scope was closed.

The two OH_LOG_INFO logs above can be compared to verify the behavior. The first is printed while the microtask scope is open, and the second after it is closed. The expected output is as follows:

| Scenario | First Log | Second Log |
| -------- | -------- | -------- |
| With a microtask scope | reactionCalled = 0, returnCode = 1 | reactionCalled = 1, returnCode = 3 |
| Without a microtask scope (remove MyMicrotaskScope) | reactionCalled = 1, returnCode = 0 | reactionCalled = 1, returnCode = 2 |
