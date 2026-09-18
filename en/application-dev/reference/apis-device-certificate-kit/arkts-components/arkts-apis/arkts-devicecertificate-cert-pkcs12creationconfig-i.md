# Pkcs12CreationConfig

Represents the configuration for creating .p12 files.

**Since:** 21

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certEncParams

```TypeScript
certEncParams?: PbesParams
```

Algorithm parameters for encrypting the certificate.

**Type:** [PbesParams](arkts-devicecertificate-cert-pbesparams-i.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Security.Cert

## encryptCert

```TypeScript
encryptCert?: boolean
```

Whether to encrypt the certificate. The default value is **true**. **true** means to encrypt the certificate; **false** otherwise.

**Type:** boolean

**Default:** true

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Security.Cert

## keyEncParams

```TypeScript
keyEncParams?: PbesParams
```

Algorithm parameters for encrypting the private key.

**Type:** [PbesParams](arkts-devicecertificate-cert-pbesparams-i.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Security.Cert

## macDigestAlgorithm

```TypeScript
macDigestAlgorithm?: Pkcs12MacDigestAlgorithm
```

MAC digest algorithm for the P12. The default value is **SHA256**.

**Type:** [Pkcs12MacDigestAlgorithm](arkts-devicecertificate-cert-pkcs12macdigestalgorithm-e.md)

**Default:** Pkcs12MacDigestAlgorithm.SHA256

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Security.Cert

## macIterations

```TypeScript
macIterations?: number
```

Number of P12 MAC iterations. The default value is **2048**. The value must be a positive integer.

**Type:** number

**Default:** 2048

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Security.Cert

## macSaltLen

```TypeScript
macSaltLen?: number
```

Length of the salt value of the P12 MAC. The minimum value is **8**, and the default value is **16**. The value must be an integer greater than or equal to 8.

**Type:** number

**Default:** 16

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Security.Cert

## password

```TypeScript
password: string
```

Password of the .p12 file. The minimum length is 4.

**Type:** string

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Security.Cert
