# TlsConfig

```TypeScript
export interface TlsConfig
```

Defines the TLS configuration, including the version and cipher suite.

**Since:** 18

<!--Device-http-export interface TlsConfig--><!--Device-http-export interface TlsConfig-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## cipherSuites

```TypeScript
cipherSuites?: CipherSuite[]
```

Array of cipher suite types. If no cipher suite type is set, all supported cipher suite types are carried by default. For details about the cipher suite types, see [TlsV13SpecificCipherSuite](arkts-network-http-tlsv13specificciphersuite-t.md), [TlsV12SpecificCipherSuite](arkts-network-http-tlsv12specificciphersuite-t.md) and [TlsV10SpecificCipherSuite](arkts-network-http-tlsv10specificciphersuite-t.md).

**Type:** [CipherSuite](arkts-network-http-ciphersuite-t.md)[]

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-TlsConfig-cipherSuites?: CipherSuite[]--><!--Device-TlsConfig-cipherSuites?: CipherSuite[]-End-->

**System capability:** SystemCapability.Communication.NetStack

## tlsVersionMax

```TypeScript
tlsVersionMax: TlsVersion
```

Latest TLS version.

**Type:** [TlsVersion](arkts-network-http-tlsversion-e.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-TlsConfig-tlsVersionMax: TlsVersion--><!--Device-TlsConfig-tlsVersionMax: TlsVersion-End-->

**System capability:** SystemCapability.Communication.NetStack

## tlsVersionMin

```TypeScript
tlsVersionMin: TlsVersion
```

Earliest TLS version.

**Type:** [TlsVersion](arkts-network-http-tlsversion-e.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-TlsConfig-tlsVersionMin: TlsVersion--><!--Device-TlsConfig-tlsVersionMin: TlsVersion-End-->

**System capability:** SystemCapability.Communication.NetStack
