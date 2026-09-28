# inputmethod_private_command_capi.h

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4c244f2ed12456a4c6059eccff764e442d7872b9 translatedAt=2026-08-20T07:04:22.766Z pushedAt=2026-08-24T07:08:10.183Z -->

## Overview

Provides methods for creating, destroying, reading, and writing private data objects. **InputMethod_PrivateCommand** uses a key-value mechanism to transfer custom private data between the input method app and the edit box client, enabling feature extension, delivery of scenario-specific commands, or exchange of custom configuration information.

The value of this struct supports three data types: Boolean, int32_t, and string. However, only one type of value can be set for a single **PrivateCommand** instance. Setting a value overwrites any previously‑set value and its associated type. It is recommended that you first determine the data type of the current value using **OH_PrivateCommand_GetValueType**, and then call the corresponding **GetValue** function to obtain the actual value. Otherwise, **IME_ERR_QUERY_FAILED** is returned when the requested type does not match the actual stored type.

This struct is mainly used in two scenarios: the input method app sends private commands to the edit box client through **OH_InputMethodProxy_SendPrivateCommand**, and the edit box client receives private commands from the input method app through the **OH_TextEditorProxy_ReceivePrivateCommandFunc** callback. The total size of all private data and keys sent in a single call is limited to 32 KB, and up to 5 **PrivateCommand** instances can be sent.

**Header file**: <inputmethod/inputmethod_private_command_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) | InputMethod_PrivateCommand | Represents the struct type of private data, used for private data communication between the edit box and the input method app. It adopts a key-value mechanism and supports three value types: Boolean, int32_t, and string. |

### Functions

| Name| Description                                                 |
| -- |-----------------------------------------------------|
| [InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)](#oh_privatecommand_create) | Creates an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance.     |
| [void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)](#oh_privatecommand_destroy) | Destroys an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance.          |
| [InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)](#oh_privatecommand_setkey) | Sets the key value for [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).         |
| [InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)](#oh_privatecommand_setboolvalue) | Sets the value of the Boolean type for [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).   |
| [InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)](#oh_privatecommand_setintvalue) | Sets the value of the integer type for [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).   |
| [InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)](#oh_privatecommand_setstrvalue) | Sets the value of the string type for [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).  |
| [InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)](#oh_privatecommand_getkey) | Obtains the key value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).         |
| [InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)](#oh_privatecommand_getvaluetype) | Obtains the data type of value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).   |
| [InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)](#oh_privatecommand_getboolvalue) | Obtains the value of the Boolean type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)](#oh_privatecommand_getintvalue) | Obtains the value of the integer type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)](#oh_privatecommand_getstrvalue) | Obtains the value of the string type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).|

## Function Description

### OH_PrivateCommand_Create()

```c
InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)
```

**Description**

Creates a new [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. A key value must be specified at creation. The key is the identifier of the private command, used to distinguish different private data items. The value type of the created instance defaults to **IME_COMMAND_VALUE_TYPE_NONE**, and the value and its type must be set subsequently through **SetBoolValue**, **SetIntValue**, or **SetStrValue**.

Usage scenarios: When the input method app needs to transfer private data to the edit box client, call this function first to create a **PrivateCommand** instance. After setting the key and value, send the instance through **OH_InputMethodProxy_SendPrivateCommand**. On the edit box client side, while receiving a **PrivateCommand** instance within the **OH_TextEditorProxy_ReceivePrivateCommandFunc**, you can also use this function to create new reply commands.

Preconditions: The **key** parameter must be a non-null pointer, and **keyLength** shall be greater than 0 and shall not exceed the 32 KB total size limit for all private data values and keys in a single transmission.

Use effect: When the operation is successful, returns a pointer to the newly created **InputMethod_PrivateCommand** instance whose initial value type is **IME_COMMAND_VALUE_TYPE_NONE**. You are responsible for the lifecycle management of this instance and must destroy it by calling **OH_PrivateCommand_Destroy** to free memory after use.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| char key[] | Key of the private data, which identifies the meaning of this private command. The key is in string format. A null pointer is not allowed. The total size of all private data values and keys in one transmission (keys and values across all **PrivateCommand** instances) is limited to 32 KB. It is recommended that keys carry clear semantic identifiers for easy parsing by the receiver. |
| size_t keyLength | Byte length of the key, excluding the trailing null character. Must be greater than 0. Subject to the 32 KB total size limit for all private data values and keys in a single transmission. Creation behavior is undefined if **keyLength** is 0. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) * | On success, returns a pointer to the newly created  [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. You shall manage the lifecycle of the instance and call [OH_PrivateCommand_Destroy](#oh_privatecommand_destroy) to destroy the instance and release memory after use.<br> On failure, returns **NULL**. Possible failure cause: insufficient memory allocation (app address space exhausted). Subsequent operations (such as **Set** or **Get** functions) against a null pointer return **IME_ERR_NULL_POINTER**. |

### OH_PrivateCommand_Destroy()

```c
void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)
```

**Description**

Destroys an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance and releases occupied memory resources, including internal memory occupied by the key and string‑type values.

Usage scenarios: Call this function to destroy an **PrivateCommand** instance when it is no longer in use. Invoke it only after the **Create** function returns successfully and when the instance is not referenced by any other objects. Special note: After an instance is sent via **OH_InputMethodProxy_SendPrivateCommand**, the original instance still needs to be destroyed by the sender. For an instance received through the **ReceivePrivateCommandFunc** callback, its lifecycle is managed within callback execution. Its memory is released upon callback return; you must neither destroy nor access this instance afterwards.

Lifecycle management: **OH_PrivateCommand_Create** and **OH_PrivateCommand_Destroy** must be used in pairs. Every instance created via **Create** shall have a corresponding **Destroy** call; otherwise, memory leaks will occur. The original pointer becomes invalid after **Destroy** is called and shall not be used further.

Preconditions: The **command** parameter shall be a non‑null pointer returned by a successful **OH_PrivateCommand_Create** call.

Use effect: Memory pointed to by command is freed, including memory for the internally stored key string and value string. The command pointer becomes invalid. Any subsequent access to a destroyed pointer results in undefined behavior.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to be destroyed. If **NULL** is passed, the function performs no operation and returns safely. It is recommended that you set the pointer to **NULL** after destruction to avoid misuse of a dangling pointer. |

### OH_PrivateCommand_SetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)
```

**Description**

Sets the key value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). The key value is the identifier of the private command, used by the receiver to distinguish private data with different meanings.

Usage scenarios: Call this function when you need to modify the key value of an existing **PrivateCommand** instance. An initial key value is normally set during **Create**. You may call this function again if you need to update the key.

Preconditions: The **command** parameter shall be a non‑null pointer returned by a successful **OH_PrivateCommand_Create** call. The **key** parameter must be a non-null pointer and **keyLength** must be greater than 0.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to be set. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| char key[] | Key of the private data, which identifies the semantics of this private command. A **NULL** pointer must not be passed; otherwise, **IME_ERR_NULL_POINTER** is returned. It is recommended that you use strings with clear semantics as keys for easy parsing and processing by the receiver. |
| size_t keyLength | Byte length of the key, excluding the trailing null character. Must be greater than 0. Subject to the 32 KB total size limit for all private data values and keys in a single transmission. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): The passed **command** or **key** parameter is a null pointer.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_SetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)
```

**Description**

Sets the Boolean type value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). Calling this function changes the value type of this **PrivateCommand** instance to **IME_COMMAND_VALUE_TYPE_BOOL**, and overwrites any previously set value of other types (int32_t or string).

Usage scenarios: Call this function when the value of a private command needs to carry Boolean type data, such as switch states, feature enablement flags, or other Boolean semantic data.

Preconditions: The **command** parameter shall be a non‑null pointer returned by a successful **OH_PrivateCommand_Create** call.

Value type constraints: The same **PrivateCommand** instance can only hold a value of one type. Calling **SetBoolValue** changes the value type to **IME_COMMAND_VALUE_TYPE_BOOL**, and overwrites any value previously set through **SetIntValue** or **SetStrValue**. Subsequently calling **GetIntValue** or **GetStrValue** to retrieve the value returns **IME_ERR_QUERY_FAILED**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| bool value | Boolean type value, **true** or **false**. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The value type has been set to **IME_COMMAND_VALUE_TYPE_BOOL**.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command** parameter is **NULL**.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_SetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)
```

**Description**

Sets the integer type value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). Calling this function changes the value type of this **PrivateCommand** instance to **IME_COMMAND_VALUE_TYPE_INT32**, and overwrites any previously set value of other types (Boolean or string).

Usage scenarios: Call this function when the value of a private command needs to carry integer type data, such as numeric parameters, counts, version numbers, and other integer semantic data.

Preconditions: The **command** parameter shall be a non‑null pointer returned by a successful **OH_PrivateCommand_Create** call.

Value type constraints: The same **PrivateCommand** instance can only hold a value of one type. Calling **SetIntValue** changes the value type to **IME_COMMAND_VALUE_TYPE_INT32**, and overwrites any value previously set through **SetBoolValue** or **SetStrValue**. Subsequently calling **GetBoolValue** or **GetStrValue** to retrieve the value returns **IME_ERR_QUERY_FAILED**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| int32_t value | Integer type value, a 32-bit signed integer. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The value type has been set to **IME_COMMAND_VALUE_TYPE_INT32**.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command** parameter is **NULL**.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_SetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)
```

**Description**

Sets the string type value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). Calling this function changes the value type of this **PrivateCommand** instance to **IME_COMMAND_VALUE_TYPE_STRING**, and overwrites any previously set value of other types (Boolean or int32_t).

Usage scenarios: Call this function when the value of a private command needs to carry string type data, such as text configuration, URL, JSON format parameter, and other string-semantic data.

Preconditions: The **command** parameter shall be a non‑null pointer returned by a successful **OH_PrivateCommand_Create** call. The **value** parameter must be a non-null pointer and **valueLength** must be greater than 0.

Value type constraints: The same **PrivateCommand** instance can only hold a value of one type. Calling **SetStrValue** changes the value type to **IME_COMMAND_VALUE_TYPE_STRING**, and overwrites any value previously set through **SetBoolValue** or **SetIntValue**. Subsequently calling **GetBoolValue** or **GetIntValue** to retrieve the value returns **IME_ERR_QUERY_FAILED**.

Memory management: The value string is provided by you. The **SetStrValue** function copies the string content into the internal storage of the **PrivateCommand** instance. You can release the original **value** memory immediately after calling **SetStrValue**, without keeping the **value** pointer valid.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| char value[] | String type value. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. The string content will be copied into the internal storage of the **PrivateCommand** instance, and you do not need to keep the **value** pointer valid after **SetStrValue** is called. |
| size_t valueLength | Byte length of the string value, excluding the trailing null character. Must be greater than 0. Subject to the 32 KB total size limit for all private data values and keys in a single transmission. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The value type has been set to **IME_COMMAND_VALUE_TYPE_STRING**.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command** or **value** parameter is **NULL**.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)
```

**Description**

Obtains the key from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md), which is the identifier of the private command.

Usage scenarios: After obtaining a **PrivateCommand** instance in the **OH_TextEditorProxy_ReceivePrivateCommandFunc** callback, you shall call this function first to get the key, and determine how to process the corresponding value data according to the key semantics.

Preconditions: The **command** parameter shall be a non‑null pointer. The output **key** and **keyLength** parameters shall also be non‑null pointers, and allocated by you.

Memory management: The lifecycle of the string pointed to by **key** is tied to that of the **command** instance. Do not store the key address directly, as it becomes invalid once **command** is destroyed. Do not modify the key content directly. It is recommended that you copy the key string into the caller‑owned memory before using it. After the command instance is destroyed (via **OH_PrivateCommand_Destroy** or upon callback return), the key pointer becomes invalid, and any access to this invalid pointer results in undefined behavior.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance whose key value is to be obtained. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| const char **key | Output parameter, used to receive the string pointer of the key value. The lifecycle of **key** is the same as that of **command**. Do not save the **key** address directly, and do not directly modify the **key** content. It is recommended that you copy it before use. After the **command** instance is destroyed, the **key** pointer becomes invalid and should not be accessed again. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| size_t *keyLength | Output parameter, used to receive the byte length of the key value. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The **key** and **keyLength** parameters have been written with values.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command**, **key**, or **keyLength** parameter is **NULL**.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetValueType()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)
```

**Description**

Obtains the data type of the value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). The returned type indicates the data type of the value currently stored in the instance and determines which **GetValue** function to call to obtain the actual value.

Usage scenarios: Before obtaining the value, you must first call this function to determine the value type, and then call the corresponding **GetValue** function (**GetBoolValue**, **GetIntValue**, or **GetStrValue**) based on the type. If you directly call a **GetValue** function that does not match the actual type, the **IME_ERR_QUERY_FAILED** error code is returned.

Preconditions: The **command** parameter shall be a non‑null pointer. The output **type** parameter shall also be a non‑null pointer, and allocated by you.

Usage suggestions: It is recommended that you call **GetValueType** to identify the type before getting the value each time, to avoid the **IME_ERR_QUERY_FAILED** error caused by type mismatch. Typical call sequence: 1. Call **OH_PrivateCommand_GetValueType** to get the type. 2. Based on the type, call **OH_PrivateCommand_GetBoolValue**, **OH_PrivateCommand_GetIntValue**, or **OH_PrivateCommand_GetStrValue**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance whose value type is to be obtained. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| [InputMethod_CommandValueType](capi-inputmethod-types-capi-h.md#inputmethod_commandvaluetype) *type | Output parameter, used to obtain the data type of the value. The return value is an [InputMethod_CommandValueType](capi-inputmethod-types-capi-h.md#inputmethod_commandvaluetype) enum value: **IME_COMMAND_VALUE_TYPE_NONE** indicates that no value is set; **IME_COMMAND_VALUE_TYPE_STRING** indicates a string type; **IME_COMMAND_VALUE_TYPE_BOOL** indicates a boolean type; **IME_COMMAND_VALUE_TYPE_INT32** indicates a 32-bit signed integer type. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The **type** parameter has been written with the data type of the current value.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command** or **type** parameter is **NULL**.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)
```

**Description**

Obtains the value of the Boolean type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

Usage scenarios: After confirming that the value type is **IME_COMMAND_VALUE_TYPE_BOOL** via **OH_PrivateCommand_GetValueType**, call this function to obtain the boolean value.

Preconditions: The **command** parameter must be a non‑null pointer. The output parameter **value** must also be a non‑null pointer with memory allocated by you. The value type of the current **PrivateCommand** instance must be **IME_COMMAND_VALUE_TYPE_BOOL**; otherwise, **IME_ERR_QUERY_FAILED** is returned.

Type mismatch handling: If the current value type is not **IME_COMMAND_VALUE_TYPE_BOOL** (for example, **IME_COMMAND_VALUE_TYPE_INT32** or **IME_COMMAND_VALUE_TYPE_STRING**), this function returns the error code **IME_ERR_QUERY_FAILED**, indicating a query failure—no boolean value exists in the command. It is recommended that you call **OH_PrivateCommand_GetValueType** to verify the type before obtaining the value.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance whose value is to be obtained. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| bool *value | Output parameter, used to receive the Boolean value. This parameter is an output pointer. You shall allocate memory for a Boolean variable and pass its address into the parameter. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The memory pointed to by the **value** parameter has been written with a boolean value.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command** or **value** parameter is **NULL**.<br>- [IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Query failed. No boolean value is in the command, that is, the current value type is not **IME_COMMAND_VALUE_TYPE_BOOL** (type mismatch). It is recommended that you call **OH_PrivateCommand_GetValueType** first to verify the type.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)
```

**Description**

Obtains the value of the integer type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

Usage scenarios: After confirming that the value type is **IME_COMMAND_VALUE_TYPE_INT32** via **OH_PrivateCommand_GetValueType**, call this function to obtain the integer value.

Preconditions: The **command** parameter must be a non‑null pointer. The output parameter **value** must also be a non‑null pointer with memory allocated by you. The value type of the current **PrivateCommand** instance must be **IME_COMMAND_VALUE_TYPE_INT32**; otherwise, **IME_ERR_QUERY_FAILED** is returned.

Type mismatch handling: If the current value type is not **IME_COMMAND_VALUE_TYPE_INT32** (for example, **IME_COMMAND_VALUE_TYPE_BOOL** or **IME_COMMAND_VALUE_TYPE_STRING**), this function returns the error code **IME_ERR_QUERY_FAILED**, indicating a query failure—no integer value exists in the command. It is recommended that you call **OH_PrivateCommand_GetValueType** to verify the type before obtaining the value.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance whose value is to be obtained. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| int32_t *value | Output parameter, used to receive the integer value. This parameter is an output pointer. You must allocate memory for an **int32_t** variable and pass its address into the parameter. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The memory pointed to by the **value** parameter has been written with an integer value.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command** or **value** parameter is **NULL**.<br>- [IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Query failed. No integer value is in the command, that is, the current value type is not **IME_COMMAND_VALUE_TYPE_INT32** (type mismatch). It is recommended that you call **OH_PrivateCommand_GetValueType** first to verify the type.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)
```

**Description**

Obtains the value of the string type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

Usage scenarios: After confirming that the value type is **IME_COMMAND_VALUE_TYPE_STRING** via **OH_PrivateCommand_GetValueType**, call this function to obtain the string value.

Preconditions: The **command** parameter must be a non‑null pointer. The output parameters **value** and **valueLength** must also be non‑null pointers with memory allocated by you. The value type of the current **PrivateCommand** instance must be **IME_COMMAND_VALUE_TYPE_STRING**; otherwise, **IME_ERR_QUERY_FAILED** is returned.

Type mismatch handling: If the current value type is not **IME_COMMAND_VALUE_TYPE_STRING** (for example, **IME_COMMAND_VALUE_TYPE_BOOL** or **IME_COMMAND_VALUE_TYPE_INT32**), this function returns the error code **IME_ERR_QUERY_FAILED**, indicating a query failure—no string value exists in the command. It is recommended that you call **OH_PrivateCommand_GetValueType** to verify the type before obtaining the value.

Memory management: The lifecycle of the string pointed to by **value** is tied to that of the **command** instance. Do not store the value address directly, as it becomes invalid once **command** is destroyed. Do not modify the value content directly. It is recommended that you copy the value string into the caller‑owned memory before using it. After the command instance is destroyed (via **OH_PrivateCommand_Destroy** or upon callback return), the value pointer becomes invalid, and any access to this invalid pointer results in undefined behavior.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance whose value is to be obtained. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| const char **value | Output parameter, used to receive the pointer to the string value. The lifecycle of **value** is consistent with **command**. Do not store the **value** address directly, and do not modify the **value** content directly. It is recommended that you copy the value before use. After the **command** instance is destroyed, the **value** pointer becomes invalid and should not be accessed again. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |
| size_t *valueLength | Output parameter, used to return the byte length of the string value. Passing a **NULL** pointer is not allowed; otherwise, **IME_ERR_NULL_POINTER** is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code.<br>- [IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Success. The **value** and **valueLength** parameters have been written with the value.<br>- [IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Unexpected null pointer. The **command**, **value**, or **valueLength** parameter is **NULL**.<br>- [IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): Query failed. No string value is in the command, that is, the current value type is not **IME_COMMAND_VALUE_TYPE_STRING** (type mismatch). It is recommended that you call **OH_PrivateCommand_GetValueType** first to verify the type.<br> For details about the error codes, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |