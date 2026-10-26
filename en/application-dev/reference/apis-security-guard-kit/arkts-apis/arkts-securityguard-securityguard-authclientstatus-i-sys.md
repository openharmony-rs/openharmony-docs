# AuthClientStatus (System API)

```TypeScript
interface AuthClientStatus
```

Defines the client session status.

**Since:** 26.1.0

<!--Device-securityGuard-interface AuthClientStatus--><!--Device-securityGuard-interface AuthClientStatus-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## clientId

```TypeScript
clientId: string
```

Unique ID of a client session.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthClientStatus-clientId: string--><!--Device-AuthClientStatus-clientId: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## isDegraded

```TypeScript
isDegraded: boolean
```

Indicates whether an event is downgraded. A downgraded event is only reported, and the authorization result does not need to be received.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthClientStatus-isDegraded: boolean--><!--Device-AuthClientStatus-isDegraded: boolean-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
