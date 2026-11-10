# ui_json_wrapper.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-03T08:43:38.891Z pushedAt=2026-11-04T07:18:34.669Z nl=1 -->

## Overview

Declares the JSON data object shared by APIs such as UI awareness and UI control.<br>The APIs report errors through their return values. For details, see the return value description of each API. These APIs do not report errors through the error code variable **errno**. After an API is called, the value of this variable is unspecified and must not be used to determine whether the call succeeds.<br>Provided that the object lifecycle requirements are met, these APIs can be called from any thread, including the UI thread. Read-only queries on the same valid object can be executed concurrently. The caller must ensure that a destroy operation does not run concurrently with access to the object or its borrowed data. Operations on independent objects can be executed concurrently. These APIs do not trigger application callbacks. When the ownership and lifecycle requirements are met, they can be called from callbacks. These APIs are not async-signal-safe and must not be called from signal handlers.<br>Query APIs read data from local memory synchronously. Creating and destroying objects also involve memory allocation or deallocation, and the upper bound of the time consumed by these memory operations is not guaranteed.<br>These APIs do not support asynchronous completion and do not provide cancellation.

**File to include:** <arkui/ui_json_wrapper.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 26.1.0

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) | OH_ArkUI_NativeModule_UIJsonWrapper | Defines the immutable JSON data object whose internal structure is not exposed.<br>The object holds a JSON string, which is used both to carry data passed by the framework (UI awareness) and to carry commands injected by the application (UI control). The top level of the JSON object must contain the **schemaVersion** field, which is used for version control and subsequent compatibility maintenance. The JSON passed in by the application, as well as the JSON returned by the framework through APIs or passed through callbacks, must meet this requirement. Even if no content is collected, the returned JSON must carry this field.<br>The object does not use reference counting. Copying an object pointer only creates a borrowed alias; it does not create an independent object or increase ownership. The owner of the object must destroy the object exactly once. After destruction, all aliases and data pointers become invalid and must not be used or destroyed again. |

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIJsonFormat](#oh_arkui_nativemodule_uijsonformat) | OH_ArkUI_NativeModule_UIJsonFormat | Enumerates the JSON output formats. |

### Functions

| Name | Description |
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIJsonWrapperCreate(const char *data, uint32_t size, OH_ArkUI_NativeModule_UIJsonWrapper **outOwned)](#oh_arkui_nativemodule_uijsonwrappercreate) | Creates a JSON data object from the JSON string provided by the caller.<br>The passed-in string is copied into the object. The caller owns the created object and must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release it when it is no longer used. Copying the returned pointer does not extend the object lifecycle or create a new owner. After the object is destroyed, the pointer and all its aliases become invalid and must not be used or destroyed again.<br>The passed-in string must represent a valid JSON object, and the top level of the object must contain the **schemaVersion** field. If this field is missing, or if its value is outside the supported version range, this API returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) and does not use a default version. An example is as follows: { "schemaVersion": 1, ... }<br>Note: The passed-in data string remains owned by the caller. Destroying the JSON wrapper object returned by this API does not release the memory pointed to by **data** on behalf of the caller. For parameter errors, correct the input and retry. For size overflow or memory allocation failure, reduce the input or release resources and retry, and avoid a busy loop. On failure, ownership of any object is not transferred. |
| [const char *OH_ArkUI_NativeModule_UIJsonWrapperGetData(const OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrappergetdata) | Obtains the JSON string held by the object.<br>The returned string is a read-only, null-terminated string. The memory where the string resides is owned by the JSON object and remains valid until the object is destroyed. The caller must not modify or release the returned string. The top level of the JSON object contains the **schemaVersion** field. |
| [uint32_t OH_ArkUI_NativeModule_UIJsonWrapperGetSize(const OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrappergetsize) | Obtains the byte length of the JSON string.<br>The returned length does not include the trailing null character, and it includes the bytes occupied by the **schemaVersion** field in the JSON string.<br>This query does not allocate or release resources. |
| [void OH_ArkUI_NativeModule_UIJsonWrapperDestroy(OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrapperdestroy) | Destroys a JSON data object and releases its resources.<br>After this API is called, all pointers returned by [OH_ArkUI_NativeModule_UIJsonWrapperGetData](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) become invalid.<br>Note: The caller must own the JSON wrapper object to call this API to destroy it, for example, the object created by [OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate), or the object whose ownership is explicitly obtained through an ownership transfer API. Do not use this API to release a JSON wrapper object constructed and passed out by the system, for example, the object passed in through [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback). |

## Enum Description

### OH_ArkUI_NativeModule_UIJsonFormat

```c
enum OH_ArkUI_NativeModule_UIJsonFormat
```

**Description**

Enumerates the JSON output formats.

**Since:** 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_JSON_COMPACT = 0 | Outputs canonical JSON without extra whitespace. |
| OH_ARKUI_NATIVE_MODULE_UI_JSON_PRETTY = 1 | Outputs JSON with two-space indentation and line breaks. |


## Function Description

### OH_ArkUI_NativeModule_UIJsonWrapperCreate()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIJsonWrapperCreate(const char *data, uint32_t size, OH_ArkUI_NativeModule_UIJsonWrapper **outOwned)
```

**Description**

Creates a JSON data object from the JSON string provided by the caller.<br>The passed-in string is copied into the object. The caller owns the created object and must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release it when it is no longer used. Copying the returned pointer does not extend the object lifecycle or create a new owner. After the object is destroyed, the pointer and all its aliases become invalid and must not be used or destroyed again.<br>The passed-in string must represent a valid JSON object, and the top level of the object must contain the **schemaVersion** field. If this field is missing, or if its value is outside the supported version range, this API returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) and does not use a default version. An example is as follows: { "schemaVersion": 1, ... }<br>Note: The passed-in data string remains owned by the caller. Destroying the JSON wrapper object returned by this API does not release the memory pointed to by **data** on behalf of the caller. For parameter errors, correct the input and retry. For size overflow or memory allocation failure, reduce the input or release resources and retry, and avoid a busy loop. On failure, ownership of any object is not transferred.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| const char *data | [Input parameter] Pointer to a UTF-8 encoded JSON String. It cannot be **NULL** and must remain valid throughout the call. The callee does not retain this pointer. The string must contain a valid JSON object, and the value of **schemaVersion** must be a supported version. An empty string is invalid. At least **size** bytes must be readable. The input does not need to be null-terminated; the created object appends its own terminating null character. The JSON text must not contain embedded null bytes; U+0000 should be represented using JSON escaping. |
| uint32_t size | [Input parameter] Number of bytes copied from data, excluding the terminating null character. This API copies bytes according to **size**, does not validate the actual string length, and appends a null character at the end of the copy. The value of **size** must be greater than 0; passing 0 returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode). |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) **outOwned | [Output parameter] Pointer to the output parameter used to receive the successfully created object. The caller owns the returned object and must call [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) to release it. **outOwned** cannot be **NULL**, and the object pointer it points to does not need to be initialized; on creation failure, the object pointer is set to **NULL**. |

**Return value**

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if **data** or **outOwned** is **NULL**, the value of size is **0**, **data** does not represent a valid JSON object, or the **schemaVersion** field is missing or its version is unsupported.<br>Returns [ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the buffer size including the terminating null character cannot be represented on the current architecture, or if memory allocation or data copy fails. |

### OH_ArkUI_NativeModule_UIJsonWrapperGetData()

```c
const char *OH_ArkUI_NativeModule_UIJsonWrapperGetData(const OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**Description**

Obtains the JSON string held by the object.<br>The returned string is a read-only, null-terminated string. The memory where the string resides is owned by the JSON object and remains valid until the object is destroyed. The caller must not modify or release the returned string. The top level of the JSON object contains the **schemaVersion** field.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [Input parameter] Pointer to the JSON data object, which cannot be **NULL**. This object is a borrowed object and must remain valid throughout the call. The callee does not retain this object. |

**Return value**

| Type | Description |
| -- | -- |
| const char * | Pointer to the borrowed JSON string. The caller must not modify or release this pointer.<br>**NULL** is returned if **json** is **NULL**. |

### OH_ArkUI_NativeModule_UIJsonWrapperGetSize()

```c
uint32_t OH_ArkUI_NativeModule_UIJsonWrapperGetSize(const OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**Description**

Obtains the byte length of the JSON string.<br>The returned length does not include the trailing null character, and it includes the bytes occupied by the **schemaVersion** field in the JSON string.<br>This query does not allocate or release resources.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [Input parameter] Pointer to the JSON data object, which cannot be **NULL**. This object is a borrowed object and must remain valid throughout the call. The callee does not retain this object. If **NULL** is passed in, the length of the object cannot be obtained. Provide a valid object that has not been destroyed and retry. |

**Return value**

| Type | Description |
| -- | -- |
| uint32_t | Byte length of the JSON string, excluding the trailing null character.<br>**0** is returned if **json** is **NULL**. |

### OH_ArkUI_NativeModule_UIJsonWrapperDestroy()

```c
void OH_ArkUI_NativeModule_UIJsonWrapperDestroy(OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**Description**

Destroys a JSON data object and releases its resources.<br>After this API is called, all pointers returned by [OH_ArkUI_NativeModule_UIJsonWrapperGetData](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) become invalid.<br>Note: The caller must own the JSON wrapper object to call this API to destroy it, for example, the object created by [OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate), or the object whose ownership is explicitly obtained through an ownership transfer API. Do not use this API to release a JSON wrapper object constructed and passed out by the system, for example, the object passed in through [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback).

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [Input parameter] Pointer to the JSON data object to destroy. It can be **NULL**. If **NULL** is passed in, no operation is performed. The caller must own the object. After destruction, the object and all its aliases become invalid immediately and must not be used or destroyed again. Do not pass a borrowed object to this API. |
