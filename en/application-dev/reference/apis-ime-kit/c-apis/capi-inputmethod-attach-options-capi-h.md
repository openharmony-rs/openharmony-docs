# inputmethod_attach_options_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing input method attach option objects, used to manage configuration parameters when an app attaches to an input method.

**File to Include**: <inputmethod/inputmethod_attach_options_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) | InputMethod_AttachOptions | Options for binding the input method. |

### Functions

| Name | Description |
| -- | -- |
| [InputMethod_AttachOptions *OH_AttachOptions_Create(bool showKeyboard)](#oh_attachoptions_create) | Creates an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance for simple scenarios where only keyboard visibility needs to be controlled. If you also need to specify the reason for requesting the keyboard, it is recommended that you use [OH_AttachOptions_CreateWithRequestKeyboardReason](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_createwithrequestkeyboardreason). <br>Paired calls: This function must be called in pairs with [OH_AttachOptions_Destroy](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_destroy). Objects created by **<br>OH_AttachOptions_Create** must be destroyed via **OH_AttachOptions_Destroy**; otherwise, memory leaks will occur. <br>Lifecycle management: <br> <br> - After creation, it can be read multiple times (IsShowKeyboard). <br> - After options are passed to the attach function, the attach function reads configuration information. Once the attach operation completes, options can be destroyed immediately, as the configuration has already been read. <br> - Destroyed options must not be used again. |
| [InputMethod_AttachOptions *OH_AttachOptions_CreateWithRequestKeyboardReason(bool showKeyboard, InputMethod_RequestKeyboardReason requestKeyboardReason)](#oh_attachoptions_createwithrequestkeyboardreason) | Creates an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance, specifying both keyboard visibility and the reason for requesting the keyboard. The **requestKeyboardReason** parameter identifies the scenario that triggers the keyboard request, enabling the system to recognize input scenarios and deliver improved user experience. <br>Paired calls: This function must be called in pairs with [OH_AttachOptions_Destroy](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_destroy). The object created by the create function must be destroyed via **OH_AttachOptions_Destroy**. <br>Lifecycle management: Consistent with **OH_AttachOptions_Create**. Multiple read operations can be performed after creation. The instance can be destroyed immediately once the attach operation completes. |
| [void OH_AttachOptions_Destroy(InputMethod_AttachOptions *options)](#oh_attachoptions_destroy) | Destroys an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance, releasing memory resources allocated by the **<br>OH_AttachOptions_Create** function. This method is used in pairs with **OH_AttachOptions_Create** and **<br>OH_AttachOptions_CreateWithRequestKeyboardReason**. <br>Paired calls: This function must be called in pairs with **OH_AttachOptions_Create** or **<br>OH_AttachOptions_CreateWithRequestKeyboardReason**. Each instance created by **OH_AttachOptions_Create** shall be destroyed by exactly one invocation of **OH_AttachOptions_Destroy**. <br>Lifecycle management: <br> - After OH_AttachOptions_Destroy is called, the options pointer becomes invalid and shall not be used further. <br> - OH_AttachOptions_Destroy cannot be called twice on the same options pointer; otherwise, a double-free error will occur. <br> - It is recommended that you call OH_AttachOptions_Destroy immediately after a successful attach operation, since configuration information has already been read upon attachment. |
| [InputMethod_ErrorCode OH_AttachOptions_IsShowKeyboard(InputMethod_AttachOptions *options, bool *showKeyboard)](#oh_attachoptions_isshowkeyboard) | Obtains the value that indicates whether to show the keyboard from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md). <br>Preconditions: **options** must be a valid instance created via the **OH_AttachOptions_Create** function, and **<br>showKeyboard** must point to a valid **bool** variable. |
| [InputMethod_ErrorCode OH_AttachOptions_GetRequestKeyboardReason(InputMethod_AttachOptions *options, int *requestKeyboardReason)](#oh_attachoptions_getrequestkeyboardreason) | Obtains the reason for requesting the keyboard from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md). <br>Preconditions: **options** must be a valid instance created via **<br>OH_AttachOptions_CreateWithRequestKeyboardReason** (For instances created via **OH_AttachOptions_Create**, the default value of **requestKeyboardReason** is **IME_REQUEST_REASON_NONE**). **requestKeyboardReason** must point to a valid variable of **InputMethod_RequestKeyboardReason**. |

## Function description

### OH_AttachOptions_Create()

```c
InputMethod_AttachOptions *OH_AttachOptions_Create(bool showKeyboard)
```

**Description**

Creates an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance for simple scenarios where only keyboard visibility needs to be controlled. If you also need to specify the reason for requesting the keyboard, it is recommended that you use [OH_AttachOptions_CreateWithRequestKeyboardReason](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_createwithrequestkeyboardreason). <br>Paired calls: This function must be called in pairs with [OH_AttachOptions_Destroy](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_destroy). Objects created by **<br>OH_AttachOptions_Create** must be destroyed via **OH_AttachOptions_Destroy**; otherwise, memory leaks will occur. <br>Lifecycle management: <br> <br> - After creation, it can be read multiple times (IsShowKeyboard). <br> - After options are passed to the attach function, the attach function reads configuration information. Once the attach operation completes, options can be destroyed immediately, as the configuration has already been read. <br> - Destroyed options must not be used again.

<!--Device-InputMethod_AttachOptions *OH_AttachOptions_Create(bool showKeyboard)--><!--Device-InputMethod_AttachOptions *OH_AttachOptions_Create(bool showKeyboard)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool showKeyboard | Input parameter that indicates whether to show the keyboard upon attachment. <br>Usage scenarios: Set to **true** for scenarios requiring immediate input after an input box gains focus (for example, a text‑editing box). Set to **false** for scenarios where an interaction channel is established first with no keyboard brought up (for example, a search box that brings up the keyboard only after user clicks). <br>Use effect: When **showKeyboard** is **true**, the keyboard pops up automatically upon successful attachment. When **showKeyboard** is **false**, the keyboard does not pop up after successful attachment; you need to call *<br>*OH_InputMethodProxy_ShowKeyboard** to bring up the keyboard. <br>Value range: **true** or **false**. <br>Default value: No default value. You must specify it explicitly. <br>Value‑setting guideline: Parameter values are determined based on service scenarios. A value of **true**<br>applies to scenarios requiring immediate input, while a value of **false** applies to scenarios requiring delayed keyboard display. For the latter, you can call **ShowKeyboard** to bring up the keyboard at a later time. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_AttachOptions *](capi-inputmethod-inputmethod-attachoptions.md) | Pointer type. <br>Creation successful: Returns a pointer to the newly created **InputMethod_AttachOptions** instance. The pointer is valid and can be used for subsequent operations. <br>Creation failed: Returns **NULL**. Possible causes include full app address space (insufficient memory). <br>Null check: You must check whether the return value is **NULL** before using it. If **NULL** is returned, the pointer cannot be used and you should troubleshoot memory conditions or retry later. <br>Memory management: Memory for the returned pointer is allocated internally by the create function. You need to release it using **OH_AttachOptions_Destroy**. Do not use **free()** or other methods to release the memory. |

### OH_AttachOptions_CreateWithRequestKeyboardReason()

```c
InputMethod_AttachOptions *OH_AttachOptions_CreateWithRequestKeyboardReason(bool showKeyboard, InputMethod_RequestKeyboardReason requestKeyboardReason)
```

**Description**

Creates an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance, specifying both keyboard visibility and the reason for requesting the keyboard. The **requestKeyboardReason** parameter identifies the scenario that triggers the keyboard request, enabling the system to recognize input scenarios and deliver improved user experience. <br>Paired calls: This function must be called in pairs with [OH_AttachOptions_Destroy](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_destroy). The object created by the create function must be destroyed via **OH_AttachOptions_Destroy**. <br>Lifecycle management: Consistent with **OH_AttachOptions_Create**. Multiple read operations can be performed after creation. The instance can be destroyed immediately once the attach operation completes.

<!--Device-InputMethod_AttachOptions *OH_AttachOptions_CreateWithRequestKeyboardReason(bool showKeyboard, InputMethod_RequestKeyboardReason requestKeyboardReason)--><!--Device-InputMethod_AttachOptions *OH_AttachOptions_CreateWithRequestKeyboardReason(bool showKeyboard, InputMethod_RequestKeyboardReason requestKeyboardReason)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool showKeyboard | Input parameter indicating whether to show the keyboard upon attachment. Its meaning, functionality, usage scenarios, use effect, value range and value‑setting guideline are consistent with the **<br>showKeyboard** parameter in **OH_AttachOptions_Create**. |
| [InputMethod_RequestKeyboardReason](capi-inputmethod-types-capi-h.md#inputmethod_requestkeyboardreason) requestKeyboardReason | Input parameter indicating the reason for requesting keyboard input. <br>Meaning/Function: Identifies the scenario triggering the keyboard request to help the system recognize input scenarios and optimize user experience. <br>Usage scenarios: Used when an app needs to inform the system why the keyboard is brought up. Examples include distinguishing triggers such as mouse clicks, touch events, or active API calls from the app. <br>Use effect: The system can adjust input method behaviors according to this reason (for example, selecting an appropriate keyboard layout or input mode). <br>Value range: Enum values of **InputMethod_RequestKeyboardReason**, including: <br>- **IME_REQUEST_REASON_NONE** (**0**): No specific reason. <br>- **IME_REQUEST_REASON_MOUSE** (**1**): Triggered by a mouse click. <br>- **IME_REQUEST_REASON_TOUCH** (**2**): Triggered by a touch event. <br>- **IME_REQUEST_REASON_OTHER** (**20**): Other reasons (such as active API calls initiated by the app). <br>Value‑setting guideline: The corresponding enumerated value is selected based on the actual trigger scenario. **IME_REQUEST_REASON_TOUCH** applies to triggers where the user taps an input box, **IME_REQUEST_REASON_MOUSE**<br>applies to mouse click triggers, and **IME_REQUEST_REASON_OTHER** applies to triggers initiated actively by the app's internal logic. <br>Specification constraints: Only the above enum values are supported. Passing other values may lead to undefined behavior. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_AttachOptions *](capi-inputmethod-inputmethod-attachoptions.md) | Pointer type. <br>Creation successful: Returns a pointer to the newly created **InputMethod_AttachOptions** instance. <br>Creation failed: Returns **NULL**. Possible causes include full app address space (insufficient memory). <br>Null check: You must check whether the return value is **NULL** before using it. If **NULL** is returned, the pointer cannot be used. <br>Memory management: Memory for the returned pointer is allocated internally by the create function. You need to release it using **OH_AttachOptions_Destroy**. Do not use **free()** or other methods to release the memory. |

### OH_AttachOptions_Destroy()

```c
void OH_AttachOptions_Destroy(InputMethod_AttachOptions *options)
```

**Description**

Destroys an [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) instance, releasing memory resources allocated by the **<br>OH_AttachOptions_Create** function. This method is used in pairs with **OH_AttachOptions_Create** and **<br>OH_AttachOptions_CreateWithRequestKeyboardReason**. <br>Paired calls: This function must be called in pairs with **OH_AttachOptions_Create** or **<br>OH_AttachOptions_CreateWithRequestKeyboardReason**. Each instance created by **OH_AttachOptions_Create** shall be destroyed by exactly one invocation of **OH_AttachOptions_Destroy**. <br>Lifecycle management: <br> - After OH_AttachOptions_Destroy is called, the options pointer becomes invalid and shall not be used further. <br> - OH_AttachOptions_Destroy cannot be called twice on the same options pointer; otherwise, a double-free error will occur. <br> - It is recommended that you call OH_AttachOptions_Destroy immediately after a successful attach operation, since configuration information has already been read upon attachment.

<!--Device-void OH_AttachOptions_Destroy(InputMethod_AttachOptions *options)--><!--Device-void OH_AttachOptions_Destroy(InputMethod_AttachOptions *options)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Input pointer representing the **InputMethod_AttachOptions** instance to be destroyed. <br>Meaning/Function: Specifies the **AttachOptions** instance to destroy. **OH_AttachOptions_Destroy** releases memory occupied by this instance. <br>Usage scenarios: Called when the **AttachOptions** is no longer required, typically after the attach operation completes. <br>Use effect: Memory pointed to by **options** is released, and the pointer becomes invalid. <br>Null pointer handling: If **options** is **NULL**, **OH_AttachOptions_Destroy** performs no operation (safe handling) and will not trigger a crash. However, you are advised to avoid passing **NULL**, as this indicates unsuccessful handling of failures from **OH_AttachOptions_Create**. <br>Memory release responsibility: You are responsible for calling **OH_AttachOptions_Destroy** at the appropriate time to release memory. |

### OH_AttachOptions_IsShowKeyboard()

```c
InputMethod_ErrorCode OH_AttachOptions_IsShowKeyboard(InputMethod_AttachOptions *options, bool *showKeyboard)
```

**Description**

Obtains the value that indicates whether to show the keyboard from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md). <br>Preconditions: **options** must be a valid instance created via the **OH_AttachOptions_Create** function, and **<br>showKeyboard** must point to a valid **bool** variable.

<!--Device-InputMethod_ErrorCode OH_AttachOptions_IsShowKeyboard(InputMethod_AttachOptions *options, bool *showKeyboard)--><!--Device-InputMethod_ErrorCode OH_AttachOptions_IsShowKeyboard(InputMethod_AttachOptions *options, bool *showKeyboard)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Input pointer to the **InputMethod_AttachOptions** instance to be read. <br>Meaning/Function: Specifies the **AttachOptions** instance from which to read **showKeyboard**. <br>Null pointer handling: The pointer cannot be **NULL**. Passing **NULL** returns **IME_ERR_NULL_POINTER**. <br>Preconditions: It must be a valid instance created via the **OH_AttachOptions_Create** function. |
| bool *showKeyboard | Output pointer that obtains the value from **InputMethod_AttachOptions** indicating whether to display the keyboard. <br>Meaning/Function: Obtains the value of the **showKeyboard** property. **true** indicates that the keyboard needs to be shown after attachment completes; **false** indicates that the keyboard does not need to be shown after attachment completes. <br>Usage scenarios: Used for querying the keyboard display configuration of **AttachOptions**, such as verifying configurations before attachment or validating settings during debugging. <br>Null pointer handling: This parameter cannot be **NULL**. Passing **NULL** returns **IME_ERR_NULL_POINTER**. You need to ensure **showKeyboard** points to a valid **bool** variable. <br>Memory allocation responsibility: Memory for the **bool** variable is allocated by you. **IsShowKeyboard**<br>only writes the value and does not allocate memory. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. *showKeyboard has been assigned the correct Boolean value. <br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **options** or **showKeyboard** is a null pointer. Ensure that both parameters are properly initialized and not **NULL** before you call them. <br>Error handling suggestion: If **IME_ERR_NULL_POINTER** is returned, verify whether **options** and ** showKeyboard** are valid pointers. If **IME_ERR_OK** is returned, *showKeyboard holds the correct configuration value. Refer to [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) for detailed error code definitions. |

### OH_AttachOptions_GetRequestKeyboardReason()

```c
InputMethod_ErrorCode OH_AttachOptions_GetRequestKeyboardReason(InputMethod_AttachOptions *options, int *requestKeyboardReason)
```

**Description**

Obtains the reason for requesting the keyboard from [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md). <br>Preconditions: **options** must be a valid instance created via **<br>OH_AttachOptions_CreateWithRequestKeyboardReason** (For instances created via **OH_AttachOptions_Create**, the default value of **requestKeyboardReason** is **IME_REQUEST_REASON_NONE**). **requestKeyboardReason** must point to a valid variable of **InputMethod_RequestKeyboardReason**.

<!--Device-InputMethod_ErrorCode OH_AttachOptions_GetRequestKeyboardReason(InputMethod_AttachOptions *options, int *requestKeyboardReason)--><!--Device-InputMethod_ErrorCode OH_AttachOptions_GetRequestKeyboardReason(InputMethod_AttachOptions *options, int *requestKeyboardReason)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | Input pointer to the **InputMethod_AttachOptions** instance whose value is read. <br>Meaning/Function: Specifies the **AttachOptions** instance from which the **requestKeyboardReason**<br>attribute is read. <br>Null pointer handling: Must not be **NULL**. Passing **NULL** returns **IME_ERR_NULL_POINTER**. <br>Preconditions: Must be a valid instance created through the **<br>OH_AttachOptions_CreateWithRequestKeyboardReason** function. If the instance is created through **<br>OH_AttachOptions_Create** (rather than **CreateWithRequestKeyboardReason**), the default value of the read **<br>requestKeyboardReason** is **IME_REQUEST_REASON_NONE**. |
| int *requestKeyboardReason | Output pointer, representing the reason for requesting keyboard input. <br>Meaning/Function: Output parameter used to obtain the enum value of the reason that triggers the input method to be brought up. <br>Usage scenarios: Used when querying the request keyboard reason configuration of **AttachOptions**. <br>Value range: The output value is the [InputMethod_RequestKeyboardReason](capi-inputmethod-types-capi-h.md#inputmethod_requestkeyboardreason) enum: **<br>IME_REQUEST_REASON_NONE(0)**, **IME_REQUEST_REASON_MOUSE(1)**, **IME_REQUEST_REASON_TOUCH(2)**, **<br>IME_REQUEST_REASON_OTHER(20)**. <br>Null pointer handling: Must not be **NULL**. Passing **NULL** returns **IME_ERR_NULL_POINTER**. You must ensure that **requestKeyboardReason** points to a valid variable. <br>Memory allocation responsibility: You allocate the memory for the variable. **GetRequestKeyboardReason**<br>only writes the value and does not allocate memory. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. *requestKeyboardReason has been assigned the correct enum value. <br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. **options** or **requestKeyboardReason** is a null pointer. Ensure that both parameters are properly initialized and not **NULL** before you call them. <br>Error handling suggestion: If **IME_ERR_NULL_POINTER** is returned, verify whether **options** and ** requestKeyboardReason** are valid pointers. If **IME_ERR_OK** is returned, *requestKeyboardReason holds the correct configuration value. Refer to [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) for detailed error code definitions. |


