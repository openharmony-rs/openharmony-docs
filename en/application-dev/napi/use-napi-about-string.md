---
kits: ["ArkTS Kit"]
description: "Describes how to create and obtain string values using Node-API with multiple character encodings (ASCII, UTF-8, UTF-16, and Latin-1) for string interaction between Node-API modules and ArkTS."
keywords: [Node-API, string, strings, napi_create_string, UTF-8, UTF-16, ASCII, character encoding, string conversion]
doctype: guide
status: active
---

# Working with String Using Node-API
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @shilei123; @liudachuan3-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=168caf601a8ed7899a458e51351d604fc48a1943 translatedAt=2026-11-09T08:52:17.384Z nl=1 -->

## Introduction

This topic walks you through on how to use Node-API to convert data between native strings and ArkTS strings.

## Basic Concepts

Strings are a common data type in programming. They are used to store and manipulate text data, represent and process character sequences, build user interface (UI) elements such as tags, buttons, and text boxes, process user input, and validate and format data. Different encodings support different character sets and languages. Major encoding schemes include the following:

- ASCII<br>ASCII is one of the earliest character encoding schemes. It uses 7 bits to represent English letters, digits, and some basic symbols. It serves as the foundation for encoding schemes.
- UTF-8<br>UTF-8 is a variable-length encoding scheme that can represent any Unicode character. It uses 8 bits per character and uses byte sequences of different lengths depending on the range of the character. UTF-8 is widely used for web content.
- UTF-16<br>UTF-16 is a fixed-length or variable-length encoding scheme that uses 16 bits per character. It can represent all Unicode characters and is suitable for larger character sets.
- ISO-8859-1 (Latin-1)<br>ISO-8859-1 is a single-byte coding scheme that uses 8 bits per character. It is mainly used to represent Latin alphabet characters and commonly used in European languages.

## Available APIs

The following table lists the APIs provided by the Node-API module for creating and obtaining strings.

| API| Description| Earliest Version|
| -------- | -------- | -------- |
| napi_get_value_string_utf8 | Converts ArkTS character data into UTF-8 encoded characters. | 10 |
| napi_create_string_utf8 | Creates an ArkTS string value from a UTF-8 encoded C string. | 10 |
| napi_get_value_string_utf16 | Converts ArkTS character data into UTF-16 encoded characters. | 10 |
| napi_create_string_utf16 | Creates an ArkTS string value from a UTF-16 encoded C string. | 10 |
| napi_get_value_string_latin1 | Obtains an ISO-8859-1-encoded string from an ArkTS value.| 10 |
| napi_create_string_latin1 | Creates an ArkTS string from an ISO-8859-1-encoded string.| 10 |
| napi_create_external_string_utf16 | Creates an ArkTS string from an external UTF-16 encoded string buffer, without performing memory copy operations.| 22 |
| napi_create_external_string_ascii | Creates an ArkTS string from an external ASCII encoded string buffer, without performing memory copy operations.| 22 |

## Example

If you are just starting out with Node-API, see [Node-API Development Process](use-napi-process.md). The following demonstrates only the C++ and ArkTS code involved in the string-related APIs.

### napi_get_value_string_utf8

Use **napi_get_value_string_utf8** to convert an ArkTS string to a UTF-8-encoded string.

CPP code:

<!-- @[napi_get_value_string_utf8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetValueStringUtf8(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1] = {nullptr};

    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
    // Obtain the length of the string.
    size_t length = 0;
    napi_status status = napi_get_value_string_utf8(env, args[0], nullptr, 0, &length);
    // napi_string_expected will be returned for non-string inputs.
    if (status != napi_ok) {
        OH_LOG_ERROR(LOG_APP, "napi_get_value_string_utf8 failed");
        return nullptr;
    }
    char *buf = new char[length + 1];
    std::memset(buf, 0, length + 1);
    status = napi_get_value_string_utf8(env, args[0], buf, length + 1, &length);
    if (status != napi_ok) {
        if (buf) {
            delete[] buf;
        }
        OH_LOG_ERROR(LOG_APP, "napi_get_value_string_utf8 failed");
        return nullptr;
    }
    napi_value result = nullptr;
    status = napi_create_string_utf8(env, buf, length, &result);
    if (buf) {
        delete[] buf;
    }
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_create_string_utf8 failed");
        return nullptr;
    }
    return result;
}
```

API declaration:

<!-- @[napi_get_value_string_utf8_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const getValueStringUtf8: (param: string | number) => string | undefined;
```

ArkTS code:

<!-- @[ark_napi_get_value_string_utf8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Pass in a string and a number respectively. If the input is a string, the string will be returned. If the input is not a string, 'undefined' will be returned.
hilog.info(0x0000, 'testTag', 'Test Node-API get_value_string_utf8_string %{public}s',
  testNapi.getValueStringUtf8('aaBC+-$%^Hello123'));
hilog.info(0x0000, 'testTag', 'Test Node-API get_value_string_utf8_not_string %{public}s',
  testNapi.getValueStringUtf8(50));
```

### napi_create_string_utf8

Use **napi_create_string_utf8** to create an ArkTS string from a UTF8-encoded C string.

CPP code:

<!-- @[napi_create_string_utf8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value CreateStringUtf8(napi_env env, napi_callback_info info)
{
    const char *str = u8"Hello, World!, successes to create UTF-8 string! 111";
    size_t length = strlen(str);
    napi_value result = nullptr;
    napi_status status = napi_create_string_utf8(env, str, length, &result);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "Failed to create UTF-8 string");
        return nullptr;
    }
    return result;
}
```

API declaration:

<!-- @[napi_create_string_utf8_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const createStringUtf8: () => string | undefined;
```

ArkTS code:

<!-- @[ark_napi_create_string_utf8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
hilog.info(0x0000, 'testTag', 'Test Node-API napi_create_string_utf8:%{public}s',
  testNapi.createStringUtf8());
```

### napi_get_value_string_utf16

Use **napi_get_value_string_utf16** to convert an ArkTS string to a UTF-16-encoded string.

CPP code:

<!-- @[napi_get_value_string_utf16](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetValueStringUtf16(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1];
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
    napi_value result = nullptr;
    // Buffer of the string.
    char16_t buffer[MAX_BUFFER_SIZE];
    // Size of the buffer for storing the string.
    size_t bufferSize = MAX_BUFFER_SIZE;
    // Length of the string.
    size_t stringLen;
    // Obtain the value and length of the string.
    napi_get_value_string_utf16(env, args[0], buffer, bufferSize, &stringLen);
    // Obtain the string.
    napi_create_string_utf16(env, buffer, stringLen, &result);
    // Return the result.
    return result;
}
```

API declaration:

<!-- @[napi_get_value_string_utf16_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const getValueStringUtf16: (data: string) => string;
```

ArkTS code:

<!-- @[ark_napi_get_value_string_utf16](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let result = testNapi.getValueStringUtf16('hello,');
hilog.info(0x0000, 'testTag', 'Node-API napi_get_value_string_utf16:%{public}s', result);
```

### napi_create_string_utf16

Use **napi_create_string_utf16** to create an ArkTS string from a UTF16-encoded C string.

CPP code:

<!-- @[napi_create_string_utf16](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value CreateStringUtf16(napi_env env, napi_callback_info info)
{
    const char16_t *str = u"Hello, World!, successes to create UTF-16 string! 111";
    size_t length = NAPI_AUTO_LENGTH;
    napi_value result = nullptr;
    napi_status status = napi_create_string_utf16(env, str, length, &result);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "Failed to create UTF-16 string");
        return nullptr;
    }
    return result;
}
```

API declaration:

<!-- @[napi_create_string_utf16_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const createStringUtf16: () => string | undefined;
```

ArkTS code:

<!-- @[ark_napi_create_string_utf16](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
hilog.info(0x0000, 'testTag', 'Test Node-API napi_create_string_utf16:%{public}s ',
  testNapi.createStringUtf16());
```

### napi_get_value_string_latin1

Use **napi_get_value_string_latin1** to convert an ArkTS string into an ISO-8859-1-encoded string.

CPP code:

<!-- @[napi_get_value_string_latin1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetValueStringLatin1(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
    char buf[MAX_BUFFER_SIZE];
    size_t length = 0;
    napi_value napi_Res = nullptr;
    napi_status status = napi_get_value_string_latin1(env, args[0], buf, MAX_BUFFER_SIZE, &length);
    // If the value passed in is not a string, napi_string_expected will be returned.
    if (status != napi_ok) {
        return nullptr;
    }
    napi_create_string_latin1(env, buf, length, &napi_Res);
    return napi_Res;
}
```

API declaration:

<!-- @[napi_get_value_string_latin1_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const getValueStringLatin1: (param: number | string) => string | undefined;
```

ArkTS code:

<!-- @[ark_napi_get_value_string_latin1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// If non-character data is passed in, undefined will be returned.
hilog.info(0x0000, 'testTag', 'Test Node-API get_value_string_latin1_not_string %{public}s',
  testNapi.getValueStringLatin1(10));
// The ISO-8859-1 encoding does not support Chinese characters. If Chinese characters are passed in, garbled characters will be displayed.
hilog.info(0x0000, 'testTag', 'Test Node-API get_value_string_latin1_string_chinese %{public}s',
  testNapi.getValueStringLatin1('Chinese'));
// Passing in characters of other languages will not cause garbled characters.
hilog.info(0x0000, 'testTag', 'Test Node-API get_value_string_latin1_string %{public}s',
  testNapi.getValueStringLatin1('abo ABP=-&*/'));
```

### napi_create_string_latin1

Creates a Latin-1 encoded ArkTS string.

CPP code:

<!-- @[napi_create_string_latin1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value CreateStringLatin1(napi_env env, napi_callback_info info)
{
    const char *str = "Hello, World! éçñ, successes to create Latin1 string! 111";
    size_t length = NAPI_AUTO_LENGTH;
    napi_value result = nullptr;
    napi_status status = napi_create_string_latin1(env, str, length, &result);
    if (status != napi_ok) {
        // Error handling.
        napi_throw_error(env, nullptr, "Failed to create Latin1 string");
        return nullptr;
    }
    return result;
}
```

API declaration:

<!-- @[napi_create_string_latin1_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const createStringLatin1: () => string | undefined;
```

ArkTS code:

<!-- @[ark_napi_create_string_latin1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
hilog.info(0x0000, 'testTag', 'Test Node-API  napi_create_string_latin1:%{public}s',
  testNapi.createStringLatin1());
```

### napi_create_external_string_utf16

Use **napi_create_external_string_utf16** to create an ArkTS UTF-16 string that references external resources.

CPP code:

<!-- @[napi_create_external_string_utf16](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) --> 

``` C++
// Define the destruction callback function of the string to release external resources.
// The hint parameter can be used to pass some additional information, such as the reference count. You can also ignore this parameter and pass nullptr.
static void StringFinalizerUTF16(void* data, void* hint)
{
    // Release external resources.
    delete[] static_cast<char16_t*>(data);
    // Important: When the destructor callback executes, it suspends other JS threads. Therefore, ensure that the callback performs no lock operations during execution. Otherwise, a deadlock may occur.
    // Since the callback is executed on a non-registered thread, ensure that the callback is thread-safe.
}

static napi_value CreateExternalStringUtf16(napi_env env, napi_callback_info info)
{
    const char16_t source[] = u"Hello, World!, successes to create UTF-16 string! 111";
    napi_value result = nullptr;
    int char16tLength = sizeof(source) / sizeof(char16_t);
    // Allocate memory dynamically on the heap and copy the string content.
    char16_t* str = new char16_t[char16tLength];
    std::copy(source, source + char16tLength, str);
    // When the created string is reclaimed by GC at the end of its lifecycle in ArkTS, the StringFinalizerUTF16(str, finalize_hint) function is called.
    // If finalize_callback is set to nullptr, no callback function is called. You need to manage the lifecycle of the external resource str.
    napi_status status = napi_create_external_string_utf16(
        env,
        str,                    // External string buffer.
        NAPI_AUTO_LENGTH,       // String length. If NAPI_AUTO_LENGTH is passed in, the string ends with '\0'.
        StringFinalizerUTF16,   // Destruction callback function of the string.
        nullptr,                // The hint parameter passed to the destruction callback function. This parameter is not required in this example.
        &result);               // Receive the created ArkTS string value.
    // Important: The memory pointed to by str must remain valid throughout the entire lifecycle of the ArkTS string object.
    // After this API is called, the content of the memory pointed to by str must remain immutable. Any write operation to this memory may cause a program crash.
    if (status != napi_ok) {
        // Error handling.
        delete[] str;
        napi_throw_error(env, nullptr, "Failed to create utf16 string");
        return nullptr;
    }
    return result;
}
```

API declaration:

<!-- @[napi_create_external_string_utf16_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const CreateExternalStringUtf16: () => string | undefined;
```

ArkTS code:

<!-- @[ark_napi_create_external_string_utf16](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
hilog.info(0x0000, 'testTag', 'Test Node-API  napi_create_external_string_utf16:%{public}s',
  testNapi.CreateExternalStringUtf16());
```
The ArkTS string object created by **napi_create_external_string_utf16** is managed by GC. When the lifecycle of the ArkTS string object ends, GC reclaims the object and triggers the **StringFinalizerUTF16** function to reclaim the native resources referenced by it.

### napi_create_external_string_ascii

Use **napi_create_external_string_ascii** to create an ASCII-encoded ArkTS string that references an external resource.

CPP code:

<!-- @[napi_create_external_string_ascii](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// Define the destruction callback function of the string to release external resources.
// The hint parameter can be used to pass some additional information, such as the reference count. You can also ignore this parameter and pass nullptr.
static void StringFinalizerASCII(void* data, void* hint)
{
    // Release external resources.
    delete[] static_cast<char*>(data);
    // Important: When the destructor callback executes, it suspends other JS threads. Therefore, ensure that the callback performs no lock operations during execution. Otherwise, a deadlock may occur.
    // Since the callback is executed on a non-registered thread, ensure that the callback is thread-safe.
}

static napi_value CreateExternalStringAscii(napi_env env, napi_callback_info info)
{
    const char source[] = "hello, World!, successes to create ASCII string! 111";
    napi_value result = nullptr;
    int charLength = sizeof(source) / sizeof(char);
    // Allocate memory dynamically on the heap and copy the string content.
    char* str = new char[charLength];
    std::copy(source, source + charLength, str);
    // When the created string is reclaimed by GC at the end of its lifecycle in ArkTS, the StringFinalizerASCII(str, finalize_hint) function is called.
    // If finalize_callback is set to nullptr, no callback function is called. You need to manage the lifecycle of the external resource str.
    // napi_create_external_string_ascii requires that the input string must not contain the null character '\0' within the specified length range. Otherwise, unexpected behavior may occur.
    napi_status status = napi_create_external_string_ascii(
        env,
        str,                    // External string buffer.
        NAPI_AUTO_LENGTH,       // String length. If NAPI_AUTO_LENGTH is passed in, the string ends with '\0'.
        StringFinalizerASCII,   // Destruction callback function of the string.
        nullptr,                // The hint parameter passed to the destruction callback function. This parameter is not required in this example.
        &result);               // Receive the created ArkTS string value.
    // Important: The memory pointed to by str must remain valid throughout the entire lifecycle of the ArkTS string object.
    // After this API is called, the content of the memory pointed to by str must remain immutable. Any write operation to this memory may cause a program crash.
    if (status != napi_ok) {
        // Error handling.
        delete[] str;
        napi_throw_error(env, nullptr, "Failed to create ascii string");
        return nullptr;
    }
    return result;
}
```

API declaration:

<!-- @[napi_create_external_string_ascii_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const CreateExternalStringAscii: () => string | undefined;
```

ArkTS code:

<!-- @[ark_napi_create_external_string_ascii](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIUse/NodeAPIString/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
hilog.info(0x0000, 'testTag', 'Test Node-API  napi_create_external_string_ascii:%{public}s',
  testNapi.CreateExternalStringAscii());
```
The ArkTS string object created by **napi_create_external_string_ascii** is managed by GC. When the lifecycle of the ArkTS string object ends, GC reclaims the object and triggers the **StringFinalizerASCII** function to reclaim the native resources referenced by it.

To print logs in the native CPP, add the following information to the **CMakeLists.txt** file and add the header file by using **#include "hilog/log.h"**.

```text
// CMakeLists.txt
add_definitions( "-DLOG_DOMAIN=0xd0d0" )
add_definitions( "-DLOG_TAG=\"testTag\"" )
target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so)
```
