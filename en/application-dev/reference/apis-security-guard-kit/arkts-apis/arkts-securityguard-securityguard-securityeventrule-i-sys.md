# SecurityEventRule (System API)

```TypeScript
interface SecurityEventRule
```

Provides the conditions of querySecurityEvent.

@interface SecurityEventRule

**Since:** 12

<!--Device-securityGuard-interface SecurityEventRule--><!--Device-securityGuard-interface SecurityEventRule-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## beginTime

```TypeScript
beginTime?: string
```

The begin time, format is YYYYMMDDHHMMSS.

**Type:** string

**Since:** 12

<!--Device-SecurityEventRule-beginTime?: string--><!--Device-SecurityEventRule-beginTime?: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## endTime

```TypeScript
endTime?: string
```

The end time, format is YYYYMMDDHHMMSS.

**Type:** string

**Since:** 12

<!--Device-SecurityEventRule-endTime?: string--><!--Device-SecurityEventRule-endTime?: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## eventId

```TypeScript
eventId: number
```

The security event ids.

**Type:** number

**Since:** 12

<!--Device-SecurityEventRule-eventId: number--><!--Device-SecurityEventRule-eventId: number-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## param

```TypeScript
param?: string
```

The query condition.

**Type:** string

**Since:** 12

<!--Device-SecurityEventRule-param?: string--><!--Device-SecurityEventRule-param?: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
