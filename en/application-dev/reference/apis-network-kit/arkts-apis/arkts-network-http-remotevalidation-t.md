# RemoteValidation

```TypeScript
export type RemoteValidation = 'system' | 'skip' | ValidationCallback
```

Enumerates the identity verification modes of the remote server.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NetStack

| Type | Description |
| --- | --- |
| 'system' | Use of the system CA. This field is defaulted to **system** when the value is not set. |
| 'skip' | Skipping of CA verification. This field has a fixed value of **skip**. |
| [ValidationCallback](arkts-network-http-validationcallback-t.md) | use custom validation. [since 26.0.0] |
