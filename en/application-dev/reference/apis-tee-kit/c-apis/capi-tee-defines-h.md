# tee_defines.h

## Overview

Defines basic data types and data structures of TEE.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [TEE_Param](capi-teetrusted-tee-param.md) | TEE_Param | Enumerates the TEE parameter. |
| [TEE_ObjectInfo](capi-teetrusted-tee-objectinfo.md) | TEE_ObjectInfo | Defines an object information. |
| [TEE_Attribute](capi-teetrusted-tee-attribute.md) | TEE_Attribute | Defines an object attribute. |
| [\_\_TEE_ObjectHandle](capi-teetrusted---tee-objecthandle.md) | *TEE_ObjectHandle | Defines an object handle. |
| [tee_uuid](capi-teetrusted-tee-uuid.md) | TEE_UUID | Defines an UUID of TA. |
| [spawn_uuid](capi-teetrusted-spawn-uuid.md) | spawn_uuid_t | Defines the type of spawn UUID. |
| [TEE_Identity](capi-teetrusted-tee-identity.md) | TEE_Identity | Definitions the TEE Identity. |
| [TEE_Time](capi-teetrusted-tee-time.md) | TEE_Time | Definitions the TEE time. |
| [TEE_Date_Time](capi-teetrusted-tee-date-time.md) | TEE_Date_Time | Definitions the date time of TEE. |
| [\_\_TEE_ObjectEnumHandle](capi-teetrusted---tee-objectenumhandle.md) | *TEE_ObjectEnumHandle | Defines the pointer to <b>TEE_ObjectEnumHandle</b>. |
| [\_\_TEE_OperationHandle](capi-teetrusted---tee-operationhandle.md) | *TEE_OperationHandle | Defines the pointer to <b>\_\_TEE_OperationHandle</b>. |

### Enums

| Name | Description |
| -- | -- |
| [TEE_ParamType](#tee_paramtype) | Enumerates the types of the TEE parameter. |
| [TEE_ObjectAttribute](#tee_objectattribute) | Enumerates the types of object attribute. |
| [TEE_ObjectType](#tee_objecttype) | Enumerates the types of object. |
| [TEE_Result_Value](#tee_result_value) | Enumerates the result codes used in the TEEKit APIs. |
| [TEE_LoginMethod](#tee_loginmethod) | Login type definitions |

### Macros

| Name | Description |
| -- | -- |
| TA_EXPORT | Represents the export attribute for Trusted Applications.<br>**Since**: 20 |
| API_LEVEL1_1_1 2 | Represents API level 1.1.1.<br>**Since**: 20 |
| API_LEVEL1_2   3 | Represents API level 1.2.<br>**Since**: 20 |
| TEE_PARAMS_NUM 4 | Represents the number of TEE parameters.<br>**Since**: 20 |
| NULL ((void*)0) | Represents a null pointer constant.<br>**Since**: 20 |
| PARAM_NOT_USED(val) ((void)(val)) | Marks a parameter as unused.<br>**Since**: 20 |
| TEE_PARAM_TYPES(param0Type, param1Type, param2Type, param3Type)  (((param3Type) << 12) \| ((param2Type) << 8) \| ((param1Type) << 4) \| (param0Type)) | Constructs the TEE parameter types from the provided types.<br>**Since**: 20 |
| TEE_PARAM_TYPE_GET(paramTypes, index) (((paramTypes) >> (4U * (index))) & 0x0F) | Extracts the parameter type at the specified index from the TEE parameter types.<br>**Since**: 20 |
| S_VAR_NOT_USED(variable)  do {                          (void)(variable);         } while (0) | Marks a variable as unused.<br>**Since**: 20 |
| OBJECT_NAME_LEN_MAX 256 | Maximum length for the object name.<br>**Since**: 20 |
| NODE_LEN 8 | Defines the length of the node.<br>**Since**: 20 |
| TEE_ORIGIN_TEE             0x00000003 | Origin of the TEE.<br>**Since**: 20 |
| TEE_ORIGIN_TRUSTED_APP     0x00000004 | Origin of the Trusted Application.<br>**Since**: 20 |
| _TEE_TA_SESSION_HANDLE | Defines the handle for a TA session.<br>**Since**: 20 |
| TEE_TIMEOUT_INFINITE (0xFFFFFFFF) | Defines the infinite timeout value.<br>**Since**: 20 |

### Functions

| Name | Description |
| -- | -- |
| [static inline bool check_param_type(uint32_t param_to_check, uint32_t valid0, uint32_t valid1, uint32_t valid2, uint32_t valid3)
{return (TEE_PARAM_TYPES(valid0, valid1, valid2, valid3) == param_to_check)](#check_param_type) | Checks parameter types. |

### Variables

| Name | Description |
| -- | -- |
| int *tee_mutex_handle | Defines the tee mutex handle.<br>**Since**: 20<br>**System capability**: SystemCapability.Tee.TeeClient<br><!--Device-int *tee_mutex_handle--><!--Device-int *tee_mutex_handle-End--> |
| uint32_t TEE_Result | Defines the return values.<br>**Since**: 20<br>**System capability**: SystemCapability.Tee.TeeClient<br><!--Device-uint32_t TEE_Result--><!--Device-uint32_t TEE_Result-End--> |
| TEE_Result TEEC_Result | Defines the return values.<br>**Since**: 20<br>**System capability**: SystemCapability.Tee.TeeClient<br><!--Device-TEE_Result TEEC_Result--><!--Device-TEE_Result TEEC_Result-End--> |
| uint32_t TEE_TASessionHandle | Defines the handle of TA session.<br>**Since**: 20<br>**System capability**: SystemCapability.Tee.TeeClient<br><!--Device-uint32_t TEE_TASessionHandle--><!--Device-uint32_t TEE_TASessionHandle-End--> |
| typedef uint32_t TEE_Result | Defines the return values.<br>**Since**: 20<br>**System capability**: SystemCapability.Tee.TeeClient<br><!--Device-typedef uint32_t TEE_Result--><!--Device-typedef uint32_t TEE_Result-End--> |
| typedef uint32_t TEE_TASessionHandle | Defines the handle of TA session.<br>**Since**: 20<br>**System capability**: SystemCapability.Tee.TeeClient<br><!--Device-typedef uint32_t TEE_TASessionHandle--><!--Device-typedef uint32_t TEE_TASessionHandle-End--> |

## Enum type description

### TEE_ParamType

```c
enum TEE_ParamType
```

**Description**

Enumerates the types of the TEE parameter.

<!--Device-enum TEE_ParamType--><!--Device-enum TEE_ParamType-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_PARAM_TYPE_NONE = 0x0 | Represents no parameter type.<br><!--Device-TEE_PARAM_TYPE_NONE = 0x0--><!--Device-TEE_PARAM_TYPE_NONE = 0x0-End--> |
| TEE_PARAM_TYPE_VALUE_INPUT = 0x1 | Represents a value input type.<br><!--Device-TEE_PARAM_TYPE_VALUE_INPUT = 0x1--><!--Device-TEE_PARAM_TYPE_VALUE_INPUT = 0x1-End--> |
| TEE_PARAM_TYPE_VALUE_OUTPUT = 0x2 | Represents a value output type.<br><!--Device-TEE_PARAM_TYPE_VALUE_OUTPUT = 0x2--><!--Device-TEE_PARAM_TYPE_VALUE_OUTPUT = 0x2-End--> |
| TEE_PARAM_TYPE_VALUE_INOUT = 0x3 | Represents a value inout type.<br><!--Device-TEE_PARAM_TYPE_VALUE_INOUT = 0x3--><!--Device-TEE_PARAM_TYPE_VALUE_INOUT = 0x3-End--> |
| TEE_PARAM_TYPE_MEMREF_INPUT = 0x5 | Represents a memory reference input type.<br><!--Device-TEE_PARAM_TYPE_MEMREF_INPUT = 0x5--><!--Device-TEE_PARAM_TYPE_MEMREF_INPUT = 0x5-End--> |
| TEE_PARAM_TYPE_MEMREF_OUTPUT = 0x6 | Represents a memory reference output type.<br><!--Device-TEE_PARAM_TYPE_MEMREF_OUTPUT = 0x6--><!--Device-TEE_PARAM_TYPE_MEMREF_OUTPUT = 0x6-End--> |
| TEE_PARAM_TYPE_MEMREF_INOUT = 0x7 | Represents a memory reference inout type.<br><!--Device-TEE_PARAM_TYPE_MEMREF_INOUT = 0x7--><!--Device-TEE_PARAM_TYPE_MEMREF_INOUT = 0x7-End--> |
| TEE_PARAM_TYPE_ION_INPUT = 0x8 | Represents an ION input type.<br><!--Device-TEE_PARAM_TYPE_ION_INPUT = 0x8--><!--Device-TEE_PARAM_TYPE_ION_INPUT = 0x8-End--> |
| TEE_PARAM_TYPE_ION_SGLIST_INPUT = 0x9 | Represents an ION single list input type.<br><!--Device-TEE_PARAM_TYPE_ION_SGLIST_INPUT = 0x9--><!--Device-TEE_PARAM_TYPE_ION_SGLIST_INPUT = 0x9-End--> |
| TEE_PARAM_TYPE_MEMREF_SHARED_INOUT = 0xa | Represents a shared memory reference inout type.<br><!--Device-TEE_PARAM_TYPE_MEMREF_SHARED_INOUT = 0xa--><!--Device-TEE_PARAM_TYPE_MEMREF_SHARED_INOUT = 0xa-End--> |
| TEE_PARAM_TYPE_RESMEM_INPUT = 0xc | Represents a resource memory input type.<br><!--Device-TEE_PARAM_TYPE_RESMEM_INPUT = 0xc--><!--Device-TEE_PARAM_TYPE_RESMEM_INPUT = 0xc-End--> |
| TEE_PARAM_TYPE_RESMEM_OUTPUT = 0xd | Represents a resource memory output type.<br><!--Device-TEE_PARAM_TYPE_RESMEM_OUTPUT = 0xd--><!--Device-TEE_PARAM_TYPE_RESMEM_OUTPUT = 0xd-End--> |
| TEE_PARAM_TYPE_RESMEM_INOUT = 0xe | Represents a resource memory inout type.<br><!--Device-TEE_PARAM_TYPE_RESMEM_INOUT = 0xe--><!--Device-TEE_PARAM_TYPE_RESMEM_INOUT = 0xe-End--> |

### TEE_ObjectAttribute

```c
enum TEE_ObjectAttribute
```

**Description**

Enumerates the types of object attribute.

<!--Device-enum TEE_ObjectAttribute--><!--Device-enum TEE_ObjectAttribute-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_ATTR_SECRET_VALUE = 0xC0000000 | Secret value attribute.<br><!--Device-TEE_ATTR_SECRET_VALUE = 0xC0000000--><!--Device-TEE_ATTR_SECRET_VALUE = 0xC0000000-End--> |
| TEE_ATTR_RSA_MODULUS = 0xD0000130 | RSA modulus attribute.<br><!--Device-TEE_ATTR_RSA_MODULUS = 0xD0000130--><!--Device-TEE_ATTR_RSA_MODULUS = 0xD0000130-End--> |
| TEE_ATTR_RSA_PUBLIC_EXPONENT = 0xD0000230 | RSA public exponent attribute.<br><!--Device-TEE_ATTR_RSA_PUBLIC_EXPONENT = 0xD0000230--><!--Device-TEE_ATTR_RSA_PUBLIC_EXPONENT = 0xD0000230-End--> |
| TEE_ATTR_RSA_PRIVATE_EXPONENT = 0xC0000330 | RSA private exponent attribute.<br><!--Device-TEE_ATTR_RSA_PRIVATE_EXPONENT = 0xC0000330--><!--Device-TEE_ATTR_RSA_PRIVATE_EXPONENT = 0xC0000330-End--> |
| TEE_ATTR_RSA_PRIME1 = 0xC0000430 | RSA prime1 attribute.<br><!--Device-TEE_ATTR_RSA_PRIME1 = 0xC0000430--><!--Device-TEE_ATTR_RSA_PRIME1 = 0xC0000430-End--> |
| TEE_ATTR_RSA_PRIME2 = 0xC0000530 | RSA prime2 attribute.<br><!--Device-TEE_ATTR_RSA_PRIME2 = 0xC0000530--><!--Device-TEE_ATTR_RSA_PRIME2 = 0xC0000530-End--> |
| TEE_ATTR_RSA_EXPONENT1 = 0xC0000630 | RSA exponent1 attribute.<br><!--Device-TEE_ATTR_RSA_EXPONENT1 = 0xC0000630--><!--Device-TEE_ATTR_RSA_EXPONENT1 = 0xC0000630-End--> |
| TEE_ATTR_RSA_EXPONENT2 = 0xC0000730 | RSA exponent2 attribute.<br><!--Device-TEE_ATTR_RSA_EXPONENT2 = 0xC0000730--><!--Device-TEE_ATTR_RSA_EXPONENT2 = 0xC0000730-End--> |
| TEE_ATTR_RSA_COEFFICIENT = 0xC0000830 | RSA coefficient attribute.<br><!--Device-TEE_ATTR_RSA_COEFFICIENT = 0xC0000830--><!--Device-TEE_ATTR_RSA_COEFFICIENT = 0xC0000830-End--> |
| TEE_ATTR_RSA_MGF1_HASH = 0xF0000830 | RSA MGF1 hash attribute.<br><!--Device-TEE_ATTR_RSA_MGF1_HASH = 0xF0000830--><!--Device-TEE_ATTR_RSA_MGF1_HASH = 0xF0000830-End--> |
| TEE_ATTR_DSA_PRIME = 0xD0001031 | DSA prime attribute.<br><!--Device-TEE_ATTR_DSA_PRIME = 0xD0001031--><!--Device-TEE_ATTR_DSA_PRIME = 0xD0001031-End--> |
| TEE_ATTR_DSA_SUBPRIME = 0xD0001131 | DSA subprime attribute.<br><!--Device-TEE_ATTR_DSA_SUBPRIME = 0xD0001131--><!--Device-TEE_ATTR_DSA_SUBPRIME = 0xD0001131-End--> |
| TEE_ATTR_DSA_BASE = 0xD0001231 | DSA base attribute.<br><!--Device-TEE_ATTR_DSA_BASE = 0xD0001231--><!--Device-TEE_ATTR_DSA_BASE = 0xD0001231-End--> |
| TEE_ATTR_DSA_PUBLIC_VALUE = 0xD0000131 | DSA public value attribute.<br><!--Device-TEE_ATTR_DSA_PUBLIC_VALUE = 0xD0000131--><!--Device-TEE_ATTR_DSA_PUBLIC_VALUE = 0xD0000131-End--> |
| TEE_ATTR_DSA_PRIVATE_VALUE = 0xC0000231 | DSA private value attribute.<br><!--Device-TEE_ATTR_DSA_PRIVATE_VALUE = 0xC0000231--><!--Device-TEE_ATTR_DSA_PRIVATE_VALUE = 0xC0000231-End--> |
| TEE_ATTR_DH_PRIME = 0xD0001032 | DH prime attribute.<br><!--Device-TEE_ATTR_DH_PRIME = 0xD0001032--><!--Device-TEE_ATTR_DH_PRIME = 0xD0001032-End--> |
| TEE_ATTR_DH_SUBPRIME = 0xD0001132 | DH subprime attribute.<br><!--Device-TEE_ATTR_DH_SUBPRIME = 0xD0001132--><!--Device-TEE_ATTR_DH_SUBPRIME = 0xD0001132-End--> |
| TEE_ATTR_DH_BASE = 0xD0001232 | DH base attribute.<br><!--Device-TEE_ATTR_DH_BASE = 0xD0001232--><!--Device-TEE_ATTR_DH_BASE = 0xD0001232-End--> |
| TEE_ATTR_DH_X_BITS = 0xF0001332 | DH X bits attribute.<br><!--Device-TEE_ATTR_DH_X_BITS = 0xF0001332--><!--Device-TEE_ATTR_DH_X_BITS = 0xF0001332-End--> |
| TEE_ATTR_DH_PUBLIC_VALUE = 0xD0000132 | DH public value attribute.<br><!--Device-TEE_ATTR_DH_PUBLIC_VALUE = 0xD0000132--><!--Device-TEE_ATTR_DH_PUBLIC_VALUE = 0xD0000132-End--> |
| TEE_ATTR_DH_PRIVATE_VALUE = 0xC0000232 | DH private value attribute.<br><!--Device-TEE_ATTR_DH_PRIVATE_VALUE = 0xC0000232--><!--Device-TEE_ATTR_DH_PRIVATE_VALUE = 0xC0000232-End--> |
| TEE_ATTR_RSA_OAEP_LABEL = 0xD0000930 | RSA OAEP label attribute.<br><!--Device-TEE_ATTR_RSA_OAEP_LABEL = 0xD0000930--><!--Device-TEE_ATTR_RSA_OAEP_LABEL = 0xD0000930-End--> |
| TEE_ATTR_RSA_PSS_SALT_LENGTH = 0xF0000A30 | RSA PSS salt length attribute.<br><!--Device-TEE_ATTR_RSA_PSS_SALT_LENGTH = 0xF0000A30--><!--Device-TEE_ATTR_RSA_PSS_SALT_LENGTH = 0xF0000A30-End--> |
| TEE_ATTR_ECC_PUBLIC_VALUE_X = 0xD0000141 | ECC public value X attribute.<br><!--Device-TEE_ATTR_ECC_PUBLIC_VALUE_X = 0xD0000141--><!--Device-TEE_ATTR_ECC_PUBLIC_VALUE_X = 0xD0000141-End--> |
| TEE_ATTR_ECC_PUBLIC_VALUE_Y = 0xD0000241 | ECC public value Y attribute.<br><!--Device-TEE_ATTR_ECC_PUBLIC_VALUE_Y = 0xD0000241--><!--Device-TEE_ATTR_ECC_PUBLIC_VALUE_Y = 0xD0000241-End--> |
| TEE_ATTR_ECC_PRIVATE_VALUE = 0xC0000341 | ECC private value attribute.<br><!--Device-TEE_ATTR_ECC_PRIVATE_VALUE = 0xC0000341--><!--Device-TEE_ATTR_ECC_PRIVATE_VALUE = 0xC0000341-End--> |
| TEE_ATTR_ECC_CURVE = 0xF0000441 | ECC curve attribute.<br><!--Device-TEE_ATTR_ECC_CURVE = 0xF0000441--><!--Device-TEE_ATTR_ECC_CURVE = 0xF0000441-End--> |
| TEE_ATTR_ED25519_CTX = 0xD0000643 | ED25519 context attribute.<br><!--Device-TEE_ATTR_ED25519_CTX = 0xD0000643--><!--Device-TEE_ATTR_ED25519_CTX = 0xD0000643-End--> |
| TEE_ATTR_ED25519_PUBLIC_VALUE = 0xD0000743 | ED25519 public value attribute.<br><!--Device-TEE_ATTR_ED25519_PUBLIC_VALUE = 0xD0000743--><!--Device-TEE_ATTR_ED25519_PUBLIC_VALUE = 0xD0000743-End--> |
| TEE_ATTR_ED25519_PRIVATE_VALUE = 0xC0000843 | ED25519 private value attribute.<br><!--Device-TEE_ATTR_ED25519_PRIVATE_VALUE = 0xC0000843--><!--Device-TEE_ATTR_ED25519_PRIVATE_VALUE = 0xC0000843-End--> |
| TEE_ATTR_ED25519_PH = 0xF0000543 | ED25519 PH attribute.<br><!--Device-TEE_ATTR_ED25519_PH = 0xF0000543--><!--Device-TEE_ATTR_ED25519_PH = 0xF0000543-End--> |
| TEE_ATTR_X25519_PUBLIC_VALUE = 0xD0000944 | X25519 public value attribute.<br><!--Device-TEE_ATTR_X25519_PUBLIC_VALUE = 0xD0000944--><!--Device-TEE_ATTR_X25519_PUBLIC_VALUE = 0xD0000944-End--> |
| TEE_ATTR_X25519_PRIVATE_VALUE = 0xC0000A44 | X25519 private value attribute.<br><!--Device-TEE_ATTR_X25519_PRIVATE_VALUE = 0xC0000A44--><!--Device-TEE_ATTR_X25519_PRIVATE_VALUE = 0xC0000A44-End--> |
| TEE_ATTR_PBKDF2_HMAC_PASSWORD = 0xD0000133 | PBKDF2 HMAC password attribute.<br><!--Device-TEE_ATTR_PBKDF2_HMAC_PASSWORD = 0xD0000133--><!--Device-TEE_ATTR_PBKDF2_HMAC_PASSWORD = 0xD0000133-End--> |
| TEE_ATTR_PBKDF2_HMAC_SALT = 0xD0000134 | PBKDF2 HMAC salt attribute.<br><!--Device-TEE_ATTR_PBKDF2_HMAC_SALT = 0xD0000134--><!--Device-TEE_ATTR_PBKDF2_HMAC_SALT = 0xD0000134-End--> |
| TEE_ATTR_PRF_LABEL = 0xD0000136 | PRF label attribute.<br><!--Device-TEE_ATTR_PRF_LABEL = 0xD0000136--><!--Device-TEE_ATTR_PRF_LABEL = 0xD0000136-End--> |
| TEE_ATTR_PRF_SEED = 0xD0000137 | PRF seed attribute.<br><!--Device-TEE_ATTR_PRF_SEED = 0xD0000137--><!--Device-TEE_ATTR_PRF_SEED = 0xD0000137-End--> |
| TEE_ATTR_PRF_HASH_ALGORITHM = 0xF0000138 | PRF hash algorithm attribute.<br><!--Device-TEE_ATTR_PRF_HASH_ALGORITHM = 0xF0000138--><!--Device-TEE_ATTR_PRF_HASH_ALGORITHM = 0xF0000138-End--> |
| TEE_ATTR_HKDF_SALT = 0xD0000946 | HKDF salt attribute.<br><!--Device-TEE_ATTR_HKDF_SALT = 0xD0000946--><!--Device-TEE_ATTR_HKDF_SALT = 0xD0000946-End--> |
| TEE_ATTR_HKDF_INFO = 0xD0000A46 | HKDF info attribute.<br><!--Device-TEE_ATTR_HKDF_INFO = 0xD0000A46--><!--Device-TEE_ATTR_HKDF_INFO = 0xD0000A46-End--> |
| TEE_ATTR_PBKDF2_HMAC_DIGEST = 0xF0000135 | PBKDF2 HMAC digest attribute.<br><!--Device-TEE_ATTR_PBKDF2_HMAC_DIGEST = 0xF0000135--><!--Device-TEE_ATTR_PBKDF2_HMAC_DIGEST = 0xF0000135-End--> |
| TEE_ATTR_HKDF_HASH_ALGORITHM = 0xF0000B46 | HKDF hash algorithm attribute.<br><!--Device-TEE_ATTR_HKDF_HASH_ALGORITHM = 0xF0000B46--><!--Device-TEE_ATTR_HKDF_HASH_ALGORITHM = 0xF0000B46-End--> |
| TEE_ATTR_KDF_KEY_SIZE = 0xF0000C46 | KDF key size attribute.<br><!--Device-TEE_ATTR_KDF_KEY_SIZE = 0xF0000C46--><!--Device-TEE_ATTR_KDF_KEY_SIZE = 0xF0000C46-End--> |

### TEE_ObjectType

```c
enum TEE_ObjectType
```

**Description**

Enumerates the types of object.

<!--Device-enum TEE_ObjectType--><!--Device-enum TEE_ObjectType-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_TYPE_AES = 0xA0000010 | AES object type.<br><!--Device-TEE_TYPE_AES = 0xA0000010--><!--Device-TEE_TYPE_AES = 0xA0000010-End--> |
| TEE_TYPE_DES = 0xA0000011 | DES object type.<br><!--Device-TEE_TYPE_DES = 0xA0000011--><!--Device-TEE_TYPE_DES = 0xA0000011-End--> |
| TEE_TYPE_DES3 = 0xA0000013 | DES3 object type.<br><!--Device-TEE_TYPE_DES3 = 0xA0000013--><!--Device-TEE_TYPE_DES3 = 0xA0000013-End--> |
| TEE_TYPE_HMAC_MD5 = 0xA0000001 | HMAC MD5 object type.<br><!--Device-TEE_TYPE_HMAC_MD5 = 0xA0000001--><!--Device-TEE_TYPE_HMAC_MD5 = 0xA0000001-End--> |
| TEE_TYPE_HMAC_SHA1 = 0xA0000002 | HMAC SHA1 object type.<br><!--Device-TEE_TYPE_HMAC_SHA1 = 0xA0000002--><!--Device-TEE_TYPE_HMAC_SHA1 = 0xA0000002-End--> |
| TEE_TYPE_HMAC_SHA224 = 0xA0000003 | HMAC SHA224 object type.<br><!--Device-TEE_TYPE_HMAC_SHA224 = 0xA0000003--><!--Device-TEE_TYPE_HMAC_SHA224 = 0xA0000003-End--> |
| TEE_TYPE_HMAC_SHA256 = 0xA0000004 | HMAC SHA256 object type.<br><!--Device-TEE_TYPE_HMAC_SHA256 = 0xA0000004--><!--Device-TEE_TYPE_HMAC_SHA256 = 0xA0000004-End--> |
| TEE_TYPE_HMAC_SHA384 = 0xA0000005 | HMAC SHA384 object type.<br><!--Device-TEE_TYPE_HMAC_SHA384 = 0xA0000005--><!--Device-TEE_TYPE_HMAC_SHA384 = 0xA0000005-End--> |
| TEE_TYPE_HMAC_SHA512 = 0xA0000006 | HMAC SHA512 object type.<br><!--Device-TEE_TYPE_HMAC_SHA512 = 0xA0000006--><!--Device-TEE_TYPE_HMAC_SHA512 = 0xA0000006-End--> |
| TEE_TYPE_RSA_PUBLIC_KEY = 0xA0000030 | RSA public key object type.<br><!--Device-TEE_TYPE_RSA_PUBLIC_KEY = 0xA0000030--><!--Device-TEE_TYPE_RSA_PUBLIC_KEY = 0xA0000030-End--> |
| TEE_TYPE_RSA_KEYPAIR = 0xA1000030 | RSA keypair object type.<br><!--Device-TEE_TYPE_RSA_KEYPAIR = 0xA1000030--><!--Device-TEE_TYPE_RSA_KEYPAIR = 0xA1000030-End--> |
| TEE_TYPE_DSA_PUBLIC_KEY = 0xA0000031 | DSA public key object type.<br><!--Device-TEE_TYPE_DSA_PUBLIC_KEY = 0xA0000031--><!--Device-TEE_TYPE_DSA_PUBLIC_KEY = 0xA0000031-End--> |
| TEE_TYPE_DSA_KEYPAIR = 0xA1000031 | DSA keypair object type.<br><!--Device-TEE_TYPE_DSA_KEYPAIR = 0xA1000031--><!--Device-TEE_TYPE_DSA_KEYPAIR = 0xA1000031-End--> |
| TEE_TYPE_DH_KEYPAIR = 0xA1000032 | DH keypair object type.<br><!--Device-TEE_TYPE_DH_KEYPAIR = 0xA1000032--><!--Device-TEE_TYPE_DH_KEYPAIR = 0xA1000032-End--> |
| TEE_TYPE_GENERIC_SECRET = 0xA0000000 | Generic secret object type.<br><!--Device-TEE_TYPE_GENERIC_SECRET = 0xA0000000--><!--Device-TEE_TYPE_GENERIC_SECRET = 0xA0000000-End--> |
| TEE_TYPE_DATA = 0xA1000033 | Data object type.<br><!--Device-TEE_TYPE_DATA = 0xA1000033--><!--Device-TEE_TYPE_DATA = 0xA1000033-End--> |
| TEE_TYPE_DATA_GP1_1 = 0xA00000BF | Data GP1.1 object type.<br><!--Device-TEE_TYPE_DATA_GP1_1 = 0xA00000BF--><!--Device-TEE_TYPE_DATA_GP1_1 = 0xA00000BF-End--> |
| TEE_TYPE_ECDSA_PUBLIC_KEY = 0xA0000041 | ECDSA public key object type.<br><!--Device-TEE_TYPE_ECDSA_PUBLIC_KEY = 0xA0000041--><!--Device-TEE_TYPE_ECDSA_PUBLIC_KEY = 0xA0000041-End--> |
| TEE_TYPE_ECDSA_KEYPAIR = 0xA1000041 | ECDSA keypair object type.<br><!--Device-TEE_TYPE_ECDSA_KEYPAIR = 0xA1000041--><!--Device-TEE_TYPE_ECDSA_KEYPAIR = 0xA1000041-End--> |
| TEE_TYPE_ECDH_PUBLIC_KEY = 0xA0000042 | ECDH public key object type.<br><!--Device-TEE_TYPE_ECDH_PUBLIC_KEY = 0xA0000042--><!--Device-TEE_TYPE_ECDH_PUBLIC_KEY = 0xA0000042-End--> |
| TEE_TYPE_ECDH_KEYPAIR = 0xA1000042 | ECDH keypair object type.<br><!--Device-TEE_TYPE_ECDH_KEYPAIR = 0xA1000042--><!--Device-TEE_TYPE_ECDH_KEYPAIR = 0xA1000042-End--> |
| TEE_TYPE_ED25519_PUBLIC_KEY = 0xA0000043 | ED25519 public key object type.<br><!--Device-TEE_TYPE_ED25519_PUBLIC_KEY = 0xA0000043--><!--Device-TEE_TYPE_ED25519_PUBLIC_KEY = 0xA0000043-End--> |
| TEE_TYPE_ED25519_KEYPAIR = 0xA1000043 | ED25519 keypair object type.<br><!--Device-TEE_TYPE_ED25519_KEYPAIR = 0xA1000043--><!--Device-TEE_TYPE_ED25519_KEYPAIR = 0xA1000043-End--> |
| TEE_TYPE_X25519_PUBLIC_KEY = 0xA0000044 | X25519 public key object type.<br><!--Device-TEE_TYPE_X25519_PUBLIC_KEY = 0xA0000044--><!--Device-TEE_TYPE_X25519_PUBLIC_KEY = 0xA0000044-End--> |
| TEE_TYPE_X25519_KEYPAIR = 0xA1000044 | X25519 keypair object type.<br><!--Device-TEE_TYPE_X25519_KEYPAIR = 0xA1000044--><!--Device-TEE_TYPE_X25519_KEYPAIR = 0xA1000044-End--> |
| TEE_TYPE_SM2_DSA_PUBLIC_KEY = 0xA0000045 | SM2 DSA public key object type.<br><!--Device-TEE_TYPE_SM2_DSA_PUBLIC_KEY = 0xA0000045--><!--Device-TEE_TYPE_SM2_DSA_PUBLIC_KEY = 0xA0000045-End--> |
| TEE_TYPE_SM2_DSA_KEYPAIR = 0xA1000045 | SM2 DSA keypair object type.<br><!--Device-TEE_TYPE_SM2_DSA_KEYPAIR = 0xA1000045--><!--Device-TEE_TYPE_SM2_DSA_KEYPAIR = 0xA1000045-End--> |
| TEE_TYPE_SM2_KEP_PUBLIC_KEY = 0xA0000046 | SM2 KEP public key object type.<br><!--Device-TEE_TYPE_SM2_KEP_PUBLIC_KEY = 0xA0000046--><!--Device-TEE_TYPE_SM2_KEP_PUBLIC_KEY = 0xA0000046-End--> |
| TEE_TYPE_SM2_KEP_KEYPAIR = 0xA1000046 | SM2 KEP keypair object type.<br><!--Device-TEE_TYPE_SM2_KEP_KEYPAIR = 0xA1000046--><!--Device-TEE_TYPE_SM2_KEP_KEYPAIR = 0xA1000046-End--> |
| TEE_TYPE_SM2_PKE_PUBLIC_KEY = 0xA0000047 | SM2 PKE public key object type.<br><!--Device-TEE_TYPE_SM2_PKE_PUBLIC_KEY = 0xA0000047--><!--Device-TEE_TYPE_SM2_PKE_PUBLIC_KEY = 0xA0000047-End--> |
| TEE_TYPE_SM2_PKE_KEYPAIR = 0xA1000047 | SM2 PKE keypair object type.<br><!--Device-TEE_TYPE_SM2_PKE_KEYPAIR = 0xA1000047--><!--Device-TEE_TYPE_SM2_PKE_KEYPAIR = 0xA1000047-End--> |
| TEE_TYPE_HMAC_SM3 = 0xA0000007 | HMAC SM3 object type.<br><!--Device-TEE_TYPE_HMAC_SM3 = 0xA0000007--><!--Device-TEE_TYPE_HMAC_SM3 = 0xA0000007-End--> |
| TEE_TYPE_SM4 = 0xA0000014 | SM4 object type.<br><!--Device-TEE_TYPE_SM4 = 0xA0000014--><!--Device-TEE_TYPE_SM4 = 0xA0000014-End--> |
| TEE_TYPE_HKDF = 0xA000004A | HKDF object type.<br><!--Device-TEE_TYPE_HKDF = 0xA000004A--><!--Device-TEE_TYPE_HKDF = 0xA000004A-End--> |
| TEE_TYPE_SIP_HASH = 0xF0000002 | SIP Hash object type.<br><!--Device-TEE_TYPE_SIP_HASH = 0xF0000002--><!--Device-TEE_TYPE_SIP_HASH = 0xF0000002-End--> |
| TEE_TYPE_PBKDF2_HMAC = 0xF0000004 | PBKDF2 HMAC object type.<br><!--Device-TEE_TYPE_PBKDF2_HMAC = 0xF0000004--><!--Device-TEE_TYPE_PBKDF2_HMAC = 0xF0000004-End--> |
| TEE_TYPE_PRF = 0xF0000005 | PRF object type.<br><!--Device-TEE_TYPE_PRF = 0xF0000005--><!--Device-TEE_TYPE_PRF = 0xF0000005-End--> |
| TEE_TYPE_CORRUPTED_OBJECT = 0xA00000BE | Corrupted object type.<br><!--Device-TEE_TYPE_CORRUPTED_OBJECT = 0xA00000BE--><!--Device-TEE_TYPE_CORRUPTED_OBJECT = 0xA00000BE-End--> |

### TEE_Result_Value

```c
enum TEE_Result_Value
```

**Description**

Enumerates the result codes used in the TEEKit APIs.

<!--Device-enum TEE_Result_Value--><!--Device-enum TEE_Result_Value-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_SUCCESS = 0x00000000 | The operation is successful.<br><!--Device-TEE_SUCCESS = 0x00000000--><!--Device-TEE_SUCCESS = 0x00000000-End--> |
| TEE_ERROR_INVALID_CMD = 0x00000001 | The command is invalid.<br><!--Device-TEE_ERROR_INVALID_CMD = 0x00000001--><!--Device-TEE_ERROR_INVALID_CMD = 0x00000001-End--> |
| TEE_ERROR_SERVICE_NOT_EXIST = 0x00000002 | The service does not exist.<br><!--Device-TEE_ERROR_SERVICE_NOT_EXIST = 0x00000002--><!--Device-TEE_ERROR_SERVICE_NOT_EXIST = 0x00000002-End--> |
| TEE_ERROR_SESSION_NOT_EXIST = 0x00000003 | The session does not exist.<br><!--Device-TEE_ERROR_SESSION_NOT_EXIST = 0x00000003--><!--Device-TEE_ERROR_SESSION_NOT_EXIST = 0x00000003-End--> |
| TEE_ERROR_SESSION_MAXIMUM = 0x00000004 | The number of sessions exceeds the limit.<br><!--Device-TEE_ERROR_SESSION_MAXIMUM = 0x00000004--><!--Device-TEE_ERROR_SESSION_MAXIMUM = 0x00000004-End--> |
| TEE_ERROR_REGISTER_EXIST_SERVICE = 0x00000005 | The service has been already registered.<br><!--Device-TEE_ERROR_REGISTER_EXIST_SERVICE = 0x00000005--><!--Device-TEE_ERROR_REGISTER_EXIST_SERVICE = 0x00000005-End--> |
| TEE_ERROR_TARGET_DEAD_FATAL = 0x00000006 | An internal error occurs.<br><!--Device-TEE_ERROR_TARGET_DEAD_FATAL = 0x00000006--><!--Device-TEE_ERROR_TARGET_DEAD_FATAL = 0x00000006-End--> |
| TEE_ERROR_READ_DATA = 0x00000007 | Failed to read data.<br><!--Device-TEE_ERROR_READ_DATA = 0x00000007--><!--Device-TEE_ERROR_READ_DATA = 0x00000007-End--> |
| TEE_ERROR_WRITE_DATA = 0x00000008 | Failed to write data.<br><!--Device-TEE_ERROR_WRITE_DATA = 0x00000008--><!--Device-TEE_ERROR_WRITE_DATA = 0x00000008-End--> |
| TEE_ERROR_TRUNCATE_OBJECT = 0x00000009 | Failed to truncate data.<br><!--Device-TEE_ERROR_TRUNCATE_OBJECT = 0x00000009--><!--Device-TEE_ERROR_TRUNCATE_OBJECT = 0x00000009-End--> |
| TEE_ERROR_SEEK_DATA = 0x0000000A | Failed to seek data.<br><!--Device-TEE_ERROR_SEEK_DATA = 0x0000000A--><!--Device-TEE_ERROR_SEEK_DATA = 0x0000000A-End--> |
| TEE_ERROR_SYNC_DATA = 0x0000000B | Failed to synchronize data.<br><!--Device-TEE_ERROR_SYNC_DATA = 0x0000000B--><!--Device-TEE_ERROR_SYNC_DATA = 0x0000000B-End--> |
| TEE_ERROR_RENAME_OBJECT = 0x0000000C | Failed to rename the file.<br><!--Device-TEE_ERROR_RENAME_OBJECT = 0x0000000C--><!--Device-TEE_ERROR_RENAME_OBJECT = 0x0000000C-End--> |
| TEE_ERROR_TRUSTED_APP_LOAD_ERROR = 0x0000000D | An error occurs when the TA is loaded.<br><!--Device-TEE_ERROR_TRUSTED_APP_LOAD_ERROR = 0x0000000D--><!--Device-TEE_ERROR_TRUSTED_APP_LOAD_ERROR = 0x0000000D-End--> |
| TEE_ERROR_OTRP_LOAD_NOT_MATCHED = 0x80000100 | TA type is inconsistent with the loading mode.<br><!--Device-TEE_ERROR_OTRP_LOAD_NOT_MATCHED = 0x80000100--><!--Device-TEE_ERROR_OTRP_LOAD_NOT_MATCHED = 0x80000100-End--> |
| TEE_ERROR_OTRP_LOAD_EXCEED = 0x80000101 | The not open session's otrp service num exceeds.<br><!--Device-TEE_ERROR_OTRP_LOAD_EXCEED = 0x80000101--><!--Device-TEE_ERROR_OTRP_LOAD_EXCEED = 0x80000101-End--> |
| TEE_ERROR_OTRP_ACCESS_DENIED = 0x80000102 | UUID of load cmd is not inconsistent with the sec file.<br><!--Device-TEE_ERROR_OTRP_ACCESS_DENIED = 0x80000102--><!--Device-TEE_ERROR_OTRP_ACCESS_DENIED = 0x80000102-End--> |
| TEE_ERROR_OTRP_SERVICE_AGED = 0x80000103 | Otrp service is aged.<br><!--Device-TEE_ERROR_OTRP_SERVICE_AGED = 0x80000103--><!--Device-TEE_ERROR_OTRP_SERVICE_AGED = 0x80000103-End--> |
| TEE_ERROR_STORAGE_EIO = 0x80001001 | An I/O error occurs when data is stored.<br><!--Device-TEE_ERROR_STORAGE_EIO = 0x80001001--><!--Device-TEE_ERROR_STORAGE_EIO = 0x80001001-End--> |
| TEE_ERROR_STORAGE_EAGAIN = 0x80001002 | The storage section is unavailable.<br><!--Device-TEE_ERROR_STORAGE_EAGAIN = 0x80001002--><!--Device-TEE_ERROR_STORAGE_EAGAIN = 0x80001002-End--> |
| TEE_ERROR_STORAGE_ENOTDIR = 0x80001003 | The operation target is not a directory.<br><!--Device-TEE_ERROR_STORAGE_ENOTDIR = 0x80001003--><!--Device-TEE_ERROR_STORAGE_ENOTDIR = 0x80001003-End--> |
| TEE_ERROR_STORAGE_EISDIR = 0x80001004 | This operation cannot be performed on a directory.<br><!--Device-TEE_ERROR_STORAGE_EISDIR = 0x80001004--><!--Device-TEE_ERROR_STORAGE_EISDIR = 0x80001004-End--> |
| TEE_ERROR_STORAGE_ENFILE = 0x80001005 | The number of opened files exceeds the limit in system.<br><!--Device-TEE_ERROR_STORAGE_ENFILE = 0x80001005--><!--Device-TEE_ERROR_STORAGE_ENFILE = 0x80001005-End--> |
| TEE_ERROR_STORAGE_EMFILE = 0x80001006 | The number of files opened for the process exceeds the limit.<br><!--Device-TEE_ERROR_STORAGE_EMFILE = 0x80001006--><!--Device-TEE_ERROR_STORAGE_EMFILE = 0x80001006-End--> |
| TEE_ERROR_STORAGE_EROFS = 0x80001007 | The storage section is read only.<br><!--Device-TEE_ERROR_STORAGE_EROFS = 0x80001007--><!--Device-TEE_ERROR_STORAGE_EROFS = 0x80001007-End--> |
| TEE_ERROR_STORAGE_EROLLBACK = 0x80001008 | The file object has been rolled back.<br><!--Device-TEE_ERROR_STORAGE_EROLLBACK = 0x80001008--><!--Device-TEE_ERROR_STORAGE_EROLLBACK = 0x80001008-End--> |
| TEE_ERROR_STORAGE_PATH_WRONG = 0x8000100A | The file path is not correct.<br><!--Device-TEE_ERROR_STORAGE_PATH_WRONG = 0x8000100A--><!--Device-TEE_ERROR_STORAGE_PATH_WRONG = 0x8000100A-End--> |
| TEE_ERROR_MSG_QUEUE_OVERFLOW = 0x8000100B | The service message queue overflows.<br><!--Device-TEE_ERROR_MSG_QUEUE_OVERFLOW = 0x8000100B--><!--Device-TEE_ERROR_MSG_QUEUE_OVERFLOW = 0x8000100B-End--> |
| TEE_ERROR_SUBTHREAD_ACCESS = 0x8000100C | The subthread created by TA cannot access the service<br><!--Device-TEE_ERROR_SUBTHREAD_ACCESS = 0x8000100C--><!--Device-TEE_ERROR_SUBTHREAD_ACCESS = 0x8000100C-End--> |
| TEE_ERROR_ORIGIN_PARTITION_INACTIVE = 0x8000100D | Enable backup feature, original partition is inactive<br><!--Device-TEE_ERROR_ORIGIN_PARTITION_INACTIVE = 0x8000100D--><!--Device-TEE_ERROR_ORIGIN_PARTITION_INACTIVE = 0x8000100D-End--> |
| TEE_ERROR_BACKUP_PARTITION_INACTIVE = 0x8000100E | Enable backup feature, backup partition is inactive<br><!--Device-TEE_ERROR_BACKUP_PARTITION_INACTIVE = 0x8000100E--><!--Device-TEE_ERROR_BACKUP_PARTITION_INACTIVE = 0x8000100E-End--> |
| TEE_ERROR_CORRUPT_OBJECT = 0xF0100001 | The file object is corrupted.<br><!--Device-TEE_ERROR_CORRUPT_OBJECT = 0xF0100001--><!--Device-TEE_ERROR_CORRUPT_OBJECT = 0xF0100001-End--> |
| TEE_ERROR_STORAGE_NOT_AVAILABLE = 0xF0100003 | The storage section is unavailable.<br><!--Device-TEE_ERROR_STORAGE_NOT_AVAILABLE = 0xF0100003--><!--Device-TEE_ERROR_STORAGE_NOT_AVAILABLE = 0xF0100003-End--> |
| TEE_ERROR_CIPHERTEXT_INVALID = 0xF0100006 | The cipher text is incorrect.<br><!--Device-TEE_ERROR_CIPHERTEXT_INVALID = 0xF0100006--><!--Device-TEE_ERROR_CIPHERTEXT_INVALID = 0xF0100006-End--> |
| TEE_ISOCKET_ERROR_PROTOCOL = 0xF1007001 | Protocol error in socket connection.<br><!--Device-TEE_ISOCKET_ERROR_PROTOCOL = 0xF1007001--><!--Device-TEE_ISOCKET_ERROR_PROTOCOL = 0xF1007001-End--> |
| TEE_ISOCKET_ERROR_REMOTE_CLOSED = 0xF1007002 | The socket is closed by the remote end.<br><!--Device-TEE_ISOCKET_ERROR_REMOTE_CLOSED = 0xF1007002--><!--Device-TEE_ISOCKET_ERROR_REMOTE_CLOSED = 0xF1007002-End--> |
| TEE_ISOCKET_ERROR_TIMEOUT = 0xF1007003 | The socket connection timed out.<br><!--Device-TEE_ISOCKET_ERROR_TIMEOUT = 0xF1007003--><!--Device-TEE_ISOCKET_ERROR_TIMEOUT = 0xF1007003-End--> |
| TEE_ISOCKET_ERROR_OUT_OF_RESOURCES = 0xF1007004 | There is no resource available for the socket connection.<br><!--Device-TEE_ISOCKET_ERROR_OUT_OF_RESOURCES = 0xF1007004--><!--Device-TEE_ISOCKET_ERROR_OUT_OF_RESOURCES = 0xF1007004-End--> |
| TEE_ISOCKET_ERROR_LARGE_BUFFER = 0xF1007005 | The buffer is too large for the socket connection.<br><!--Device-TEE_ISOCKET_ERROR_LARGE_BUFFER = 0xF1007005--><!--Device-TEE_ISOCKET_ERROR_LARGE_BUFFER = 0xF1007005-End--> |
| TEE_ISOCKET_WARNING_PROTOCOL = 0xF1007006 | A warning is given in the socket connection.<br><!--Device-TEE_ISOCKET_WARNING_PROTOCOL = 0xF1007006--><!--Device-TEE_ISOCKET_WARNING_PROTOCOL = 0xF1007006-End--> |
| TEE_ERROR_GENERIC = 0xFFFF0000 | Generic error.<br><!--Device-TEE_ERROR_GENERIC = 0xFFFF0000--><!--Device-TEE_ERROR_GENERIC = 0xFFFF0000-End--> |
| TEE_ERROR_ACCESS_DENIED = 0xFFFF0001 | The access is denied.<br><!--Device-TEE_ERROR_ACCESS_DENIED = 0xFFFF0001--><!--Device-TEE_ERROR_ACCESS_DENIED = 0xFFFF0001-End--> |
| TEE_ERROR_CANCEL = 0xFFFF0002 | The operation has been canceled.<br><!--Device-TEE_ERROR_CANCEL = 0xFFFF0002--><!--Device-TEE_ERROR_CANCEL = 0xFFFF0002-End--> |
| TEE_ERROR_ACCESS_CONFLICT = 0xFFFF0003 | An access conflict occurs.<br><!--Device-TEE_ERROR_ACCESS_CONFLICT = 0xFFFF0003--><!--Device-TEE_ERROR_ACCESS_CONFLICT = 0xFFFF0003-End--> |
| TEE_ERROR_EXCESS_DATA = 0xFFFF0004 | The data size exceeds the maximum.<br><!--Device-TEE_ERROR_EXCESS_DATA = 0xFFFF0004--><!--Device-TEE_ERROR_EXCESS_DATA = 0xFFFF0004-End--> |
| TEE_ERROR_BAD_FORMAT = 0xFFFF0005 | Incorrect data format.<br><!--Device-TEE_ERROR_BAD_FORMAT = 0xFFFF0005--><!--Device-TEE_ERROR_BAD_FORMAT = 0xFFFF0005-End--> |
| TEE_ERROR_BAD_PARAMETERS = 0xFFFF0006 | Incorrect parameters.<br><!--Device-TEE_ERROR_BAD_PARAMETERS = 0xFFFF0006--><!--Device-TEE_ERROR_BAD_PARAMETERS = 0xFFFF0006-End--> |
| TEE_ERROR_BAD_STATE = 0xFFFF0007 | The current state does not support the operation.<br><!--Device-TEE_ERROR_BAD_STATE = 0xFFFF0007--><!--Device-TEE_ERROR_BAD_STATE = 0xFFFF0007-End--> |
| TEE_ERROR_ITEM_NOT_FOUND = 0xFFFF0008 | Failed to find the target item.<br><!--Device-TEE_ERROR_ITEM_NOT_FOUND = 0xFFFF0008--><!--Device-TEE_ERROR_ITEM_NOT_FOUND = 0xFFFF0008-End--> |
| TEE_ERROR_NOT_IMPLEMENTED = 0xFFFF0009 | The API is not implemented.<br><!--Device-TEE_ERROR_NOT_IMPLEMENTED = 0xFFFF0009--><!--Device-TEE_ERROR_NOT_IMPLEMENTED = 0xFFFF0009-End--> |
| TEE_ERROR_NOT_SUPPORTED = 0xFFFF000A | The API is not supported.<br><!--Device-TEE_ERROR_NOT_SUPPORTED = 0xFFFF000A--><!--Device-TEE_ERROR_NOT_SUPPORTED = 0xFFFF000A-End--> |
| TEE_ERROR_NO_DATA = 0xFFFF000B | There is no data available for this operation.<br><!--Device-TEE_ERROR_NO_DATA = 0xFFFF000B--><!--Device-TEE_ERROR_NO_DATA = 0xFFFF000B-End--> |
| TEE_ERROR_OUT_OF_MEMORY = 0xFFFF000C | There is no memory available for this operation.<br><!--Device-TEE_ERROR_OUT_OF_MEMORY = 0xFFFF000C--><!--Device-TEE_ERROR_OUT_OF_MEMORY = 0xFFFF000C-End--> |
| TEE_ERROR_BUSY = 0xFFFF000D | The system does not respond to this operation.<br><!--Device-TEE_ERROR_BUSY = 0xFFFF000D--><!--Device-TEE_ERROR_BUSY = 0xFFFF000D-End--> |
| TEE_ERROR_COMMUNICATION = 0xFFFF000E | Failed to communicate with the target.<br><!--Device-TEE_ERROR_COMMUNICATION = 0xFFFF000E--><!--Device-TEE_ERROR_COMMUNICATION = 0xFFFF000E-End--> |
| TEE_ERROR_SECURITY = 0xFFFF000F | A security error occurs.<br><!--Device-TEE_ERROR_SECURITY = 0xFFFF000F--><!--Device-TEE_ERROR_SECURITY = 0xFFFF000F-End--> |
| TEE_ERROR_SHORT_BUFFER = 0xFFFF0010 | The buffer is insufficient for this operation.<br><!--Device-TEE_ERROR_SHORT_BUFFER = 0xFFFF0010--><!--Device-TEE_ERROR_SHORT_BUFFER = 0xFFFF0010-End--> |
| TEE_ERROR_EXTERNAL_CANCEL = 0xFFFF0011 | The operation has been canceled.<br><!--Device-TEE_ERROR_EXTERNAL_CANCEL = 0xFFFF0011--><!--Device-TEE_ERROR_EXTERNAL_CANCEL = 0xFFFF0011-End--> |
| TEE_PENDING = 0xFFFF2000 | The service is in the pending state (asynchronous state).<br><!--Device-TEE_PENDING = 0xFFFF2000--><!--Device-TEE_PENDING = 0xFFFF2000-End--> |
| TEE_PENDING2 = 0xFFFF2001 | The service is in the pending state().<br><!--Device-TEE_PENDING2 = 0xFFFF2001--><!--Device-TEE_PENDING2 = 0xFFFF2001-End--> |
| TEE_PENDING3 = 0xFFFF2002 | Reserved.<br><!--Device-TEE_PENDING3 = 0xFFFF2002--><!--Device-TEE_PENDING3 = 0xFFFF2002-End--> |
| TEE_ERROR_TIMEOUT = 0xFFFF3001 | The operation timed out.<br><!--Device-TEE_ERROR_TIMEOUT = 0xFFFF3001--><!--Device-TEE_ERROR_TIMEOUT = 0xFFFF3001-End--> |
| TEE_ERROR_OVERFLOW = 0xFFFF300f | Overflow occurs.<br><!--Device-TEE_ERROR_OVERFLOW = 0xFFFF300f--><!--Device-TEE_ERROR_OVERFLOW = 0xFFFF300f-End--> |
| TEE_ERROR_TARGET_DEAD = 0xFFFF3024 | The TA is crashed.<br><!--Device-TEE_ERROR_TARGET_DEAD = 0xFFFF3024--><!--Device-TEE_ERROR_TARGET_DEAD = 0xFFFF3024-End--> |
| TEE_ERROR_STORAGE_NO_SPACE = 0xFFFF3041 | There is no enough space to store data.<br><!--Device-TEE_ERROR_STORAGE_NO_SPACE = 0xFFFF3041--><!--Device-TEE_ERROR_STORAGE_NO_SPACE = 0xFFFF3041-End--> |
| TEE_ERROR_MAC_INVALID = 0xFFFF3071 | The MAC operation failed.<br><!--Device-TEE_ERROR_MAC_INVALID = 0xFFFF3071--><!--Device-TEE_ERROR_MAC_INVALID = 0xFFFF3071-End--> |
| TEE_ERROR_SIGNATURE_INVALID = 0xFFFF3072 | The signature verification failed.<br><!--Device-TEE_ERROR_SIGNATURE_INVALID = 0xFFFF3072--><!--Device-TEE_ERROR_SIGNATURE_INVALID = 0xFFFF3072-End--> |
| TEE_ERROR_CERTIFICATE_INVALID = 0xFFFF3073 | Thecertificate verify failed.<br><!--Device-TEE_ERROR_CERTIFICATE_INVALID = 0xFFFF3073--><!--Device-TEE_ERROR_CERTIFICATE_INVALID = 0xFFFF3073-End--> |
| TEE_CLIENT_INTR = 0xFFFF4000 | Interrupted by CFC. Broken control flow is detected.<br><!--Device-TEE_CLIENT_INTR = 0xFFFF4000--><!--Device-TEE_CLIENT_INTR = 0xFFFF4000-End--> |
| TEE_ERROR_TIME_NOT_SET = 0xFFFF5000 | Time is not set.<br><!--Device-TEE_ERROR_TIME_NOT_SET = 0xFFFF5000--><!--Device-TEE_ERROR_TIME_NOT_SET = 0xFFFF5000-End--> |
| TEE_ERROR_TIME_NEEDS_RESET = 0xFFFF5001 | Time needs to be reset.<br><!--Device-TEE_ERROR_TIME_NEEDS_RESET = 0xFFFF5001--><!--Device-TEE_ERROR_TIME_NEEDS_RESET = 0xFFFF5001-End--> |
| TEE_FAIL = 0xFFFF5002 | System error.<br><!--Device-TEE_FAIL = 0xFFFF5002--><!--Device-TEE_FAIL = 0xFFFF5002-End--> |
| TEE_ERROR_TIMER = 0xFFFF6000 | Base value of the timer error code.<br><!--Device-TEE_ERROR_TIMER = 0xFFFF6000--><!--Device-TEE_ERROR_TIMER = 0xFFFF6000-End--> |
| TEE_ERROR_TIMER_CREATE_FAILED = 0xFFFF6001 | Failed to create the timer.<br><!--Device-TEE_ERROR_TIMER_CREATE_FAILED = 0xFFFF6001--><!--Device-TEE_ERROR_TIMER_CREATE_FAILED = 0xFFFF6001-End--> |
| TEE_ERROR_TIMER_DESTROY_FAILED = 0xFFFF6002 | Failed to destroy the timer.<br><!--Device-TEE_ERROR_TIMER_DESTROY_FAILED = 0xFFFF6002--><!--Device-TEE_ERROR_TIMER_DESTROY_FAILED = 0xFFFF6002-End--> |
| TEE_ERROR_TIMER_NOT_FOUND = 0xFFFF6003 | The timer is not found.<br><!--Device-TEE_ERROR_TIMER_NOT_FOUND = 0xFFFF6003--><!--Device-TEE_ERROR_TIMER_NOT_FOUND = 0xFFFF6003-End--> |
| TEE_ERROR_RPMB_BASE = 0xFFFF7000 | Base value of RPMB error codes.<br><!--Device-TEE_ERROR_RPMB_BASE = 0xFFFF7000--><!--Device-TEE_ERROR_RPMB_BASE = 0xFFFF7000-End--> |
| TEE_ERROR_RPMB_GENERIC = 0xFFFF7001 | Generic error of RPMB operations.<br><!--Device-TEE_ERROR_RPMB_GENERIC = 0xFFFF7001--><!--Device-TEE_ERROR_RPMB_GENERIC = 0xFFFF7001-End--> |
| TEE_ERROR_RPMB_MAC_FAIL = 0xFFFF7002 | Verify MAC failed in RPMB operations.<br><!--Device-TEE_ERROR_RPMB_MAC_FAIL = 0xFFFF7002--><!--Device-TEE_ERROR_RPMB_MAC_FAIL = 0xFFFF7002-End--> |
| TEE_ERROR_RPMB_COUNTER_FAIL = 0xFFFF7003 | Invalid counter in RPMB operations.<br><!--Device-TEE_ERROR_RPMB_COUNTER_FAIL = 0xFFFF7003--><!--Device-TEE_ERROR_RPMB_COUNTER_FAIL = 0xFFFF7003-End--> |
| TEE_ERROR_RPMB_ADDR_FAIL = 0xFFFF7004 | Address check failed in RPMB operations.<br><!--Device-TEE_ERROR_RPMB_ADDR_FAIL = 0xFFFF7004--><!--Device-TEE_ERROR_RPMB_ADDR_FAIL = 0xFFFF7004-End--> |
| TEE_ERROR_RPMB_WRITE_FAIL = 0xFFFF7005 | Fail to write data to RPMB.<br><!--Device-TEE_ERROR_RPMB_WRITE_FAIL = 0xFFFF7005--><!--Device-TEE_ERROR_RPMB_WRITE_FAIL = 0xFFFF7005-End--> |
| TEE_ERROR_RPMB_READ_FAIL = 0xFFFF7006 | Fail to read data in RPMB.<br><!--Device-TEE_ERROR_RPMB_READ_FAIL = 0xFFFF7006--><!--Device-TEE_ERROR_RPMB_READ_FAIL = 0xFFFF7006-End--> |
| TEE_ERROR_RPMB_KEY_NOT_PROGRAM = 0xFFFF7007 | Key is not provisioned in RPMB.<br><!--Device-TEE_ERROR_RPMB_KEY_NOT_PROGRAM = 0xFFFF7007--><!--Device-TEE_ERROR_RPMB_KEY_NOT_PROGRAM = 0xFFFF7007-End--> |
| TEE_ERROR_RPMB_RESP_UNEXPECT_MSGTYPE = 0xFFFF7100 | Incorrect message type in RPMB response.<br><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_MSGTYPE = 0xFFFF7100--><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_MSGTYPE = 0xFFFF7100-End--> |
| TEE_ERROR_RPMB_RESP_UNEXPECT_BLKCNT = 0xFFFF7101 | Incorrect message data block count in RPMB response.<br><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_BLKCNT = 0xFFFF7101--><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_BLKCNT = 0xFFFF7101-End--> |
| TEE_ERROR_RPMB_RESP_UNEXPECT_BLKIDX = 0xFFFF7102 | Incorrect message data block count in RPMB response.<br><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_BLKIDX = 0xFFFF7102--><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_BLKIDX = 0xFFFF7102-End--> |
| TEE_ERROR_RPMB_RESP_UNEXPECT_WRCNT = 0xFFFF7103 | Incorrect message data counter in RPMB response.<br><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_WRCNT = 0xFFFF7103--><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_WRCNT = 0xFFFF7103-End--> |
| TEE_ERROR_RPMB_RESP_UNEXPECT_NONCE = 0xFFFF7104 | Incorrect message data nonce in RPMB response.<br><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_NONCE = 0xFFFF7104--><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_NONCE = 0xFFFF7104-End--> |
| TEE_ERROR_RPMB_RESP_UNEXPECT_MAC = 0xFFFF7105 | Incorrect message data MAC in RPMB response.<br><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_MAC = 0xFFFF7105--><!--Device-TEE_ERROR_RPMB_RESP_UNEXPECT_MAC = 0xFFFF7105-End--> |
| TEE_ERROR_RPMB_FILE_NOT_FOUND = 0xFFFF7106 | The file is not found in RPMB.<br><!--Device-TEE_ERROR_RPMB_FILE_NOT_FOUND = 0xFFFF7106--><!--Device-TEE_ERROR_RPMB_FILE_NOT_FOUND = 0xFFFF7106-End--> |
| TEE_ERROR_RPMB_NOSPC = 0xFFFF7107 | No spece left for RPMB operations.<br><!--Device-TEE_ERROR_RPMB_NOSPC = 0xFFFF7107--><!--Device-TEE_ERROR_RPMB_NOSPC = 0xFFFF7107-End--> |
| TEE_ERROR_RPMB_SPC_CONFLICT = 0xFFFF7108 | Exceeds max space of RPMB for this TA.<br><!--Device-TEE_ERROR_RPMB_SPC_CONFLICT = 0xFFFF7108--><!--Device-TEE_ERROR_RPMB_SPC_CONFLICT = 0xFFFF7108-End--> |
| TEE_ERROR_RPMB_NOT_AVAILABLE = 0xFFFF7109 | RPMB service not ready.<br><!--Device-TEE_ERROR_RPMB_NOT_AVAILABLE = 0xFFFF7109--><!--Device-TEE_ERROR_RPMB_NOT_AVAILABLE = 0xFFFF7109-End--> |
| TEE_ERROR_RPMB_DAMAGED = 0xFFFF710A | RPMB partition is damaged.<br><!--Device-TEE_ERROR_RPMB_DAMAGED = 0xFFFF710A--><!--Device-TEE_ERROR_RPMB_DAMAGED = 0xFFFF710A-End--> |
| TEE_ERROR_TUI_IN_USE = 0xFFFF7110 | TUI is being used.<br><!--Device-TEE_ERROR_TUI_IN_USE = 0xFFFF7110--><!--Device-TEE_ERROR_TUI_IN_USE = 0xFFFF7110-End--> |
| TEE_ERROR_TUI_SWITCH_CHANNAL = 0xFFFF7111 | Incorrect message switch channal in TUI response.<br><!--Device-TEE_ERROR_TUI_SWITCH_CHANNAL = 0xFFFF7111--><!--Device-TEE_ERROR_TUI_SWITCH_CHANNAL = 0xFFFF7111-End--> |
| TEE_ERROR_TUI_CFG_DRIVER = 0xFFFF7112 | Incorrect message configurator driver in TUI response.<br><!--Device-TEE_ERROR_TUI_CFG_DRIVER = 0xFFFF7112--><!--Device-TEE_ERROR_TUI_CFG_DRIVER = 0xFFFF7112-End--> |
| TEE_ERROR_TUI_INVALID_EVENT = 0xFFFF7113 | Invalid TUI event.<br><!--Device-TEE_ERROR_TUI_INVALID_EVENT = 0xFFFF7113--><!--Device-TEE_ERROR_TUI_INVALID_EVENT = 0xFFFF7113-End--> |
| TEE_ERROR_TUI_POLL_EVENT = 0xFFFF7114 | Incorrect message polling events in TUI response.<br><!--Device-TEE_ERROR_TUI_POLL_EVENT = 0xFFFF7114--><!--Device-TEE_ERROR_TUI_POLL_EVENT = 0xFFFF7114-End--> |
| TEE_ERROR_TUI_CANCELED = 0xFFFF7115 | TUI is cancelled.<br><!--Device-TEE_ERROR_TUI_CANCELED = 0xFFFF7115--><!--Device-TEE_ERROR_TUI_CANCELED = 0xFFFF7115-End--> |
| TEE_ERROR_TUI_EXIT = 0xFFFF7116 | TUI is exited.<br><!--Device-TEE_ERROR_TUI_EXIT = 0xFFFF7116--><!--Device-TEE_ERROR_TUI_EXIT = 0xFFFF7116-End--> |
| TEE_ERROR_TUI_NOT_AVAILABLE = 0xFFFF7117 | TUI unavailable.<br><!--Device-TEE_ERROR_TUI_NOT_AVAILABLE = 0xFFFF7117--><!--Device-TEE_ERROR_TUI_NOT_AVAILABLE = 0xFFFF7117-End--> |
| TEE_ERROR_SEC_FLASH_NOT_AVAILABLE = 0xFFFF7118 | sec flash is not available.<br><!--Device-TEE_ERROR_SEC_FLASH_NOT_AVAILABLE = 0xFFFF7118--><!--Device-TEE_ERROR_SEC_FLASH_NOT_AVAILABLE = 0xFFFF7118-End--> |
| TEE_ERROR_SESRV_NOT_AVAILABLE = 0xFFFF7119 | SE service has crashed or not enable.<br><!--Device-TEE_ERROR_SESRV_NOT_AVAILABLE = 0xFFFF7119--><!--Device-TEE_ERROR_SESRV_NOT_AVAILABLE = 0xFFFF7119-End--> |
| TEE_ERROR_BIOSRV_NOT_AVAILABLE = 0xFFFF711A | The BIO service is not available.<br><!--Device-TEE_ERROR_BIOSRV_NOT_AVAILABLE = 0xFFFF711A--><!--Device-TEE_ERROR_BIOSRV_NOT_AVAILABLE = 0xFFFF711A-End--> |
| TEE_ERROR_ROTSRV_NOT_AVAILABLE = 0xFFFF711B | The ROT service is not available.<br><!--Device-TEE_ERROR_ROTSRV_NOT_AVAILABLE = 0xFFFF711B--><!--Device-TEE_ERROR_ROTSRV_NOT_AVAILABLE = 0xFFFF711B-End--> |
| TEE_ERROR_ARTSRV_NOT_AVAILABLE = 0xFFFF711C | The TA Anti-Rollback service is not available.<br><!--Device-TEE_ERROR_ARTSRV_NOT_AVAILABLE = 0xFFFF711C--><!--Device-TEE_ERROR_ARTSRV_NOT_AVAILABLE = 0xFFFF711C-End--> |
| TEE_ERROR_HSMSRV_NOT_AVAILABLE = 0xFFFF711D | The HSM service is not available.<br><!--Device-TEE_ERROR_HSMSRV_NOT_AVAILABLE = 0xFFFF711D--><!--Device-TEE_ERROR_HSMSRV_NOT_AVAILABLE = 0xFFFF711D-End--> |
| TEE_ERROR_VRPMB_AGENT_FAIL = 0xFFFF7200 | REE vrpmb agent check magic failed, maybe cache fail.<br><!--Device-TEE_ERROR_VRPMB_AGENT_FAIL = 0xFFFF7200--><!--Device-TEE_ERROR_VRPMB_AGENT_FAIL = 0xFFFF7200-End--> |
| TEE_ERROR_VRPMB_RW_FAIL = 0xFFFF7201 | REE ssd driver rw failed.<br><!--Device-TEE_ERROR_VRPMB_RW_FAIL = 0xFFFF7201--><!--Device-TEE_ERROR_VRPMB_RW_FAIL = 0xFFFF7201-End--> |
| TEE_ERROR_VRPMB_SUPER_MAC_FAILED = 0xFFFF7202 | vrpmb check super block mac failed.<br><!--Device-TEE_ERROR_VRPMB_SUPER_MAC_FAILED = 0xFFFF7202--><!--Device-TEE_ERROR_VRPMB_SUPER_MAC_FAILED = 0xFFFF7202-End--> |
| TEE_ERROR_VRPMB_WRITE_REJECT = 0xFFFF7203 | reject write to vrpmb.<br><!--Device-TEE_ERROR_VRPMB_WRITE_REJECT = 0xFFFF7203--><!--Device-TEE_ERROR_VRPMB_WRITE_REJECT = 0xFFFF7203-End--> |
| TEE_ERROR_ANTIROOT_RSP_FAIL = 0xFFFF9110 | Failed to verify AntiRoot response.<br><!--Device-TEE_ERROR_ANTIROOT_RSP_FAIL = 0xFFFF9110--><!--Device-TEE_ERROR_ANTIROOT_RSP_FAIL = 0xFFFF9110-End--> |
| TEE_ERROR_ANTIROOT_INVOKE_ERROR = 0xFFFF9111 | AntiRoot error in invokeCmd().<br><!--Device-TEE_ERROR_ANTIROOT_INVOKE_ERROR = 0xFFFF9111--><!--Device-TEE_ERROR_ANTIROOT_INVOKE_ERROR = 0xFFFF9111-End--> |
| TEE_ERROR_AUDIT_FAIL = 0xFFFF9112 | Audit failed.<br><!--Device-TEE_ERROR_AUDIT_FAIL = 0xFFFF9112--><!--Device-TEE_ERROR_AUDIT_FAIL = 0xFFFF9112-End--> |
| TEE_FAIL2 = 0xFFFF9113 | Unused.<br><!--Device-TEE_FAIL2 = 0xFFFF9113--><!--Device-TEE_FAIL2 = 0xFFFF9113-End--> |
| TEE_ERROR_IPC_OVERFLOW = 0xFFFF9114 | IPC Channel overflow error.<br><!--Device-TEE_ERROR_IPC_OVERFLOW = 0xFFFF9114--><!--Device-TEE_ERROR_IPC_OVERFLOW = 0xFFFF9114-End--> |
| TEE_ERROR_APM = 0xFFFF9115 | APM error.<br><!--Device-TEE_ERROR_APM = 0xFFFF9115--><!--Device-TEE_ERROR_APM = 0xFFFF9115-End--> |
| TEE_ERROR_CA_AUTHFILE_NOT_EXIST = 0xFFFF9116 | CA auth file not exist.<br><!--Device-TEE_ERROR_CA_AUTHFILE_NOT_EXIST = 0xFFFF9116--><!--Device-TEE_ERROR_CA_AUTHFILE_NOT_EXIST = 0xFFFF9116-End--> |
| TEE_ERROR_CA_CALLER_ACCESS_DENIED = 0xFFFF9117 | CA caller access is denied.<br><!--Device-TEE_ERROR_CA_CALLER_ACCESS_DENIED = 0xFFFF9117--><!--Device-TEE_ERROR_CA_CALLER_ACCESS_DENIED = 0xFFFF9117-End--> |
| TEE_ERROR_INVALID_TA_FORMAT = 0xFFFF9118 | Invalid TA format.<br><!--Device-TEE_ERROR_INVALID_TA_FORMAT = 0xFFFF9118--><!--Device-TEE_ERROR_INVALID_TA_FORMAT = 0xFFFF9118-End--> |
| TEE_DSTB_LOCAL_SIGN_REPORT_ERROR = 0xFFFF9200 | local dstb service sign report error.<br><!--Device-TEE_DSTB_LOCAL_SIGN_REPORT_ERROR = 0xFFFF9200--><!--Device-TEE_DSTB_LOCAL_SIGN_REPORT_ERROR = 0xFFFF9200-End--> |
| TEE_DSTB_REMOTE_SIGN_REPORT_ERROR = 0xFFFF9201 | remote dstb service sign report error.<br><!--Device-TEE_DSTB_REMOTE_SIGN_REPORT_ERROR = 0xFFFF9201--><!--Device-TEE_DSTB_REMOTE_SIGN_REPORT_ERROR = 0xFFFF9201-End--> |
| TEE_DSTB_LOCAL_REPORT_CERT_CHAIN_ERROR = 0xFFFF9202 | local dstb service report cert chain error.<br><!--Device-TEE_DSTB_LOCAL_REPORT_CERT_CHAIN_ERROR = 0xFFFF9202--><!--Device-TEE_DSTB_LOCAL_REPORT_CERT_CHAIN_ERROR = 0xFFFF9202-End--> |
| TEE_DSTB_REMOTE_REPORT_CERT_CHAIN_ERROR = 0xFFFF9203 | remote dstb service report cert chain error.<br><!--Device-TEE_DSTB_REMOTE_REPORT_CERT_CHAIN_ERROR = 0xFFFF9203--><!--Device-TEE_DSTB_REMOTE_REPORT_CERT_CHAIN_ERROR = 0xFFFF9203-End--> |
| TEE_DSTB_LOCAL_REPORT_VERIFY_ERROR = 0xFFFF9204 | local dstb service verify report error.<br><!--Device-TEE_DSTB_LOCAL_REPORT_VERIFY_ERROR = 0xFFFF9204--><!--Device-TEE_DSTB_LOCAL_REPORT_VERIFY_ERROR = 0xFFFF9204-End--> |
| TEE_DSTB_REMOTE_REPORT_VERIFY_ERROR = 0xFFFF9205 | remote dstb service verify report error.<br><!--Device-TEE_DSTB_REMOTE_REPORT_VERIFY_ERROR = 0xFFFF9205--><!--Device-TEE_DSTB_REMOTE_REPORT_VERIFY_ERROR = 0xFFFF9205-End--> |
| TEE_DSTB_LOCAL_CERT_CHAIN_VERIFY_ERROR = 0xFFFF9206 | local dstb service verify cert chain error.<br><!--Device-TEE_DSTB_LOCAL_CERT_CHAIN_VERIFY_ERROR = 0xFFFF9206--><!--Device-TEE_DSTB_LOCAL_CERT_CHAIN_VERIFY_ERROR = 0xFFFF9206-End--> |
| TEE_DSTB_REMOTE_CERT_CHAIN_VERIFY_ERROR = 0xFFFF9207 | remote dstb service verify cert chain error.<br><!--Device-TEE_DSTB_REMOTE_CERT_CHAIN_VERIFY_ERROR = 0xFFFF9207--><!--Device-TEE_DSTB_REMOTE_CERT_CHAIN_VERIFY_ERROR = 0xFFFF9207-End--> |
| TEE_DSTB_LOCAL_INVALID_KEY_VERSION_ERROR = 0xFFFF9208 | local dstb service key version error.<br><!--Device-TEE_DSTB_LOCAL_INVALID_KEY_VERSION_ERROR = 0xFFFF9208--><!--Device-TEE_DSTB_LOCAL_INVALID_KEY_VERSION_ERROR = 0xFFFF9208-End--> |
| TEE_DSTB_REMOTE_INVALID_KEY_VERSION_ERROR = 0xFFFF9209 | remote dstb service key version error.<br><!--Device-TEE_DSTB_REMOTE_INVALID_KEY_VERSION_ERROR = 0xFFFF9209--><!--Device-TEE_DSTB_REMOTE_INVALID_KEY_VERSION_ERROR = 0xFFFF9209-End--> |
| TEE_DSTB_INVALID_UDID = 0xFFFF920A | udid is invalid.<br><!--Device-TEE_DSTB_INVALID_UDID = 0xFFFF920A--><!--Device-TEE_DSTB_INVALID_UDID = 0xFFFF920A-End--> |
| TEE_DSTB_DERIVE_KEY_ERROR = 0xFFFF920B | dstb service derive key error.<br><!--Device-TEE_DSTB_DERIVE_KEY_ERROR = 0xFFFF920B--><!--Device-TEE_DSTB_DERIVE_KEY_ERROR = 0xFFFF920B-End--> |
| TEE_DSTB_REE_SRV_ERROR = 0xFFFF920C | dstb service of ree error.<br><!--Device-TEE_DSTB_REE_SRV_ERROR = 0xFFFF920C--><!--Device-TEE_DSTB_REE_SRV_ERROR = 0xFFFF920C-End--> |
| TEE_ERROR_TA_ANTI_ROLLBACK = 0xFFFF920D | TA load fail becauce of anti-rollback.<br><!--Device-TEE_ERROR_TA_ANTI_ROLLBACK = 0xFFFF920D--><!--Device-TEE_ERROR_TA_ANTI_ROLLBACK = 0xFFFF920D-End--> |
| TEE_ERROR_RETRY_OPEN_SESSION = 0xFFFF920E | open_session fail becauce of race with close_session.<br><!--Device-TEE_ERROR_RETRY_OPEN_SESSION = 0xFFFF920E--><!--Device-TEE_ERROR_RETRY_OPEN_SESSION = 0xFFFF920E-End--> |
| TEE_ERROR_TA_CTRL_FILE_LOAD_FAIL = 0xFFFF920F | TA control file load fail.<br><!--Device-TEE_ERROR_TA_CTRL_FILE_LOAD_FAIL = 0xFFFF920F--><!--Device-TEE_ERROR_TA_CTRL_FILE_LOAD_FAIL = 0xFFFF920F-End--> |
| TEE_ERROR_TA_CTRL_FILE_VERIFY_FAIL = 0xFFFF9210 | TA control file verify fail.<br><!--Device-TEE_ERROR_TA_CTRL_FILE_VERIFY_FAIL = 0xFFFF9210--><!--Device-TEE_ERROR_TA_CTRL_FILE_VERIFY_FAIL = 0xFFFF9210-End--> |
| TEE_ERROR_TA_VER_BELOW_CONTROL_VER = 0xFFFF9211 | TA version is below the version in control file.<br><!--Device-TEE_ERROR_TA_VER_BELOW_CONTROL_VER = 0xFFFF9211--><!--Device-TEE_ERROR_TA_VER_BELOW_CONTROL_VER = 0xFFFF9211-End--> |
| TEE_DSTB_LOCAL_CERT_VALIDITY_ERROR = 0xFFFF9212 | Local dstb cert chain validity check failed.<br><!--Device-TEE_DSTB_LOCAL_CERT_VALIDITY_ERROR = 0xFFFF9212--><!--Device-TEE_DSTB_LOCAL_CERT_VALIDITY_ERROR = 0xFFFF9212-End--> |
| TEE_DSTB_REMOTE_CERT_VALIDITY_ERROR = 0xFFFF9213 | Remote dstb cert chain validity check failed.<br><!--Device-TEE_DSTB_REMOTE_CERT_VALIDITY_ERROR = 0xFFFF9213--><!--Device-TEE_DSTB_REMOTE_CERT_VALIDITY_ERROR = 0xFFFF9213-End--> |

### TEE_LoginMethod

```c
enum TEE_LoginMethod
```

**Description**

Login type definitions

<!--Device-enum TEE_LoginMethod--><!--Device-enum TEE_LoginMethod-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_LOGIN_PUBLIC = 0x0 | Public login method.<br><!--Device-TEE_LOGIN_PUBLIC = 0x0--><!--Device-TEE_LOGIN_PUBLIC = 0x0-End--> |
| TEE_LOGIN_USER | User login method.<br><!--Device-TEE_LOGIN_USER--><!--Device-TEE_LOGIN_USER-End--> |
| TEE_LOGIN_GROUP | Group login method.<br><!--Device-TEE_LOGIN_GROUP--><!--Device-TEE_LOGIN_GROUP-End--> |
| TEE_LOGIN_APPLICATION = 0x4 | Application login method.<br><!--Device-TEE_LOGIN_APPLICATION = 0x4--><!--Device-TEE_LOGIN_APPLICATION = 0x4-End--> |
| TEE_LOGIN_USER_APPLICATION = 0x5 | User-application login method.<br><!--Device-TEE_LOGIN_USER_APPLICATION = 0x5--><!--Device-TEE_LOGIN_USER_APPLICATION = 0x5-End--> |
| TEE_LOGIN_GROUP_APPLICATION = 0x6 | Group-application login method.<br><!--Device-TEE_LOGIN_GROUP_APPLICATION = 0x6--><!--Device-TEE_LOGIN_GROUP_APPLICATION = 0x6-End--> |
| TEE_LOGIN_IDENTIFY = 0x7 | Customized login type.<br><!--Device-TEE_LOGIN_IDENTIFY = 0x7--><!--Device-TEE_LOGIN_IDENTIFY = 0x7-End--> |
| TEEK_LOGIN_IDENTIFY = 0x80000001 | Login type from the Linux kernel.<br><!--Device-TEEK_LOGIN_IDENTIFY = 0x80000001--><!--Device-TEEK_LOGIN_IDENTIFY = 0x80000001-End--> |


## Function description

### check_param_type()

```c
static inline bool check_param_type(uint32_t param_to_check, uint32_t valid0, uint32_t valid1, uint32_t valid2, uint32_t valid3)
{return (TEE_PARAM_TYPES(valid0, valid1, valid2, valid3) == param_to_check)
```

**Description**

Checks parameter types.

<!--Device-static inline bool check_param_type(uint32_t param_to_check, uint32_t valid0, uint32_t valid1, uint32_t valid2, uint32_t valid3) {return (TEE_PARAM_TYPES(valid0, valid1, valid2, valid3) == param_to_check)--><!--Device-static inline bool check_param_type(uint32_t param_to_check, uint32_t valid0, uint32_t valid1, uint32_t valid2, uint32_t valid3) {return (TEE_PARAM_TYPES(valid0, valid1, valid2, valid3) == param_to_check)-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| valid3) == param_to_check | Indicates the expected parameter values. |
| [](capi-tee-defines-h.md#)v[](capi-tee-defines-h.md#)a[](capi-tee-defines-h.md#)l[](capi-tee-defines-h.md#)i[](capi-tee-defines-h.md#)d[](capi-tee-defines-h.md#)0[](capi-tee-defines-h.md#) | Indicates the first parameter type to check. |
| [](capi-tee-defines-h.md#)v[](capi-tee-defines-h.md#)a[](capi-tee-defines-h.md#)l[](capi-tee-defines-h.md#)i[](capi-tee-defines-h.md#)d[](capi-tee-defines-h.md#)1[](capi-tee-defines-h.md#) | Indicates the second parameter type to check. |
| [](capi-tee-defines-h.md#)v[](capi-tee-defines-h.md#)a[](capi-tee-defines-h.md#)l[](capi-tee-defines-h.md#)i[](capi-tee-defines-h.md#)d[](capi-tee-defines-h.md#)2[](capi-tee-defines-h.md#) | Indicates the third parameter type to check. |
| valid3) == param_to_check | Indicates the fourth parameter type to check. |

**Returns**:

| Type | Description |
| -- | -- |
| static inline bool | Returns <b>true</b> if the parameter types are correct. Returns <b>false</b> otherwise. |


