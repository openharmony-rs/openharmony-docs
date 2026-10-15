# ui_json_wrapper.h

## Overview

Declares the shared JSON data object for APIs such as UI perception and control.<br> Errors are reported through the documented return values. errno is not an error-reporting channel for these APIs; its value after a call is unspecified and must not be used to determine success or failure.<br> These functions may be called from any thread, including the UI thread, within the object's documented lifetime. Read-only queries on the same live object may run concurrently. The caller must serialize destruction with all uses of that object and its borrowed data. Operations on independent objects may run concurrently. These functions do not invoke application callbacks; they may be called from callbacks when the ownership and lifetime requirements are met. They are not async-signal-safe and must not be called from a signal handler. Queries read local memory synchronously; creation and destruction also allocate or free memory. There is no asynchronous completion or cancellation operation, and no maximum allocator latency is guaranteed.

**Include**: <arkui/ui_json_wrapper.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) | OH_ArkUI_NativeModule_UIJsonWrapper | Defines an opaque, immutable JSON data object.<br> The object holds a JSON string. It is used both to carry data delivered by the framework (UI sensing) and to carry commands injected by the application (UI control). The JSON object must contain a top-level schemaVersion field for version control and future compatibility. This requirement applies both to JSON supplied by the application and to JSON returned or delivered through callbacks by the framework, including results with no collected content.<br> The object is not reference-counted. Copying its pointer creates a borrowed alias, not an independent object or an additional ownership claim. The owner must destroy the object exactly once. Destruction invalidates all aliases and data pointers; do not use or destroy them again. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIJsonFormat](#oh_arkui_nativemodule_uijsonformat) | OH_ArkUI_NativeModule_UIJsonFormat | Enumerated type of the JSON output format. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIJsonWrapperCreate(const char *data, uint32_t size, OH_ArkUI_NativeModule_UIJsonWrapper **outOwned)](#oh_arkui_nativemodule_uijsonwrappercreate) | Creates a JSON data object from a caller-provided JSON string.<br> The provided string is copied into the object. The caller owns the created object and must release it with [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) when it is no longer needed. Copying the returned pointer does not retain the object or create another owner. After destruction, the pointer and all its aliases are invalid and must not be reused or destroyed again.<br> The provided string must represent a valid JSON object with a top-level schemaVersion field. If this field is missing or its value is outside the supported version range, this function returns ARKUI_ERROR_CODE_PARAM_INVALID; no default version is used. For example: { "schemaVersion": 1, ... }<br> Note: the data string passed to this function remains owned by the caller. Destroying the JSON wrapper object returned by this API does not release the memory pointed to by data on the caller's behalf. A parameter error requires correcting the input before retrying. For a size-overflow or allocation failure, reduce the input size or release resources before retrying; do not retry in a busy loop. On failure, no object ownership is transferred and a valid output slot contains NULL. |
| [const char *OH_ArkUI_NativeModule_UIJsonWrapperGetData(const OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrappergetdata) | Obtains the JSON string held by the object.<br> The returned string is read-only and terminated by '\0'. It points to memory owned by the JSON object and remains valid until the object is destroyed. The caller must not modify or free the returned string. The JSON object contains a top-level schemaVersion field. |
| [uint32_t OH_ArkUI_NativeModule_UIJsonWrapperGetSize(const OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrappergetsize) | Obtains the byte length of the JSON string.<br> The returned length excludes the terminating '\0' character and includes the schemaVersion field in the JSON string.<br> A NULL input does not produce a size for an object. Provide a valid live object before retrying; retrying with the same NULL input cannot succeed. This query does not allocate or release resources. |
| [void OH_ArkUI_NativeModule_UIJsonWrapperDestroy(OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrapperdestroy) | Destroys a JSON data object and releases its resources.<br> Passing NULL has no effect. Any pointer returned by [OH_ArkUI_NativeModule_UIJsonWrapperGetData](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) becomes invalid after this call.<br> Note: call this function only on a JSON wrapper object whose ownership you explicitly hold, for example, a wrapper created with [OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate), or a wrapper whose ownership you have explicitly obtained through an ownership transfer function. Do not use this function to release JSON wrapper objects that are constructed and handed out by the system, for example, the object delivered through [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback). |

## Enum type description

### OH_ArkUI_NativeModule_UIJsonFormat

```c
enum OH_ArkUI_NativeModule_UIJsonFormat
```

**Description**

Enumerated type of the JSON output format.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_JSON_COMPACT = 0 | Produces canonical JSON without unnecessary whitespace.<br>**Since**: 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_JSON_PRETTY = 1 | Generates JSON with double-space indentation and line breaks.<br>**Since**: 26.2.0 |


## Function description

### OH_ArkUI_NativeModule_UIJsonWrapperCreate()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIJsonWrapperCreate(const char *data, uint32_t size, OH_ArkUI_NativeModule_UIJsonWrapper **outOwned)
```

**Description**

Creates a JSON data object from a caller-provided JSON string.<br> The provided string is copied into the object. The caller owns the created object and must release it with [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) when it is no longer needed. Copying the returned pointer does not retain the object or create another owner. After destruction, the pointer and all its aliases are invalid and must not be reused or destroyed again.<br> The provided string must represent a valid JSON object with a top-level schemaVersion field. If this field is missing or its value is outside the supported version range, this function returns ARKUI_ERROR_CODE_PARAM_INVALID; no default version is used. For example: { "schemaVersion": 1, ... }<br> Note: the data string passed to this function remains owned by the caller. Destroying the JSON wrapper object returned by this API does not release the memory pointed to by data on the caller's behalf. A parameter error requires correcting the input before retrying. For a size-overflow or allocation failure, reduce the input size or release resources before retrying; do not retry in a busy loop. On failure, no object ownership is transferred and a valid output slot contains NULL.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Resource release**: ui_json_wrapper/OH_ArkUI_NativeModule_UIJsonWrapperDestroy {outOwned}

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *data | [in] Pointer to the UTF-8 encoded JSON string. It must not be NULL and must remain valid for the duration of the call. The callee does not retain it. The string must contain a valid JSON object with a supported schemaVersion. An empty string is invalid. At least size bytes must be readable. The input need not be terminated by '\0'; the created object appends its own terminator. The JSON text must not contain embedded NUL bytes; encode U+0000 as a JSON escape. |
| uint32_t size | [in] Number of bytes to copy from data, excluding any terminating null character. The function copies exactly size bytes without checking the actual string length, then appends a null terminator to the copy. The value must be greater than 0; a size of 0 returns ARKUI_ERROR_CODE_PARAM_INVALID. |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) **outOwned | [out] Receives the created object on success. The caller owns the returned object and must release it with [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy). It must not be NULL, requires no initialization, and on failure is set to NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if data or outOwned is NULL, size is 0, or data does not represent a valid JSON object, or schemaVersion is missing or unsupported.</li> <li>ARKUI_ERROR_CODE_INTERNAL_ERROR if the buffer size including its terminator cannot be represented on the current architecture, memory allocation fails, or copying fails.</li> </ul> |

### OH_ArkUI_NativeModule_UIJsonWrapperGetData()

```c
const char *OH_ArkUI_NativeModule_UIJsonWrapperGetData(const OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**Description**

Obtains the JSON string held by the object.<br> The returned string is read-only and terminated by '\0'. It points to memory owned by the JSON object and remains valid until the object is destroyed. The caller must not modify or free the returned string. The JSON object contains a top-level schemaVersion field.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [in] The JSON data object. It must not be NULL. The object is borrowed and must remain valid for the entire call. The callee does not retain it. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | <ul> <li>The borrowed JSON string. The caller must not modify or free it.</li> <li>NULL if json is NULL.</li> </ul> |

### OH_ArkUI_NativeModule_UIJsonWrapperGetSize()

```c
uint32_t OH_ArkUI_NativeModule_UIJsonWrapperGetSize(const OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**Description**

Obtains the byte length of the JSON string.<br> The returned length excludes the terminating '\0' character and includes the schemaVersion field in the JSON string.<br> A NULL input does not produce a size for an object. Provide a valid live object before retrying; retrying with the same NULL input cannot succeed. This query does not allocate or release resources.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [in] The JSON data object. It must not be NULL. The object is borrowed and must remain valid for the entire call. The callee does not retain it. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | <ul> <li>The byte length of the JSON string, excluding the terminating '\0' character.</li> <li>0 if json is NULL.</li> </ul> |

### OH_ArkUI_NativeModule_UIJsonWrapperDestroy()

```c
void OH_ArkUI_NativeModule_UIJsonWrapperDestroy(OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**Description**

Destroys a JSON data object and releases its resources.<br> Passing NULL has no effect. Any pointer returned by [OH_ArkUI_NativeModule_UIJsonWrapperGetData](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) becomes invalid after this call.<br> Note: call this function only on a JSON wrapper object whose ownership you explicitly hold, for example, a wrapper created with [OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate), or a wrapper whose ownership you have explicitly obtained through an ownership transfer function. Do not use this function to release JSON wrapper objects that are constructed and handed out by the system, for example, the object delivered through [OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [in] The JSON data object to destroy. NULL is allowed and has no effect. The caller must own the object. Destruction invalidates the object and all aliases immediately; they must not be used or destroyed again. Borrowed objects must not be passed to this function. |


