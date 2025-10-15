# Performing Lifecycle Management Using Node-API
<!--Kit: NDK-->
<!--Subsystem: arkcompiler-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @fang-jinxu-->

## Introduction

In Node-API, **napi_value** is an abstract data type that represents an ArkTS value of any type, which includes the basic type (such as number, string, or Boolean) and the composite type (such as array, function, or object).

The **napi_value** lifecycle is closely related to the lifecycle of the ArkTS value. When an ArkTS value is garbage-collected, the **napi_value** associated with it is no longer valid. Avoid using the **napi_value** when the ArkTS value no longer exists.

Scope is used to manage the **napi_value** lifecycle in the framework layer. You can use **napi_open_handle_scope** to open a scope and use **napi_close_handle_scope** to close it. By creating a **napi_value** in a scope, you can ensure that the **napi_value** is automatically released when the scope ends. This helps prevent memory leaks.

**napi_ref** is a Node-API type used to manage the **napi_value** lifecycle. It allows reference to a **napi_value** during its lifecycle, even if the value is beyond its original context. The reference allows a **napi_value** to be shared in different contexts and released in a timely manner.

## Basic Concepts

Node-API provides APIs for creating and manipulating ArkTS objects, managing references to and lifecycle of the ArkTS objects, and registering garbage collection (GC) callbacks in C/C++. Before you get started, you need to understand the following concepts:

- **Scope**: Used to manage the lifecycle of ArkTS objects. Object handles created in a scope can be used only within the scope by default. After the scope is closed, the objects created in the scope cannot be accessed unless they are explicitly escaped from the current scope.
- Reference management: Node-API provides APIs for creating, deleting, and managing object references to extend the lifecycle of objects and prevent the use-after-free issues. In addition, reference management also helps prevent memory leaks.
- Escapable scope: used to return the values created within the **escapable_handle_scope** to a parent scope. It is created by **napi_open_escapable_handle_scope** and closed by **napi_close_escapable_handle_scope**.
- GC callback: You can register GC callbacks to perform specific cleanup operations when ArkTS objects are garbage-collected.

Understanding these concepts helps you securely and effectively manipulate ArkTS objects in C/C++ and perform object lifecycle management.

## Available APIs

The following table lists the APIs for ArkTS object lifecycle management.  
| API| Description|
| -------- | -------- |
| napi_open_handle_scope<br>napi_close_handle_scope| Opens a scope and closes a scope respectively. When processing ArkTS objects with Node-API, you need to create a temporary scope to store object references so that the objects can be correctly accessed during the execution and closed after the execution.|
| napi_open_escapable_handle_scope<br>napi_close_escapable_handle_scope| Creates an escapable scope so that the ArkTS object created in the native function can be correctly returned to the external ArkTS environment that calls the function.|
| napi_escape_handle | Promotes the handle to an ArkTS object so that it is valid for the lifetime of its parent scope.|
| napi_create_reference<br>napi_delete_reference| Creates a reference to a value to extend the ArkTS object's lifespan and deletes a reference respectively.|
| napi_reference_ref<br>napi_reference_unref| Increments the reference count and decrements the reference count respectively.|
| napi_get_reference_value | Obtains the ArkTS object associated with the reference.|
| napi_add_finalizer | Adds a **napi_finalize** callback, which will be called to clean up or release resources before the ArkTS object is garbage-collected.|

## Example

If you are just starting out with Node-API, see [Node-API Development Process](use-napi-process.md). The following demonstrates only the C++ and ArkTS code related to lifecycle management.

### napi_open_handle_scope and napi_close_handle_scope

Use **napi_open_handle_scope** to create a context and use **napi_close_handle_scope** to close the context. You can use these two APIs to manage the **napi_value** lifecycle of an ArkTS object, which prevents the object from being incorrectly garbage-collected. 
Properly using these two APIs can minimize lifecycle and prevent memory leaks.

For details about the code, see:
[Lifecycle Management](napi-guidelines.md#lifecycle-management)

CPP code:

```cpp
#include "napi/native_api.h"

static napi_value HandleScopeTest(napi_env env, napi_callback_info info)
{
    // Call napi_open_handle_scope to open a scope.
    napi_handle_scope scope;
    napi_open_handle_scope(env, &scope);
    // Create an object within the scope.
    napi_value obj = nullptr;
    napi_create_object(env, &obj);
    // Add a property to the object.
    napi_value value = nullptr;
    napi_create_string_utf8(env, "handleScope", NAPI_AUTO_LENGTH, &value);
    napi_set_named_property(env, obj, "key", value);
    // Obtain the object property in the scope and return it.
    napi_value result = nullptr;
    napi_get_named_property(env, obj, "key", &result);
    // Close the scope. Then, the object handle created within the scope is automatically released.
    napi_close_handle_scope(env, scope);
    // The value of result is 'handleScope'.
    return result;
}

static napi_value HandleScope(napi_env env, napi_callback_info info)
{
    // Call napi_open_handle_scope to open a scope.
    napi_handle_scope scope;
    napi_open_handle_scope(env, &scope);
    // Create an object within the scope.
    napi_value obj = nullptr;
    napi_create_object(env, &obj);
    // Add a property to the object.
    napi_value value = nullptr;
    napi_create_string_utf8(env, "handleScope", NAPI_AUTO_LENGTH, &value);
    napi_set_named_property(env, obj, "key", value);
    // Close the scope. Then, the object handle created within the scope is automatically released.
    napi_close_handle_scope(env, scope);
    // Obtain and return the object property outside the scope. In this example, "undefined" is obtained.
    napi_value result = nullptr;
    napi_get_named_property(env, obj, "key", &result);
    return result;
}
```
<!-- @[napi_open_close_handle_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/cpp/napi_init.cpp) -->

API declaration:

```ts
// index.d.ts
export const handleScopeTest: () => string;
export const handleScope: () => string;
```
<!-- @[napi_open_close_handle_scope_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS code:

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
try {
  hilog.info(0x0000, 'testTag', 'Test Node-API handleScopeTest: %{public}s', testNapi.handleScopeTest());
  hilog.info(0x0000, 'testTag', 'Test Node-API handleScope: %{public}s', testNapi.handleScope());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'Test Node-API handleScopeTest errorCode: %{public}s, errorMessage: %{public}s', error.code, error.message);
}
```
<!-- @[ark_napi_open_close_handle_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/ets/pages/Index.ets) -->

### napi_open_escapable_handle_scope, napi_close_escapable_handle_scope, and napi_escape_handle

Use **napi_open_escapable_handle_scope** to open an escapable scope, which allows the declared values in the scope to be returned to the parent scope. The scope must be closed using **napi_close_escapable_handle_scope**. Use **napi_escape_handle** to promote the lifecycle of an ArkTS object so that it is valid for the lifetime of the parent scope.
These APIs are helpful for managing ArkTS objects more flexibly in C/C++, especially when passing cross-scope values.

CPP code:

```cpp
#include "napi/native_api.h"

static napi_value EscapableHandleScopeTest(napi_env env, napi_callback_info info)
{
    // Create an escapable scope.
    napi_escapable_handle_scope scope;
    napi_open_escapable_handle_scope(env, &scope);
    // Create an object within the escapable scope.
    napi_value obj = nullptr;
    napi_create_object(env, &obj);
    // Add a property to the object.
    napi_value value = nullptr;
    napi_create_string_utf8(env, "Test napi_escapable_handle_scope", NAPI_AUTO_LENGTH, &value);
    napi_set_named_property(env, obj, "key", value);
    // Call napi_escape_handle to promote the ArkTS object handle to make it valid with the lifetime of the outer scope.
    napi_value escapedObj = nullptr;
    napi_escape_handle(env, scope, obj, &escapedObj);
    // Close the escapable scope to clear resources.
    napi_close_escapable_handle_scope(env, scope);
    // Obtain and return the property of the object whose scope is promoted. You can also obtain napi_escapable_handle_scope here.
    napi_value result = nullptr;
    // To verify the escape implementation, obtain the object property here. "undefined" is obtained.
    napi_get_named_property(env, escapedObj, "key", &result);
    return result;
}
```
<!-- @[napi_open_close_escapable_handle_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/cpp/napi_init.cpp) -->

API declaration:

```ts
// index.d.ts
export const escapableHandleScopeTest: () => string;
```
<!-- @[napi_open_close_escapable_handle_scope_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS code:

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
try {
  hilog.info(0x0000, 'testTag', 'Test Node-API EscapableHandleScopeTest: %{public}s', testNapi.escapableHandleScopeTest());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'Test Node-API EscapableHandleScopeTest errorCode: %{public}s, errorMessage: %{public}s', error.code, error.message);
}
```
<!-- @[ark_napi_open_close_escapable_handle_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/ets/pages/Index.ets) -->

### napi_create_reference and napi_delete_reference

Use **napi_create_reference** to create a reference for an object to extend its lifespan. The caller needs to manage the reference lifespan. Use **napi_delete_reference** to delete a reference.

### napi_reference_ref and napi_reference_unref

Use **napi_reference_ref** to increment the reference count and use **napi_reference_unref** to decrement the reference count, and return the new count value.

### napi_get_reference_value

Use **napi_get_reference_value** to obtain the ArkTS object associated with the reference.

> **NOTE**
>
> The release of a weak reference (**napi_ref** whose reference count is 0) and GC of a JS object do not occur at the same time.
>
> Consequently, the JS object may be garbage-collected before the weak reference is released.
>
> As a result, calling this API may yield a null pointer even if **napi_ref** is valid.

### napi_add_finalizer

Use **napi_add_finalizer** to add a **napi_finalizer** callback, which will be called when the ArkTS object is garbage-collected.

CPP code:

```cpp
// log.h is used to print logs in C++.
#include "hilog/log.h"
#include "napi/native_api.h"
// Create a pointer to napi_ref to store the created reference. Before calling napi_add_finalizer, allocate a variable of the napi_ref type and pass its address as the result parameter.
napi_ref gRefFinalizer = nullptr;

// Create a pointer to napi_ref to store the created reference. Before calling napi_create_reference, allocate a variable of the napi_ref type and pass its address as the result parameter.
napi_ref gRef = nullptr;

void Finalizer(napi_env env, void *data, void *hint)
{
    // Clear resources.
    OH_LOG_INFO(LOG_APP, "Test Node-API Use Finalizer to release resources.");
    // Release resources.
}

static napi_value AddFinalizer(napi_env env, napi_callback_info info)
{
    napi_value obj = nullptr;
    napi_status status = napi_create_object(env, &obj);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_create_object fail");
        return nullptr;
    }
    napi_value value = nullptr;
    status = napi_create_string_utf8(env, "AddFinalizer", NAPI_AUTO_LENGTH, &value);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_create_string_utf8 fail");
        return nullptr;
    }
    // Add a property to the object.
    status = napi_set_named_property(env, obj, "key", value);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_set_named_property fail");
        return nullptr;
    }

    // Register a Finalizer to release resources.
    void *data = {};
    status = napi_add_finalizer(env, obj, data, Finalizer, nullptr, &gRefFinalizer);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_add_finalizer fail");
        return nullptr;
    }

    return obj;
}

static napi_value CreateReference(napi_env env, napi_callback_info info)
{
    napi_value obj = nullptr;
    napi_status status = napi_create_object(env, &obj);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_create_object fail");
        return nullptr;
    }
    napi_value value = nullptr;
    status = napi_create_string_utf8(env, "CreateReference", NAPI_AUTO_LENGTH, &value);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_create_string_utf8 fail");
        return nullptr;
    }
    // Add a property to the object.
    status = napi_set_named_property(env, obj, "key", value);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_set_named_property fail");
        return nullptr;
    }
    // Create a reference to the ArkTS object.
    status = napi_create_reference(env, obj, 1, &gRef);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_create_reference fail");
        return nullptr;
    }
    // Increment the reference count and return the new reference count.
    uint32_t result = 0;
    status = napi_reference_ref(env, gRef, &result);
    OH_LOG_INFO(LOG_APP, "Test Node-API napi_reference_ref, count = %{public}d.", result);
    if (status != napi_ok || result != 2) {
        // If the reference count passed in does not increase, throw an error.
        napi_throw_error(env, nullptr, "napi_reference_ref fail");
        return nullptr;
    }
    return obj;
}

static napi_value UseReference(napi_env env, napi_callback_info info)
{
    napi_value obj = nullptr;
    // Call napi_get_reference_value to obtain the referenced ArkTS object.
    napi_status status = napi_get_reference_value(env, gRef, &obj);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_get_reference_value fail");
        return nullptr;
    }
    // Return the obtained object.
    return obj;
}

static napi_value DeleteReference(napi_env env, napi_callback_info info)
{
    // Decrement the reference count and return the new reference count.
    uint32_t result = 0;
    napi_value count = nullptr;
    napi_status status = napi_reference_unref(env, gRef, &result);
    OH_LOG_INFO(LOG_APP, "Test Node-API napi_reference_unref, count = %{public}d.", result);
    if (status != napi_ok || result != 1) {
        // If the reference count passed in does not decrease, throw an error.
        napi_throw_error(env, nullptr, "napi_reference_unref fail");
        return nullptr;
    }

    // Call napi_delete_reference to delete the reference to the ArkTS object.
    status = napi_delete_reference(env, gRef);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_delete_reference fail");
        return nullptr;
    }

    status = napi_delete_reference(env, gRefFinalizer);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_delete_reference fail");
        return nullptr;
    }
    napi_value returnResult = nullptr;
    status = napi_create_string_utf8(env, "napi_delete_reference success", NAPI_AUTO_LENGTH, &returnResult);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_create_string_utf8 fail");
        return nullptr;
    }
    return returnResult;
}
```
<!-- @[napi_create_delete_reference](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/cpp/napi_init.cpp) -->

API declaration:

```ts
// index.d.ts
export const addFinalizer: () => Object | undefined;
export const createReference: () => Object | undefined;
export const useReference: () => Object | undefined;
export const deleteReference: () => string | undefined;
```
<!-- @[napi_create_delete_reference_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS code:

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
try {
  hilog.info(0x0000, 'testTag', 'Test Node-API addFinalizer: %{public}s', JSON.stringify(testNapi.addFinalizer()));
  hilog.info(0x0000, 'testTag', 'Test Node-API createReference: %{public}s', JSON.stringify(testNapi.createReference()));
  hilog.info(0x0000, 'testTag', 'Test Node-API useReference: %{public}s', JSON.stringify(testNapi.useReference()));
  hilog.info(0x0000, 'testTag', 'Test Node-API deleteReference: %{public}s', testNapi.deleteReference());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'Test Node-API ReferenceTest errorCode: %{public}s, errorMessage: %{public}s', error.code, error.message);
}
```
<!-- @[ark_napi_create_delete_reference](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPILifeCycle/entry/src/main/ets/pages/Index.ets) -->

To print logs in the native CPP, add the following information to the **CMakeLists.txt** file and add the header file by using **#include "hilog/log.h"**.

```text
// CMakeLists.txt
add_definitions( "-DLOG_DOMAIN=0xd0d0" )
add_definitions( "-DLOG_TAG=\"testTag\"" )
target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
```
