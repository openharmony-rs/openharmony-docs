# Working with Class Using Node-API
<!--Kit: NDK-->
<!--Subsystem: arkcompiler-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @fang-jinxu-->

## Introduction

Node-API provides APIs for managing ArkTS classes, for example, defining an ArkTS class and creating an ArkTS instance, in C/C++.

## Basic Concepts

To begin with, it is important to understand the following basic concepts:

- Class: a template used to create an object. It provides a way to define object properties and methods in a structured manner. Classes in ArkTS are based on prototypes and added with unique syntax and semantics.
- Instance: an object created from a class. A class defines the structure and behavior of an object, and an instance is a specific representation of a class. Instantiating a class allows access to the properties and methods defined in the class. Each instance has its own property values.

## Available APIs

The following table lists the APIs for manipulating ArkTS classes.  
| API| Description|
| -------- | -------- |
| napi_new_instance | Creates an instance based on the given constructor.|
| napi_get_new_target | Obtains the **new.target** of the constructor call.|
| napi_define_class | Defines an ArkTS class corresponding to the C/C++ class. This API binds an ArkTS class and a C/C++ class.|
| napi_wrap | Wraps a native object into an ArkTS object. This API allows the methods and properties of a native object to be called from ArkTS.|
| napi_unwrap | Unwraps the native object from an ArkTS object.|
| napi_remove_wrap | Removes the wrapping after the native object is unwrapped from an ArkTS object.|

## Example

If you are just starting out with Node-API, see [Node-API Development Process](use-napi-process.md). The following demonstrates only the C++ and ArkTS code involved in the class-related APIs.

### napi_new_instance

Call **napi_new_instance** to create an ArkTS instance with the given constructor. This API returns an instance that can be called from ArkTS.

> **NOTE**
>
> If **constructor** is not of the function type, **napi_function_expected** will be returned.

CPP code:

```cpp
static napi_value NewInstance(napi_env env, napi_callback_info info)
{
    // Pass in and parse parameters. The first parameter is the constructor, and the second parameter is the parameters of the constructor.
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
    // Call napi_new_instance to create an instance and return the instance created.
    napi_value result = nullptr;
    napi_new_instance(env, args[0], 1, &args[1], &result);
    return result;
}
```
<!-- @[napi_new_instance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIClass/entry/src/main/cpp/napi_init.cpp) -->

API declaration:

```ts
// index.d.ts
export const newInstance: (obj: Object, param: string) => Object;
```
<!-- @[napi_new_instance_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIClass/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS code:

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
class Fruit {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}
// Call the function and use the variable obj to hold the instance created.
let obj = testNapi.newInstance(Fruit, 'test');
// Print the information about the object obj.
hilog.info(0x0000, 'Node-API', 'napi_new_instance %{public}s', JSON.stringify(obj));
```
<!-- @[ark_napi_new_instance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIClass/entry/src/main/ets/pages/Index.ets) -->

### napi_get_new_target

Call **napi_get_new_target** to obtain **new.target** of a constructor. In ArkTS, **new.target** is a meta property used to determine whether a constructor was called using the **new** operator.

For more information, see:

[Wrapping a Native Object in an ArkTS Object](use-napi-object-wrap.md)

### napi_define_class

Call **napi_define_class** to define an ArkTS class. This API creates an ArkTS class and associates the methods and properties of the ArkTS class with those of a C/C++ class.

For more information, see:

[Wrapping a Native Object in an ArkTS Object](use-napi-object-wrap.md)

### napi_wrap

Call **napi_wrap** to wrap a native instance in an ArkTS object.

> **NOTE**
>
> If **js_object** is not of the object or function type, **napi_object_expected** will be returned.

### napi_unwrap

Call **napi_unwrap** to unwrap a native instance from an ArkTS object and obtain the pointer to the data.

> **NOTE**
>
> If **js_object** is not of the object or function type, **napi_object_expected** will be returned.

### napi_remove_wrap

Call **napi_remove_wrap** to remove the wrapping after a native instance is unwrapped from an ArkTS object.

> **NOTE**
>
> If **js_object** is not of the object or function type, **napi_object_expected** will be returned.

CPP code:

```cpp
#include <hilog/log.h>
#include <string>
#include "napi/native_api.h"

static constexpr int INT_ARG_18 = 18; // Age: 18 years old

struct Object {
    std::string name;
    int32_t age;
};

static void DerefItem(napi_env env, void *data, void *hint) {
    // Optional native callback, which is used to release the native instance when the ArkTS object is garbage-collected.
    OH_LOG_INFO(LOG_APP, "Node-API DerefItem");
    Object *obj = reinterpret_cast<Object *>(data);
    if (obj != nullptr) {
        delete obj;
    }
}

static napi_value Wrap(napi_env env, napi_callback_info info)
{
    OH_LOG_INFO(LOG_APP, "Node-API wrap");
    // Initialize the native object.
    struct Object *obj = new struct Object();
    obj->name = "liLei";
    obj->age = INT_ARG_18;
    size_t argc = 1;
    napi_value toWrap;
    // Call napi_wrap to wrap the native object in an ArkTS object.
    napi_status status_cb = napi_get_cb_info(env, info, &argc, &toWrap, NULL, NULL);
    if (status_cb != napi_ok) {
        OH_LOG_ERROR(LOG_APP, "napi_get_cb_info failed");
        delete obj;
        return nullptr;
    }
    napi_status status = napi_wrap(env, toWrap, reinterpret_cast<void *>(obj), DerefItem, NULL, NULL);
    if (status != napi_ok) {
        // Proactively release the memory.
        delete obj;
    }

    return toWrap;
}

static napi_value RemoveWrap(napi_env env, napi_callback_info info)
{
    OH_LOG_INFO(LOG_APP, "Node-API removeWrap");
    size_t argc = 1;
    napi_value wrapped = nullptr;
    void *data = nullptr;
    // Call napi_remove_wrap to remove the wrapping.
    napi_get_cb_info(env, info, &argc, &wrapped, nullptr, nullptr);
    napi_remove_wrap(env, wrapped, &data);
    return nullptr;
}

static napi_value UnWrap(napi_env env, napi_callback_info info)
{
    OH_LOG_INFO(LOG_APP, "Node-API unWrap");
    size_t argc = 1;
    napi_value wrapped = nullptr;
    napi_get_cb_info(env, info, &argc, &wrapped, nullptr, nullptr);
    // Call napi_unwrap to retrieve the data from the ArkTS object and print the data.
    struct Object *data = nullptr;
    napi_status status = napi_unwrap(env, wrapped, reinterpret_cast<void **>(&data));
    if (status != napi_ok || data == nullptr) {
        OH_LOG_ERROR(LOG_APP, "Node-API napi_unwrap failed or data is nullptr");
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "Node-API name: %{public}s", data->name.c_str());
    OH_LOG_INFO(LOG_APP, "Node-API age: %{public}d", data->age);
    return nullptr;
}
```
<!-- @[napi_wrap_unwrap_remove_wrap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIClass/entry/src/main/cpp/napi_init.cpp) -->

API declaration:

```ts
// index.d.ts
export const wrap: (obj: Object) => Object;
export const unWrap: (obj: Object) => void;
export const removeWrap: (obj: Object) => void;
```
<!-- @[napi_wrap_unwrap_remove_wrap_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIClass/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS code:

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
try {
    class Obj {}
    let obj: Obj = {};
    testNapi.wrap(obj)
    testNapi.unWrap(obj)
    testNapi.removeWrap(obj)
} catch (error) {
    hilog.error(0x0000, 'testTag', 'Test Node-API error: %{public}s', error.message);
}
```
<!-- @[ark_napi_wrap_unwrap_remove_wrap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIClass/entry/src/main/ets/pages/Index.ets) -->

To print logs in the native CPP, add the following information to the **CMakeLists.txt** file and add the header file by using **#include "hilog/log.h"**.

```text
// CMakeLists.txt
add_definitions( "-DLOG_DOMAIN=0xd0d0" )
add_definitions( "-DLOG_TAG=\"testTag\"" )
target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
```
