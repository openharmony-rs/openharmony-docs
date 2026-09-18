# net_ssl_c.h

## Overview

Defines C APIs for the SSL/TLS certificate chain verification module.

**Library**: libnet_ssl.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [uint32_t OH_NetStack_CertVerification(const struct NetStack_CertBlob *cert, const struct NetStack_CertBlob *caCert)](#oh_netstack_certverification) | Provides certificate chain verification APIs for external systems. |
| [int32_t OH_NetStack_GetPinSetForHostName(const char *hostname, NetStack_CertificatePinning *pin)](#oh_netstack_getpinsetforhostname) | Obtains the certificate lock information. |
| [int32_t OH_NetStack_GetCertificatesForHostName(const char *hostname, NetStack_Certificates *certs)](#oh_netstack_getcertificatesforhostname) | Obtains the certificate information. |
| [void OH_Netstack_DestroyCertificatesContent(NetStack_Certificates *certs)](#oh_netstack_destroycertificatescontent) | Releases the certificate content. |
| [int32_t OH_Netstack_IsCleartextPermitted(bool *isCleartextPermitted)](#oh_netstack_iscleartextpermitted) | Boolean value indicating whether plaintext HTTP is allowed. |
| [int32_t OH_Netstack_IsCleartextPermittedByHostName(const char *hostname, bool *isCleartextPermitted)](#oh_netstack_iscleartextpermittedbyhostname) | Boolean value indicating whether host name–based plaintext HTTP is allowed. |
| [int32_t OH_Netstack_IsCleartextCfgByComponent(const char *component, bool *componentCfg)](#oh_netstack_iscleartextcfgbycomponent) | Checks whether plaintext HTTP interception is enabled. |
| [uint32_t OH_NetStack_CreateAndVerifySortedCertChain(const struct NetStack_CertBlob *cert, size_t certCount, const struct NetStack_CertBlob *caCert, const char *hostname, struct NetStack_CertBlob **outSortedChain, size_t *outSortedCount)](#oh_netstack_createandverifysortedcertchain) | Creates and verifies a sorted certificate chain. |
| [void OH_NetStack_FreeCertChain(struct NetStack_CertBlob *certChain, size_t certCount)](#oh_netstack_freecertchain) | Frees the certificate chain allocated by OH_NetStack_CreateAndVerifySortedCertChain. |

## Function description

### OH_NetStack_CertVerification()

```c
uint32_t OH_NetStack_CertVerification(const struct NetStack_CertBlob *cert, const struct NetStack_CertBlob *caCert)
```

**Description**

Provides certificate chain verification APIs for external systems.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const struct NetStack_CertBlob *cert | Certificate to be verified. |
| const struct NetStack_CertBlob *caCert | Certificate specified by the user. If this parameter is left blank, the preset certificate is used for verification. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | 0: Success.      <br>2305001: Unknown error.      <br>2305002: Failed to obtain the issuer certificate.      <br>2305003: Failed to obtain the certificate revocation list (CRL).      <br>2305004: Failed to decrypt the certificate signature.      <br>2305005: Failed to decrypt the CRL signature.      <br>2305006: Failed to decode the issuer public key.      <br>2305007: Failed to sign the certificate.      <br>2305008: Failed to sign the CRL.      <br>2305009: Certificate not activated.      <br>2305010: Certificate expired.      <br>2305011: CRL not activated.      <br>2305012: CRL expired.      <br>2305023: Certificate revoked.      <br>2305024: Invalid certificate authority (CA).      <br>2305027: Untrusted certificate. |

### OH_NetStack_GetPinSetForHostName()

```c
int32_t OH_NetStack_GetPinSetForHostName(const char *hostname, NetStack_CertificatePinning *pin)
```

**Description**

Obtains the certificate lock information.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *hostname | Host name. |
| NetStack_CertificatePinning *pin | Defines the certificate lock information structure. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>401: Parameter error.      <br>2305999: Memory error. |

### OH_NetStack_GetCertificatesForHostName()

```c
int32_t OH_NetStack_GetCertificatesForHostName(const char *hostname, NetStack_Certificates *certs)
```

**Description**

Obtains the certificate information.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *hostname | Host name. |
| NetStack_Certificates *certs | Defines the certificate information structure. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>401: Parameter error.      <br>2305999: Memory error. |

### OH_Netstack_DestroyCertificatesContent()

```c
void OH_Netstack_DestroyCertificatesContent(NetStack_Certificates *certs)
```

**Description**

Releases the certificate content.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| NetStack_Certificates *certs | Represents the certificate information. |

### OH_Netstack_IsCleartextPermitted()

```c
int32_t OH_Netstack_IsCleartextPermitted(bool *isCleartextPermitted)
```

**Description**

Boolean value indicating whether plaintext HTTP is allowed.

**Required permission**: ohos.permission.INTERNET

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool *isCleartextPermitted | Boolean value indicating whether plaintext HTTP is allowed. The value **true** means that plaintext HTTP is allowed, and the value **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Permission denied.      <br>401: Parameter error. |

### OH_Netstack_IsCleartextPermittedByHostName()

```c
int32_t OH_Netstack_IsCleartextPermittedByHostName(const char *hostname, bool *isCleartextPermitted)
```

**Description**

Boolean value indicating whether host name–based plaintext HTTP is allowed.

**Required permission**: ohos.permission.INTERNET

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *hostname | Host name. |
| bool *isCleartextPermitted | Boolean value indicating whether host name–based plaintext HTTP is allowed. The value **<br>true** means that host name–based plaintext HTTP is allowed, and the value **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Permission denied.      <br>401: Parameter error. |

### OH_Netstack_IsCleartextCfgByComponent()

```c
int32_t OH_Netstack_IsCleartextCfgByComponent(const char *component, bool *componentCfg)
```

**Description**

Checks whether plaintext HTTP interception is enabled.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *component | Component name. The following components are supported: Network Kit and ArkWeb. |
| bool *componentCfg | Output parameter, which indicates whether plaintext HTTP interception is enabled. The value **<br>true** indicates that plaintext HTTP interception is enabled, and the value **false** indicates the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>2100001: Invalid parameter value. |

### OH_NetStack_CreateAndVerifySortedCertChain()

```c
uint32_t OH_NetStack_CreateAndVerifySortedCertChain(const struct NetStack_CertBlob *cert, size_t certCount, const struct NetStack_CertBlob *caCert, const char *hostname, struct NetStack_CertBlob **outSortedChain, size_t *outSortedCount)
```

**Description**

Creates and verifies a sorted certificate chain.

> **Note**:
>
> After use, you must call [OH_NetStack_FreeCertChain](capi-net-ssl-c-h.md#oh_netstack_freecertchain) to release the allocated memory pointed by outSortedChain. Failure to do so will cause memory leaks.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const struct NetStack_CertBlob *cert | Certificate chain to be verified. Cannot be NULL or empty. |
| size_t certCount | Certificate number of param cert. |
| const struct NetStack_CertBlob *caCert | CA certificate specified by the user. If NULL, the preset certificate is used. |
| const char *hostname | The expected server hostname. |
| struct NetStack_CertBlob **outSortedChain | Pointer to receive the sorted certificate chain. Can be NULL if the caller does not need the chain data. Valid only if return value is 0. Allocated memory must be freed using OH_NetStack_FreeCertChain. |
| size_t *outSortedCount | Pointer to receive the count of sorted certificates. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | 0 - success.          2305001 - Unspecified error.          2305002 - Unable to get issuer certificate.          2305004 - Unable to decrypt certificate signature.          2305006 - Unable to decode issuer public key.          2305007 - Certificate signature failure.          2305009 - Certificate is not yet valid.          2305010 - Certificate has expired.          2305024 - Invalid certificate authority (CA).          2305062 - Hostname verification failed.          2305027 - Certificate is untrusted. |

### OH_NetStack_FreeCertChain()

```c
void OH_NetStack_FreeCertChain(struct NetStack_CertBlob *certChain, size_t certCount)
```

**Description**

Frees the certificate chain allocated by OH_NetStack_CreateAndVerifySortedCertChain.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct NetStack_CertBlob *certChain | The certificate chain pointer received from outSortedChain. If NULL, this function does nothing. |
| size_t certCount | The number of certificates in the chain. |


