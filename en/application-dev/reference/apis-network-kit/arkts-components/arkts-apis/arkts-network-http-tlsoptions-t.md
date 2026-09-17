# TlsOptions

```TypeScript
export type TlsOptions = 'system' | TlsConfig
```

Defines the TLS configuration.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NetStack

| Type | Description |
| --- | --- |
| 'system' | TLS version of the system. This field is defaulted to **system** when the value is not set. |
| [TlsConfig](arkts-network-http-tlsconfig-i.md) | Custom TLS version and cipher suites. |
