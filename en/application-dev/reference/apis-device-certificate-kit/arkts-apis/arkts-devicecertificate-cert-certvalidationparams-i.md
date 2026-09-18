# CertValidationParams

Parameters for certificate validation.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## allowDownloadIntermediateCa

```TypeScript
allowDownloadIntermediateCa?: boolean
```

Whether to allow intermediate CA certificates to be downloaded from the network. The default value is **false**.  
- **true**: attempts to use the issuer address in the certificate AIA extension to download the issuer  
certificate when an intermediate certificate is missing in the certificate chain, resolving the incomplete certificate chain issue;  
- **false**: intermediate CA certificates cannot be downloaded from the network.  
<br>The download address is obtained from the certificate AIA extension. Only HTTP is supported. To use the network for download, you need to request the **ohos.permission.INTERNET** permission. For details about the permission configuration, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## date

```TypeScript
date?: string
```

Validation date, in the format of YYMMDDHHMMSSZ or YYYYMMDDHHMMSSZ. By default, the current system time is used. <br>Custom verification time is supported, which is applicable to scenarios such as offline verification of historical signatures.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## emailAddresses

```TypeScript
emailAddresses?: Array<string>
```

Email address list. Verify that the certificate contains the specified email address. The maximum number is 1. The maximum length of the email address is 128.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## hostnames

```TypeScript
hostnames?: Array<string>
```

List of hostnames. Verify that the certificate's subject alternative name (SAN) or common name (CN) contains the specified hostname. Maximum number: 100; maximum length of each host name: 128. <br>Verification is successful as long as one of the hostnames is matched.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## ignoreErrs

```TypeScript
ignoreErrs?: Array<CertResult>
```

Allows specific validation errors to be ignored. Maximum count: 8. <br>The errors that can be ignored include: ERR_CERT_NOT_YET_VALID, ERR_CERT_HAS_EXPIRED, ERR_UNKNOWN_CRITICAL_EXTENSION, ERR_CRL_NOT_FOUND, ERR_CRL_NOT_YET_VALID, ERR_CRL_HAS_EXPIRED, ERR_OCSP_RESPONSE_NOT_FOUND, ERR_NETWORK_TIMEOUT.

**Type:** Array&lt;[CertResult](arkts-devicecertificate-cert-certresult-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## keyUsage

```TypeScript
keyUsage?: Array<KeyUsageType>
```

Key usage list. Verify that the certificate's key usage extension includes the specified usage. Maximum count: 9. <br>The certificate must contain all specified key usages for verification to be successful.

**Type:** Array&lt;[KeyUsageType](arkts-devicecertificate-cert-keyusagetype-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## partialChain

```TypeScript
partialChain?: boolean
```

Whether to allow partial chain validation. The default value is **false**.  
- **true**: any certificate in the trusted certificates can be used as the trust anchor instead of the root  
certificate;  
- **false**: the root certificate must be traced during certificate chain construction.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## revokedParams

```TypeScript
revokedParams?: X509CertRevokedParams
```

Indicates the certificate revocation check parameter. Used to check whether a certificate is revoked. The configuration includes the CRL list, OCSP response data, and whether online check is allowed.

**Type:** [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## trustedCerts

```TypeScript
trustedCerts?: Array<X509Cert>
```

Trust certificate list. Specifies the trusted root certificate or intermediate CA certificate as the trust anchor for validation. Maximum count: 100. <br>During verification, the certificate chain must trace back to a trusted certificate. You must set this parameter or set trustSystemCa to true.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## trustSystemCa

```TypeScript
trustSystemCa?: boolean
```

Whether to trust the system CA. The default value is **false**.  
- **true**: uses the system preset CA certificate library as a trust anchor;  
- **false**: does not use the system preset CA certificate library as a trust anchor.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## untrustedCerts

```TypeScript
untrustedCerts?: Array<X509Cert>
```

Indicates the list of untrusted certificates. An intermediate certificate is used only to construct a certificate chain and is not used as a trust anchor. Maximum count: 100.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## userId

```TypeScript
userId?: Uint8Array
```

User ID. Used to set the user identifier required for signature verification when verifying the SM2 certificate. Maximum length: 128 characters. <br>The most commonly used value in the SM2 certificate scenario is [0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38, 0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38]. (The corresponding ASCII character string is 1234567812345678, 16 bytes.) Certificate revocation check is not supported after userId is set.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## validateDate

```TypeScript
validateDate?: boolean
```

Indicates whether to verify the date. true: Verify the validity period of the certificate and CRL. false: The validity period of the certificate and CRL is not verified.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert
