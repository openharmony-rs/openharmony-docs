# AuthResult (System API)

```TypeScript
interface AuthResult
```

Represents the authorization results of all clients.

**Since:** 26.1.0

<!--Device-securityGuard-interface AuthResult--><!--Device-securityGuard-interface AuthResult-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## clientAuthResult

```TypeScript
clientAuthResult: ClientAuthResult[]
```

List of client authorization results.

**Type:** [ClientAuthResult](arkts-securityguard-securityguard-clientauthresult-i-sys.md)[]

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthResult-clientAuthResult: ClientAuthResult[]--><!--Device-AuthResult-clientAuthResult: ClientAuthResult[]-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## mergedAuthStrategy

```TypeScript
mergedAuthStrategy: AuthStrategy
```

Aggregated authorization policies of all clients.

**Type:** [AuthStrategy](arkts-securityguard-securityguard-authstrategy-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthResult-mergedAuthStrategy: AuthStrategy--><!--Device-AuthResult-mergedAuthStrategy: AuthStrategy-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
