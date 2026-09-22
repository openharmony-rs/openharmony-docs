# inputmethod_attach_options_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing the option object bound to the input method.

**Include**: <inputmethod/inputmethod_attach_options_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) | InputMethod_AttachOptions | Options for binding the input method.<br> The options when attaching input method. |

### Function

| Name | Description |
| -- | -- |
| [InputMethod_AttachOptions *OH_AttachOptions_Create(bool showKeyboard)](#oh_attachoptions_create) | Create a new [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance. |
| [InputMethod_AttachOptions *OH_AttachOptions_CreateWithRequestKeyboardReason(bool showKeyboard, InputMethod_RequestKeyboardReason requestKeyboardReason)](#oh_attachoptions_createwithrequestkeyboardreason) | Create a new [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance. |
| [void OH_AttachOptions_Destroy(InputMethod_AttachOptions *options)](#oh_attachoptions_destroy) | Delete a [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance. |
| [InputMethod_ErrorCode OH_AttachOptions_IsShowKeyboard(InputMethod_AttachOptions *options, bool *showKeyboard)](#oh_attachoptions_isshowkeyboard) | Get showKeyboard value from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md). |
| [InputMethod_ErrorCode OH_AttachOptions_GetRequestKeyboardReason(InputMethod_AttachOptions *options, int *requestKeyboardReason)](#oh_attachoptions_getrequestkeyboardreason) | Obtains the reason that triggers the input method from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md). |

## Function description

### OH_AttachOptions_Create()

```c
InputMethod_AttachOptions *OH_AttachOptions_Create(bool showKeyboard)
```

**Description**

Create a new [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool showKeyboard | Pointer to whether to display the keyboard during binding. true: The keyboard is displayed after the binding is complete. false: The keyboard is hidden after the binding is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_AttachOptions *](capi-inputmethod-inputmethod-attachoptions.md) | If the creation succeeds, a pointer to the newly created [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md)  instance is returned. If the creation fails, NULL is returned, possible cause is insufficient memory. |

### OH_AttachOptions_CreateWithRequestKeyboardReason()

```c
InputMethod_AttachOptions *OH_AttachOptions_CreateWithRequestKeyboardReason(bool showKeyboard, InputMethod_RequestKeyboardReason requestKeyboardReason)
```

**Description**

Create a new [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool showKeyboard | Represents whether to show the keyboard. |
| InputMethod_RequestKeyboardReason requestKeyboardReason |  Reason for requesting the keyboard. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_AttachOptions *](capi-inputmethod-inputmethod-attachoptions.md) | If the creation succeeds, a pointer to the newly created [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md)  instance is returned. If the creation fails, NULL is returned, possible cause is insufficient memory. |

### OH_AttachOptions_Destroy()

```c
void OH_AttachOptions_Destroy(InputMethod_AttachOptions *options)
```

**Description**

Delete a [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Represents a pointer to an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance which will be destroyed. |

### OH_AttachOptions_IsShowKeyboard()

```c
InputMethod_ErrorCode OH_AttachOptions_IsShowKeyboard(InputMethod_AttachOptions *options, bool *showKeyboard)
```

**Description**

Get showKeyboard value from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Represents a pointer to an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance which will be get value from. |
| bool *showKeyboard |  Represents showKeyboard value. true - need to show keyboard. false - no need to show keyboard. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_AttachOptions_GetRequestKeyboardReason()

```c
InputMethod_ErrorCode OH_AttachOptions_GetRequestKeyboardReason(InputMethod_AttachOptions *options, int *requestKeyboardReason)
```

**Description**

Obtains the reason that triggers the input method from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Represents a pointer to an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance which will be get value from. |
| int *requestKeyboardReason |  Pointer to the reason for requesting the keyboard. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer. If options is NULL, or requestKeyboardReason is NULL.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |


