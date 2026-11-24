# inputmethod_private_command_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing private data objects.

**File to Include**: <inputmethod/inputmethod_private_command_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) | InputMethod_PrivateCommand | Private command structure, which uses the key-value mechanism and functions as the carrier for transferring private data between the text box and the input method application. It can be used to transfer customized instructions, extended capability parameters, and specific scenario data, improving the scalability and compatibility of the input method function. Each PrivateCommand instance contains a key (identifier string) and a value. (Boolean, integer, or string. You can select only one of the three types.), the data type of the value is identified by InputMethod_CommandValueType. <br> <br> Purpose: Transfers private data between the input method application and the edit box client to implement customized communication between the two parties. The input method application sends a private instruction to the edit box client through the OH_InputMethodProxy_SendPrivateCommand. The edit box client receives private instructions from the input method application through the OH_TextEditorProxy_ReceivePrivateCommandFunc callback. Each PrivateCommand instance carries a key-value private data record. A maximum of five private data instances can be sent at the same time. The total size of all private data and key values sent at a time is limited to 32 KB. <br><br>Application scenario: <br>-An input method application sends a private instruction to the edit box: An input method application creates a PrivateCommand instance, sets the key and value, and sends the private instruction to the edit box client through [OH_InputMethodProxy_SendPrivateCommand](capi-inputmethod-inputmethod-proxy-capi-h. md#oh_inputmethodproxy_sendprivatecommand). <br>- The edit box client receives private instructions: The edit box client receives the private command instance array in the [OH_TextEditorProxy_ReceivePrivateCommandFunc] (capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_receiveprivatecommandfunc) callback, traverses the array, and parses the key and value of each instance. <br> <br> Related functions: <br> \| Function \| Description \| \| --- \| --- \| \| [OH_PrivateCommand_Create](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_create) \| Creates an InputMethod_PrivateCommand instance. \| \| [OH_PrivateCommand_Destroy](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_destroy) \| Destroys the InputMethod_PrivateCommand instance. \| \| [OH_PrivateCommand_SetKey](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_setkey) \| Sets the key value. \| \| [OH_PrivateCommand_SetBoolValue](capi-inputmethod-private-command-capi-h. md#oh_privatecommand_setboolvalue) \| Sets the value of the Boolean type. \| \| [OH_PrivateCommand_SetIntValue](capi-inputmethod-private-command-capi-h. md#oh_privatecommand_setintvalue) \| Sets the value of the integer type. \| \| [OH_PrivateCommand_SetStrValue](capi-inputmethod-private-command-capi-h. md#oh_privatecommand_setstrvalue) \| Sets the value of the string type. \| \| [OH_PrivateCommand_GetKey](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_getkey) \| Obtains the key value. \| \| [OH_PrivateCommand_GetValueType](capi-inputmethod-private-command-capi-h. md#oh_privatecommand_getvaluetype) \| Obtains the data type of the value. \| \| [OH_PrivateCommand_GetBoolValue](capi-inputmethod-private-command-capi-h. md#oh_privatecommand_getboolvalue) \| Obtains the value of the Boolean type. \| \| [OH_PrivateCommand_GetIntValue](capi-inputmethod-private-command-capi-h. md#oh_privatecommand_getintvalue) \| Obtains the value of the integer type. \| \| [OH_PrivateCommand_GetStrValue](capi-inputmethod-private-command-capi-h. md#oh_privatecommand_getstrvalue) \| Obtains the value of the character string type. \| <br> <br> Related interfaces: <br> \| Interface \| Description The \| \| --- \| --- \| \| [OH_InputMethodProxy_SendPrivateCommand](capi-inputmethod-inputmethod-proxy-capi-h. md#oh_inputmethodproxy_sendprivatecommand) \| input method application sends a private instruction to the edit box client. The PrivateCommand instance array is transferred as a parameter. A maximum of five instances are supported, and the total data size is limited to 32 KB. Callback function for the \| \| [OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_receiveprivatecommandfunc) \| edit box client to receive private instructions. The PrivateCommand instance array is transferred as a parameter. The instance memory is released after the callback is returned. \| <br> <br> Related enumerations: <br> \| Enumeration \| Describes the enumeration of the data type (NONE, STRING, BOOL, and INT32) of the value in \| \| --- \| --- \| \| [InputMethod_CommandValueType](capi-inputmethod-types-capi-h. md#inputmethod_commandvaluetype) \| PrivateCommand.
\| <br> <br> Handle and Ownership: Only valid handles created by this API or borrowed handles provided by the framework can be used. Only independently created objects can be destroyed. The object provided by the callback and the child object view of TextConfig are borrowed objects. The provider returns IME_ERR_PARAMCHECK for an unregistered or invalid handle. The null parameter still returns an error according to the original rule. <br>Protection boundary: Life cycle check does not guarantee the thread security of object members, nor does it identify all invalid addresses after address reuse. After the object is destroyed, the pointer should be null. The callback object must not be retained after the callback ends. |

### Functions

| Name | Description |
| -- | -- |
| [InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)](#oh_privatecommand_create) | Creates an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. |
| [void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)](#oh_privatecommand_destroy) | Destroys an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to release the memory resources occupied by the instance, including the internal memory occupied by the key value and value value(string type value). <br> <br> Usage scenario: When a PrivateCommand instance is no longer used, this function is called to destroy the instance. Must be called after the Create function returns successfully and the instance is no longer referenced by any other object. Note: After the original instance is sent through OH_InputMethodProxy_SendPrivateCommand, the original instance needs to be destroyed by the sender. The life cycle of an instance received through the ReceivePrivateCommandFunc callback is managed during the callback. After the callback is returned, the memory of the instance is released and cannot be destroyed or accessed. <br> <br>Life cycle management: OH_PrivateCommand_Create and OH_PrivateCommand_Destroy must be used together. Each instance created by Create must have a corresponding Destroy call. Otherwise, memory leakage occurs. After Destroy is called, the original pointer becomes invalid and cannot be used any more. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create. <br>Only independently created objects can be destroyed. Framework callbacks provide borrowed objects that cannot be destroyed even during callback execution. Destroy requests for borrowed or unregistered objects are rejected and logged. <br> <br> Effect: The memory pointed to by the command is released, including the memory of the key and value strings stored internally. The command pointer becomes invalid. Any subsequent access to a destroyed pointer is an undefined behavior. |
| [InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)](#oh_privatecommand_setkey) | Sets the key value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). The key value is an identifier of a private command, which is used by the receiver to distinguish private data with different meanings. <br> <br> Usage scenario: This function is invoked to change the key value of an existing PrivateCommand instance. Generally, the initial key value has been set during the creation. To update the key, call this function again. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create successfully, or a valid non-null borrowing object provided by the framework callback. The key parameter must be a non-null pointer. keyLength must be greater than 0. |
| [InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)](#oh_privatecommand_setboolvalue) | Sets the Boolean value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). After this function is called, the value type of the PrivateCommand instance changes to IME_COMMAND_VALUE_TYPE_BOOL, and the value type(int32_t or string) that has been set is overwritten. <br> <br>Application scenario: This function is invoked when the value of a private command needs to transfer Boolean data, such as the switch status and whether to enable a function. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create successfully, or a valid non-null borrow object provided by the framework callback. <br> <br>Value type rule: A PrivateCommand instance can have only one type of value. After SetBoolValue is called, the value type changes to IME_COMMAND_VALUE_TYPE_BOOL. The value set by SetIntValue or SetStrValue is overwritten. IME_ERR_QUERY_FAILED is returned when a value is obtained using GetIntValue or GetStrValue. |
| [InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)](#oh_privatecommand_setintvalue) |  |
| [InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)](#oh_privatecommand_setstrvalue) | Sets the string type value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). After this function is called, the value type of the PrivateCommand instance changes to IME_COMMAND_VALUE_TYPE_STRING, and other values(bool or int32_t) that have been set are overwritten. <br> <br>Application scenario: This function is invoked when the value of a private command needs to transfer string data, such as text configuration, URL, and JSON parameter. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create successfully, or a valid non-null borrowing object provided by the framework callback. The value parameter must be a non-null pointer. valueLength must be greater than 0. <br> <br>Value type rule: A PrivateCommand instance can have only one type of value. After SetStrValue is called, the value type changes to IME_COMMAND_VALUE_TYPE_STRING. The value set by SetBoolValue or SetIntValue is overwritten. IME_ERR_QUERY_FAILED is returned when a value is obtained by using GetBoolValue or GetIntValue. <br> <br>Memory management: The value string is provided by the caller. The SetStrValue function copies the string content to the internal storage of the PrivateCommand instance. The caller can release the original value memory immediately after the SetStrValue call. The value pointer does not need to be valid. |
| [InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)](#oh_privatecommand_getkey) | Obtains the key value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)](#oh_privatecommand_getvaluetype) | Obtains the data type of value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)](#oh_privatecommand_getboolvalue) | Obtains the value of the Boolean type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)](#oh_privatecommand_getintvalue) | Obtains the value of the integer type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)](#oh_privatecommand_getstrvalue) | Obtains the value of the string type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |

## Function description

### OH_PrivateCommand_Create()

```c
InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)
```

**Description**

Creates an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance.

<!--Device-InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)--><!--Device-InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char key[] | Key value of the private data. |
| size_t keyLength | Key length. The total size of all private data and keys in a single operation cannot exceed 32 KB. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_PrivateCommand *](capi-inputmethod-inputmethod-privatecommand.md) | If the operation is successful, a pointer to the created [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance is returned. <br>If the operation failed, **NULL** is returned, which may be caused by insufficient application address space. |

### OH_PrivateCommand_Destroy()

```c
void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)
```

**Description**

Destroys an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to release the memory resources occupied by the instance, including the internal memory occupied by the key value and value value(string type value). <br> <br> Usage scenario: When a PrivateCommand instance is no longer used, this function is called to destroy the instance. Must be called after the Create function returns successfully and the instance is no longer referenced by any other object. Note: After the original instance is sent through OH_InputMethodProxy_SendPrivateCommand, the original instance needs to be destroyed by the sender. The life cycle of an instance received through the ReceivePrivateCommandFunc callback is managed during the callback. After the callback is returned, the memory of the instance is released and cannot be destroyed or accessed. <br> <br>Life cycle management: OH_PrivateCommand_Create and OH_PrivateCommand_Destroy must be used together. Each instance created by Create must have a corresponding Destroy call. Otherwise, memory leakage occurs. After Destroy is called, the original pointer becomes invalid and cannot be used any more. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create. <br>Only independently created objects can be destroyed. Framework callbacks provide borrowed objects that cannot be destroyed even during callback execution. Destroy requests for borrowed or unregistered objects are rejected and logged. <br> <br> Effect: The memory pointed to by the command is released, including the memory of the key and value strings stored internally. The command pointer becomes invalid. Any subsequent access to a destroyed pointer is an undefined behavior.

<!--Device-void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)--><!--Device-void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to be destroyed. |

### OH_PrivateCommand_SetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)
```

**Description**

Sets the key value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). The key value is an identifier of a private command, which is used by the receiver to distinguish private data with different meanings. <br> <br> Usage scenario: This function is invoked to change the key value of an existing PrivateCommand instance. Generally, the initial key value has been set during the creation. To update the key, call this function again. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create successfully, or a valid non-null borrowing object provided by the framework callback. The key parameter must be a non-null pointer. keyLength must be greater than 0.

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to be set. |
| char key[] | Key value. |
| size_t keyLength | Key length. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The input command or key parameter is a null pointer. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_SetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)
```

**Description**

Sets the Boolean value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). After this function is called, the value type of the PrivateCommand instance changes to IME_COMMAND_VALUE_TYPE_BOOL, and the value type(int32_t or string) that has been set is overwritten. <br> <br>Application scenario: This function is invoked when the value of a private command needs to transfer Boolean data, such as the switch status and whether to enable a function. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create successfully, or a valid non-null borrow object provided by the framework callback. <br> <br>Value type rule: A PrivateCommand instance can have only one type of value. After SetBoolValue is called, the value type changes to IME_COMMAND_VALUE_TYPE_BOOL. The value set by SetIntValue or SetStrValue is overwritten. IME_ERR_QUERY_FAILED is returned when a value is obtained using GetIntValue or GetStrValue.

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to be set. |
| bool value | Boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success. The value type has been set to IME_COMMAND_VALUE_TYPE_BOOL. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_SetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)
```

**Description**

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to be set. |
| int32_t value | Value of the integer type. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success and the value type has been set to IME_COMMAND_VALUE_TYPE_INT32. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_SetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)
```

**Description**

Sets the string type value of [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). After this function is called, the value type of the PrivateCommand instance changes to IME_COMMAND_VALUE_TYPE_STRING, and other values(bool or int32_t) that have been set are overwritten. <br> <br>Application scenario: This function is invoked when the value of a private command needs to transfer string data, such as text configuration, URL, and JSON parameter. <br> <br> Prerequisites: The command parameter must be a non-null pointer returned by OH_PrivateCommand_Create successfully, or a valid non-null borrowing object provided by the framework callback. The value parameter must be a non-null pointer. valueLength must be greater than 0. <br> <br>Value type rule: A PrivateCommand instance can have only one type of value. After SetStrValue is called, the value type changes to IME_COMMAND_VALUE_TYPE_STRING. The value set by SetBoolValue or SetIntValue is overwritten. IME_ERR_QUERY_FAILED is returned when a value is obtained by using GetBoolValue or GetIntValue. <br> <br>Memory management: The value string is provided by the caller. The SetStrValue function copies the string content to the internal storage of the PrivateCommand instance. The caller can release the original value memory immediately after the SetStrValue call. The value pointer does not need to be valid.

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance to be set. |
| char value[] | Value of the string type. |
| size_t valueLength | Value length. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success and the value type has been set to IME_COMMAND_VALUE_TYPE_STRING. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command or value parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_GetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)
```

**Description**

Obtains the key value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance from which the key value is to be obtained. |
| const char **key | The lifespan of **key** is consistent with that of **command**. You are advised to copy instead of directly saving the key address or writing **key**. |
| size_t *keyLength | Key length. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success, and the values of key and keyLength have been written. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command, key, or keyLength parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_GetValueType()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)
```

**Description**

Obtains the data type of value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance from which the value is to be obtained. |
| [InputMethod_CommandValueType](capi-inputmethod-types-capi-h.md#inputmethod_commandvaluetype) *type | Pointer to the [InputMethod_CommandValueType](capi-inputmethod-types-capi-h.md#inputmethod_commandvaluetype) instance, used to indicate the data type of the value. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates that the operation is successful and the type has been written to the data type of the current value. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command or type parameter is NULL. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_GetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)
```

**Description**

Obtains the value of the Boolean type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance from which the value is to be obtained. |
| bool *value | Boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates success, and a Boolean value has been written to the memory to which the value pointer points. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command or value parameter is NULL. </li> <li>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Query failed. There is no Boolean value in the command. That is, the current value type is not IME_COMMAND_VALUE_TYPE_BOOL. Match). You are advised to call OH_PrivateCommand_GetValueType to confirm the type. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_GetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)
```

**Description**

Obtains the value of the integer type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance from which the value is to be obtained. |
| int32_t *value | Value of the integer type. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode): indicates that the operation is successful and an integer value has been written to the memory to which the value pointer points. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command or value parameter is NULL. </li> <li>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Query failed. The command does not contain an integer value. That is, the current value type is not IME_COMMAND_VALUE_TYPE_INT32(type). Doesn't match). You are advised to call OH_PrivateCommand_GetValueType to confirm the type. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |

### OH_PrivateCommand_GetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)
```

**Description**

Obtains the value of the string type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

<!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)--><!--Device-InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Pointer to the [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance from which the value is to be obtained. |
| const char **value | Value of the string type. |
| size_t *valueLength | The lifespan of **value** is consistent with that of **command**. You are advised to copy instead of directly saving the value address or writing **value**. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | Returns a specific error code. <ul> <li>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - indicates that the operation is successful, and the values of value and valueLength have been written. </li> <li>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - The object handle is not registered or invalid. </li> <li>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Unexpected null pointer. The command, value, or valueLength parameter is NULL. </li> <li>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - Query failed. The command does not contain a string value, that is, the current value type is not IME_COMMAND_VALUE_TYPE_STRING(class type mismatch). You are advised to call OH_PrivateCommand_GetValueType to confirm the type. </li> <li>For details about the error code, see [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). </li> </ul> |


