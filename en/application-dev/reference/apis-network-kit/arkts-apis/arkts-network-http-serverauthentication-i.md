# ServerAuthentication

```TypeScript
export interface ServerAuthentication
```

Defines HTTP server identity verification information.

**Since:** 18

<!--Device-http-export interface ServerAuthentication--><!--Device-http-export interface ServerAuthentication-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## authenticationType

```TypeScript
authenticationType?: AuthenticationType
```

Server identity verification type. If the type is not set, negotiation with the server is required.

**Type:** [AuthenticationType](arkts-network-http-authenticationtype-t.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ServerAuthentication-authenticationType?: AuthenticationType--><!--Device-ServerAuthentication-authenticationType?: AuthenticationType-End-->

**System capability:** SystemCapability.Communication.NetStack

## credential

```TypeScript
credential: Credential
```

Server credential. The default value is **undefined**.

**Type:** [Credential](arkts-network-http-credential-i.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ServerAuthentication-credential: Credential--><!--Device-ServerAuthentication-credential: Credential-End-->

**System capability:** SystemCapability.Communication.NetStack
