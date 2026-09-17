# tee_defines.h

## Overview

Defines basic data types and data structures of TEE.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Struct

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

### Enum

| Name | Description |
| -- | -- |
| [TEE_ParamType](#tee_paramtype) | Enumerates the types of the TEE parameter. |
| [TEE_ObjectAttribute](#tee_objectattribute) | Enumerates the types of object attribute. |
| [TEE_ObjectType](#tee_objecttype) | Enumerates the types of object. |
| [TEE_Result_Value](#tee_result_value) | Enumerates the result codes used in the TEEKit APIs. |
| [TEE_LoginMethod](#tee_loginmethod) | Login type definitions |

### Macro

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

### Function

| Name | Description |
| -- | -- |
| [static inline bool check_param_type(uint32_t param_to_check, uint32_t valid0, uint32_t valid1, uint32_t valid2, uint32_t valid3)](#check_param_type) | Checks parameter types. |

### Variable

| Name | Description |
| -- | -- |
| int *tee_mutex_handle | Defines the tee mutex handle.<br>**Since**: 20 |
| uint32_t TEE_Result | Defines the return values.<br>**Since**: 20 |
| TEE_Result TEEC_Result | Defines the return values.<br>**Since**: 20 |
| uint32_t TEE_TASessionHandle | Defines the handle of TA session.<br>**Since**: 20 |

## Enum type description

### TEE_ParamType

```c
enum TEE_ParamType
```

**Description**

Enumerates the types of the TEE parameter.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_PARAM_TYPE_NONE             = 0x0 | Represents no parameter type. |
| TEE_PARAM_TYPE_VALUE_INPUT      = 0x1 | Represents a value input type. |
| TEE_PARAM_TYPE_VALUE_OUTPUT     = 0x2 | Represents a value output type. |
| TEE_PARAM_TYPE_VALUE_INOUT      = 0x3 | Represents a value inout type. |
| TEE_PARAM_TYPE_MEMREF_INPUT     = 0x5 | Represents a memory reference input type. |
| TEE_PARAM_TYPE_MEMREF_OUTPUT    = 0x6 | Represents a memory reference output type. |
| TEE_PARAM_TYPE_MEMREF_INOUT     = 0x7 | Represents a memory reference inout type. |
| TEE_PARAM_TYPE_ION_INPUT        = 0x8 | Represents an ION input type. |
| TEE_PARAM_TYPE_ION_SGLIST_INPUT = 0x9 | Represents an ION single list input type. |
| TEE_PARAM_TYPE_MEMREF_SHARED_INOUT = 0xa | Represents a shared memory reference inout type. |
| TEE_PARAM_TYPE_RESMEM_INPUT        = 0xc | Represents a resource memory input type. |
| TEE_PARAM_TYPE_RESMEM_OUTPUT       = 0xd | Represents a resource memory output type. |
| TEE_PARAM_TYPE_RESMEM_INOUT        = 0xe | Represents a resource memory inout type. |

### TEE_ObjectAttribute

```c
enum TEE_ObjectAttribute
```

**Description**

Enumerates the types of object attribute.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_ATTR_SECRET_VALUE          = 0xC0000000 | Secret value attribute. |
| TEE_ATTR_RSA_MODULUS           = 0xD0000130 | RSA modulus attribute. |
| TEE_ATTR_RSA_PUBLIC_EXPONENT   = 0xD0000230 | RSA public exponent attribute. |
| TEE_ATTR_RSA_PRIVATE_EXPONENT  = 0xC0000330 | RSA private exponent attribute. |
| TEE_ATTR_RSA_PRIME1            = 0xC0000430 | RSA prime1 attribute. |
| TEE_ATTR_RSA_PRIME2            = 0xC0000530 | RSA prime2 attribute. |
| TEE_ATTR_RSA_EXPONENT1         = 0xC0000630 | RSA exponent1 attribute. |
| TEE_ATTR_RSA_EXPONENT2         = 0xC0000730 | RSA exponent2 attribute. |
| TEE_ATTR_RSA_COEFFICIENT       = 0xC0000830 | RSA coefficient attribute. |
| TEE_ATTR_RSA_MGF1_HASH         = 0xF0000830 | RSA MGF1 hash attribute. |
| TEE_ATTR_DSA_PRIME             = 0xD0001031 | DSA prime attribute. |
| TEE_ATTR_DSA_SUBPRIME          = 0xD0001131 | DSA subprime attribute. |
| TEE_ATTR_DSA_BASE              = 0xD0001231 | DSA base attribute. |
| TEE_ATTR_DSA_PUBLIC_VALUE      = 0xD0000131 | DSA public value attribute. |
| TEE_ATTR_DSA_PRIVATE_VALUE     = 0xC0000231 | DSA private value attribute. |
| TEE_ATTR_DH_PRIME              = 0xD0001032 | DH prime attribute. |
| TEE_ATTR_DH_SUBPRIME           = 0xD0001132 | DH subprime attribute. |
| TEE_ATTR_DH_BASE               = 0xD0001232 | DH base attribute. |
| TEE_ATTR_DH_X_BITS             = 0xF0001332 | DH X bits attribute. |
| TEE_ATTR_DH_PUBLIC_VALUE       = 0xD0000132 | DH public value attribute. |
| TEE_ATTR_DH_PRIVATE_VALUE      = 0xC0000232 | DH private value attribute. |
| TEE_ATTR_RSA_OAEP_LABEL        = 0xD0000930 | RSA OAEP label attribute. |
| TEE_ATTR_RSA_PSS_SALT_LENGTH   = 0xF0000A30 | RSA PSS salt length attribute. |
| TEE_ATTR_ECC_PUBLIC_VALUE_X    = 0xD0000141 | ECC public value X attribute. |
| TEE_ATTR_ECC_PUBLIC_VALUE_Y    = 0xD0000241 | ECC public value Y attribute. |
| TEE_ATTR_ECC_PRIVATE_VALUE     = 0xC0000341 | ECC private value attribute. |
| TEE_ATTR_ECC_CURVE             = 0xF0000441 | ECC curve attribute. |
| TEE_ATTR_ED25519_CTX           = 0xD0000643 | ED25519 context attribute. |
| TEE_ATTR_ED25519_PUBLIC_VALUE  = 0xD0000743 | ED25519 public value attribute. |
| TEE_ATTR_ED25519_PRIVATE_VALUE = 0xC0000843 | ED25519 private value attribute. |
| TEE_ATTR_ED25519_PH            = 0xF0000543 | ED25519 PH attribute. |
| TEE_ATTR_X25519_PUBLIC_VALUE   = 0xD0000944 | X25519 public value attribute. |
| TEE_ATTR_X25519_PRIVATE_VALUE  = 0xC0000A44 | X25519 private value attribute. |
| TEE_ATTR_PBKDF2_HMAC_PASSWORD  = 0xD0000133 | PBKDF2 HMAC password attribute. |
| TEE_ATTR_PBKDF2_HMAC_SALT      = 0xD0000134 | PBKDF2 HMAC salt attribute. |
| TEE_ATTR_PRF_LABEL             = 0xD0000136 | PRF label attribute. |
| TEE_ATTR_PRF_SEED              = 0xD0000137 | PRF seed attribute. |
| TEE_ATTR_PRF_HASH_ALGORITHM    = 0xF0000138 | PRF hash algorithm attribute. |
| TEE_ATTR_HKDF_SALT             = 0xD0000946 | HKDF salt attribute. |
| TEE_ATTR_HKDF_INFO             = 0xD0000A46 | HKDF info attribute. |
| TEE_ATTR_PBKDF2_HMAC_DIGEST    = 0xF0000135 | PBKDF2 HMAC digest attribute. |
| TEE_ATTR_HKDF_HASH_ALGORITHM   = 0xF0000B46 | HKDF hash algorithm attribute. |
| TEE_ATTR_KDF_KEY_SIZE          = 0xF0000C46 | KDF key size attribute. |

### TEE_ObjectType

```c
enum TEE_ObjectType
```

**Description**

Enumerates the types of object.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_TYPE_AES                = 0xA0000010 | AES object type. |
| TEE_TYPE_DES                = 0xA0000011 | DES object type. |
| TEE_TYPE_DES3               = 0xA0000013 | DES3 object type. |
| TEE_TYPE_HMAC_MD5           = 0xA0000001 | HMAC MD5 object type. |
| TEE_TYPE_HMAC_SHA1          = 0xA0000002 | HMAC SHA1 object type. |
| TEE_TYPE_HMAC_SHA224        = 0xA0000003 | HMAC SHA224 object type. |
| TEE_TYPE_HMAC_SHA256        = 0xA0000004 | HMAC SHA256 object type. |
| TEE_TYPE_HMAC_SHA384        = 0xA0000005 | HMAC SHA384 object type. |
| TEE_TYPE_HMAC_SHA512        = 0xA0000006 | HMAC SHA512 object type. |
| TEE_TYPE_RSA_PUBLIC_KEY     = 0xA0000030 | RSA public key object type. |
| TEE_TYPE_RSA_KEYPAIR        = 0xA1000030 | RSA keypair object type. |
| TEE_TYPE_DSA_PUBLIC_KEY     = 0xA0000031 | DSA public key object type. |
| TEE_TYPE_DSA_KEYPAIR        = 0xA1000031 | DSA keypair object type. |
| TEE_TYPE_DH_KEYPAIR         = 0xA1000032 | DH keypair object type. |
| TEE_TYPE_GENERIC_SECRET     = 0xA0000000 | Generic secret object type. |
| TEE_TYPE_DATA               = 0xA1000033 | Data object type. |
| TEE_TYPE_DATA_GP1_1         = 0xA00000BF | Data GP1.1 object type. |
| TEE_TYPE_ECDSA_PUBLIC_KEY   = 0xA0000041 | ECDSA public key object type. |
| TEE_TYPE_ECDSA_KEYPAIR      = 0xA1000041 | ECDSA keypair object type. |
| TEE_TYPE_ECDH_PUBLIC_KEY    = 0xA0000042 | ECDH public key object type. |
| TEE_TYPE_ECDH_KEYPAIR       = 0xA1000042 | ECDH keypair object type. |
| TEE_TYPE_ED25519_PUBLIC_KEY = 0xA0000043 | ED25519 public key object type. |
| TEE_TYPE_ED25519_KEYPAIR    = 0xA1000043 | ED25519 keypair object type. |
| TEE_TYPE_X25519_PUBLIC_KEY  = 0xA0000044 | X25519 public key object type. |
| TEE_TYPE_X25519_KEYPAIR     = 0xA1000044 | X25519 keypair object type. |
| TEE_TYPE_SM2_DSA_PUBLIC_KEY = 0xA0000045 | SM2 DSA public key object type. |
| TEE_TYPE_SM2_DSA_KEYPAIR    = 0xA1000045 | SM2 DSA keypair object type. |
| TEE_TYPE_SM2_KEP_PUBLIC_KEY = 0xA0000046 | SM2 KEP public key object type. |
| TEE_TYPE_SM2_KEP_KEYPAIR    = 0xA1000046 | SM2 KEP keypair object type. |
| TEE_TYPE_SM2_PKE_PUBLIC_KEY = 0xA0000047 | SM2 PKE public key object type. |
| TEE_TYPE_SM2_PKE_KEYPAIR    = 0xA1000047 | SM2 PKE keypair object type. |
| TEE_TYPE_HMAC_SM3           = 0xA0000007 | HMAC SM3 object type. |
| TEE_TYPE_SM4                = 0xA0000014 | SM4 object type. |
| TEE_TYPE_HKDF               = 0xA000004A | HKDF object type. |
| TEE_TYPE_SIP_HASH           = 0xF0000002 | SIP Hash object type. |
| TEE_TYPE_PBKDF2_HMAC        = 0xF0000004 | PBKDF2 HMAC object type. |
| TEE_TYPE_PRF                = 0xF0000005 | PRF object type. |
| TEE_TYPE_CORRUPTED_OBJECT = 0xA00000BE | Corrupted object type. |

### TEE_Result_Value

```c
enum TEE_Result_Value
```

**Description**

Enumerates the result codes used in the TEEKit APIs.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_SUCCESS                        = 0x00000000 | The operation is successful. |
| TEE_ERROR_INVALID_CMD              = 0x00000001 | The command is invalid. |
| TEE_ERROR_SERVICE_NOT_EXIST        = 0x00000002 | The service does not exist. |
| TEE_ERROR_SESSION_NOT_EXIST        = 0x00000003 | The session does not exist. |
| TEE_ERROR_SESSION_MAXIMUM          = 0x00000004 | The number of sessions exceeds the limit. |
| TEE_ERROR_REGISTER_EXIST_SERVICE   = 0x00000005 | The service has been already registered. |
| TEE_ERROR_TARGET_DEAD_FATAL        = 0x00000006 | An internal error occurs. |
| TEE_ERROR_READ_DATA                = 0x00000007 | Failed to read data. |
| TEE_ERROR_WRITE_DATA               = 0x00000008 | Failed to write data. |
| TEE_ERROR_TRUNCATE_OBJECT          = 0x00000009 | Failed to truncate data. |
| TEE_ERROR_SEEK_DATA                = 0x0000000A | Failed to seek data. |
| TEE_ERROR_SYNC_DATA                = 0x0000000B | Failed to synchronize data. |
| TEE_ERROR_RENAME_OBJECT            = 0x0000000C | Failed to rename the file. |
| TEE_ERROR_TRUSTED_APP_LOAD_ERROR   = 0x0000000D | An error occurs when the TA is loaded. |
| TEE_ERROR_OTRP_LOAD_NOT_MATCHED    = 0x80000100 | TA type is inconsistent with the loading mode. |
| TEE_ERROR_OTRP_LOAD_EXCEED         = 0x80000101 | The not open session's otrp service num exceeds. |
| TEE_ERROR_OTRP_ACCESS_DENIED       = 0x80000102 | UUID of load cmd is not inconsistent with the sec file. |
| TEE_ERROR_OTRP_SERVICE_AGED        = 0x80000103 | Otrp service is aged. |
| TEE_ERROR_STORAGE_EIO              = 0x80001001 | An I/O error occurs when data is stored. |
| TEE_ERROR_STORAGE_EAGAIN           = 0x80001002 | The storage section is unavailable. |
| TEE_ERROR_STORAGE_ENOTDIR          = 0x80001003 | The operation target is not a directory. |
| TEE_ERROR_STORAGE_EISDIR           = 0x80001004 | This operation cannot be performed on a directory. |
| TEE_ERROR_STORAGE_ENFILE           = 0x80001005 | The number of opened files exceeds the limit in system. |
| TEE_ERROR_STORAGE_EMFILE           = 0x80001006 | The number of files opened for the process exceeds the limit. |
| TEE_ERROR_STORAGE_EROFS            = 0x80001007 | The storage section is read only. |
| TEE_ERROR_STORAGE_EROLLBACK        = 0x80001008 | The file object has been rolled back. |
| TEE_ERROR_STORAGE_PATH_WRONG       = 0x8000100A | The file path is not correct. |
| TEE_ERROR_MSG_QUEUE_OVERFLOW       = 0x8000100B | The service message queue overflows. |
| TEE_ERROR_SUBTHREAD_ACCESS         = 0x8000100C | The subthread created by TA cannot access the service |
| TEE_ERROR_ORIGIN_PARTITION_INACTIVE = 0x8000100D | Enable backup feature, original partition is inactive |
| TEE_ERROR_BACKUP_PARTITION_INACTIVE = 0x8000100E | Enable backup feature, backup partition is inactive |
| TEE_ERROR_CORRUPT_OBJECT           = 0xF0100001 | The file object is corrupted. |
| TEE_ERROR_STORAGE_NOT_AVAILABLE    = 0xF0100003 | The storage section is unavailable. |
| TEE_ERROR_CIPHERTEXT_INVALID       = 0xF0100006 | The cipher text is incorrect. |
| TEE_ISOCKET_ERROR_PROTOCOL         = 0xF1007001 | Protocol error in socket connection. |
| TEE_ISOCKET_ERROR_REMOTE_CLOSED    = 0xF1007002 | The socket is closed by the remote end. |
| TEE_ISOCKET_ERROR_TIMEOUT          = 0xF1007003 | The socket connection timed out. |
| TEE_ISOCKET_ERROR_OUT_OF_RESOURCES = 0xF1007004 | There is no resource available for the socket connection. |
| TEE_ISOCKET_ERROR_LARGE_BUFFER     = 0xF1007005 | The buffer is too large for the socket connection. |
| TEE_ISOCKET_WARNING_PROTOCOL       = 0xF1007006 | A warning is given in the socket connection. |
| TEE_ERROR_GENERIC                  = 0xFFFF0000 | Generic error. |
| TEE_ERROR_ACCESS_DENIED            = 0xFFFF0001 | The access is denied. |
| TEE_ERROR_CANCEL                   = 0xFFFF0002 | The operation has been canceled. |
| TEE_ERROR_ACCESS_CONFLICT          = 0xFFFF0003 | An access conflict occurs. |
| TEE_ERROR_EXCESS_DATA              = 0xFFFF0004 | The data size exceeds the maximum. |
| TEE_ERROR_BAD_FORMAT               = 0xFFFF0005 | Incorrect data format. |
| TEE_ERROR_BAD_PARAMETERS           = 0xFFFF0006 | Incorrect parameters. |
| TEE_ERROR_BAD_STATE                = 0xFFFF0007 | The current state does not support the operation. |
| TEE_ERROR_ITEM_NOT_FOUND           = 0xFFFF0008 | Failed to find the target item. |
| TEE_ERROR_NOT_IMPLEMENTED          = 0xFFFF0009 | The API is not implemented. |
| TEE_ERROR_NOT_SUPPORTED            = 0xFFFF000A | The API is not supported. |
| TEE_ERROR_NO_DATA                  = 0xFFFF000B | There is no data available for this operation. |
| TEE_ERROR_OUT_OF_MEMORY            = 0xFFFF000C | There is no memory available for this operation. |
| TEE_ERROR_BUSY                     = 0xFFFF000D | The system does not respond to this operation. |
| TEE_ERROR_COMMUNICATION            = 0xFFFF000E | Failed to communicate with the target. |
| TEE_ERROR_SECURITY                 = 0xFFFF000F | A security error occurs. |
| TEE_ERROR_SHORT_BUFFER             = 0xFFFF0010 | The buffer is insufficient for this operation. |
| TEE_ERROR_EXTERNAL_CANCEL          = 0xFFFF0011 | The operation has been canceled. |
| TEE_PENDING                        = 0xFFFF2000 | The service is in the pending state (asynchronous state). |
| TEE_PENDING2                       = 0xFFFF2001 | The service is in the pending state(). |
| TEE_PENDING3                       = 0xFFFF2002 | Reserved. |
| TEE_ERROR_TIMEOUT                  = 0xFFFF3001 | The operation timed out. |
| TEE_ERROR_OVERFLOW                 = 0xFFFF300f | Overflow occurs. |
| TEE_ERROR_TARGET_DEAD              = 0xFFFF3024 | The TA is crashed. |
| TEE_ERROR_STORAGE_NO_SPACE         = 0xFFFF3041 | There is no enough space to store data. |
| TEE_ERROR_MAC_INVALID              = 0xFFFF3071 | The MAC operation failed. |
| TEE_ERROR_SIGNATURE_INVALID        = 0xFFFF3072 | The signature verification failed. |
| TEE_ERROR_CERTIFICATE_INVALID      = 0xFFFF3073 | Thecertificate verify failed. |
| TEE_CLIENT_INTR                    = 0xFFFF4000 | Interrupted by CFC. Broken control flow is detected. |
| TEE_ERROR_TIME_NOT_SET             = 0xFFFF5000 | Time is not set. |
| TEE_ERROR_TIME_NEEDS_RESET         = 0xFFFF5001 | Time needs to be reset. |
| TEE_FAIL                           = 0xFFFF5002 | System error. |
| TEE_ERROR_TIMER                    = 0xFFFF6000 | Base value of the timer error code. |
| TEE_ERROR_TIMER_CREATE_FAILED      = 0xFFFF6001 | Failed to create the timer. |
| TEE_ERROR_TIMER_DESTROY_FAILED     = 0xFFFF6002 | Failed to destroy the timer. |
| TEE_ERROR_TIMER_NOT_FOUND          = 0xFFFF6003 | The timer is not found. |
| TEE_ERROR_RPMB_BASE                = 0xFFFF7000 | Base value of RPMB error codes. |
| TEE_ERROR_RPMB_GENERIC             = 0xFFFF7001 | Generic error of RPMB operations. |
| TEE_ERROR_RPMB_MAC_FAIL            = 0xFFFF7002 | Verify MAC failed in RPMB operations. |
| TEE_ERROR_RPMB_COUNTER_FAIL        = 0xFFFF7003 | Invalid counter in RPMB operations. |
| TEE_ERROR_RPMB_ADDR_FAIL           = 0xFFFF7004 | Address check failed in RPMB operations. |
| TEE_ERROR_RPMB_WRITE_FAIL          = 0xFFFF7005 | Fail to write data to RPMB. |
| TEE_ERROR_RPMB_READ_FAIL           = 0xFFFF7006 | Fail to read data in RPMB. |
| TEE_ERROR_RPMB_KEY_NOT_PROGRAM     = 0xFFFF7007 | Key is not provisioned in RPMB. |
| TEE_ERROR_RPMB_RESP_UNEXPECT_MSGTYPE = 0xFFFF7100 | Incorrect message type in RPMB response. |
| TEE_ERROR_RPMB_RESP_UNEXPECT_BLKCNT = 0xFFFF7101 | Incorrect message data block count in RPMB response. |
| TEE_ERROR_RPMB_RESP_UNEXPECT_BLKIDX = 0xFFFF7102 | Incorrect message data block count in RPMB response. |
| TEE_ERROR_RPMB_RESP_UNEXPECT_WRCNT = 0xFFFF7103 | Incorrect message data counter in RPMB response. |
| TEE_ERROR_RPMB_RESP_UNEXPECT_NONCE = 0xFFFF7104 | Incorrect message data nonce in RPMB response. |
| TEE_ERROR_RPMB_RESP_UNEXPECT_MAC   = 0xFFFF7105 | Incorrect message data MAC in RPMB response. |
| TEE_ERROR_RPMB_FILE_NOT_FOUND      = 0xFFFF7106 | The file is not found in RPMB. |
| TEE_ERROR_RPMB_NOSPC               = 0xFFFF7107 | No spece left for RPMB operations. |
| TEE_ERROR_RPMB_SPC_CONFLICT        = 0xFFFF7108 | Exceeds max space of RPMB for this TA. |
| TEE_ERROR_RPMB_NOT_AVAILABLE       = 0xFFFF7109 | RPMB service not ready. |
| TEE_ERROR_RPMB_DAMAGED             = 0xFFFF710A | RPMB partition is damaged. |
| TEE_ERROR_TUI_IN_USE               = 0xFFFF7110 | TUI is being used. |
| TEE_ERROR_TUI_SWITCH_CHANNAL       = 0xFFFF7111 | Incorrect message switch channal in TUI response. |
| TEE_ERROR_TUI_CFG_DRIVER           = 0xFFFF7112 | Incorrect message configurator driver in TUI response. |
| TEE_ERROR_TUI_INVALID_EVENT        = 0xFFFF7113 | Invalid TUI event. |
| TEE_ERROR_TUI_POLL_EVENT           = 0xFFFF7114 | Incorrect message polling events in TUI response. |
| TEE_ERROR_TUI_CANCELED             = 0xFFFF7115 | TUI is cancelled. |
| TEE_ERROR_TUI_EXIT                 = 0xFFFF7116 | TUI is exited. |
| TEE_ERROR_TUI_NOT_AVAILABLE        = 0xFFFF7117 | TUI unavailable. |
| TEE_ERROR_SEC_FLASH_NOT_AVAILABLE  = 0xFFFF7118 | sec flash is not available. |
| TEE_ERROR_SESRV_NOT_AVAILABLE      = 0xFFFF7119 | SE service has crashed or not enable. |
| TEE_ERROR_BIOSRV_NOT_AVAILABLE     = 0xFFFF711A | The BIO service is not available. |
| TEE_ERROR_ROTSRV_NOT_AVAILABLE     = 0xFFFF711B | The ROT service is not available. |
| TEE_ERROR_ARTSRV_NOT_AVAILABLE     = 0xFFFF711C | The TA Anti-Rollback service is not available. |
| TEE_ERROR_HSMSRV_NOT_AVAILABLE     = 0xFFFF711D | The HSM service is not available. |
| TEE_ERROR_VRPMB_AGENT_FAIL              = 0xFFFF7200 | REE vrpmb agent check magic failed, maybe cache fail. |
| TEE_ERROR_VRPMB_RW_FAIL                 = 0xFFFF7201 | REE ssd driver rw failed. |
| TEE_ERROR_VRPMB_SUPER_MAC_FAILED        = 0xFFFF7202 | vrpmb check super block mac failed. |
| TEE_ERROR_VRPMB_WRITE_REJECT            = 0xFFFF7203 | reject write to vrpmb. |
| TEE_ERROR_ANTIROOT_RSP_FAIL        = 0xFFFF9110 | Failed to verify AntiRoot response. |
| TEE_ERROR_ANTIROOT_INVOKE_ERROR    = 0xFFFF9111 | AntiRoot error in invokeCmd(). |
| TEE_ERROR_AUDIT_FAIL               = 0xFFFF9112 | Audit failed. |
| TEE_FAIL2                          = 0xFFFF9113 | Unused. |
| TEE_ERROR_IPC_OVERFLOW             = 0xFFFF9114 | IPC Channel overflow error. |
| TEE_ERROR_APM                           = 0xFFFF9115 | APM error. |
| TEE_ERROR_CA_AUTHFILE_NOT_EXIST         = 0xFFFF9116 | CA auth file not exist. |
| TEE_ERROR_CA_CALLER_ACCESS_DENIED       = 0xFFFF9117 | CA caller access is denied. |
| TEE_ERROR_INVALID_TA_FORMAT             = 0xFFFF9118 | Invalid TA format. |
| TEE_DSTB_LOCAL_SIGN_REPORT_ERROR        = 0xFFFF9200 | local dstb service sign report error. |
| TEE_DSTB_REMOTE_SIGN_REPORT_ERROR       = 0xFFFF9201 | remote dstb service sign report error. |
| TEE_DSTB_LOCAL_REPORT_CERT_CHAIN_ERROR  = 0xFFFF9202 | local dstb service report cert chain error. |
| TEE_DSTB_REMOTE_REPORT_CERT_CHAIN_ERROR = 0xFFFF9203 | remote dstb service report cert chain error. |
| TEE_DSTB_LOCAL_REPORT_VERIFY_ERROR      = 0xFFFF9204 | local dstb service verify report error. |
| TEE_DSTB_REMOTE_REPORT_VERIFY_ERROR     = 0xFFFF9205 | remote dstb service verify report error. |
| TEE_DSTB_LOCAL_CERT_CHAIN_VERIFY_ERROR  = 0xFFFF9206 | local dstb service verify cert chain error. |
| TEE_DSTB_REMOTE_CERT_CHAIN_VERIFY_ERROR = 0xFFFF9207 | remote dstb service verify cert chain error. |
| TEE_DSTB_LOCAL_INVALID_KEY_VERSION_ERROR = 0xFFFF9208 | local dstb service key version error. |
| TEE_DSTB_REMOTE_INVALID_KEY_VERSION_ERROR = 0xFFFF9209 | remote dstb service key version error. |
| TEE_DSTB_INVALID_UDID                   = 0xFFFF920A | udid is invalid. |
| TEE_DSTB_DERIVE_KEY_ERROR               = 0xFFFF920B | dstb service derive key error. |
| TEE_DSTB_REE_SRV_ERROR                  = 0xFFFF920C | dstb service of ree error. |
| TEE_ERROR_TA_ANTI_ROLLBACK              = 0xFFFF920D | TA load fail becauce of anti-rollback. |
| TEE_ERROR_RETRY_OPEN_SESSION            = 0xFFFF920E | open_session fail becauce of race with close_session. |
| TEE_ERROR_TA_CTRL_FILE_LOAD_FAIL        = 0xFFFF920F | TA control file load fail. |
| TEE_ERROR_TA_CTRL_FILE_VERIFY_FAIL      = 0xFFFF9210 | TA control file verify fail. |
| TEE_ERROR_TA_VER_BELOW_CONTROL_VER      = 0xFFFF9211 | TA version is below the version in control file. |
| TEE_DSTB_LOCAL_CERT_VALIDITY_ERROR      = 0xFFFF9212 | Local dstb cert chain validity check failed. |
| TEE_DSTB_REMOTE_CERT_VALIDITY_ERROR     = 0xFFFF9213 | Remote dstb cert chain validity check failed. |

### TEE_LoginMethod

```c
enum TEE_LoginMethod
```

**Description**

Login type definitions

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_LOGIN_PUBLIC = 0x0 | Public login method. |
| TEE_LOGIN_USER | User login method. |
| TEE_LOGIN_GROUP | Group login method. |
| TEE_LOGIN_APPLICATION = 0x4 | Application login method. |
| TEE_LOGIN_USER_APPLICATION = 0x5 | User-application login method. |
| TEE_LOGIN_GROUP_APPLICATION = 0x6 | Group-application login method. |
| TEE_LOGIN_IDENTIFY = 0x7 | Customized login type. |
| TEEK_LOGIN_IDENTIFY = 0x80000001 | Login type from the Linux kernel. |


## Function description

### check_param_type()

```c
static inline bool check_param_type(uint32_t param_to_check, uint32_t valid0, uint32_t valid1, uint32_t valid2, uint32_t valid3)
{return (TEE_PARAM_TYPES(valid0, valid1, valid2, valid3) == param_to_check)
}
```

**Description**

Checks parameter types.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t param_to_check | Indicates the expected parameter values. |
| uint32_t valid0 | Indicates the first parameter type to check. |
| uint32_t valid1 | Indicates the second parameter type to check. |
| uint32_t valid2 | Indicates the third parameter type to check. |
| uint32_t valid3 | Indicates the fourth parameter type to check. |

**Returns**:

| Type | Description |
| -- | -- |
| static inline bool | Returns <b>true</b> if the parameter types are correct.          Returns <b>false</b> otherwise. |


