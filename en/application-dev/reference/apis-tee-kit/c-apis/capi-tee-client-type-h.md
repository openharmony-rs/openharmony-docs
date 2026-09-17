# tee_client_type.h

## Overview

Defines basic data types and data structures.

**Library**: libteec.so

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ListNode](capi-teeclient-listnode.md) | - | Defines the linked list type. |
| [TEEC_UUID](capi-teeclient-teec-uuid.md) | TEEC_UUID | Defines the universally unique identifier (UUID) as defined in RFC4122 [2]. The UUIDs are used to identify TAs. |
| [TEEC_Context](capi-teeclient-teec-context.md) | TEEC_Context | Defines the context, a logical connection between a CA and a TEE. |
| [TEEC_Session](capi-teeclient-teec-session.md) | TEEC_Session | Defines the session between a CA and a TA. |
| [TEEC_SharedMemory](capi-teeclient-teec-sharedmemory.md) | TEEC_SharedMemory | Defines a shared memory block, which can be registered or allocated. |
| [TEEC_TempMemoryReference](capi-teeclient-teec-tempmemoryreference.md) | TEEC_TempMemoryReference | Defines a pointer to a temporary buffer. |
| [TEEC_RegisteredMemoryReference](capi-teeclient-teec-registeredmemoryreference.md) | TEEC_RegisteredMemoryReference | Defines a pointer to the shared memory that is registered or allocated. |
| [TEEC_Value](capi-teeclient-teec-value.md) | TEEC_Value | Describes a parameter that carries small raw data passed by <b>value</b>. |
| [TEEC_IonReference](capi-teeclient-teec-ionreference.md) | TEEC_IonReference | Describes the size and handle of the ION memory. |
| [TEEC_Parameter](capi-teeclient-teec-parameter.md) | TEEC_Parameter | Defines a parameter of {@code TEEC_Operation}. |
| [TEEC_Operation](capi-teeclient-teec-operation.md) | TEEC_Operation | Defines the parameters for opening a session or sending a command. |

