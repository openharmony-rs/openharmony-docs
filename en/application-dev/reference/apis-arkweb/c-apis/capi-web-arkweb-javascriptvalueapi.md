# ArkWeb_JavaScriptValueAPI

```c
struct ArkWeb_JavaScriptValueAPI {...}
```

## Overview

ArkWeb_JavaScriptValueAPI is a JavaScript-related Native API struct. This struct provides functions for creating JavaScript values, supporting the conversion of Native data into a JavaScript-recognizable format and returning it to HTML. This conversion mechanism parses and encapsulates the Native data buffer based on the specified JavaScript value type to generate the corresponding JavaScript value object. It is applicable to scenarios where data needs to be passed from the Native layer to the Web layer, enabling bidirectional data interaction between Native and Web and improving app development flexibility. <br>Call the OH_ArkWeb_GetNativeAPI method on the UI thread to obtain JavaScript-related APIs. Before calling, you are advised to use {@link ARKWEB_MEMBER_MISSING} to check the availability of the function pointer, to prevent crashes caused by mismatch between the SDK and device ROM.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t size | Size of the struct. |


### Member functions

| Name | Description |
| -- | -- |
| [ArkWeb_JavaScriptValuePtr (\*createJavaScriptValue)(ArkWeb_JavaScriptValueType type, void* data, size_t dataLength)](#createjavascriptvalue) | Creates a JavaScript value to be returned to HTML. This function performs type conversion and encapsulation on the data in the data buffer based on the specified type parameter to generate the corresponding JavaScript value object. NULL is returned if the conversion fails. Before using this function, obtain the JavaScript API through OH_ArkWeb_GetNativeAPI and check the availability of the function pointer. |

## Member function description

### createJavaScriptValue()

```c
ArkWeb_JavaScriptValuePtr (*createJavaScriptValue)(ArkWeb_JavaScriptValueType type, void* data, size_t dataLength)
```

**Description**

Creates a JavaScript value to be returned to HTML. This function performs type conversion and encapsulation on the data in the data buffer based on the specified type parameter to generate the corresponding JavaScript value object. NULL is returned if the conversion fails. Before using this function, obtain the JavaScript API through OH_ArkWeb_GetNativeAPI and check the availability of the function pointer.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_JavaScriptValueType](capi-arkweb-type-h.md#arkweb_javascriptvaluetype) type | Type of the JavaScript value. |
|  void* data | Pointer to the data buffer of the JavaScript value. The data must be provided in the type corresponding to **type**. The memory is managed by the caller and must remain valid until the function returns. For types that do not require data, **nullptr** can be passed. |
|  size_t dataLength | Number of bytes pointed to by the data buffer of the JavaScript value. This value must match the length of the buffer pointed to by **data**. When **data** is **nullptr**, this value must be set to **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkWeb_JavaScriptValuePtr](capi-web-arkweb-javascriptvalue8h.md) | Created JavaScript value. NULL is returned when the input parameter is invalid or memory allocation          fails. |


