# inputmethod_controller_capi.h

## Overview

Provides methods for binding and unbinding input methods.

**Include**: <inputmethod/inputmethod_controller_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [InputMethod_ErrorCode OH_InputMethodController_Attach(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)](#oh_inputmethodcontroller_attach) | Attach application to the input method service. |
| [InputMethod_ErrorCode OH_InputMethodController_AttachWithUIContext(ArkUI_ContextHandle context, InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)](#oh_inputmethodcontroller_attachwithuicontext) | Attach application to the input method service. |
| [InputMethod_ErrorCode OH_InputMethodController_Detach(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodcontroller_detach) | Detach application from the input method service. |

## Function description

### OH_InputMethodController_Attach()

```c
InputMethod_ErrorCode OH_InputMethodController_Attach(InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)
```

**Description**

Attach application to the input method service.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| InputMethod_TextEditorProxy *textEditorProxy | Pointer to the {@link InputMethod_TextEditorProxy} instance. The caller needs to manage the **textEditorProxy** lifecycle. If the calling is successful, the caller cannot release **textEditorProxy** before the next binding or unbinding call. |
| InputMethod_AttachOptions *options | Represents a pointer to an {@link InputMethod_AttachOptions} instance. The options when attaching input method. |
| InputMethod_InputMethodProxy **inputMethodProxy | Represents a pointer to an {@link InputMethod_InputMethodProxy} instance. Lifecycle is maintained until the next attach or detach call. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_PARAMCHECK} - parameter check failed.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodController_AttachWithUIContext()

```c
InputMethod_ErrorCode OH_InputMethodController_AttachWithUIContext(ArkUI_ContextHandle context, InputMethod_TextEditorProxy *textEditorProxy, InputMethod_AttachOptions *options, InputMethod_InputMethodProxy **inputMethodProxy)
```

**Description**

Attach application to the input method service.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_ContextHandle context | Pointer to the [ArkUI_Context](../apis-arkui/capi-arkui-nativemodule-arkui-context.md) instance. |
| InputMethod_TextEditorProxy *textEditorProxy | Pointer to the {@link InputMethod_TextEditorProxy} instance. The caller needs to manage the **textEditorProxy** lifecycle. If the calling is successful, the caller cannot release **textEditorProxy** before the next binding or unbinding call. |
| InputMethod_AttachOptions *options | Represents a pointer to an {@link InputMethod_AttachOptions} instance. The options when attaching input method. |
| InputMethod_InputMethodProxy **inputMethodProxy | Represents a pointer to an {@link InputMethod_InputMethodProxy} instance. Lifecycle is maintained until the next attach or detach call. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_PARAMCHECK} - parameter check failed.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |

### OH_InputMethodController_Detach()

```c
InputMethod_ErrorCode OH_InputMethodController_Detach(InputMethod_InputMethodProxy *inputMethodProxy)
```

**Description**

Detach application from the input method service.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| InputMethod_InputMethodProxy *inputMethodProxy | Represents a pointer to an {@link InputMethod_InputMethodProxy} instance. The inputMethodProxy is obtained from [OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach). |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>{@link IME_ERR_OK} - success.<br>    <br>{@link IME_ERR_IMCLIENT} - input method client error.<br>    <br>{@link IME_ERR_IMMS} - input method manager service error.<br>    <br>{@link IME_ERR_NULL_POINTER} - unexpected null pointer.<br>    <br>Specific error codes can be referenced {@link InputMethod_ErrorCode}. |


