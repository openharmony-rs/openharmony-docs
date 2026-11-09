# OH_InputMethod_PreviewTextStyle

```c
typedef struct OH_InputMethod_PreviewTextStyle OH_InputMethod_PreviewTextStyle
```

## Overview

OH_InputMethod_PreviewTextStyle is an opaque type of the pre-screen text style, and is used to describe the underline style and color information of the pre-screen text. The caller cannot directly access its internal members. The caller can perform operations only through the function interfaces provided in this header file. <br> <br>Use: Provide style description for the pre-screen text with style for the input method. Contains the following attributes: <br>-underlineStyle: enumerated value. The value is [OH_InputMethod_UnderlineStyle](capi-inputmethod-types-capi-h.md#oh_inputmethod_underlinestyle). The default value is OH_INPUTMETHOD_DOWNLINE_SPECIAL_NONE. <br>- UnderlineColor: The format is 0xRRGGBB. This parameter is valid only when hasUnderlineColor is set to true. Transparency channel(AA) is invalid and will be Ignored by the editor. <br>- Indicates whether to explicitly set the color(hasUnderlineColor): false indicates that the theme color is applied. <br> <br>Lifecycle Management: <br>-Creation mode: The [OH_InputMethod_PreviewTextStyle_Create](#oh_inputmethod_previewtextstyle_create) function is used to create a file. One is returned. Pointer to the new OH_InputMethod_PreviewTextStyle instance. If the creation fails, NULL is returned. The possible cause is that the memory is insufficient. <br>- Destruction mode: Destroy by using the [OH_InputMethod_PreviewTextStyle_Destroy](#oh_inputmethod_previewtextstyle_destroy) function. Pointer to the instance to be destroyed. The pointer cannot be used after being destroyed. You are advised to set the pointer to NULL to avoid misuse. <br>-Pairing relationship: OH_InputMethod_PreviewTextStyle_Create and OH_InputMethod_PreviewTextStyle_Destroy must be used in pairs. The memory must be released through Destroy. Otherwise, memory leakage occurs.

<!--Device-typedef struct OH_InputMethod_PreviewTextStyle OH_InputMethod_PreviewTextStyle--><!--Device-typedef struct OH_InputMethod_PreviewTextStyle OH_InputMethod_PreviewTextStyle-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

**Header file**: [inputmethod_preview_text_style_capi.h](capi-inputmethod-preview-text-style-capi-h.md)

