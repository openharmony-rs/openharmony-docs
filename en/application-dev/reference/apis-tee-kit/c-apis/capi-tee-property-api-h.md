# tee_property_api.h

## Overview

Reference of TEE object api definitions.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Pseudo_PropSetHandle](#pseudo_propsethandle) | Pseudo_PropSetHandle | Enumerates the types of the property set. |

### Function

| Name | Description |
| -- | -- |
| [TEE_Result TEE_GetPropertyAsString(TEE_PropSetHandle propsetOrEnumerator, const char *name, char *valueBuffer, size_t *valueBufferLen)](#tee_getpropertyasstring) | Obtains a property from a property set and converts its value into a printable string.<br> * |
| [TEE_Result TEE_GetPropertyAsBool(TEE_PropSetHandle propsetOrEnumerator, const char *name, bool *value)](#tee_getpropertyasbool) | Obtains a property from a property set and converts its value into a Boolean value. |
| [TEE_Result TEE_GetPropertyAsU32(TEE_PropSetHandle propsetOrEnumerator, const char *name, uint32_t *value)](#tee_getpropertyasu32) | Obtains a property from a property set and converts its value into a 32-bit unsigned integer. |
| [TEE_Result TEE_GetPropertyAsU64(TEE_PropSetHandle propsetOrEnumerator, const char *name, uint64_t *value)](#tee_getpropertyasu64) | Obtains a property from a property set and converts its value into a 64-bit unsigned integer. |
| [TEE_Result TEE_GetPropertyAsBinaryBlock(TEE_PropSetHandle propsetOrEnumerator, const char *name, void *valueBuffer, size_t *valueBufferLen)](#tee_getpropertyasbinaryblock) | Obtains a property from a property set and converts its value into a binary block. |
| [TEE_Result TEE_GetPropertyAsUUID(TEE_PropSetHandle propsetOrEnumerator, const char *name, TEE_UUID *value)](#tee_getpropertyasuuid) | Obtains a property from a property set and converts its value to the <b>TEE_UUID</b> struct. |
| [TEE_Result TEE_GetPropertyAsIdentity(TEE_PropSetHandle propsetOrEnumerator, const char *name, TEE_Identity *value)](#tee_getpropertyasidentity) | Obtains a property from a property set and converts its value to the <b>TEE_Identity</b> struct. |
| [TEE_Result TEE_AllocatePropertyEnumerator(TEE_PropSetHandle *enumerator)](#tee_allocatepropertyenumerator) | Allocates a property enumerator object. |
| [void TEE_FreePropertyEnumerator(TEE_PropSetHandle enumerator)](#tee_freepropertyenumerator) | Releases a property enumerator object. |
| [void TEE_StartPropertyEnumerator(TEE_PropSetHandle enumerator, TEE_PropSetHandle propSet)](#tee_startpropertyenumerator) | Starts to enumerate the properties in an enumerator. |
| [void TEE_ResetPropertyEnumerator(TEE_PropSetHandle enumerator)](#tee_resetpropertyenumerator) | Resets a property enumerator immediately after allocation. |
| [TEE_Result TEE_GetPropertyName(TEE_PropSetHandle enumerator, void *nameBuffer, size_t *nameBufferLen)](#tee_getpropertyname) | Obtains the name of this property in an enumerator. |
| [TEE_Result TEE_GetNextProperty(TEE_PropSetHandle enumerator)](#tee_getnextproperty) | Obtains the next property in an enumerator. |

### Variable

| Name | Description |
| -- | -- |
| uint32_t TEE_PropSetHandle | Defines the property set handle type.<br>**Since**: 20 |

## Enum type description

### Pseudo_PropSetHandle

```c
enum Pseudo_PropSetHandle
```

**Description**

Enumerates the types of the property set.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_PROPSET_UNKNOW             = 0 | Unknown property set type. |
| TEE_PROPSET_TEE_IMPLEMENTATION = 0xFFFFFFFD | Property set type for TEE implementation. |
| TEE_PROPSET_CURRENT_CLIENT     = 0xFFFFFFFE | Property set type for the current client. |
| TEE_PROPSET_CURRENT_TA         = 0xFFFFFFFF | Property set type for the current Trusted Application (TA). |


## Function description

### TEE_GetPropertyAsString()

```c
TEE_Result TEE_GetPropertyAsString(TEE_PropSetHandle propsetOrEnumerator, const char *name, char *valueBuffer, size_t *valueBufferLen)
```

**Description**

Obtains a property from a property set and converts its value into a printable string.<br> *

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle propsetOrEnumerator | Indicates one of the TEE_PROPSET_XXX pseudo-handles or a handle on a property enumerator. |
| const char *name | Indicates the pointer to the zero-terminated string containing the name of the property to obtain. |
| char *valueBuffer | Indicates the pointer to the buffer for holding the property value obtained. |
| size_t *valueBufferLen | Indicates the pointer to the buffer length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetPropertyAsBool()

```c
TEE_Result TEE_GetPropertyAsBool(TEE_PropSetHandle propsetOrEnumerator, const char *name, bool *value)
```

**Description**

Obtains a property from a property set and converts its value into a Boolean value.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle propsetOrEnumerator | Indicates one of the TEE_PROPSET_XXX pseudo-handles or a handle on a property enumerator. |
| const char *name | Indicates the pointer to the zero-terminated string containing the name of the property to obtain. |
| bool *value | Indicates the pointer to the variable that holds the property value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetPropertyAsU32()

```c
TEE_Result TEE_GetPropertyAsU32(TEE_PropSetHandle propsetOrEnumerator, const char *name, uint32_t *value)
```

**Description**

Obtains a property from a property set and converts its value into a 32-bit unsigned integer.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle propsetOrEnumerator | Indicates one of the TEE_PROPSET_XXX pseudo-handles or a handle on a property enumerator. |
| const char *name | Indicates the pointer to the zero-terminated string containing the name of the property to obtain. |
| uint32_t *value | Indicates the pointer to the variable that holds the property value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetPropertyAsU64()

```c
TEE_Result TEE_GetPropertyAsU64(TEE_PropSetHandle propsetOrEnumerator, const char *name, uint64_t *value)
```

**Description**

Obtains a property from a property set and converts its value into a 64-bit unsigned integer.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle propsetOrEnumerator | Indicates one of the TEE_PROPSET_XXX pseudo-handles or a handle on a property enumerator. |
| const char *name | Indicates the pointer to the zero-terminated string containing the name of the property to obtain. |
| uint64_t *value | Indicates the pointer to the variable that holds the property value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetPropertyAsBinaryBlock()

```c
TEE_Result TEE_GetPropertyAsBinaryBlock(TEE_PropSetHandle propsetOrEnumerator, const char *name, void *valueBuffer, size_t *valueBufferLen)
```

**Description**

Obtains a property from a property set and converts its value into a binary block.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle propsetOrEnumerator | Indicates one of the TEE_PROPSET_XXX pseudo-handles or a handle on a property enumerator. |
| const char *name | Indicates the pointer to the zero-terminated string containing the name of the property to obtain. |
| void *valueBuffer | Indicates the pointer to the buffer for holding the property value obtained. |
| size_t *valueBufferLen | Indicates the pointer to the buffer length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetPropertyAsUUID()

```c
TEE_Result TEE_GetPropertyAsUUID(TEE_PropSetHandle propsetOrEnumerator, const char *name, TEE_UUID *value)
```

**Description**

Obtains a property from a property set and converts its value to the <b>TEE_UUID</b> struct.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle propsetOrEnumerator | Indicates one of the TEE_PROPSET_XXX pseudo-handles or a handle on a property enumerator. |
| const char *name | Indicates the pointer to the zero-terminated string containing the name of the property to obtain. |
| TEE_UUID *value | Indicates the pointer to the variable that holds the property value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetPropertyAsIdentity()

```c
TEE_Result TEE_GetPropertyAsIdentity(TEE_PropSetHandle propsetOrEnumerator, const char *name, TEE_Identity *value)
```

**Description**

Obtains a property from a property set and converts its value to the <b>TEE_Identity</b> struct.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle propsetOrEnumerator | Indicates one of the TEE_PROPSET_XXX pseudo-handles or a handle on a property enumerator. |
| const char *name | Indicates the pointer to the zero-terminated string containing the name of the property to obtain. |
| TEE_Identity *value | Indicates the pointer to the variable that holds the property value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_AllocatePropertyEnumerator()

```c
TEE_Result TEE_AllocatePropertyEnumerator(TEE_PropSetHandle *enumerator)
```

**Description**

Allocates a property enumerator object.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle *enumerator | Indicates the pointer to the property enumerator filled with an opaque handle. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_FreePropertyEnumerator()

```c
void TEE_FreePropertyEnumerator(TEE_PropSetHandle enumerator)
```

**Description**

Releases a property enumerator object.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle enumerator | Indicates the handle on the property enumerator to release. |

### TEE_StartPropertyEnumerator()

```c
void TEE_StartPropertyEnumerator(TEE_PropSetHandle enumerator, TEE_PropSetHandle propSet)
```

**Description**

Starts to enumerate the properties in an enumerator.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle enumerator | Indicates the handle on the enumerator. |
| TEE_PropSetHandle propSet | Indicates the pseudo-handle on the property set to enumerate. |

### TEE_ResetPropertyEnumerator()

```c
void TEE_ResetPropertyEnumerator(TEE_PropSetHandle enumerator)
```

**Description**

Resets a property enumerator immediately after allocation.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle enumerator | Indicates the handle on the enumerator to reset. |

### TEE_GetPropertyName()

```c
TEE_Result TEE_GetPropertyName(TEE_PropSetHandle enumerator, void *nameBuffer, size_t *nameBufferLen)
```

**Description**

Obtains the name of this property in an enumerator.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle enumerator | Indicates the handle on the enumerator. |
| void *nameBuffer | Indicates the pointer to the buffer that stores the property name obtained. |
| size_t *nameBufferLen | Indicates the pointer to the buffer length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_GetNextProperty()

```c
TEE_Result TEE_GetNextProperty(TEE_PropSetHandle enumerator)
```

**Description**

Obtains the next property in an enumerator.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_PropSetHandle enumerator | Indicates the handle on the enumerator. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |


