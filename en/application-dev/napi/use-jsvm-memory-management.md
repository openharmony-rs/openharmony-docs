---
kits: ["ArkTS Kit"]
description: "How to use OH_JSVM_AdjustExternalMemory to account for externally allocated memory held by JS objects and notify the VM of memory pressure to optimize memory management and garbage collection."
keywords: [OH_JSVM_AdjustExternalMemory, OH_JSVM_MemoryPressureNotification, external memory, memory pressure notification, garbage collection, memory management]
doctype: guide
status: active
---

# Performing Memory Management Using JSVM-API
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=1bcf41641a10f17d0f56bfc82362dc9488eaf7eb translatedAt=2026-11-09T08:52:17.351Z nl=1 -->

## Introduction

JSVM-API provides APIs for managing JavaScript virtual machine (JSVM) memory. With these APIs, you can better control the memory used by JS code and optimize memory management and garbage collection (GC) mechanisms.

## Basic Concepts

In JS, memory management and GC are performed automatically. The JSVM is responsible for tracking the allocation and release of objects and reclaiming the memory that is no longer required. However, if a JSVM consumes a large amount of memory, an out-of-memory error may occur. To prevent this type of errors, JSVM-API provides APIs to better control memory management and GC mechanisms.

## Available APIs

| API                      | Description                           |
|----------------------------|-------------------------------------|
| OH_JSVM_AdjustExternalMemory         | Manages the external allocated memory held by a JS object.|
| OH_JSVM_MemoryPressureNotification   | Notifies the underlying JSVM that the VM system memory is insufficient and selectively trigger GC.|

## Example

If you are just starting out with JSVM-API, see [JSVM-API Development Process](use-jsvm-process.md). The following demonstrates only the C++ code and ArkTS code involved in related APIs.

### OH_JSVM_AdjustExternalMemory

Call **OH_JSVM_AdjustExternalMemory** to adjust the amount of externally allocated memory that is kept alive for a JS object.

CPP code:

<!-- @[oh_jsvm_adjust_external_memory](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/UsageInstructionsTwo/adjustexternalmemory/src/main/cpp/hello.cpp) -->

``` C++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// Define OH_JSVM_AdjustExternalMemory.
static JSVM_Value AdjustExternalMemory(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Allocate 1 MB of memory.
    int64_t change = 1024 * 1024;
    int64_t adjustedValue = 0;
    JSVM_Status status = OH_JSVM_AdjustExternalMemory(env, change, &adjustedValue);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM OH_JSVM_AdjustExternalMemory: failed");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM OH_JSVM_AdjustExternalMemory: success");
        OH_LOG_INFO(LOG_APP, "JSVM Allocate memory size: %{public}d", adjustedValue);
    }
    JSVM_Value checked;
    OH_JSVM_GetBoolean(env, true, &checked);
    return checked;
}
// Register the AdjustExternalMemory callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = AdjustExternalMemory},
};
static JSVM_CallbackStruct *method = param;
// Alias for the AdjustExternalMemory method to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"adjustExternalMemory", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};

const char *SRC_CALL_NATIVE = R"JS(adjustExternalMemory())JS";
```

JS example:

```c++
const char *srcCallNative = R"JS(adjustExternalMemory())JS";
```

Expected result:

Expected result:
``` C++
JSVM OH_JSVM_AdjustExternalMemory: success
JSVM Allocate memory size: 1048576
```
### OH_JSVM_MemoryPressureNotification

Call **OH_JSVM_MemoryPressureNotification** to notify the VM of insufficient system memory and selectively triggers garbage collection.

CPP code:

<!-- @[oh_jsvm_memory_pressure_notification](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/UsageInstructionsTwo/memorypressurenotification/src/main/cpp/hello.cpp) -->

``` C++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// Define OH_JSVM_MemoryPressureNotification.
static JSVM_Value MemoryPressureNotification(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Set the memory pressure level of the current JSVM.
    JSVM_Status status = OH_JSVM_MemoryPressureNotification(env, JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM OH_JSVM_MemoryPressureNotification: failed");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM OH_JSVM_MemoryPressureNotification: success");
        OH_LOG_INFO(LOG_APP, "JSVM Current JSVM memory pressure level: %{public}d",
                    JSVM_MEMORY_PRESSURE_LEVEL_CRITICAL);
    }
    return nullptr;
}
// Register the MemoryPressureNotification callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = MemoryPressureNotification},
};
static JSVM_CallbackStruct *method = param;
// Alias for the MemoryPressureNotification method to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"memoryPressureNotification", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};

const char *SRC_CALL_NATIVE = R"JS(memoryPressureNotification())JS";
```

JS example:

```c++
const char *srcCallNative = R"JS(memoryPressureNotification())JS";
```

Expected result:

Expected result:
``` C++
JSVM OH_JSVM_MemoryPressureNotification: success
JSVM Current JSVM memory pressure level: 2
```
