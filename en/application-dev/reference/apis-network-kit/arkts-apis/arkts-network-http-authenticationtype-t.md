# AuthenticationType

```TypeScript
export type AuthenticationType = 'basic' | 'ntlm' | 'digest'
```

Enumerates server authentication modes in a session.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NetStack

| Type | Description |
| --- | --- |
| 'basic' | Basic authentication mode. This field has a fixed value of **basic**. |
| 'ntlm' | NTLM authentication mode. This field has a fixed value of **ntlm**. |
| 'digest' | Digest authentication mode. This field has a fixed value of **digest**. |
