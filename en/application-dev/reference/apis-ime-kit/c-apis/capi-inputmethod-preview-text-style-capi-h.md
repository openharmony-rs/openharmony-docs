# inputmethod_preview_text_style_capi.h

## Overview

Provides methods for creating, destroying, and accessing the preview text style object. PreviewTextStyle describes the underline style and color for preview text, used when the input method sets preview text with style. Create/Destroy must be paired. <br> <br>Function: Creates and manages OH_InputMethod_PreviewTextStyle instances, describing the underline style (none/solid/wavy/dashed) and color of preview text. The color format is 0xRRGGBB; the alpha channel (AA) is invalid and will be ignored by the editor. <br> <br>Usage scenario: When the input method app sets preview text with style via the SetPreviewTextWithStyleFunc callback, the system constructs a PreviewTextStyle object and passes it to the app, which reads the style information via Get methods for rendering.

**File to Include**: <inputmethod/inputmethod_preview_text_style_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) | OH_InputMethod_PreviewTextStyle | OH_InputMethod_PreviewTextStyle is an opaque type of the pre-screen text style, and is used to describe the underline style and color information of the pre-screen text. The caller cannot directly access its internal members. The caller can perform operations only through the function interfaces provided in this header file. <br> <br>Use: Provide style description for the pre-screen text with style for the input method. Contains the following attributes: <br>-underlineStyle: enumerated value. The value is [OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle). The default value is OH_INPUTMETHOD_DOWNLINE_SPECIAL_NONE. <br>- UnderlineColor: The format is 0xRRGGBB. This parameter is valid only when hasUnderlineColor is set to true. Transparency channel(AA) is invalid and will be Ignored by the editor. <br>- Indicates whether to explicitly set the color(hasUnderlineColor): false indicates that the theme color is applied. <br> <br>Lifecycle Management: <br>-Creation mode: The [OH_InputMethod_PreviewTextStyle_Create](#oh_inputmethod_previewtextstyle_create) function is used to create a file. One is returned. Pointer to the new OH_InputMethod_PreviewTextStyle instance. If the creation fails, NULL is returned. The possible cause is that the memory is insufficient. <br>- Destruction mode: Destroy by using the [OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy) function. Pointer to the instance to be destroyed. The pointer cannot be used after being destroyed. You are advised to set the pointer to NULL to avoid misuse. <br>-Pairing relationship: OH_InputMethod_PreviewTextStyle_Create and OH_InputMethod_PreviewTextStyle_Destroy must be used in pairs. The memory must be released through Destroy. Otherwise, memory leakage occurs. |

### Functions

| Name | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)](#oh_inputmethod_previewtextstyle_create) | Create a new [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance. The default underline style is OH_INPUTMETHOD_DOWNLINE_SHOP_NONE. The default underline color is 0, and hasUnderlineColor is false. <br> <br>Application scenario: This function is called when you need to construct a pre-screen text style object. <br> <br>Lifecycle management: The returned object must pass the [OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy). Destroy. Create and Destroy must be used in pairs. If the memory is not destroyed, a memory leak occurs. |
| [void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)](#oh_inputmethod_previewtextstyle_destroy) | Destroy a [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance. The style pointer cannot be used after being destroyed. You are advised to set the pointer to NULL to avoid misuse. <br> <br>Application scenario: This function is invoked to release memory when the PreviewTextStyle instance is no longer required. <br> <br>Life cycle management: When NULL is input, the function does not perform any processing and does not break down. |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)](#oh_inputmethod_previewtextstyle_setunderlinestyle) | Sets the underline style of the pre-screen text. |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)](#oh_inputmethod_previewtextstyle_getunderlinestyle) | Gets the underline style of the pre-screen text. |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)](#oh_inputmethod_previewtextstyle_setunderlinecolor) | Sets the underline color of the pre-screen text. The color format is 0xRRGGBB. The transparency channel(AA) is invalid and will be ignored by the editor. When this function is called, the underline color is marked as explicitly specified; When [OH_InputMethod_PreviewTextStyle_HasUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_hasunderlinecolor) is called later, its hasUnderlineColor output parameter will be true. |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)](#oh_inputmethod_previewtextstyle_getunderlinecolor) | Obtains the underline color of the pre-screen text. |
| [InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)](#oh_inputmethod_previewtextstyle_hasunderlinecolor) | Obtains whether the underline color is set from [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md).<br> The result is determined by whether [OH_InputMethod_PreviewTextStyle_SetUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_setunderlinecolor) has been invoked. If hasUnderlineColor has been called, the output value is true. Otherwise, the output value is false. |

## Function description

### OH_InputMethod_PreviewTextStyle_Create()

```c
OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)
```

**Description**

Create a new [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance. The default underline style is OH_INPUTMETHOD_DOWNLINE_SHOP_NONE. The default underline color is 0, and hasUnderlineColor is false. <br> <br>Application scenario: This function is called when you need to construct a pre-screen text style object. <br> <br>Lifecycle management: The returned object must pass the [OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy). Destroy. Create and Destroy must be used in pairs. If the memory is not destroyed, a memory leak occurs.

<!--Device-OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)--><!--Device-OH_InputMethod_PreviewTextStyle *OH_InputMethod_PreviewTextStyle_Create(void)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Returns**:

| Type | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle *](capi-inputmethod-oh-inputmethod-previewtextstyle.md) | If the creation is successful, a pointer to the newly created [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance is returned. If the creation fails, NULL is returned, Possible failure causes are insufficient memory. |

### OH_InputMethod_PreviewTextStyle_Destroy()

```c
void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)
```

**Description**

Destroy a [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance. The style pointer cannot be used after being destroyed. You are advised to set the pointer to NULL to avoid misuse. <br> <br>Application scenario: This function is invoked to release memory when the PreviewTextStyle instance is no longer required. <br> <br>Life cycle management: When NULL is input, the function does not perform any processing and does not break down.

<!--Device-void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)--><!--Device-void OH_InputMethod_PreviewTextStyle_Destroy(OH_InputMethod_PreviewTextStyle *style)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] Input pointer to the [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance to be destroyed. If NULL is input, the function does not perform any processing. |

### OH_InputMethod_PreviewTextStyle_SetUnderlineStyle()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)
```

**Description**

Sets the underline style of the pre-screen text.

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle underlineStyle)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] Input pointer to the [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance to be set. Cannot be NULL. |
| [OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle) underlineStyle | [in] Input parameter. The value is underlined. For details, see [OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle). |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_InputMethod_PreviewTextStyle_GetUnderlineStyle()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)
```

**Description**

Gets the underline style of the pre-screen text.

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineStyle(OH_InputMethod_PreviewTextStyle *style, OH_InputMethod_UnderlineStyle *underlineStyle)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] Input pointer to the [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance to be read. Cannot be NULL. |
| [OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle) *underlineStyle | [out] Output pointer, which is used to return the underline style. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_InputMethod_PreviewTextStyle_SetUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)
```

**Description**

Sets the underline color of the pre-screen text. The color format is 0xRRGGBB. The transparency channel(AA) is invalid and will be ignored by the editor. When this function is called, the underline color is marked as explicitly specified; When [OH_InputMethod_PreviewTextStyle_HasUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_hasunderlinecolor) is called later, its hasUnderlineColor output parameter will be true.

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_SetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t underlineColor)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] Input pointer to the [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance to be set. Cannot be NULL. |
| uint32_t underlineColor | [in] Input parameter, underlined, in the format of 0xRRGGBB. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_InputMethod_PreviewTextStyle_GetUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)
```

**Description**

Obtains the underline color of the pre-screen text.

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_GetUnderlineColor(OH_InputMethod_PreviewTextStyle *style, uint32_t *underlineColor)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] Input pointer to the [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance to be read. Cannot be NULL. |
| uint32_t *underlineColor | [out] Output pointer, which is used to return the underline color. The format is 0xRRGGBB. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_InputMethod_PreviewTextStyle_HasUnderlineColor()

```c
InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)
```

**Description**

Obtains whether the underline color is set from [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md).<br> The result is determined by whether [OH_InputMethod_PreviewTextStyle_SetUnderlineColor](capi-inputmethod-preview-text-style-capi-h.md#oh_inputmethod_previewtextstyle_setunderlinecolor) has been invoked. If hasUnderlineColor has been called, the output value is true. Otherwise, the output value is false.

<!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)--><!--Device-InputMethod_ErrorCode OH_InputMethod_PreviewTextStyle_HasUnderlineColor(OH_InputMethod_PreviewTextStyle *style, bool *hasUnderlineColor)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) *style | [in] Input pointer to the [OH_InputMethod_PreviewTextStyle](capi-inputmethod-oh-inputmethod-previewtextstyle.md) instance to be read. Cannot be NULL. |
| bool *hasUnderlineColor | [out] Output pointer, which is used to return whether the underline color is set. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |


