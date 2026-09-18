# SslType

```TypeScript
export type SslType = 'TLS' | 'TLCP'
```

Defines the secure communications protocol.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Communication.NetStack

| Type | Description |
| --- | --- |
| 'TLS' | TLS protocol. The value is fixed to **TLS**. |
| 'TLCP' | TLCP protocol. The value is fixed to **TLCP**.<br>**NOTE:** <br>(1) The certificate supports the following string specifications: <br> - UTF8String (English character set) <br> - PrintableString <br> - IA5String <br>Supported since API Version 22: <br> - TeletexString <br>(2) The certificate supports the following extended specifications: <br> - BasicConstraints (OID 2.5.29.19) <br> - KeyUsage (OID2.5.29.15) <br> - SubjectKeyIdentifier (OID2.5.29.14) <br> - AuthorityKeyIdentifier (OID2.5.29.35) <br>Supported since API Version 22: <br> - SubjectAltName (OID 2.5.29.17) <br> - ExtendedKeyUsage (OID 2.5.29.37) <br> |
