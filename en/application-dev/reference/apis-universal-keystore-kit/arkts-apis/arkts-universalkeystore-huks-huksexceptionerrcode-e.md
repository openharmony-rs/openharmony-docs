# HuksExceptionErrCode

Enumerates error codes and error details.

For details about the error codes, see [Universal Error Codes](../../../reference/errorcode-universal.md) and [HUKS Error Codes](../../../reference/apis-universal-keystore-kit/errorcode-huks.md).

**Since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_PERMISSION_FAIL

```TypeScript
HUKS_ERR_CODE_PERMISSION_FAIL = 201
```

Permission verification failed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_NOT_SYSTEM_APP

```TypeScript
HUKS_ERR_CODE_NOT_SYSTEM_APP = 202
```

The caller is not a system application and cannot call the system API.

**Since:** 12

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_ILLEGAL_ARGUMENT

```TypeScript
HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401
```

Invalid parameters are detected. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_NOT_SUPPORTED_API

```TypeScript
HUKS_ERR_CODE_NOT_SUPPORTED_API = 801
```

The API is not supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED

```TypeScript
HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001
```

The feature is not supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT

```TypeScript
HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002
```

Key algorithm parameters are missing.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT

```TypeScript
HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003
```

Invalid key algorithm parameters are detected.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_FILE_OPERATION_FAIL

```TypeScript
HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004
```

The file operation failed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_COMMUNICATION_FAIL

```TypeScript
HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005
```

The communication failed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_CRYPTO_FAIL

```TypeScript
HUKS_ERR_CODE_CRYPTO_FAIL = 12000006
```

Failed to operate the algorithm library.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED

```TypeScript
HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007
```

Failed to access the key because the key has expired.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED

```TypeScript
HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008
```

Failed to access the key because the authentication has failed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_KEY_AUTH_TIME_OUT

```TypeScript
HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009
```

Key access timed out.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_SESSION_LIMIT

```TypeScript
HUKS_ERR_CODE_SESSION_LIMIT = 12000010
```

The number of key operation sessions has reached the limit.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_ITEM_NOT_EXIST

```TypeScript
HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011
```

The target object does not exist.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_EXTERNAL_ERROR

```TypeScript
HUKS_ERR_CODE_EXTERNAL_ERROR = 12000012
```

An external error occurs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST

```TypeScript
HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013
```

The credential does not exist.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_INSUFFICIENT_MEMORY

```TypeScript
HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014
```

The memory is insufficient.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_CALL_SERVICE_FAILED

```TypeScript
HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015
```

Failed to call other system services.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET

```TypeScript
HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016
```

The required lock screen password is not set.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_ERR_CODE_KEY_ALREADY_EXIST

```TypeScript
HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017
```

A key with the same name already exists.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_INVALID_ARGUMENT

```TypeScript
HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018
```

The argument is invalid.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_ITEM_EXISTS

```TypeScript
HUKS_ERR_CODE_ITEM_EXISTS = 12000019
```

A provider with the same name has been registered.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_EXTERNAL_MODULE

```TypeScript
HUKS_ERR_CODE_EXTERNAL_MODULE = 12000020
```

The external module on which this API depends returns an error.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_PIN_LOCKED

```TypeScript
HUKS_ERR_CODE_PIN_LOCKED = 12000021
```

The UKey PIN is locked.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_ERR_CODE_PIN_INCORRECT

```TypeScript
HUKS_ERR_CODE_PIN_INCORRECT = 12000022
```

The UKey PIN is incorrect.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_ERR_CODE_PIN_NO_AUTH

```TypeScript
HUKS_ERR_CODE_PIN_NO_AUTH = 12000023
```

The UKey PIN is not authenticated.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_ERR_CODE_BUSY

```TypeScript
HUKS_ERR_CODE_BUSY = 12000024
```

The device or resource is busy.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_EXCEED_LIMIT

```TypeScript
HUKS_ERR_CODE_EXCEED_LIMIT = 12000025
```

The resource limit is exceeded.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_SE_FAULT

```TypeScript
HUKS_ERR_CODE_SE_FAULT = 12000026
```

The secure element is faulty.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_NETWORK_UNAVAILABLE

```TypeScript
HUKS_ERR_CODE_NETWORK_UNAVAILABLE = 12000027
```

The network is unavailable.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Extension
