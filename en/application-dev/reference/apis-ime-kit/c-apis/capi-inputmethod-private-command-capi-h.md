# inputmethod_private_command_capi.h

## Overview

Provides methods for creating, destroying, reading, and writing private data objects.

**Include**: <inputmethod/inputmethod_private_command_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) | InputMethod_PrivateCommand | Represents the private data exchanged between the text box and the input method application. |

### Function

| Name | Description |
| -- | -- |
| [InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)](#oh_privatecommand_create) | Create a new [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. |
| [void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)](#oh_privatecommand_destroy) | Destroy a [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance. |
| [InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)](#oh_privatecommand_setkey) | Set key value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)](#oh_privatecommand_setboolvalue) | Set bool data value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)](#oh_privatecommand_setintvalue) | Set integer data value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)](#oh_privatecommand_setstrvalue) | Set string data value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)](#oh_privatecommand_getkey) | Get key value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)](#oh_privatecommand_getvaluetype) | Get value type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)](#oh_privatecommand_getboolvalue) | Get bool data value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)](#oh_privatecommand_getintvalue) | Get integer data value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |
| [InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)](#oh_privatecommand_getstrvalue) | Get string data value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). |

## Function description

### OH_PrivateCommand_Create()

```c
InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)
```

**Description**

Create a new [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char key[] | The key of the private command. |
| size_t keyLength | Key length. The total size of all private data and keys in a single operation cannot exceed 32 KB. |

**Returns**:

| Type | Description |
| -- | -- |
| [InputMethod_PrivateCommand *](capi-inputmethod-inputmethod-privatecommand.md) | If the creation succeeds, a pointer to the newly created [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)  instance is returned. If the creation fails, NULL is returned, possible cause is insufficient memory. |

### OH_PrivateCommand_Destroy()

```c
void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)
```

**Description**

Destroy a [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be destroyed. |

### OH_PrivateCommand_SetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)
```

**Description**

Set key value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be set value. |
| char key[] | Represents key value. |
| size_t keyLength | Represents key length. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_SetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)
```

**Description**

Set bool data value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be set value. |
| bool value | Represents bool data value. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_SetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)
```

**Description**

Set integer data value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be set value. |
| int32_t value | Represents integer data value. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_SetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)
```

**Description**

Set string data value into [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be set value. |
| char value[] | Represents string data value. |
| size_t valueLength | Represents the length of string data value. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)
```

**Description**

Get key value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be get value from. |
| const char **key | The lifespan of key is consistent with that of command. You are advised to copy instead of directly saving the key address or writing key. |
| size_t *keyLength | Represents key length. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetValueType()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)
```

**Description**

Get value type from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be get value from. |
| InputMethod_CommandValueType *type | Represents a pointer to a [InputMethod_CommandValueType](capi-inputmethod-types-capi-h.md#inputmethod_commandvaluetype) instance. Indicates the data type of the value. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)
```

**Description**

Get bool data value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be get value from. |
| bool *value | Represents bool data value. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - query failed, no bool value in command.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)
```

**Description**

Get integer data value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be get value from. |
| int32_t *value | Represents integer data value. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - query failed, no integer value in command.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |

### OH_PrivateCommand_GetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)
```

**Description**

Get string data value from [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | Represents a pointer to an [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) instance which will be get value from. |
| const char **value | Represents string data value. |
| size_t *valueLength | The lifespan of value is consistent with that of command. You are advised to copy instead of directly saving the value address or writing value. |

**Returns**:

| Type | Description |
| -- | -- |
| InputMethod_ErrorCode | Returns a specific error code.      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - success.      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - unexpected null pointer.      <br>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - query failed, no string value in command.      <br>Specific error codes can be referenced [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode). |


