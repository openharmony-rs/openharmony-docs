# tee_object_api.h

## Overview

Provides trusted storage APIs.<br> You can use these APIs to implement trusted storage features.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Enum

| Name | Description |
| -- | -- |
| [Usage_Constants](#usage_constants) | Enumerates the usages of the key of the <b>TEE_ObjectHandle</b>. |
| [Handle_Flag_Constants](#handle_flag_constants) | Defines information about the object pointed to by the flag of the <b>TEE_ObjectHandle</b>, for example, whether the object is a persistent object or is initialized. |

### Macro

| Name | Description |
| -- | -- |
| TEE_HANDLE_NULL 0x00000000 | Defines <b>HANDLE_NULL</b>, which is used to denote the absence of a handle.<br>**Since**: 20 |
| TEE_ATTR_FLAG_VALUE  0x20000000 | Defines a value attribute identifier flag.<br>**Since**: 20 |
| TEE_ATTR_FLAG_PUBLIC 0x10000000 | Defines a public attribute identifier flag.<br>**Since**: 20 |
| TEE_ATTR_IS_BUFFER(attribute_id) ((((attribute_id) << 2) >> 31) == 0) | Check whether the attribute is a buffer.<br>**Since**: 20 |
| TEE_ATTR_IS_VALUE(attribute_id)  ((((attribute_id) << 2) >> 31) == 1) | Check whether the attribute is a value.<br>**Since**: 20 |
| TEE_ATTR_IS_PROTECTED(attribute_id) ((((attribute_id) << 3) >> 31) == 0) | Check whether the attribute is protected.<br>**Since**: 20 |
| TEE_ATTR_IS_PUBLIC(attribute_id)    ((((attribute_id) << 3) >> 31) == 1) | Check whether the attribute is public.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [TEE_Result TEE_GetObjectBufferAttribute(TEE_ObjectHandle object, uint32_t attributeID, void *buffer, size_t *size)](#tee_getobjectbufferattribute) | Obtains a buffer attribute from the <b>TEE_Attribute</b> struct of the object pointed to by <b>TEE_ObjectHandle</b>.<br> The members in the <b>TEE_Attribute</b> struct must be <b>ref</b>. If the <b>TEE_Attribute</b> is private, the <b>Usage_Constants</b> of the object must include <b>TEE_USAGE_EXTRACTABLE</b>. |
| [TEE_Result TEE_GetObjectValueAttribute(TEE_ObjectHandle object, uint32_t attributeID, uint32_t *a, uint32_t *b)](#tee_getobjectvalueattribute) | Obtains a value attribute from the <b>TEE_Attribute</b> of an object.<br> The members of the <b>TEE_Attribute</b> struct must be values. If the <b>TEE_Attribute</b> is private, the <b>Usage_Constants</b> of the object must include <b>TEE_USAGE_EXTRACTABLE</b>. |
| [void TEE_CloseObject(TEE_ObjectHandle object)](#tee_closeobject) | Closes a <b>TEE_ObjectHandle</b> object.<br> The object can be persistent or transient. |
| [TEE_Result TEE_AllocateTransientObject(uint32_t objectType, uint32_t maxObjectSize, TEE_ObjectHandle *object)](#tee_allocatetransientobject) | Allocates an uninitialized object to store keys.<br> <b>objectType</b> and <b>maxObjectSize</b> must be specified. |
| [void TEE_FreeTransientObject(TEE_ObjectHandle object)](#tee_freetransientobject) | Releases a transient object that is previously allocated with <b>TEE_AllocateTransientObject</b>.<br> After the function is called, the handle becomes invalid and all allocated resources are released. <b>TEE_FreeTransientObject</b> and <b>TEE_AllocateTransientObject</b> are used in pairs. |
| [void TEE_ResetTransientObject(TEE_ObjectHandle object)](#tee_resettransientobject) | Resets a transient object to its initial state after allocation.<br> You can use an allocated object, which has not been initialized or used to store a key, to store a key. |
| [TEE_Result TEE_PopulateTransientObject(TEE_ObjectHandle object, TEE_Attribute *attrs, uint32_t attrCount)](#tee_populatetransientobject) | Populates an uninitialized object with object attributes passed by the TA in the <b>attrs</b> parameter.<br> The object must be uninitialized. The <b>attrs</b> parameter is passed by a TA. |
| [void TEE_InitRefAttribute(TEE_Attribute *attr, uint32_t attributeID, void *buffer, size_t length)](#tee_initrefattribute) | Initializes the <b>TEE_Attribute</b> of the buffer type.<br> The members in the <b>TEE_Attribute</b> struct must be <b>ref</b>. |
| [void TEE_InitValueAttribute(TEE_Attribute *attr, uint32_t attributeID, uint32_t a, uint32_t b)](#tee_initvalueattribute) | Initializes a <b>TEE_Attribute</b>. |
| [TEE_Result TEE_GenerateKey(TEE_ObjectHandle object, uint32_t keySize, TEE_Attribute *params, uint32_t paramCount)](#tee_generatekey) | Generates a random key or a key pair and populates a transient key object with the generated key. |
| [TEE_Result TEE_InfoObjectData(TEE_ObjectHandle object, uint32_t *pos, uint32_t *len)](#tee_infoobjectdata) | Get the information of the object data part, the total length of the data part and the current position of the data stream. |
| [TEE_Result TEE_GetObjectInfo1(TEE_ObjectHandle object, TEE_ObjectInfo *objectInfo)](#tee_getobjectinfo1) | Obtains <b>TEE_ObjectInfo</b>.<br> This function obtains <b>TEE_ObjectInfo</b> and copies the obtained information to the pre-allocated space pointed to by <b>objectInfo</b>. |
| [TEE_Result TEE_CopyObjectAttributes1(TEE_ObjectHandle destObject, TEE_ObjectHandle srcObject)](#tee_copyobjectattributes1) | Assigns the <b>TEE_Attribute</b> of an initialized object to an uninitialized object.<br> This function populates an uninitialized object with <b>TEE_Attribute</b>. That is, it copies <b>TEE_Attribute</b> of <b>srcobject</b> to <b>destobject</b>. The <b>TEE_Attribute</b> types and IDs of the two objects must match. |
| [TEE_Result TEE_RestrictObjectUsage1(TEE_ObjectHandle object, uint32_t objectUsage)](#tee_restrictobjectusage1) | Restricts the <b>objectUse</b> bit of an object.<br> This bit determines the usage of the key in the object. The value range is <b>Usage_Constant</b>. The bit in the <b>objectUse</b> parameter can be set as follows: If it is set to <b>1</b>, the corresponding usage flag in the object is left unchanged. If it is set to <b>0</b>, the corresponding usage flag in the object is cleared. The newly created object contains all <b>Usage_Constant</b>, and the usage flag can be cleared only. |

## Enum type description

### Usage_Constants

```c
enum Usage_Constants
```

**Description**

Enumerates the usages of the key of the <b>TEE_ObjectHandle</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_USAGE_EXTRACTABLE = 0x00000001 | The object's key is extractable. |
| TEE_USAGE_ENCRYPT     = 0x00000002 | Used for encryption. |
| TEE_USAGE_DECRYPT     = 0x00000004 | Used for decryption. |
| TEE_USAGE_MAC         = 0x00000008 | Used for hash calculation. |
| TEE_USAGE_SIGN        = 0x00000010 | Used for creating a signature. |
| TEE_USAGE_VERIFY      = 0x00000020 | Used for signature verification. |
| TEE_USAGE_DERIVE      = 0x00000040 | Used for key derivation. |
| TEE_USAGE_DEFAULT     = 0xFFFFFFFF | Used for object initialization, with all permissions assigned by default. |

### Handle_Flag_Constants

```c
enum Handle_Flag_Constants
```

**Description**

Defines information about the object pointed to by the flag of the <b>TEE_ObjectHandle</b>, for example, whether the object is a persistent object or is initialized.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_HANDLE_FLAG_PERSISTENT      = 0x00010000 | The object is a persistent object. |
| TEE_HANDLE_FLAG_INITIALIZED     = 0x00020000 | The object is initialized. |
| TEE_HANDLE_FLAG_KEY_SET         = 0x00040000 | The object is a key set. |
| TEE_HANDLE_FLAG_EXPECT_TWO_KEYS = 0x00080000 | The object is expected to have two keys. |


## Function description

### TEE_GetObjectBufferAttribute()

```c
TEE_Result TEE_GetObjectBufferAttribute(TEE_ObjectHandle object, uint32_t attributeID, void *buffer, size_t *size)
```

**Description**

Obtains a buffer attribute from the <b>TEE_Attribute</b> struct of the object pointed to by <b>TEE_ObjectHandle</b>.<br> The members in the <b>TEE_Attribute</b> struct must be <b>ref</b>. If the <b>TEE_Attribute</b> is private, the <b>Usage_Constants</b> of the object must include <b>TEE_USAGE_EXTRACTABLE</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the handle of the object. |
| uint32_t attributeID | Indicates the ID of the attribute to obtain, for example, <b>TEE_ObjectAttribute</b>. The attribute ID can also be customized. |
| void *buffer | Indicates the pointer to the buffer that stores the attribute obtained. |
| size_t *size | Indicates the pointer to the length of the content stored. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetObjectValueAttribute()

```c
TEE_Result TEE_GetObjectValueAttribute(TEE_ObjectHandle object, uint32_t attributeID, uint32_t *a, uint32_t *b)
```

**Description**

Obtains a value attribute from the <b>TEE_Attribute</b> of an object.<br> The members of the <b>TEE_Attribute</b> struct must be values. If the <b>TEE_Attribute</b> is private, the <b>Usage_Constants</b> of the object must include <b>TEE_USAGE_EXTRACTABLE</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the handle of the object. |
| uint32_t attributeID | Indicates the ID of the attribute to obtain, for example, <b>TEE_ObjectAttribute</b>. The attribute ID can also be customized. |
| uint32_t *a | Indicates the pointer to the placeholder filled with the attribute field <b>a</b>. |
| uint32_t *b | Indicates the pointer to the placeholder filled with the attribute field <b>b</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_CloseObject()

```c
void TEE_CloseObject(TEE_ObjectHandle object)
```

**Description**

Closes a <b>TEE_ObjectHandle</b> object.<br> The object can be persistent or transient.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> object to close. |

### TEE_AllocateTransientObject()

```c
TEE_Result TEE_AllocateTransientObject(uint32_t objectType, uint32_t maxObjectSize, TEE_ObjectHandle *object)
```

**Description**

Allocates an uninitialized object to store keys.<br> <b>objectType</b> and <b>maxObjectSize</b> must be specified.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t objectType | Indicates the type of the object to create. The value is <b>TEE_ObjectType</b>. |
| uint32_t maxObjectSize | Indicates the maximum number of bytes of the object. |
| TEE_ObjectHandle *object | Indicates the pointer to the handle of the newly created object. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_FreeTransientObject()

```c
void TEE_FreeTransientObject(TEE_ObjectHandle object)
```

**Description**

Releases a transient object that is previously allocated with <b>TEE_AllocateTransientObject</b>.<br> After the function is called, the handle becomes invalid and all allocated resources are released. <b>TEE_FreeTransientObject</b> and <b>TEE_AllocateTransientObject</b> are used in pairs.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> to release. |

### TEE_ResetTransientObject()

```c
void TEE_ResetTransientObject(TEE_ObjectHandle object)
```

**Description**

Resets a transient object to its initial state after allocation.<br> You can use an allocated object, which has not been initialized or used to store a key, to store a key.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> to reset. |

### TEE_PopulateTransientObject()

```c
TEE_Result TEE_PopulateTransientObject(TEE_ObjectHandle object, TEE_Attribute *attrs, uint32_t attrCount)
```

**Description**

Populates an uninitialized object with object attributes passed by the TA in the <b>attrs</b> parameter.<br> The object must be uninitialized. The <b>attrs</b> parameter is passed by a TA.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the handle on a created but uninitialized object. |
| TEE_Attribute *attrs | Indicates the pointer to an array of object attributes, which can be one or more <b>TEE_Attribute</b>s. |
| uint32_t attrCount | Indicates the number of members in the attribute array. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_InitRefAttribute()

```c
void TEE_InitRefAttribute(TEE_Attribute *attr, uint32_t attributeID, void *buffer, size_t length)
```

**Description**

Initializes the <b>TEE_Attribute</b> of the buffer type.<br> The members in the <b>TEE_Attribute</b> struct must be <b>ref</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_Attribute *attr | Indicates the pointer to the <b>TEE_Attribute</b> initialized. |
| uint32_t attributeID | Indicates the ID assigned to the <b>TEE_Attribute</b>. |
| void *buffer | Indicates the pointer to the buffer that stores the content to be allocated. |
| size_t length | Indicates the length of the assigned value, in bytes. |

### TEE_InitValueAttribute()

```c
void TEE_InitValueAttribute(TEE_Attribute *attr, uint32_t attributeID, uint32_t a, uint32_t b)
```

**Description**

Initializes a <b>TEE_Attribute</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_Attribute *attr | Indicates the pointer to the <b>TEE_Attribute</b> initialized. |
| uint32_t attributeID | Indicates the ID assigned to the <b>TEE_Attribute</b>. |
| uint32_t a | Indicates the value to be assigned to the member <b>a</b> in the <b>TEE_Attribute</b>. |
| uint32_t b | Indicates the value to be assigned to the member <b>b</b> in the <b>TEE_Attribute</b>. |

### TEE_GenerateKey()

```c
TEE_Result TEE_GenerateKey(TEE_ObjectHandle object, uint32_t keySize, TEE_Attribute *params, uint32_t paramCount)
```

**Description**

Generates a random key or a key pair and populates a transient key object with the generated key.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates a transient object used to hold the generated key. |
| uint32_t keySize | Indicates the number of bytes of the key. |
| TEE_Attribute *params | Indicates the pointer to the parameters for key generation. |
| uint32_t paramCount | Indicates the number of parameters required for key generation. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_InfoObjectData()

```c
TEE_Result TEE_InfoObjectData(TEE_ObjectHandle object, uint32_t *pos, uint32_t *len)
```

**Description**

Get the information of the object data part, the total length of the data part and the current position of the data stream.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the handle of the object. |
| uint32_t *pos | Indicates the data stream position. |
| uint32_t *len | Indicates the data stream length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetObjectInfo1()

```c
TEE_Result TEE_GetObjectInfo1(TEE_ObjectHandle object, TEE_ObjectInfo *objectInfo)
```

**Description**

Obtains <b>TEE_ObjectInfo</b>.<br> This function obtains <b>TEE_ObjectInfo</b> and copies the obtained information to the pre-allocated space pointed to by <b>objectInfo</b>.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the handle of the object. |
| TEE_ObjectInfo *objectInfo | Indicates the pointer to the <b>TEE_ObjectInfo</b> obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_CopyObjectAttributes1()

```c
TEE_Result TEE_CopyObjectAttributes1(TEE_ObjectHandle destObject, TEE_ObjectHandle srcObject)
```

**Description**

Assigns the <b>TEE_Attribute</b> of an initialized object to an uninitialized object.<br> This function populates an uninitialized object with <b>TEE_Attribute</b>. That is, it copies <b>TEE_Attribute</b> of <b>srcobject</b> to <b>destobject</b>. The <b>TEE_Attribute</b> types and IDs of the two objects must match.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle destObject | Indicates the uninitialized object. |
| TEE_ObjectHandle srcObject | Indicates the initialized object. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_RestrictObjectUsage1()

```c
TEE_Result TEE_RestrictObjectUsage1(TEE_ObjectHandle object, uint32_t objectUsage)
```

**Description**

Restricts the <b>objectUse</b> bit of an object.<br> This bit determines the usage of the key in the object. The value range is <b>Usage_Constant</b>. The bit in the <b>objectUse</b> parameter can be set as follows: If it is set to <b>1</b>, the corresponding usage flag in the object is left unchanged. If it is set to <b>0</b>, the corresponding usage flag in the object is cleared. The newly created object contains all <b>Usage_Constant</b>, and the usage flag can be cleared only.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> of the target object. |
| uint32_t objectUsage | Indicates the new object usage. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |


