# Associating Data with a Running Environment to Tie Their Lifecycle Using Node-API
<!--Kit: NDK-->
<!--Subsystem: arkcompiler-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @fang-jinxu-->

## Introduction

Use Node-API to associate specific data with the currently running environment so that the data can be retrieved later when required.

## Basic Concepts

In Node-API, associated data refers to the binding of a custom C++ data structure to the lifecycle of the current environment. This means that the associated data remains valid as long as the current runtime environment exists.

## Available APIs

The following table lists the APIs.
| API| Description|
| -------- | -------- |
| napi_set_instance_data | Associates data with the currently running environment.|
| napi_get_instance_data | Retrieves the data that was previously associated with the currently running environment.|

## Example

For details about the Node-API development process, see [Node-API Development Process](use-napi-process.md). This document describes only the related C++ and ArkTS code.

### napi_set_instance_data

Associate data with the currently running environment.

CPP code

```cpp
#include <cstdlib>
#include "napi/native_api.h"

// Define a struct to store instance data.
struct InstanceData {
    int32_t value;
};

// Callback to be invoked to clear the instance data when the object is released.
void FinalizeCallback(napi_env env, void *finalize_data, void *finalize_hint)
{
    if (finalize_data) {
        InstanceData *data = reinterpret_cast<InstanceData *>(finalize_data);
        // Release the memory and clear the address pointed by the pointer.
        delete (data);
    }
}

static napi_value SetInstanceData(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value argv[1];
    napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);
    int32_t instanceDataValue;
    napi_get_value_int32(env, argv[0], &instanceDataValue);
    InstanceData *instanceData = new InstanceData;
    instanceData->value = instanceDataValue;
    // Call napi_set_instance_data to associate the instance data with the Node-API environment and specify the FinalizeCallback function.
    napi_status status = napi_set_instance_data(env, instanceData, FinalizeCallback, nullptr);
    bool success = true;
    napi_value result = nullptr;
    if (status == napi_ok) {
        napi_get_boolean(env, success, &result);
    }
    return result;
}
```
<!-- @[napi_set_instance_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIEnvironmentalLifeCycle/entry/src/main/cpp/napi_init.cpp) -->

API declaration

```ts
// index.d.ts
export const setInstanceData: (data: number) => boolean;
```
<!-- @[napi_set_instance_data_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIEnvironmentalLifeCycle/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS code

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
let data = 5;
let value = testNapi.setInstanceData(data);
hilog.info(0x0000, 'testTag', 'Test Node-API napi_set_instance_data:%{public}s', value);
```
<!-- @[ark_napi_set_instance_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIEnvironmentalLifeCycle/entry/src/main/ets/pages/Index.ets) -->

### napi_get_instance_data

Retrieves the data that was previously associated with the currently running environment.

CPP code

```cpp
#include "napi/native_api.h"

static napi_value GetInstanceData(napi_env env, napi_callback_info info) {
    InstanceData *resData = nullptr;
    // Call napi_get_instance_data to obtain the data.
    napi_status status = napi_get_instance_data(env, (void **)&resData);
    if (status != napi_ok) {
        return nullptr;
    }
    napi_value result;
    napi_create_int32(env, resData->value, &result);
    return result;
}
```
<!-- @[napi_get_instance_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIEnvironmentalLifeCycle/entry/src/main/cpp/napi_init.cpp) -->

API declaration

```ts
// index.d.ts
export const getInstanceData: () => number | undefined;
```
<!-- @[napi_get_instance_data_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIEnvironmentalLifeCycle/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS code

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
let data = 5;
testNapi.setInstanceData(data);
let value = testNapi.getInstanceData();
hilog.info(0x0000, 'testTag', 'Test Node-API napi_set_instance_data:%{public}d', value);
```
<!-- @[ark_napi_get_instance_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIEnvironmentalLifeCycle/entry/src/main/ets/pages/Index.ets) -->

To print logs in the native CPP, add the following information to the **CMakeLists.txt** file and add the header file by using **#include "hilog/log.h"**.

```text
// CMakeLists.txt
add_definitions( "-DLOG_DOMAIN=0xd0d0" )
add_definitions( "-DLOG_TAG=\"testTag\"" )
target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
```
