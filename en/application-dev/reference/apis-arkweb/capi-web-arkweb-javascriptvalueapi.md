# ArkWeb_JavaScriptValueAPI

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-03T09:53:08.124Z pushedAt=2026-08-06T11:24:14.077Z -->

```c
typedef struct {...} ArkWeb_JavaScriptValueAPI
```

## Overview

ArkWeb_JavaScriptValueAPI is a JavaScript-related Native API struct. This struct provides functions for creating JavaScript values, supporting the conversion of Native data into a JavaScript-recognizable format and returning it to HTML. This conversion mechanism parses and encapsulates the Native data buffer based on the specified JavaScript value type to generate the corresponding JavaScript value object. It is applicable to scenarios where data needs to be passed from the Native layer to the Web layer, enabling bidirectional data interaction between Native and Web and improving app development flexibility.

Call the OH_ArkWeb_GetNativeAPI method on the UI thread to obtain JavaScript-related APIs. Before calling, you are advised to use [ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#macros) to check the availability of the function pointer, to prevent crashes caused by mismatch between the SDK and device ROM.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t size | Size of the struct.|

### Member Functions

| Name                                                                                                                     | Description|
|-------------------------------------------------------------------------------------------------------------------------|----|
| [ArkWeb_JavaScriptValuePtr (\*createJavaScriptValue)(ArkWeb_JavaScriptValueType type, void* data, size_t dataLength)](#createjavascriptvalue) | Creates a JavaScript value to be returned to HTML.  |

## Member Function Description

### createJavaScriptValue()

```c
ArkWeb_JavaScriptValuePtr (*createJavaScriptValue)(ArkWeb_JavaScriptValueType type, void* data, size_t dataLength)
```

**Description**

Creates a JavaScript value to be returned to HTML. This function performs type conversion and encapsulation on the data in the data buffer based on the specified type parameter to generate the corresponding JavaScript value object. NULL is returned if the conversion fails. Before using this function, obtain the JavaScript API through OH_ArkWeb_GetNativeAPI and check the availability of the function pointer.

**Since**: 18

**Parameters**

| Name                            | Description|
|---------------------------------|----|
| ArkWeb_JavaScriptValueType type | Type of the JavaScript value.  |
| void* data | Pointer to the data buffer of the JavaScript value. The data must be provided in the type corresponding to **type**. The memory is managed by the caller and must remain valid until the function returns. For types that do not require data, **nullptr** can be passed. |
| size_t dataLength | Number of bytes pointed to by the data buffer of the JavaScript value. This value must match the length of the buffer pointed to by **data**. When **data** is **nullptr**, this value must be set to **0**. |

**Returns**

| Type                           | Description|
|-------------------------------|----|
| [ArkWeb_JavaScriptValuePtr](capi-web-arkweb-javascriptvalue8h.md) | Created JavaScript value. NULL is returned when the input parameter is invalid or memory allocation fails. |