# Credential

```TypeScript
export interface Credential
```

Represents the credential used for server identity verification in a session, including the user name and password.

**Since:** 18

<!--Device-http-export interface Credential--><!--Device-http-export interface Credential-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## password

```TypeScript
password: string
```

Password of credential. Default is ''.

**Type:** string

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Credential-password: string--><!--Device-Credential-password: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## username

```TypeScript
username: string
```

Username of credential. Default is ''.

**Type:** string

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-Credential-username: string--><!--Device-Credential-username: string-End-->

**System capability:** SystemCapability.Communication.NetStack
