# inputmethod_text_avoid_info_capi.h

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8e856b06a34a819612cae112a81452d688b21bcf translatedAt=2026-08-20T07:03:01.155Z pushedAt=2026-08-24T07:08:22.047Z -->

## Overview

Provides methods for creating, destroying, reading, and writing the text box avoidance information objects. These methods are used to dynamically adjust the position of an input box when the soft keyboard pops up, preventing input content from being obscured.

**InputMethod_TextAvoidInfo** describes the on‑screen position and height information of an edit box. The input method framework calculates the avoidance area based on this information, so that the edit box can automatically shift upward or adjust its layout when the soft keyboard pops up. This ensures the input area remains visible and operable for users.
As a sub‑property of **InputMethod_TextConfig**, this struct is obtained from **TextConfig** via **OH_TextConfig_GetTextAvoidInfo**. It is used to pass edit box avoidance parameters to the input method framework.

**File to include**: <inputmethod/inputmethod_text_avoid_info_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) | InputMethod_TextAvoidInfo | `Avoidance information used by the input box to avoid the keyboard display area, including the Y coordinate and height of the editor |

### Function

| Name| Description                                           |
| -- |-----------------------------------------------|
| [InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)](#oh_textavoidinfo_create) | Creates an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance.|
| [void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)](#oh_textavoidinfo_destroy) | Destroys an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance.     |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)](#oh_textavoidinfo_setpositiony) | Sets the Y coordinate in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).   |
| [InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)](#oh_textavoidinfo_setheight) | Sets the height in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).    |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)](#oh_textavoidinfo_getpositiony) | Obtains the Y coordinate from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).    |
| [InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)](#oh_textavoidinfo_getheight) | Obtains the height from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md).     |

## Function Description

### OH_TextAvoidInfo_Create()

```c
InputMethod_TextAvoidInfo *OH_TextAvoidInfo_Create(double positionY, double height)
```

**Description**

Creates a new [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance. This function creates an avoidance information object based on the specified Y coordinate and height to describe the position and size of the edit box on the physical screen.

Usage scenarios: When the edit box needs to pass avoidance parameters to the input method framework, call this function first to create a **TextAvoidInfo** instance and set the Y coordinate and height of the edit box. Then pass this information to the input method framework via **InputMethod_TextConfig**. The input method framework calculates the adjustment area for the edit box after the soft keyboard pops up based on the avoidance information.

Use effect: Upon successful invocation, a pointer to the newly created **InputMethod_TextAvoidInfo** instance is returned, which holds the specified **positionY** and **height** values. You shall manage the lifecycle of this instance and must call **OH_TextAvoidInfo_Destroy** to destroy the instance and free memory when it is no longer in use.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| double positionY | Y coordinate of the input box position, in px. It represents the absolute distance from the top of the input box to the top edge of the physical screen. The value shall be greater than or equal to 0. It is recommended that you use the actual coordinate value of the physical screen. If a negative value is passed, the creation still succeeds, but the value is meaningless for actual avoidance calculation. |
| double height | Height of the input box, in px. The value shall be greater than or equal to 0. It is recommended that you use the actual pixel height of the edit box. If a negative value is passed, the creation still succeeds, but the value is meaningless for actual avoidance calculation.

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) * | If creation succeeds, returns a pointer to the newly created [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance. You must manage the lifecycle of this instance and call [OH_TextAvoidInfo_Destroy](#oh_textavoidinfo_destroy) to destroy the instance and release memory after use.<br> If creation fails, returns **NULL**. Possible failure cause: insufficient memory allocation (app address space exhausted). Subsequent calls to **Set** or **Get** functions against a null pointer return **IME_ERR_NULL_POINTER**. |

### OH_TextAvoidInfo_Destroy()

```c
void OH_TextAvoidInfo_Destroy(InputMethod_TextAvoidInfo *info)
```

**Description**

Destroys an [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance and releases the memory resources it occupies.

Usage scenarios: When the **TextAvoidInfo** instance is no longer needed, call this function to destroy the instance. This function shall be called only after the **OH_TextAvoidInfo_Create** function returns successfully and when the instance is no longer referenced by any other object.

Lifecycle management: **OH_TextAvoidInfo_Create** and **OH_TextAvoidInfo_Destroy** must be used in pairs. Each instance created by the **Create** API must have a corresponding **Destroy** call; otherwise, memory leaks will occur. After the **Destroy** API is called, the original pointer becomes invalid and must no longer be used.

Preconditions: The **info** parameter shall be a non-null pointer returned by **OH_TextAvoidInfo_Create**.

Use effect: The memory pointed to by **info** is released, and the **info** pointer becomes invalid. Any subsequent access to a destroyed pointer results in undefined behavior.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance that is about to be destroyed. If **NULL** is passed, the function performs no operation and returns safely. It is recommended that you set the pointer to **NULL** after destruction to avoid misuse of a dangling pointer. |

### OH_TextAvoidInfo_SetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetPositionY(InputMethod_TextAvoidInfo *info, double positionY)
```

**Description**

Sets the Y coordinate value in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The Y coordinate value indicates the absolute value of the distance from the top of the input box to the top edge of the physical screen.

Usage scenarios: When the position of the edit box changes (for example, window movement or layout adjustment), call this function to update the Y coordinate in the avoidance information, so that the input method framework can recalculate the avoidance area based on the latest position.

Preconditions: The **info** parameter shall be a non-null pointer returned by **OH_TextAvoidInfo_Create**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance whose value is about to be set. Passing a null pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| double positionY | Y coordinate value, which is the absolute distance from the top of the input box to the top edge of the physical screen, in px. The value shall be greater than or equal to 0. It is recommended that you use the actual coordinate value of the physical screen. Passing a negative value does not trigger an error, but the value is meaningless for actual avoidance calculation. |

**Returns**

| Type | Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **info** parameter is **NULL**. Check whether the **info** parameter is **NULL**, and ensure that the instance has been successfully created via **OH_TextAvoidInfo_Create** prior to calling this function.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextAvoidInfo_SetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_SetHeight(InputMethod_TextAvoidInfo *info, double height)
```

**Description**

Sets the height value in [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The height value indicates the vertical pixel size occupied by the edit box on the screen.

Usage scenarios: When the height of the edit box changes (for example, due to layout adjustment or window scaling), update the height value in the avoidance information. This allows the input method framework to recalculate the avoidance area based on the latest height. The avoidance area calculation depends on the combination of **positionY** and **height**, ensuring the edit box is not obscured when the soft keyboard pops up.

Preconditions: The **info** parameter shall be a non-null pointer returned by **OH_TextAvoidInfo_Create**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance to be set. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| double height | Height value, in px. The value shall be greater than or equal to 0. It is recommended that you use the actual pixel height of the edit box. Passing a negative value does not trigger an error, but the value is meaningless for actual avoidance calculation. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **info** parameter is **NULL**. Check whether the **info** parameter is **NULL**, and ensure that the instance has been successfully created via **OH_TextAvoidInfo_Create** prior to calling this function.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextAvoidInfo_GetPositionY()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetPositionY(InputMethod_TextAvoidInfo *info, double *positionY)
```

**Description**

Obtains the Y coordinate value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The Y coordinate value indicates the absolute distance from the top of the input box to the top edge of the physical screen.

Usage scenarios: When processing avoidance logic, the input method app shall obtain the Y coordinate of the edit box to determine its vertical position on the screen, and accordingly decide whether to adjust the position or layout of the edit box.

Preconditions: The **info** parameter shall be a non-null pointer returned by **OH_TextAvoidInfo_Create**. The **positionY** output parameter shall be a non-null pointer of the double type, with memory allocated by you.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance whose value is about to be obtained. Passing a null pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| double *positionY | Output parameter used to receive the Y coordinate value, which is the absolute distance from the top of the input box to the top edge of the physical screen, in px. This parameter is an output pointer. You must allocate memory for a double type variable and pass its address. Passing a null pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The memory pointed to by the **positionY** pointer has been written with the Y coordinate value.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **info** or **positionY** parameter is **NULL**. Check whether the **info** and **positionY** parameters are **NULL**, and ensure that the instance has been successfully created via **OH_TextAvoidInfo_Create** prior to calling this function, and that valid memory for a double type variable has been allocated for the **positionY** parameter.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_TextAvoidInfo_GetHeight()

```c
InputMethod_ErrorCode OH_TextAvoidInfo_GetHeight(InputMethod_TextAvoidInfo *info, double *height)
```

**Description**

Obtains the height value from [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md). The height value indicates the vertical pixel size occupied by the edit box on the screen.

Usage scenarios: When processing avoidance logic, the input method app shall obtain the height value of the edit box and combine it with the Y coordinate value to determine the complete vertical range of the edit box on the screen (from **positionY** to **positionY** + **height**), and accordingly determine whether the edit box will be obscured by the keyboard.

Preconditions: The **info** parameter shall be a non-null pointer returned by **OH_TextAvoidInfo_Create**. The **height** output parameter shall be a non-null pointer of the double type, with memory allocated by you.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) *info | Pointer to the [InputMethod_TextAvoidInfo](capi-inputmethod-inputmethod-textavoidinfo.md) instance whose value is about to be obtained. Passing a null pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| double *height | Output parameter used to receive the input box height, in px. This parameter is an output pointer. You must allocate memory for a double type variable and pass its address. Passing a null pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The memory pointed to by the **height** pointer has been written with the height value.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **info** or **height** parameter is **NULL**.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |