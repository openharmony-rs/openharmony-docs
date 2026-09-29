# X509CertMatchParameters

```TypeScript
interface X509CertMatchParameters
```

Defines the parameters used to match a certificate. If no parameter is specified, all certificates are matched.

**Since:** 11

<!--Device-cert-interface X509CertMatchParameters--><!--Device-cert-interface X509CertMatchParameters-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## authorityKeyIdentifier

```TypeScript
authorityKeyIdentifier?: Uint8Array
```

Key of the certificate authority (CA).

**Type:** Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-authorityKeyIdentifier?: Uint8Array--><!--Device-X509CertMatchParameters-authorityKeyIdentifier?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## certPolicy

```TypeScript
certPolicy?: Array<string>
```

Certificate policy.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-certPolicy?: Array<string>--><!--Device-X509CertMatchParameters-certPolicy?: Array<string>-End-->

**System capability:** SystemCapability.Security.Cert

## extendedKeyUsage

```TypeScript
extendedKeyUsage?: Array<string>
```

Extended key usage.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-extendedKeyUsage?: Array<string>--><!--Device-X509CertMatchParameters-extendedKeyUsage?: Array<string>-End-->

**System capability:** SystemCapability.Security.Cert

## issuer

```TypeScript
issuer?: Uint8Array
```

Certificate issuer, in DER format.

**Type:** Uint8Array

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-issuer?: Uint8Array--><!--Device-X509CertMatchParameters-issuer?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## keyUsage

```TypeScript
keyUsage?: Array<boolean>
```

Whether to match the key usage. **true**: yes; **false**: no.

**Type:** Array&lt;boolean&gt;

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-keyUsage?: Array<boolean>--><!--Device-X509CertMatchParameters-keyUsage?: Array<boolean>-End-->

**System capability:** SystemCapability.Security.Cert

## matchAllSubjectAltNames

```TypeScript
matchAllSubjectAltNames?: boolean
```

Whether to match all SANs of the certificate. **true**: yes; **false**: no.

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-matchAllSubjectAltNames?: boolean--><!--Device-X509CertMatchParameters-matchAllSubjectAltNames?: boolean-End-->

**System capability:** SystemCapability.Security.Cert

## minPathLenConstraint

```TypeScript
minPathLenConstraint?: number
```

Minimum length of the certification path (chain of trust) that can be built from the certificate to a trusted root CA.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-minPathLenConstraint?: int--><!--Device-X509CertMatchParameters-minPathLenConstraint?: int-End-->

**System capability:** SystemCapability.Security.Cert

## nameConstraints

```TypeScript
nameConstraints?: Uint8Array
```

Constraints on the subject names that can be included in certificates.

**Type:** Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-nameConstraints?: Uint8Array--><!--Device-X509CertMatchParameters-nameConstraints?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## privateKey

```TypeScript
privateKey?: string | Uint8Array
```

Specifies the certificate private key. string indicates a private key in PEM format, and Uint8Array indicates a private key in DER format.

**Type:** string &#124; Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-X509CertMatchParameters-privateKey?: string | Uint8Array--><!--Device-X509CertMatchParameters-privateKey?: string | Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## privateKeyValid

```TypeScript
privateKeyValid?: string
```

Validity period of the certificate private key.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-privateKeyValid?: string--><!--Device-X509CertMatchParameters-privateKeyValid?: string-End-->

**System capability:** SystemCapability.Security.Cert

## publicKey

```TypeScript
publicKey?: DataBlob
```

Public key of the certificate, in DER format.

**Type:** [DataBlob](arkts-devicecertificate-cert-datablob-i.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-publicKey?: DataBlob--><!--Device-X509CertMatchParameters-publicKey?: DataBlob-End-->

**System capability:** SystemCapability.Security.Cert

## publicKeyAlgID

```TypeScript
publicKeyAlgID?: string
```

Algorithm of the certificate public key.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-publicKeyAlgID?: string--><!--Device-X509CertMatchParameters-publicKeyAlgID?: string-End-->

**System capability:** SystemCapability.Security.Cert

## serialNumber

```TypeScript
serialNumber?: bigint
```

Serial number of the certificate.

**Type:** bigint

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-serialNumber?: bigint--><!--Device-X509CertMatchParameters-serialNumber?: bigint-End-->

**System capability:** SystemCapability.Security.Cert

## subject

```TypeScript
subject?: Uint8Array
```

Certificate subject name, in DER format.

**Type:** Uint8Array

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-subject?: Uint8Array--><!--Device-X509CertMatchParameters-subject?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## subjectAlternativeNames

```TypeScript
subjectAlternativeNames?: Array<GeneralName>
```

Subject Alternative Names (SANs) of the certificate.

**Type:** Array&lt;[GeneralName](arkts-devicecertificate-cert-generalname-i.md)&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-subjectAlternativeNames?: Array<GeneralName>--><!--Device-X509CertMatchParameters-subjectAlternativeNames?: Array<GeneralName>-End-->

**System capability:** SystemCapability.Security.Cert

## subjectKeyIdentifier

```TypeScript
subjectKeyIdentifier?: Uint8Array
```

Identifier of the public key of the certificate's subject.

**Type:** Uint8Array

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-subjectKeyIdentifier?: Uint8Array--><!--Device-X509CertMatchParameters-subjectKeyIdentifier?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Cert

## validDate

```TypeScript
validDate?: string
```

Certificate validity period.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-validDate?: string--><!--Device-X509CertMatchParameters-validDate?: string-End-->

**System capability:** SystemCapability.Security.Cert

## x509Cert

```TypeScript
x509Cert?: X509Cert
```

Certificate object.

**Type:** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-X509CertMatchParameters-x509Cert?: X509Cert--><!--Device-X509CertMatchParameters-x509Cert?: X509Cert-End-->

**System capability:** SystemCapability.Security.Cert
