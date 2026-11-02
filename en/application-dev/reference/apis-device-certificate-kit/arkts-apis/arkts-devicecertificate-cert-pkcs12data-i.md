# Pkcs12Data

```TypeScript
interface Pkcs12Data
```

Represents the PKCS #12 data, including the private key, certificate, and other certificates.

**Since:** 18

<!--Device-cert-interface Pkcs12Data--><!--Device-cert-interface Pkcs12Data-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert?: X509Cert
```

Certificate that matches the private key.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-Pkcs12Data-cert?: X509Cert--><!--Device-Pkcs12Data-cert?: X509Cert-End-->

**System capability:** SystemCapability.Security.Cert

## otherCerts

```TypeScript
otherCerts?: Array<X509Cert>
```

Other certificates.

**Type:** Array&lt;[X509Cert](arkts-devicecertificate-cert-x509cert-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-Pkcs12Data-otherCerts?: Array<X509Cert>--><!--Device-Pkcs12Data-otherCerts?: Array<X509Cert>-End-->

**System capability:** SystemCapability.Security.Cert

## privateKey

```TypeScript
privateKey?: string | Uint8Array
```

Private key. The string is in PEM format, and the Uint8Array data is in DER format.

**Type:** string &#124; Uint8Array

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-Pkcs12Data-privateKey?: string | Uint8Array--><!--Device-Pkcs12Data-privateKey?: string | Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert
