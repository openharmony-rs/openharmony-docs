---
kits: ["ArkTS Kit"]
description: "How to use OH_JSVM_StrictEquals to check whether two JavaScript values are strictly equal, with the same semantics as the JS === operator and no type conversion."
keywords: [OH_JSVM_StrictEquals, strict equality, value comparison, equality checking, JSVM_Value, same type]
doctype: guide
status: active
---

# Comparing JS Values Using JSVM-API
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=1bcf41641a10f17d0f56bfc82362dc9488eaf7eb translatedAt=2026-11-09T08:52:17.356Z nl=1 -->

## Introduction

This topic walks you through on how to use JSVM-API to check whether two JavaScript (JS) values are strictly equal (equal in both value and type). The API provided is equivalent to the JS strict equality operator (**===**). This API avoids type conversion and loose equality comparison, ensuring equal values and types.

## Basic Concepts

Strictly equal: Two values are strictly equal only if they are equal in both value and type. No type conversion is performed. If the values being compared are of different types, **false** is returned even if their values appear the same.

## Available APIs

| API                      | Description                           |
|----------------------------|-------------------------------------|
| OH_JSVM_StrictEquals         | Checks whether two JSVM_Value objects are strictly equal |

## Example

If you are just starting out with JSVM-API, see [JSVM-API Development Process](use-jsvm-process.md). The following demonstrates only the C++ code involved in comparing JS values.

### OH_JSVM_StrictEquals

Use **OH_JSVM_StrictEquals** to check whether two JS values are strictly equal.

CPP code:

<!-- @[oh_jsvm_strict_equals](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/JSVMAPI/JsvmUsageGuide/UsageInstructionsTwo/strictequals/src/main/cpp/hello.cpp) -->

``` C++
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include "hilog/log.h"
// ...

// Define OH_JSVM_StrictEquals.
static JSVM_Value IsStrictEquals(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Receive two input parameters.
    size_t argc = 2;
    JSVM_Value args[2] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Call OH_JSVM_StrictEquals to check whether two given JS values are strictly equal.
    bool result = false;
    JSVM_Status status = OH_JSVM_StrictEquals(env, args[0], args[1], &result);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM OH_JSVM_StrictEquals: failed");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM OH_JSVM_StrictEquals: success: %{public}d", result);
    }
    JSVM_Value isStrictEqual = nullptr;
    OH_JSVM_GetBoolean(env, result, &isStrictEqual);
    return isStrictEqual;
}
// Register the IsStrictEquals callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = IsStrictEquals},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named isStrictEquals and associate it with a callback. This allows the isStrictEquals callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"isStrictEquals", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char* SRC_CALL_NATIVE = R"JS(data = '123';value = '123';isStrictEquals(data,value);)JS";
```

Expected result:

```ts
JSVM OH_JSVM_StrictEquals: success: 1
```
