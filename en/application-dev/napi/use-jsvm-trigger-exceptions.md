# Customizing Exception Handling Using JSVM-API
<!--Kit: NDK Development-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Introduction

JSVM-API provides APIs for handling JSVM exceptions. You can use these APIs to register callback functions with the JSVM. When the JSVM triggers an exception, the registered callback function is called.
These APIs provide customized processing of JS engine errors to help developers manage runtime errors and exceptions.

## Basic Concepts

JSVM-API provides APIs for handling the following errors: <br>Out-of-memory (OOM) error: You can use JSVM-API to register an OOM handler with a JSVM. When the JSVM encounters insufficient memory, the system will throw an OOM error and call the registered OOM error handler to perform cleanup or logging operations.
When a fatal error occurs in the JavaScript engine, for example, an unrecoverable error occurs during JavaScript code execution, the system throws a fatal error and calls the preset processing function. In this processing function, additional logs can be output or errors can be reported to prevent the program from crashing.
Promise rejection without a catch handler: You can use JSVM-API to register a promise rejection handler with a JSVM. When a promise in JS is rejected without being caught by a catch handler, the system will throw a Promise Reject error and call the registered handler to handle the promise rejection.

## Available APIs

| API                      | Description                           |
|----------------------------|-------------------------------------|
| OH_JSVM_SetHandlerForOOMError         | Sets an OOM error handler for a JSVM.|
| OH_JSVM_SetHandlerForFatalError   | Sets a fatal error handler for a JSVM.|
| OH_JSVM_SetHandlerForPromiseReject | Sets a promise rejection handler for a JSVM.|

## Example

If you are just starting out with JSVM-API, see [JSVM-API Development Process](use-jsvm-process.md). The following demonstrates only the C++ code involved in exception handling.

### OH_JSVM_SetHandlerForOOMError
Call **OH_JSVM_SetHandlerForOOMError** to set a function for handling the OOM error. If this API is called multiple times, only the last setting takes effect. If **NULL** is passed in for the function to set in this API, the previously set handler will be canceled.

CPP code:

```cpp
#include <csetjmp>
#include <vector>

static jmp_buf buf;
static bool oomHandlerFinished = false;

void OnOOMError(const char *location, const char *detail, bool isHeapOOM)
{
    oomHandlerFinished = true;
    longjmp(buf, 1);
}

static JSVM_Value TriggerOOMError(JSVM_Env env, JSVM_CallbackInfo info)
{
    oomHandlerFinished = false;
    JSVM_VM vm;
    JSVM_CALL(OH_JSVM_GetVM(env, &vm));
    // Set an OOM error handler.
    JSVM_CALL(OH_JSVM_SetHandlerForOOMError(vm, OnOOMError));
    bool oomed = false;
    setjmp(buf);
    if (!oomed) {
        oomed = true;
        // Trigger an OOM error.
        std::vector<JSVM_Value> arrayVec;
        int loopCount = 1000;
        for (int i = 0; i < loopCount; i++) {
            JSVM_Value array;
            JSVM_CALL(OH_JSVM_CreateArrayWithLength(env, 0xffffff, &array));
            arrayVec.push_back(array);
        }
    }
    if (oomHandlerFinished) {
        OH_LOG_INFO(LOG_APP, "JSVM Trigger OOM Error: success");
    } else {
        OH_LOG_ERROR(LOG_APP, "JSVM Trigger OOM Error: failed");
    }
    // Cancel the OOM error handler.
    JSVM_CALL(OH_JSVM_SetHandlerForOOMError(vm, NULL));
    JSVM_Value checked;
    OH_JSVM_GetBoolean(env, true, &checked);
    return checked;
}

static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = TriggerOOMError},
};
static JSVM_CallbackStruct *method = param;

static JSVM_PropertyDescriptor descriptor[] = {
    {"triggerOOMError", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
```
JS Example
```cpp
const char *srcCallNative = R"JS(triggerOOMError();)JS";
```
**Execution result**

Log output when the screen is clicked once:
```cpp
JSVM Trigger OOM Error: success
```
### OH_JSVM_SetHandlerForFatalError
Call **OH_JSVM_SetHandlerForFatalError** to set a function for handling the fatal error. If this API is called multiple times, only the last setting takes effect. If **NULL** is passed in for the function to set in this API, the previously set handler will be canceled.
CPP code:

```cpp
#include <csetjmp>
#include <vector>

static jmp_buf buf;
static bool fatalHandlerFinished = false;
void OnFatalError(const char *location, const char *message)
{
    fatalHandlerFinished = true;
    OH_LOG_INFO(LOG_APP, "Run in 106");
    longjmp(buf, 1);
}

static JSVM_Value TriggerFatalError(JSVM_Env env, JSVM_CallbackInfo info)
{
    fatalHandlerFinished = false;
    JSVM_VM vm;
    JSVM_CALL(OH_JSVM_GetVM(env, &vm));
    // Set a fatal error handler.
    JSVM_CALL(OH_JSVM_SetHandlerForFatalError(vm, OnFatalError));
    bool fataled = false;
    setjmp(buf);
    if (!fataled) {
        fataled = true;
        std::vector<JSVM_Value> arrayVec;
        int loopCount = 1000;
        for (int i = 0; i < loopCount; i++) {
            JSVM_Value array;
            JSVM_CALL(OH_JSVM_CreateArrayWithLength(env, 0xffffff, &array));
            arrayVec.push_back(array);
        }
    }
    if (fatalHandlerFinished) {
        OH_LOG_INFO(LOG_APP, "JSVM Trigger Fatal Error: success");
    } else {
        OH_LOG_ERROR(LOG_APP, "JSVM Trigger Fatal Error: failed");
    }
    // Cancel the fatal error handler.
    JSVM_CALL(OH_JSVM_SetHandlerForFatalError(vm, NULL));
    JSVM_Value checked;
    OH_JSVM_GetBoolean(env, true, &checked);
    return checked;
}

static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = TriggerFatalError},
};
static JSVM_CallbackStruct *method = param;

static JSVM_PropertyDescriptor descriptor[] = {
    {"triggerFatalError", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
```
JS Example
```cpp
const char* srcCallNative = R"JS(triggerFatalError())JS";
```
**Execution result:**

Log output when the screen is clicked once:
```cpp
JSVM Trigger Fatal Error: success
```
### OH_JSVM_SetHandlerForPromiseReject
Call **OH_JSVM_SetHandlerForPromiseReject** to set the function for handling promise rejection. If this API is called multiple times, only the last setting takes effect. If **NULL** is passed in for the function to set in this API, the previously set handler will be canceled.
CPP code:

```cpp
static bool promiseRejectHandlerFinished = false;

void OnPromiseReject(JSVM_Env env, JSVM_PromiseRejectEvent rejectEvent, JSVM_Value rejectInfo)
{
    bool result = false;
    OH_JSVM_IsObject(env, rejectInfo, &result);
    JSVM_Value promise;
    JSVM_Value key1;
    OH_JSVM_CreateStringUtf8(env, "promise", JSVM_AUTO_LENGTH, &key1);
    OH_JSVM_GetProperty(env, rejectInfo, key1, &promise);
    bool isPromise = false;
    OH_JSVM_IsPromise(env, promise, &isPromise);
    JSVM_Value value;
    JSVM_Value key2;
    OH_JSVM_CreateStringUtf8(env, "value", JSVM_AUTO_LENGTH, &key2);
    OH_JSVM_GetProperty(env, rejectInfo, key2, &value);
    JSVM_Value js_number;
    OH_JSVM_CoerceToNumber(env, value, &js_number);
    double res = 0;
    OH_JSVM_GetValueDouble(env, js_number, &res);
    if (res == 42 && isPromise) {
        promiseRejectHandlerFinished = true;
    }
}

static JSVM_Value TriggerPromiseReject(JSVM_Env env, JSVM_CallbackInfo info)
{
    promiseRejectHandlerFinished = false;
    JSVM_VM vm;
    JSVM_CALL(OH_JSVM_GetVM(env, &vm));
    // Set a Promise-Reject handler.
    JSVM_CALL(OH_JSVM_SetHandlerForPromiseReject(vm, OnPromiseReject));
    JSVM_Value strVal;
    char *str = "new Promise((resolve, reject) => { reject(42); })";
    OH_JSVM_CreateStringUtf8(env, str, JSVM_AUTO_LENGTH, &strVal);
    JSVM_Script script;
    OH_JSVM_CompileScript(env, strVal, nullptr, 0, false, nullptr, &script);
    JSVM_Value result;
    JSVM_Status status = OH_JSVM_RunScript(env, script, &result);

    if (promiseRejectHandlerFinished) {
        OH_LOG_INFO(LOG_APP, "JSVM Trigger Promise Reject: success");
    } else {
        OH_LOG_ERROR(LOG_APP, "JSVM Trigger Promise Reject: failed");
    }
    // Cancel the Promise-Reject handler.
    JSVM_CALL(OH_JSVM_SetHandlerForPromiseReject(vm, NULL));
    JSVM_Value checked;
    OH_JSVM_GetBoolean(env, true, &checked);
    return checked;
}

static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = TriggerPromiseReject},
};
static JSVM_CallbackStruct *method = param;

static JSVM_PropertyDescriptor descriptor[] = {
    {"triggerPromiseReject", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
```
JS Example
```cpp
const char* srcCallNative = R"JS(triggerPromiseReject())JS";
```
**Execution result:**

Log output when the screen is clicked once:
```cpp
JSVM Trigger Promise Reject: success
```
