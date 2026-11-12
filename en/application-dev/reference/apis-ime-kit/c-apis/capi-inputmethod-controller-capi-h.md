# inputmethod_controller_capi.h

## Overview

Provides methods for binding and unbinding input methods.

**File to Include**: <inputmethod/inputmethod_controller_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [InputMethod_ErrorCode OH_InputMethodController_Attach(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)](#oh_inputmethodcontroller_attach) | Binds an application to the input method service. |
| [InputMethod_ErrorCode OH_InputMethodController_AttachWithUIContext(ArkUI_ContextHandle context, InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)](#oh_inputmethodcontroller_attachwithuicontext) | Binds an application to the input method service. |
| [InputMethod_ErrorCode OH_InputMethodController_Detach(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodcontroller_detach) | Unbinds an application from the input method service. |
| [InputMethod_ErrorCode OH_InputMethod_InputMethodController_GetCurrentInputMethod(char **bundleName, uint32_t *bundleNameLength, char **abilityName, uint32_t *abilityNameLength)](#oh_inputmethod_inputmethodcontroller_getcurrentinputmethod) | Obtains the current input method. |

## Function description

### OH_InputMethodController_Attach()

```c
InputMethod_ErrorCode OH_InputMethodController_Attach(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)
```

**Description**

Binds an application to the input method service.

<!--Device-InputMethod_ErrorCode OH_InputMethodController_Attach(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)--><!--Device-InputMethod_ErrorCode OH_InputMethodController_Attach(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. The caller needs to manage the **<br>textEditorProxy** lifecycle. If the calling is successful, the caller cannot release **textEditorProxy** before the next binding or unbinding call. |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Pointer to the [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance. This parameter is used to specify the options of attaching an input method. |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) **inputMethodProxy | Double pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The lifecycle lasts until the next binding or unbinding call. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodController_AttachWithUIContext()

```c
InputMethod_ErrorCode OH_InputMethodController_AttachWithUIContext(ArkUI_ContextHandle context, InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)
```

**Description**

Binds an application to the input method service.

<!--Device-InputMethod_ErrorCode OH_InputMethodController_AttachWithUIContext(ArkUI_ContextHandle context, InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)--><!--Device-InputMethod_ErrorCode OH_InputMethodController_AttachWithUIContext(ArkUI_ContextHandle context, InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | Pointer to the [ArkUI_Context](../../apis-arkui/c-apis/capi-arkui-nativemodule-arkui-context.md) instance. |
| [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) *textEditorProxy | Pointer to the [InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md) instance. The caller needs to manage the **<br>textEditorProxy** lifecycle. If the calling is successful, the caller cannot release **textEditorProxy** before the next binding or unbinding call. |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Pointer to the [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance. This parameter is used to specify the options of attaching an input method. |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) **inputMethodProxy | Double pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance. The lifecycle lasts until the next binding or unbinding call. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Parameter error. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethodController_Detach()

```c
InputMethod_ErrorCode OH_InputMethodController_Detach(InputMethod_InputMethodProxy *inputMethodProxy)
```

**Description**

Unbinds an application from the input method service.

<!--Device-InputMethod_ErrorCode OH_InputMethodController_Detach(InputMethod_InputMethodProxy *inputMethodProxy)--><!--Device-InputMethod_ErrorCode OH_InputMethodController_Detach(InputMethod_InputMethodProxy *inputMethodProxy)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | Pointer to the [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) instance obtained by calling [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | An error code. <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Client error in input method. <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method service error. <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - An unexpected null pointer. <br>For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_InputMethod_InputMethodController_GetCurrentInputMethod()

```c
InputMethod_ErrorCode OH_InputMethod_InputMethodController_GetCurrentInputMethod(char **bundleName, uint32_t *bundleNameLength, char **abilityName, uint32_t *abilityNameLength)
```

**Description**

Obtains the current input method.

<!--Device-InputMethod_ErrorCode OH_InputMethod_InputMethodController_GetCurrentInputMethod(char **bundleName, uint32_t *bundleNameLength, char **abilityName, uint32_t *abilityNameLength)--><!--Device-InputMethod_ErrorCode OH_InputMethod_InputMethodController_GetCurrentInputMethod(char **bundleName, uint32_t *bundleNameLength, char **abilityName, uint32_t *abilityNameLength)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **bundleName | [out] This parameter is used as an output parameter and indicates the level-2 pointer that points to the obtained bundleName character string. The caller needs to use free() to release the call after using the caller, Avoid memory leakage. |
| uint32_t *bundleNameLength | [out] Pointer to the length of the obtained bundleName string. This parameter is used as an output parameter. |
| char **abilityName | [out] This parameter is used as an output parameter and indicates the level-2 pointer to the obtained abilityName character string. The caller needs to use free() to release the call after using the caller, Avoid memory leakage. |
| uint32_t *abilityNameLength | [out] Pointer to the length of the obtained abilityName character string. This parameter is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Success. </li> <li>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Input method management service error. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |


