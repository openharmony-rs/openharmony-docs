# Pkcs12ParsingConfig

```TypeScript
interface Pkcs12ParsingConfig
```

Represents the configuration for parsing P12.

**Since:** 18

<!--Device-cert-interface Pkcs12ParsingConfig--><!--Device-cert-interface Pkcs12ParsingConfig-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## needsCert

```TypeScript
needsCert?: boolean
```

Whether to obtain the certificate. The default value is **true**. **true**: yes; **false**: no.

**Type:** boolean

**Default:** true

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Pkcs12ParsingConfig-needsCert?: boolean--><!--Device-Pkcs12ParsingConfig-needsCert?: boolean-End-->

**System capability:** SystemCapability.Security.Cert

## needsOtherCerts

```TypeScript
needsOtherCerts?: boolean
```

Whether to obtain other certificates. The default value is **false**. **true**: yes; **false**: no.

**Type:** boolean

**Default:** false

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Pkcs12ParsingConfig-needsOtherCerts?: boolean--><!--Device-Pkcs12ParsingConfig-needsOtherCerts?: boolean-End-->

**System capability:** SystemCapability.Security.Cert

## needsPrivateKey

```TypeScript
needsPrivateKey?: boolean
```

Whether to obtain the private key. The default value is **true**.

**true**: To obtain the private key in PKCS #8 format; **false**: Not to obtain the private key.

**Type:** boolean

**Default:** true

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Pkcs12ParsingConfig-needsPrivateKey?: boolean--><!--Device-Pkcs12ParsingConfig-needsPrivateKey?: boolean-End-->

**System capability:** SystemCapability.Security.Cert

## password

```TypeScript
password: string
```

Password.

**Type:** string

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Pkcs12ParsingConfig-password: string--><!--Device-Pkcs12ParsingConfig-password: string-End-->

**System capability:** SystemCapability.Security.Cert

## privateKeyFormat

```TypeScript
privateKeyFormat?: EncodingBaseFormat
```

Format of the private key to be obtained. Currently, the PEM and DER formats are supported. If this parameter is not specified, the PEM format is used by default.

> **NOTE:** 
> 
> This parameter is valid only when **needsPrivateKey** is set to **true**.

**Type:** [EncodingBaseFormat](arkts-devicecertificate-cert-encodingbaseformat-e.md)

**Default:** EncodingBaseFormat.PEM

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Pkcs12ParsingConfig-privateKeyFormat?: EncodingBaseFormat--><!--Device-Pkcs12ParsingConfig-privateKeyFormat?: EncodingBaseFormat-End-->

**System capability:** SystemCapability.Security.Cert
