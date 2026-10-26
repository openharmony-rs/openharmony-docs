# ClientAuthResult (System API)

```TypeScript
interface ClientAuthResult
```

Represents the authorization result of a single client.

**Since:** 26.1.0

<!--Device-securityGuard-interface ClientAuthResult--><!--Device-securityGuard-interface ClientAuthResult-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## authStrategy

```TypeScript
authStrategy: AuthStrategy
```

Authorization policy.

**Type:** [AuthStrategy](arkts-securityguard-securityguard-authstrategy-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ClientAuthResult-authStrategy: AuthStrategy--><!--Device-ClientAuthResult-authStrategy: AuthStrategy-End-->

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

<!--Device-ClientAuthResult-clientId: string--><!--Device-ClientAuthResult-clientId: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
