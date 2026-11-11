---
kits: ["ArkTS Kit"]
description: "Describes how to use JSVM-API to create external JavaScript strings directly from native-side Latin1- or UTF16-encoded string memory and confirm the creation result through the copied parameter."
keywords: ["OH_JSVM_CreateExternalStringLatin1","OH_JSVM_CreateExternalStringUtf16","external string","Latin1","UTF16","ISO-8859-1","UTF16-LE"]
doctype: guide
status: active
---

# Working with Latin1/UTF16 Strings Using JSVM-API
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=23d7ff60c67cd3075712762902e4e8f21f8c70ac translatedAt=2026-11-09T08:52:17.330Z nl=1 -->

## Introduction

This topic walks you through on how to create and use external strings using JSVM-API.

## Basic Concepts

By using JSVM-API, you can create JavaScript strings directly in the memory allocated for Latin1/UTF16 strings. This allows you to manipulate these strings like normal JavaScript strings.

## Available APIs

| API                                  | Description                      |
|----------------------------------------|--------------------------------|
| OH_JSVM_CreateExternalStringLatin1     | Creates an external JS string from a C string encoded in ISO-8859-1 format. |
| OH_JSVM_CreateExternalStringUtf16      | Creates an external JS string from a C string encoded in UTF16-LE format. |

## Example

If you are just starting out with JSVM-API, see [JSVM-API Development Process](use-jsvm-process.md). The following demonstrates only the C++ code involved in manipulating external strings.

### Creating an External String

CPP code:

```cpp
#include <cstring>
#include <string>
static char stringLatin1[] = "hello";
static char16_t stringUTF16[] = u"world";

static JSVM_Value testExternalString(JSVM_Env env, JSVM_CallbackInfo info) {
    JSVM_VM vm;
    OH_JSVM_GetVM(env, &vm);

    JSVM_HandleScope handleScope;
    OH_JSVM_OpenHandleScope(env, &handleScope);
    JSVM_Value jsStrLatin1 = nullptr;
    bool copied = true;
    char buf[10];
    OH_JSVM_CreateExternalStringLatin1(env, stringLatin1, strlen(stringLatin1), nullptr, nullptr,
                                       &jsStrLatin1, &copied);
    OH_JSVM_GetValueStringUtf8(env, jsStrLatin1, buf, 10, nullptr);
    OH_LOG_INFO(LOG_APP, "created latin1 string is : %{public}s\n", buf);
    // If the value of copied is true, the external string fails to be created. Otherwise, the external string is created successfully.
    OH_LOG_INFO(LOG_APP, "create external string result, copied : %{public}d\n", copied);
    copied = true;
    JSVM_Value jsStrUTF16 = nullptr;
    OH_JSVM_CreateExternalStringUtf16(env, stringUTF16, std::char_traits<char16_t>::length(stringUTF16),
                                      nullptr, nullptr, &jsStrUTF16, &copied);
    OH_JSVM_GetValueStringUtf8(env, jsStrUTF16, buf, 10, nullptr);
    OH_LOG_INFO(LOG_APP, "created utf16 string is : %{public}s\n", buf);
    // If the value of copied is true, the external string fails to be created. Otherwise, the external string is created successfully.
    OH_LOG_INFO(LOG_APP, "create external string result, copied : %{public}d\n", copied);
    OH_JSVM_CloseHandleScope(env, handleScope);

    return nullptr;
}

static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = testExternalString},
};

static JSVM_CallbackStruct *method = param;

// Alias for the testExternalString method to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"testExternalString", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};

// Call the C++ code from JS.
const char *srcCallNative = R"JS(testExternalString();)JS";

```

## Expected Result
```txt
created latin1 string is : hello
create external string result, copied : 0
created utf16 string is : world
create external string result, copied : 0
```
