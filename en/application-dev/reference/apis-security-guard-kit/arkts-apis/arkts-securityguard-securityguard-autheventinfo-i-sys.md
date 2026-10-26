# AuthEventInfo (System API)

```TypeScript
interface AuthEventInfo
```

Defines the authorization event information.

**Since:** 26.1.0

<!--Device-securityGuard-interface AuthEventInfo--><!--Device-securityGuard-interface AuthEventInfo-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## clientStatus

```TypeScript
clientStatus?: AuthClientStatus[]
```

Client session status list.

**Type:** [AuthClientStatus](arkts-securityguard-securityguard-authclientstatus-i-sys.md)[]

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthEventInfo-clientStatus?: AuthClientStatus[]--><!--Device-AuthEventInfo-clientStatus?: AuthClientStatus[]-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## content

```TypeScript
content: string
```

Event content, in JSON string format.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthEventInfo-content: string--><!--Device-AuthEventInfo-content: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## eventId

```TypeScript
eventId: number
```

Event type ID.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthEventInfo-eventId: number--><!--Device-AuthEventInfo-eventId: number-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## version

```TypeScript
version: string
```

Event version number.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthEventInfo-version: string--><!--Device-AuthEventInfo-version: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
