# AuthClientInfo (System API)

```TypeScript
interface AuthClientInfo
```

Defines the client session information.

**Since:** 26.1.0

<!--Device-securityGuard-interface AuthClientInfo--><!--Device-securityGuard-interface AuthClientInfo-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## bundleName

```TypeScript
bundleName: string
```

App bundle name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthClientInfo-bundleName: string--><!--Device-AuthClientInfo-bundleName: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## clientId

```TypeScript
clientId: string
```

Unique ID of a client session.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthClientInfo-clientId: string--><!--Device-AuthClientInfo-clientId: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## defaultTimeoutMs

```TypeScript
defaultTimeoutMs: number
```

Client response timeout interval. Unit: millisecond.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthClientInfo-defaultTimeoutMs: number--><!--Device-AuthClientInfo-defaultTimeoutMs: number-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## defaultTimeoutStrategy

```TypeScript
defaultTimeoutStrategy: AuthStrategy
```

Default authorization policy upon timeout.

**Type:** [AuthStrategy](arkts-securityguard-securityguard-authstrategy-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthClientInfo-defaultTimeoutStrategy: AuthStrategy--><!--Device-AuthClientInfo-defaultTimeoutStrategy: AuthStrategy-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## subscribedEvents

```TypeScript
subscribedEvents: number[]
```

ID list of event types subscribed to by the client.

**Type:** number[]

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthClientInfo-subscribedEvents: number[]--><!--Device-AuthClientInfo-subscribedEvents: number[]-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
