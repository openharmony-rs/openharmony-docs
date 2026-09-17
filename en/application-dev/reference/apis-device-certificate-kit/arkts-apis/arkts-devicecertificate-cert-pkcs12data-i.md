# Pkcs12Data

P12(PKCS #12) data, which includes private key, certificate, and other certificates.

**Since:** 18

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert?: X509Cert
```

The certificate that matches the private key.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## otherCerts

```TypeScript
otherCerts?: Array<X509Cert>
```

Other certificates.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## privateKey

```TypeScript
privateKey?: string | Uint8Array
```

Private key. **string** corresponds to PEM format, and **Uint8Array** corresponds to DER format.

**Type:** string &#124; Uint8Array

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert
