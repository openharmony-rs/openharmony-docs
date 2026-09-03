# Working with Wrapper Objects Using JSVM-API
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e7d54c65a024645f8f688ed024b0b4059342e5b3 translatedAt=2026-09-01T02:43:32.038Z pushedAt=2026-09-02T06:46:05.210Z -->

## Introduction

JSVM-API provides APIs for quickly determining the wrapper type of an object.

## Basic Concepts

In JSVM-API, the wrapper object APIs provide a quick way to identify five types of wrapper objects.

## Available APIs

| API                                   | Description                      |
|----------------------------------------|--------------------------------|
| OH_JSVM_IsNumberObject            | Checks whether the result is a number object. |
| OH_JSVM_IsBooleanObject           | Checks whether the result is a Boolean object. |
| OH_JSVM_IsBigIntObject            | Checks whether the result is a BigInt object.  |
| OH_JSVM_IsStringObject            | Checks whether the result is a string object.  |
| OH_JSVM_IsSymbolObject            | Checks whether the result is a symbol object.  |

## Example

If you are just starting out with JSVM-API, see [JSVM-API Development Process](use-jsvm-process.md). The following demonstrates only the C++ code involved in the APIs.

### Determining a Number Object

CPP code:

```cpp
#include <string>

static JSVM_Value WrapperObject(JSVM_Env env, JSVM_CallbackInfo info) {
    JSVM_VM vm;
    OH_JSVM_GetVM(env, &vm);

    JSVM_HandleScope handleScope;
    OH_JSVM_OpenHandleScope(env, &handleScope);
    std::string src = R"JS(new Number(42))JS";
    JSVM_Value jsSrc;
    JSVM_Script script;
    JSVM_Value result;

    OH_JSVM_CreateStringUtf8(env, src.c_str(), JSVM_AUTO_LENGTH, &jsSrc);
    OH_JSVM_CompileScript(env, jsSrc, nullptr, 0, true, nullptr, &script);
    OH_JSVM_RunScript(env, script, &result);
    bool isNumberObject = false;
    OH_JSVM_IsNumberObject(env, result, &isNumberObject);
    OH_LOG_INFO(LOG_APP, "JSVM OH_JSVM_IsNumberObject: %{public}d\n", isNumberObject);
    OH_JSVM_CloseHandleScope(env, handleScope);

    return nullptr;
}

static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = WrapperObject},
};

static JSVM_CallbackStruct *method = param;

// Alias for the wrapperObject method to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"wrapperObject", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};

// Call the C++ code from JS.
const char *srcCallNative = R"JS(wrapperObject();)JS";

```

Expected result:
```txt
JSVM OH_JSVM_IsNumberObject: 1
```
