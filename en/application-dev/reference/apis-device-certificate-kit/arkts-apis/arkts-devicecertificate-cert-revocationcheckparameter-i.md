# RevocationCheckParameter

```TypeScript
interface RevocationCheckParameter
```

Represents the parameters for checking the certificate revocation status for a certificate chain.

**Since:** 12

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## crlDownloadURI

```TypeScript
crlDownloadURI?: string
```

Address used to download the CRLs.

> **NOTE:** 
> 
> The URI takes effect only for the leaf certificate.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## ocspDigest

```TypeScript
ocspDigest?: string
```

Hash algorithm used to create a certificate ID during OCSP communication. The options **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, and **SHA512** are supported. The default value is **SHA256**.

**Type:** string

**Default:** SHA256

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## ocspRequestExtension

```TypeScript
ocspRequestExtension?: Array<Uint8Array>
```

OCSP request extensions.

**Type:** Array&lt;Uint8Array&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## ocspResponderCert

```TypeScript
ocspResponderCert?: X509Cert
```

Signing certificate used for verifying the signature of the OCSP response.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## ocspResponderURI

```TypeScript
ocspResponderURI?: string
```

URI of the alternative server used to send OCSP requests. HTTP and HTTPS are supported. The specific configuration is determined via the negotiation with the server.

> **NOTE:** 
> 
> The URI takes effect only for the leaf certificate.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## ocspResponses

```TypeScript
ocspResponses?: Uint8Array
```

Alternative OCSP responses.

**Type:** Uint8Array

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## options

```TypeScript
options?: Array<RevocationCheckOptions>
```

A set of rules for obtaining the certificate revocation status.

**Type:** Array&lt;[RevocationCheckOptions](arkts-devicecertificate-cert-revocationcheckoptions-e.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert
