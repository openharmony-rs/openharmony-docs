# net_ssl_c.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=108aa11c2ceb50c68f8417aa3c60f1dcb55dabdd translatedAt=2026-09-23T01:18:19.680Z pushedAt=2026-09-24T06:00:14.101Z -->

## Overview

Defines data structures for the C APIs of the SSL/TLS certificate chain verification module.

**File to include**: <network/netstack/net_ssl/net_ssl_c.h>

**Library**: libnet_ssl.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [uint32_t OH_NetStack_CertVerification(const struct NetStack_CertBlob *cert, const struct NetStack_CertBlob *caCert)](#oh_netstack_certverification) | Verifies the exposed certificate chain. |
| [int32_t OH_NetStack_GetPinSetForHostName(const char *hostname, NetStack_CertificatePinning *pin)](#oh_netstack_getpinsetforhostname) | Obtains the certificate lock information.|
| [int32_t OH_NetStack_GetCertificatesForHostName(const char *hostname, NetStack_Certificates *certs)](#oh_netstack_getcertificatesforhostname) | Obtains certificate information.|
| [void OH_Netstack_DestroyCertificatesContent(NetStack_Certificates *certs)](#oh_netstack_destroycertificatescontent) | Releases the certificate content.|
| [int32_t OH_Netstack_IsCleartextPermitted(bool *isCleartextPermitted)](#oh_netstack_iscleartextpermitted) | Checks whether plaintext HTTP is allowed overall.|
| [int32_t OH_Netstack_IsCleartextPermittedByHostName(const char *hostname, bool *isCleartextPermitted)](#oh_netstack_iscleartextpermittedbyhostname) | Checks whether plaintext HTTP is allowed by host name.|
| [int32_t OH_Netstack_IsCleartextCfgByComponent(const char *component, bool *componentCfg)](#oh_netstack_iscleartextcfgbycomponent) | Checks whether plaintext HTTP interception is enabled.|
| [uint32_t OH_NetStack_CreateAndVerifySortedCertChain(const struct NetStack_CertBlob *cert, size_t certCount, const struct NetStack_CertBlob *caCert, const char *hostname, struct NetStack_CertBlob **outSortedChain, size_t *outSortedCount)](#oh_netstack_createandverifysortedcertchain) | Creates and verifies a certificate chain, and returns the sorted certificate chain. |
| [void OH_NetStack_FreeCertChain(struct NetStack_CertBlob *certChain, size_t certCount)](#oh_netstack_freecertchain) | Frees the certificate chain memory allocated by [OH_NetStack_CreateAndVerifySortedCertChain](#oh_netstack_createandverifysortedcertchain). |


## Function Description

### OH_NetStack_CertVerification()

```c
uint32_t OH_NetStack_CertVerification(const struct NetStack_CertBlob *cert, const struct NetStack_CertBlob *caCert)
```

**Description**

Provides certificate chain verification APIs for external systems.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *cert | Certificate to be verified.|
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *caCert |   Certificate specified by the user. If this parameter is left blank, the preset certificate is used for verification.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | **0**: Success.<br> **2305001**: Unknown error.<br> **2305002**: Failed to obtain the issuer certificate.<br> **2305003**: Failed to obtain the certificate revocation list (CRL).<br> **2305004**: Failed to decrypt the certificate signature.<br> **2305005**: Failed to decrypt the CRL signature.<br> **2305006**: Failed to decode the issuer public key.<br> **2305007**: Failed to sign the certificate.<br> **2305008**: Failed to sign the CRL.<br> **2305009**: Certificate not activated.<br> **2305010**: Certificate expired.<br> **2305011**: CRL not activated.<br> **2305012**: CRL expired.<br> **2305023**: Certificate revoked.<br> **2305024**: Invalid certificate authority (CA).<br> **2305027**: Untrusted certificate.|

### OH_NetStack_GetPinSetForHostName()

```c
int32_t OH_NetStack_GetPinSetForHostName(const char *hostname, NetStack_CertificatePinning *pin)
```

**Description**

Obtains the certificate lock information.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const char *hostname | Host name.|
| [NetStack_CertificatePinning](capi-netstack-netstack-certificatepinning.md) *pin | Defines the certificate lock information structure.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **0**: Success.<br>         **401**: Parameter error.<br>         **2305999**: Memory error.|

### OH_NetStack_GetCertificatesForHostName()

```c
int32_t OH_NetStack_GetCertificatesForHostName(const char *hostname, NetStack_Certificates *certs)
```

**Description**

Obtains the certificate information.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const char *hostname | Host name.|
| [NetStack_Certificates](capi-netstack-netstack-certificates.md) *certs | Defines the certificate information structure.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **0**: Success.<br>         **401**: Parameter error.<br>         **2305999**: Memory error.|

### OH_Netstack_DestroyCertificatesContent()

```c
void OH_Netstack_DestroyCertificatesContent(NetStack_Certificates *certs)
```

**Description**

Releases the certificate content.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [NetStack_Certificates](capi-netstack-netstack-certificates.md) *certs | Represents the certificate information.|

### OH_Netstack_IsCleartextPermitted()

```c
int32_t OH_Netstack_IsCleartextPermitted(bool *isCleartextPermitted)
```

**Description**

Boolean value indicating whether plaintext HTTP is allowed.

**Required permission**: ohos.permission.INTERNET

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| bool *isCleartextPermitted | Boolean value indicating whether plaintext HTTP is allowed. The value **true** means that plaintext HTTP is allowed, and the value **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **0**: Success.<br>         **201**: Permission denied.<br>         **401**: Parameter error.|

### OH_Netstack_IsCleartextPermittedByHostName()

```c
int32_t OH_Netstack_IsCleartextPermittedByHostName(const char *hostname, bool *isCleartextPermitted)
```

**Description**

Boolean value indicating whether host name–based plaintext HTTP is allowed.

**Required permission**: ohos.permission.INTERNET

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| const char *hostname | Host name.|
| bool *isCleartextPermitted | Boolean value indicating whether host name–based plaintext HTTP is allowed. The value **true** means that host name–based plaintext HTTP is allowed, and the value **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **0**: Success.<br>         **201**: Permission denied.<br>         **401**: Parameter error.|

### OH_Netstack_IsCleartextCfgByComponent()

```c
int32_t OH_Netstack_IsCleartextCfgByComponent(const char *component, bool *componentCfg)
```

**Description**

Checks whether plaintext HTTP interception is enabled.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| const char *component | Component name. The following components are supported: Network Kit and ArkWeb.|
| bool *componentCfg | Output parameter, which indicates whether plaintext HTTP interception is enabled. The value **true** indicates that plaintext HTTP interception is enabled, and the value **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **0**: Success.<br>         **2100001**: Invalid parameter value.|

### OH_NetStack_CreateAndVerifySortedCertChain()

```c
uint32_t OH_NetStack_CreateAndVerifySortedCertChain(
    const struct NetStack_CertBlob *cert,
    size_t certCount,
    const struct NetStack_CertBlob *caCert,
    const char *hostname,
    struct NetStack_CertBlob **outSortedChain,
    size_t *outSortedCount)
```

**Description**

Verifies the input certificate chain array and builds a sorted certificate chain from the leaf node to the root node.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Since:** 26.0.0


**Parameters**

| Name | Description |
| -- | -- |
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *cert | Array of certificates to verify. The first element (cert[0]) must be the end-entity certificate, and the remaining elements are intermediate certificates. |
| size_t certCount | Actual size of the certificate array **cert** to verify. |
| [const struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *caCert | CA certificate specified by the user. If **NULL** is passed, the system preset certificate is used for verification. |
| const char *hostname | Hostname to verify. If **NULL** is passed, hostname verification is skipped. |
| [struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) **outSortedChain | Output parameter, which is the sorted certificate chain (from the leaf node to the root node). The caller must release it using [OH_NetStack_FreeCertChain](#oh_netstack_freecertchain); otherwise, a memory leak occurs. |
| size_t *outSortedCount | Output parameter, which is the actual size of the sorted certificate chain **outSortedChain**. |

**Return**

| Type | Description |
| -- | -- |
| uint32_t | Result code.<br> **0**: Success.<br> **2305001**: Unspecified error.<br> **2305002**: Failed to obtain the issuer certificate.<br> **2305003**: Failed to obtain the certificate revocation list (CRL).<br> **2305004**: Failed to decrypt the certificate signature.<br> **2305005**: Failed to decrypt the CRL signature.<br> **2305006**: Failed to decode the issuer public key.<br> **2305007**: Certificate signature failed.<br> **2305008**: CRL signature failed.<br> **2305009**: The certificate is not yet valid.<br> **2305010**: The certificate has expired.<br> **2305011**: The CRL is not yet valid.<br> **2305012**: The CRL has expired.<br> **2305018**: Self-signed certificate.<br> **2305023**: The certificate has been revoked.<br> **2305024**: The certificate authority (CA) is invalid.<br> **2305027**: The certificate is not trusted.<br> **2305062**: Hostname verification failed.<br> **2305069**: Invalid certificate verification context. |

### OH_NetStack_FreeCertChain()

```c
void OH_NetStack_FreeCertChain(struct NetStack_CertBlob *certChain, size_t certCount)
```

**Description**

Frees the memory of the certificate chain allocated by [OH_NetStack_CreateAndVerifySortedCertChain](#oh_netstack_createandverifysortedcertchain).

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Since:** 26.0.0


**Parameters**

| Name | Description |
| -- | -- |
| [struct NetStack_CertBlob](capi-netstack-netstack-certblob.md) *certChain | Certificate chain returned by [OH_NetStack_CreateAndVerifySortedCertChain](#oh_netstack_createandverifysortedcertchain). |
| size_t certCount | Actual size of the certificate chain **certChain**. |
