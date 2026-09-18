# CMErrorCode

Enumerates the error codes used in the certificate management APIs.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_NO_PERMISSION

```TypeScript
CM_ERROR_NO_PERMISSION = 201
```

The application does not have the permission to call the API.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_INVALID_PARAMS

```TypeScript
CM_ERROR_INVALID_PARAMS = 401
```

Invalid input parameter is found.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_GENERIC

```TypeScript
CM_ERROR_GENERIC = 17500001
```

An internal error occurs when the interface is called.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_NO_FOUND

```TypeScript
CM_ERROR_NO_FOUND = 17500002
```

The certificate or credential does not exist.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_INCORRECT_FORMAT

```TypeScript
CM_ERROR_INCORRECT_FORMAT = 17500003
```

The certificate or credential is in invalid format.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_MAX_CERT_COUNT_REACHED

```TypeScript
CM_ERROR_MAX_CERT_COUNT_REACHED = 17500004
```

The number of certificates or credentials has reached the limit.

**Since:** 12

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_NO_AUTHORIZATION

```TypeScript
CM_ERROR_NO_AUTHORIZATION = 17500005
```

The application has not obtained user authorization.

**Since:** 12

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_DEVICE_ENTER_ADVSECMODE

```TypeScript
CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007
```

The device enters the advanced security mode. In this mode, CA certificate installation is restricted.

**Since:** 18

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_STORE_PATH_NOT_SUPPORTED

```TypeScript
CM_ERROR_STORE_PATH_NOT_SUPPORTED = 17500009
```

The device does not support the specified certificate storage path.

**Since:** 20

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_ACCESS_UKEY_SERVICE_FAILED

```TypeScript
CM_ERROR_ACCESS_UKEY_SERVICE_FAILED = 17500010
```

The USB Key service fails to be accessed.

**Since:** 22

**System capability:** SystemCapability.Security.CertificateManager

## CM_ERROR_PARAMETER_VALIDATION_FAILED

```TypeScript
CM_ERROR_PARAMETER_VALIDATION_FAILED = 17500011
```

The input parameter validation fails.

For example, the parameter format is incorrect or the parameter range is invalid.

**Since:** 22

**System capability:** SystemCapability.Security.CertificateManager
